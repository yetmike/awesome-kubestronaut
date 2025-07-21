# Cluster Setup

## Table of Contents
1. [Using Network Policies to Restrict Pod-to-Pod Communication](#using-network-policies-to-restrict-pod-to-pod-communication)
2. [Use CIS Benchmark to Review the Security Configuration of Kubernetes Components](#use-cis-benchmark-to-review-the-security-configuration-of-kubernetes-components)
3. [Properly Set Up Ingress with TLS](#properly-set-up-ingress-with-tls)
4. [Protect Node Metadata and Endpoints](#protect-node-metadata-and-endpoints)
5. [Verify Platform Binaries Before Deploying](#verify-platform-binaries-before-deploying)

---

## Using Network Policies to Restrict Pod-to-Pod Communication

NetworkPolicies are Kubernetes resources that restrict network communication between Pods, similar to how `iptables` works in Linux. Refer to the [Network Policies Documentation](https://kubernetes.io/docs/concepts/services-networking/network-policies/) for detailed information.

You can use tools like [editor.networkpolicy.io](https://editor.networkpolicy.io/) to visually build and learn about NetworkPolicies.

### Example Task

Create basic NetworkPolicies for a frontend, backend, and database setup:
- **Frontend**: Accepts any traffic and communicates with the backend.
- **Backend**: Accepts traffic only from the frontend on port 8080 and initiates connections to the database.
- **Database**: Accepts traffic only from the backend on port 3306.

Place all three components in different namespaces and ensure traffic flows only as described.

### Deny All Ingress Traffic

To deny all ingress traffic, use the following NetworkPolicy:

```yaml
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: deny-all-ingress
spec:
  podSelector: {} # Applies to all Pods
  policyTypes:
    - Ingress
```

### Deny Egress Traffic to External Domains

To deny egress traffic to any domain outside the cluster while allowing DNS traffic (port 53 for UDP and TCP) to Pods in any namespace:

```yaml
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: deny-egress-external
spec:
  podSelector:
    matchLabels:
      app: backend
  policyTypes:
    - Egress
  egress:
    - ports:
        - protocol: UDP
          port: 53
        - protocol: TCP
          port: 53
```

### Deny Access to Metadata Server (AWS Example)

To deny access to the metadata server on AWS:

```yaml
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: deny-egress-metadata-server
spec:
  podSelector: {}
  policyTypes:
    - Egress
  egress:
    - to:
        - ipBlock:
            cidr: 0.0.0.0/0
            except:
              - 169.254.169.254/32
```

---

## Use CIS Benchmark to Review the Security Configuration of Kubernetes Components

The [CIS Kubernetes Benchmark](https://www.cisecurity.org/benchmark/kubernetes) provides security best practices for Kubernetes components like `etcd`, `kubelet`, `kubedns`, and `kubeapi`.

### Using kube-bench

[kube-bench](https://github.com/aquasecurity/kube-bench) is an open-source tool that checks your cluster against CIS Benchmarks. To run it as a Kubernetes job:

```bash
kubectl apply -f https://raw.githubusercontent.com/aquasecurity/kube-bench/refs/heads/main/job.yaml
```

After the job finishes, view the logs to see how many checks your cluster has passed. The CIS Benchmark document includes remediation steps for any failed checks.

> **Task**:
> - Run kube-bench against your cluster and fix several identified issues.

---

## Properly Set Up Ingress with TLS

Ingress resources expose HTTP and HTTPS routes to services within the cluster. Refer to the [Ingress Documentation](https://kubernetes.io/docs/concepts/services-networking/ingress/) and the [TLS Section](https://kubernetes.io/docs/concepts/services-networking/ingress/#tls) for more details.

### Example Task

Create an Ingress resource to expose HTTPS traffic (port 443) with a custom certificate for an Nginx deployment.

1. Generate a certificate and key using OpenSSL:
   ```bash
   openssl req -nodes -new -x509 \
     -keyout nginx.key \
     -out nginx.crt \
     -subj "/CN=nginx.tls"
   ```

2. Create a Kubernetes secret for the certificate:
   ```yaml
   apiVersion: v1
   kind: Secret
   metadata:
     name: nginx-cert
   type: kubernetes.io/tls
   data:
     tls.crt: <base64 encoded cert>
     tls.key: <base64 encoded key>
   ```

3. Use the secret in an Ingress resource:
   ```yaml
   apiVersion: networking.k8s.io/v1
   kind: Ingress
   metadata:
     name: nginx-ingress
     annotations:
       nginx.ingress.kubernetes.io/rewrite-target: /
   spec:
     tls:
     - hosts:
       - nginx.tls
       secretName: nginx-cert
     rules:
     - host: nginx.tls
       http:
         paths:
         - path: /
           pathType: Prefix
           backend:
             service:
               name: nginx-service
               port:
                 number: 80
   ```

> **Task**:
> - Test the Ingress to ensure it correctly routes HTTPS traffic to the Nginx server.

---

## Protect Node Metadata and Endpoints

### Protect Metadata Server

Use a NetworkPolicy to block access to the metadata server (e.g., AWS EC2 instance profile IAM roles). Refer to the example in the [Deny Access to Metadata Server](#deny-access-to-metadata-server-aws-example) section.

### Secure Kubernetes Dashboard

If your cluster uses the Kubernetes Dashboard:
- Ensure it does not allow anonymous access.
- Avoid using insecure arguments like `--insecure-port` and `--enable-insecure-login`.

Refer to the [Kubernetes Dashboard Documentation](https://kubernetes.io/docs/tasks/access-application-cluster/web-ui-dashboard/) for more details.

---

## Verify Platform Binaries Before Deploying

Follow the [Download Kubernetes](https://kubernetes.io/releases/download/) page to learn how to download and verify binaries.

### Example Task

1. Download the binary for the Kubernetes API server:
   ```bash
   curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kube-apiserver"
   ```

2. Download the checksum file:
   ```bash
   curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kube-apiserver.sha256"
   ```

3. Verify the binary:
   ```bash
   echo "$(cat kube-apiserver.sha256)  kube-apiserver" | sha256sum --check
   ```

> **Task**:
> - Download the latest Kubernetes API server binary for Linux AMD64 and verify it using `sha256sum`.
