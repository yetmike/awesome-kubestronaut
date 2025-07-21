# Cluster Hardening

## Table of Contents
1. [Use Role Based Access Control to Minimize Exposure](#use-role-based-access-control-to-minimize-exposure)
2. [Exercise Caution in Using Service Accounts](#exercise-caution-in-using-service-accounts)
3. [Restrict Access to Kubernetes API](#restrict-access-to-kubernetes-api)
4. [Upgrade Kubernetes to Avoid Vulnerabilities](#upgrade-kubernetes-to-avoid-vulnerabilities)

---

## Use Role Based Access Control to Minimize Exposure

Role-Based Access Control (RBAC) is a mechanism in Kubernetes to control access to resources based on roles assigned to users, groups, or service accounts. RBAC policies are defined using `Role`, `ClusterRole`, `RoleBinding`, and `ClusterRoleBinding` resources.

### Role and RoleBinding

- A `Role` defines permissions within a specific namespace.
- A `RoleBinding` grants the permissions defined in a `Role` to a user, group, or service account.

Example:
```yaml
apiVersion: rbac.authorization.k8s.io/v1
kind: Role
metadata:
  namespace: default
  name: pod-reader
rules:
- apiGroups: [""]
  resources: ["pods"]
  verbs: ["get", "list"]
---
apiVersion: rbac.authorization.k8s.io/v1
kind: RoleBinding
metadata:
  name: read-pods
  namespace: default
subjects:
- kind: User
  name: alice
  apiGroup: rbac.authorization.k8s.io
roleRef:
  kind: Role
  name: pod-reader
  apiGroup: rbac.authorization.k8s.io
```

### ClusterRole and ClusterRoleBinding

- A `ClusterRole` defines permissions across the entire cluster.
- A `ClusterRoleBinding` grants the permissions defined in a `ClusterRole` to a user, group, or service account.

Example:
```yaml
apiVersion: rbac.authorization.k8s.io/v1
kind: ClusterRole
metadata:
  name: cluster-admin
rules:
- apiGroups: ["*"]
  resources: ["*"]
  verbs: ["*"]
---
apiVersion: rbac.authorization.k8s.io/v1
kind: ClusterRoleBinding
metadata:
  name: cluster-admin-binding
subjects:
- kind: User
  name: admin
  apiGroup: rbac.authorization.k8s.io
roleRef:
  kind: ClusterRole
  name: cluster-admin
  apiGroup: rbac.authorization.k8s.io
```

> **Task**:
> - Create a `Role` and `RoleBinding` to allow a user to list Pods in the `default` namespace.
> - Create a `ClusterRole` and `ClusterRoleBinding` to allow a user to manage all resources in the cluster.

Refer to the [RBAC Documentation](https://kubernetes.io/docs/reference/access-authn-authz/rbac/) for more details.

---

## Exercise Caution in Using Service Accounts

Apart from client certificates, the kube-apiserver can be accessed with service account tokens. Follow these best practices:

### Disable Default Service Account Tokens

By default, Pods use the `default` service account in their namespace. Disable token automounting for the default service account:
```bash
kubectl patch serviceaccount default -n default -p '{"automountServiceAccountToken": false}'
```

### Minimize Permissions for Service Accounts

- Create a dedicated service account with limited permissions:
  ```bash
  kubectl create serviceaccount custom-sa -n default
  ```

- Bind the service account to a specific role:
  ```yaml
  apiVersion: rbac.authorization.k8s.io/v1
  kind: RoleBinding
  metadata:
    name: custom-sa-binding
    namespace: default
  subjects:
  - kind: ServiceAccount
    name: custom-sa
    namespace: default
  roleRef:
    kind: Role
    name: pod-reader
    apiGroup: rbac.authorization.k8s.io
  ```

### Issue Tokens for Service Accounts

Generate a token for a service account:
```bash
kubectl create token custom-sa --namespace default
```

> **Task**:
> - Disable the automount of service account tokens for the default service account in the `default` namespace.
> - Create a service account with minimal permissions to list Pods in the `default` namespace.

---

## Restrict Access to Kubernetes API

To restrict access to the Kubernetes API:

### Transport Security

- Ensure the kube-apiserver is running with `--secure-port` and `--bind-address` configured to use a secure interface.
- Use TLS certificates for authentication.

### Authentication and Authorization

- Use RBAC to control access to resources.
- Example of a kubeconfig file for a user:
  ```yaml
  apiVersion: v1
  kind: Config
  users:
  - name: alice
    user:
      client-certificate: /home/alice/.kube/alice.crt
      client-key: /home/alice/.kube/alice.key
  clusters:
  - name: prod-cluster
    cluster:
      server: https://prod.example.com:6443
      certificate-authority: /home/alice/.kube/prod-ca.crt
  contexts:
  - name: alice@prod
    context:
      user: alice
      cluster: prod-cluster
  current-context: alice@prod
  ```

### Admission Controllers

Use admission controllers to enforce policies, such as disabling automounting of service account tokens.

> **Task**:
> - Create a user `Alice` with a client certificate and configure kubeconfig for her to manage Pods in the `default` namespace.

Refer to the [Controlling Access to the Kubernetes API](https://kubernetes.io/docs/concepts/security/controlling-access/) for more details.

---

## Upgrade Kubernetes to Avoid Vulnerabilities

To avoid potential security issues, upgrade Kubernetes nodes regularly. Follow these steps:

### Control Plane Nodes

1. Determine the upgrade version.
2. Install the new `kubeadm` version:
   ```bash
   sudo apt-get install -y kubeadm=<version>
   ```
3. Plan the upgrade:
   ```bash
   kubeadm upgrade plan
   ```
4. Apply the upgrade:
   ```bash
   kubeadm upgrade apply <version>
   ```
5. Drain the node:
   ```bash
   kubectl drain <node-name> --ignore-daemonsets
   ```
6. Upgrade and restart `kubelet`:
   ```bash
   sudo apt-get install -y kubelet=<version>
   sudo systemctl restart kubelet
   ```
7. Uncordon the node:
   ```bash
   kubectl uncordon <node-name>
   ```

### Worker Nodes

1. Install the new `kubeadm` version:
   ```bash
   sudo apt-get install -y kubeadm=<version>
   ```
2. Upgrade the node:
   ```bash
   kubeadm upgrade node
   ```
3. Drain the node:
   ```bash
   kubectl drain <node-name> --ignore-daemonsets
   ```
4. Upgrade and restart `kubelet`:
   ```bash
   sudo apt-get install -y kubelet=<version>
   sudo systemctl restart kubelet
   ```
5. Uncordon the node:
   ```bash
   kubectl uncordon <node-name>
   ```

> **Task**:
> - Upgrade a cluster from version 1.30 to 1.31 for both control plane and worker nodes.

Refer to the [Upgrade kubeadm clusters](https://kubernetes.io/docs/tasks/administer-cluster/kubeadm/kubeadm-upgrade/) and [Upgrade Linux nodes](https://kubernetes.io/docs/tasks/administer-cluster/kubeadm/upgrading-linux-nodes/) for more details.
