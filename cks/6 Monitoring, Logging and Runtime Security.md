# Monitoring, Logging, and Runtime Security

## Table of Contents
1. [Perform Behavioral Analytics to Detect Malicious Activities](#perform-behavioral-analytics-to-detect-malicious-activities)
2. [Detect Threats Within Physical Infrastructure, Apps, Networks, Data, Users, and Workloads](#detect-threats-within-physical-infrastructure-apps-networks-data-users-and-workloads)
3. [Investigate and Identify Phases of Attack and Bad Actors Within the Environment](#investigate-and-identify-phases-of-attack-and-bad-actors-within-the-environment)
4. [Ensure Immutability of Containers at Runtime](#ensure-immutability-of-containers-at-runtime)
5. [Use Kubernetes Audit Logs to Monitor Access](#use-kubernetes-audit-logs-to-monitor-access)

---

## Perform Behavioral Analytics to Detect Malicious Activities

Behavioral analytics involves monitoring and analyzing patterns of activity to detect anomalies that may indicate malicious behavior.

• Use **Falco** to monitor system calls and detect suspicious activities such as privilege escalation, unexpected file access, or execution of binaries not in the container image. Refer to the [Falco Documentation](https://falco.org/docs/) for installation and usage.

• Use `strace` to identify system calls made by a process and create custom Falco rules based on the observed behavior:
  - Run `strace` on a containerized process:
    ```bash
    kubectl exec -it <pod-name> -- strace -c -p <pid>
    ```
  - Analyze the output to identify suspicious system calls.
  - Create a custom Falco rule to detect those calls.

---

## Detect Threats Within Physical Infrastructure, Apps, Networks, Data, Users, and Workloads

To detect threats:

• Use **Falco** to monitor workloads and detect anomalies in system calls.

• Use **Trivy** to scan container images for vulnerabilities:
  ```bash
  trivy image <image-name>
  ```

• Use `ss` or `netstat` to identify open ports:
  - Using `ss`:
    ```bash
    ss -tuln
    ```
  - Using `netstat`:
    ```bash
    netstat -tuln
    ```
  - Use `ps aux | grep <pid>` to identify the processes associated with open ports.

---

## Investigate and Identify Phases of Attack and Bad Actors Within the Environment

To investigate attacks:

• Enable **Kubernetes audit logs** to trace actions performed by users or service accounts. Learn how to configure audit logs [here](https://kubernetes.io/docs/tasks/debug/debug-cluster/audit/).

• Use **Falco** to identify system calls or actions that triggered alerts.

• Use tools like **kubectl logs** and **kubectl describe** to investigate Pod behavior:
  ```bash
  kubectl logs <pod-name>
  kubectl describe pod <pod-name>
  ```

---

## Ensure Immutability of Containers at Runtime

Containers are mutable by default. Enforce immutability to enhance security:

• Use **distroless images** to minimize the attack surface. These images lack shells, package managers, and other unnecessary components. Refer to the [Distroless Documentation](https://github.com/GoogleContainerTools/distroless).

• Prevent write access to the container's filesystem by setting `spec.containers[].securityContext.readOnlyRootFilesystem` to `true`.

Example:
```yaml
apiVersion: v1
kind: Pod
metadata:
  name: immutable-container
spec:
  containers:
    - name: app
      image: gcr.io/distroless/nodejs:16
      securityContext:
        readOnlyRootFilesystem: true
```

• Use `Secrets` and `ConfigMaps` to manage environment variables or configuration files. Mount them as read-only volumes:
  ```yaml
  volumeMounts:
    - name: config-volume
      mountPath: /etc/config
      readOnly: true
  ```

---

## Use Kubernetes Audit Logs to Monitor Access

Kubernetes audit logs are essential for monitoring access and detecting unauthorized actions.

• Audit logs store records of events in JSON format, including:
  - Time when the event was triggered.
  - Type of the event.
  - Who triggered the event.
  - What Kubernetes component handled the request.

• Define audit policy rules with the following levels:
  1. **None**: Do not log events matching this rule.
  2. **Metadata**: Log only metadata for the event.
  3. **Request**: Log metadata and the request body.
  4. **RequestResponse**: Log metadata, request, and response body.

Example audit policy:
```yaml
apiVersion: audit.k8s.io/v1
kind: Policy
omitStages:
  - RequestReceived
rules:
  - level: RequestResponse
    resources:
      - group: ""
        resources: ["pods"]
  - level: Metadata
    resources:
      - group: ""
        resources: ["pods/log", "pods/status"]
  - level: None
    resources:
      - group: ""
        resources: ["secrets"]
```

• Configure a log backend:
  1. Specify `--audit-policy-file` pointing to the audit policy file.
  2. Specify `--audit-log-path` pointing to the log output file.
  3. Create and mount volumes for in/out files.

Refer to the [Audit Logs Documentation](https://kubernetes.io/docs/tasks/debug/debug-cluster/audit/) for more details.

> **Task**:
> - Create an audit policy to log all `update` actions for ConfigMaps and Secrets.
> - Analyze the audit logs to identify any unauthorized access attempts.

