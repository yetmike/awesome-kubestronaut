# Supply Chain Security

## Table of Contents
1. [Minimize Base Image Footprint](#minimize-base-image-footprint)
2. [Understand Your Supply Chain (e.g., SBOM, CI/CD, Artifact Repository)](#understand-your-supply-chain-eg-sbom-cicd-artifact-repository)
3. [Secure Your Supply Chain (Permitted Registries, Sign and Validate Artifacts, etc.)](#secure-your-supply-chain-permitted-registries-sign-and-validate-artifacts-etc)
4. [Perform Static Analysis of User Workloads and Container Images](#perform-static-analysis-of-user-workloads-and-container-images)

---

## Minimize Base Image Footprint

In this section, you need to be able to create small container images with a reduced attack surface. For Docker best practices, refer to the [Docker Best Practices Documentation](https://docs.docker.com/build/building-best-practices/).

### Steps to Minimize Base Image Footprint

1. **Choose the Smallest Image**:
   - Pick the smallest image that still meets your needs. For example, use `alpine` instead of `ubuntu`. Avoid using the `latest` tag; instead, specify a version and update it regularly.

2. **Use Multi-Stage Builds**:
   - Multi-stage builds allow you to use multiple `FROM` directives. The first stage is used for building the application (e.g., compiling code), and the second stage is used to copy only the necessary components (e.g., binaries, libraries) into the final image. This reduces the attack surface.

   Example of a multi-stage build:
   ```dockerfile
   # Stage 1: Build
   FROM golang:1.21 AS builder
   WORKDIR /app
   COPY . .
   RUN go build -o app

   # Stage 2: Final image
   FROM alpine:3.18
   WORKDIR /app
   COPY --from=builder /app/app .
   CMD ["./app"]
   ```

3. **Minimize Layers**:
   - Each `RUN`, `COPY`, and `CMD` directive creates a new layer. Combine commands to reduce the number of layers.

   Instead of this:
   ```dockerfile
   FROM ubuntu:22.10
   RUN apt update -y
   RUN apt upgrade -y
   RUN apt install -y curl
   ```

   Do this:
   ```dockerfile
   FROM ubuntu:22.10
   RUN apt update -y && apt upgrade -y && apt install -y curl
   ```

> **Task**:
> - Optimize the following Dockerfile to reduce its image footprint. Compare the image size before and after applying best practices.
   ```dockerfile
   FROM node:latest
   ENV NODE_ENV development
   WORKDIR /app
   COPY package.json .
   RUN npm install
   COPY . .
   EXPOSE 3001
   CMD ["node", "app.js"]
   ```

---

## Understand Your Supply Chain (e.g., SBOM, CI/CD, Artifact Repository)

To understand your supply chain, you need to be familiar with tools that generate a Software Bill of Materials (SBOM) and analyze dependencies.

### SBOM Tools

1. Use tools like **Syft** or **Trivy** to generate SBOMs in formats like JSON or SPDX.
   - Example with Trivy:
     ```bash
     trivy sbom --format spdx-json --output sbom.json nginx:1.23
     ```
     Refer to the [Trivy Documentation](https://aquasecurity.github.io/trivy/) for more details.

   - Example with `bom`:
     ```bash
     bom generate -i nginx:1.23 -o sbom.json
     ```
     This command generates an SBOM for the specified container image and outputs it in JSON format. Refer to the [bom GitHub Repository](https://github.com/kubernetes-sigs/bom) for more details.

> **Task**:
> - Generate an SBOM for the `nginx:1.23` container image using Trivy and analyze its contents.
> - Generate an SBOM using `bom` for the same image and explore its output.

---

## Secure Your Supply Chain (Permitted Registries, Sign and Validate Artifacts, etc.)

To secure your supply chain:

### Restrict Registries

Use admission controllers like **OPA Gatekeeper** or **Kyverno** to enforce policies that allow images only from permitted registries.

- Example Kyverno policy to allow only `gcr.io`:
  ```yaml
  apiVersion: kyverno.io/v1
  kind: ClusterPolicy
  metadata:
    name: allowed-repos
  spec:
    rules:
      - name: validate-image-repo
        match:
          resources:
            kinds:
              - Pod
        validate:
          message: "Images must be from gcr.io"
          pattern:
            spec:
              containers:
                - image: "gcr.io/*"
  ```
  Refer to the [Kyverno Documentation](https://kyverno.io/docs/) for more details.

### Sign and Validate Images

Use tools like **Cosign** to sign and verify container images.

- Example of signing an image:
  ```bash
  cosign sign --key cosign.key nginx:1.23
  ```

- Example of verifying an image:
  ```bash
  cosign verify --key cosign.pub nginx:1.23
  ```

> **Task**:
> - Install OPA Gatekeeper and create a policy to allow images only from `gcr.io`. Test it.
> - Repeat the same task using Kyverno. Refer to the [Kyverno Documentation](https://kyverno.io/docs/) for guidance.
> - Sign the `nginx:1.23` container image using Cosign and verify its signature.
> - Run a Pod with a `busybox` container. Retrieve its digest from Docker Hub and verify that the digest matches the one in your cluster using `kubectl describe pod`.

---

## Perform Static Analysis of User Workloads and Container Images

Static analysis tools help identify misconfigurations and vulnerabilities in Kubernetes manifests and container images.

### Tools for Static Analysis

1. **Kubesec**:
   - Use **Kubesec** to analyze Kubernetes manifests for security risks.
   - Example:
     ```bash
     kubesec scan deployment.yaml
     ```
     Refer to the [Kubesec GitHub Repository](https://github.com/controlplaneio/kubesec) for more details.

2. **KubeLinter**:
   - Use **KubeLinter** to lint Kubernetes YAML files and identify potential issues.
   - Example:
     ```bash
     kubelinter lint deployment.yaml
     ```
     Refer to the [KubeLinter GitHub Repository](https://github.com/stackrox/kube-linter) for more details.

> **Task**:
> - Create a Kubernetes Deployment manifest for an `nginx:1.23` container and use Kubesec to scan it. Review the results, try to mitigate security issues.
> - Use KubeLinter to lint the same Deployment YAML file and fix any issues reported.
