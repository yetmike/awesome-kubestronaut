# Awesome Kubestronaut

A curated and opinionated list of resources to help you ace Kubernetes certifications and achieve the title of (Golden) Kubestronaut. This list includes study materials, hands-on labs, and success stories to guide your journey.

## Contents
 * [Introduction](#introduction)
 * [Certified Kubernetes Administrator (CKA)](#certified-kubernetes-administrator-cka)
 * [Certified Kubernetes Application Developer (CKAD)](#certified-kubernetes-application-developer-ckad)
 * [Certified Kubernetes Security Specialist (CKS)](#certified-kubernetes-security-specialist-cks)
 * [Certified GitOps Associate (CGOA)](#certified-gitops-associate-cgoa)
 * [Certified Argo Project Associate (CAPA)](#certified-argo-project-associate-capa)
 * [Certified Backstage Associate (CBA)](#certified-backstage-associate-cba)
 * [Certified Cloud Native Platform Engineering Associate (CNPA)](#certified-cloud-native-platform-engineering-associate-cnpa)
 * [Cilium Certified Associate (CCA)](#cilium-certified-associate-cca)
 * [Kyverno Certified Associate (KCA)](#kyverno-certified-associate-kca)
 * [Kubernetes and Cloud Native Associate (KCNA)](#kubernetes-and-cloud-native-associate-kcna)
 * [Kubernetes and Cloud Security Associate (KCSA)](#kubernetes-and-cloud-security-associate)
 * [OpenTelemetry Certified Associate (OTCA)](#opentelemetry-certified-associate-otca)
 * [Prometheus Certified Associate (PCA)](#prometheus-certified-associate-pca)
 * [Istio Certified Associate (ICA)](#istio-certified-associate-ica)
 * [Certified Cloud Native Platform Engineer (CNPE)](#certified-cloud-native-platform-engineer-cnpe)

## Introduction

Kubernetes is the de facto standard for container orchestration, and earning a Kubernetes certification can significantly boost your career. This repository is designed to help you navigate the learning path, prepare for certifications, and gain practical experience.

## Certified Kubernetes Administrator (CKA)

### Courses
 * [CKA Certification Course – Certified Kubernetes Administrator](https://kodekloud.com/courses/cka-certification-course-certified-kubernetes-administrator/) on KodeKloud
 * [Certified Kubernetes Administrator (CKA) with Practice Tests](https://www.udemy.com/course/certified-kubernetes-administrator-with-practice-tests/?couponCode=LETSLEARNNOW) on Udemy

### Hands-On Labs
- [killer.sh/cka](https://killer.sh/cka) mock exam
- [killercoda.com/cka](https://killercoda.com/cka) labs

### Documentation, Tips and Tricks
 * [Kubernetes Cheat Sheet](https://kubernetes.io/docs/reference/kubectl/cheatsheet/)

### Books
- TBD

### Articles
 * TBD

## Certified Kubernetes Application Developer (CKAD)

### Courses
 * [Certified Kubernetes Application Developer (CKAD)](https://kodekloud.com/courses/certified-kubernetes-application-developer-ckad/) on KodeKloud
 * [Kubernetes Certified Application Developer (CKAD) with Tests](https://www.udemy.com/course/certified-kubernetes-application-developer/?couponCode=LETSLEARNNOW) on Udemy

### Hands-On Labs
* [killer.sh/ckad](https://killer.sh/ckad) mock exam
- self-hosted [CKAD-exercises](https://github.com/dgkanatsios/CKAD-exercises)
- [killercoda.com/ckad](https://killercoda.com/ckad) labs

### Documentation, Tips and Tricks
 * [Kubernetes Cheat Sheet](https://kubernetes.io/docs/reference/kubectl/cheatsheet/)

### Books
- TBD

### Articles
 * TBD

## Certified Kubernetes Security Specialist (CKS)

### Courses
 * [Kubernetes CKS Full Course Theory + Practice + Browser Scenarios](https://youtu.be/d9xfB5qaOfg?feature=shared) on YouTube


### Hands-On Labs
- [Self-paced preparation](./cks/README.md)
- [killer.sh/cks](https://killer.sh/cks)
- [killercoda.com/killer-shell-cks](https://killercoda.com/killer-shell-cks) labs

### Documentation, Tips and Tricks
 * [Kubernetes Cheat Sheet](https://kubernetes.io/docs/reference/kubectl/cheatsheet/)
 * [Kubernetes Components](https://kubernetes.io/docs/concepts/overview/components/)
 * [PKI certificates and requirements](https://kubernetes.io/docs/setup/best-practices/certificates/)
 * [Network Policies](https://kubernetes.io/docs/concepts/services-networking/network-policies/)
 * [Using RBAC Authorization](https://kubernetes.io/docs/reference/access-authn-authz/rbac/)
 * [Docker. Best practices](https://docs.docker.com/build/building/best-practices/)
 * [Auditing](https://kubernetes.io/docs/tasks/debug/debug-cluster/audit/)
 * [Restricting Container's Access to Resources with AppArmor](https://kubernetes.io/docs/tutorials/security/apparmor/)
 * [Restricting a Container's Syscalls with seccomp](https://kubernetes.io/docs/tutorials/security/seccomp/)
 * [Admission Control in Kubernetes](https://kubernetes.io/docs/reference/access-authn-authz/admission-controllers/)

### Books
- [Certified Kubernetes Security Specialist (CKS) Study Guide: In-Depth Guidance and Practice](https://www.amazon.com/Certified-Kubernetes-Security-Specialist-Depth/dp/1098132971)

### Articles
 * TBD

## Kubernetes and Cloud Native Associate (KCNA)

### Courses
 * [Kubernetes Certified (KCNA) + Hands On Labs + Practice Exams](https://www.udemy.com/course/dive-into-cloud-native-containers-kubernetes-and-the-kcna/?couponCode=LETSLEARNNOW) on Udemy
 * [Kubernetes and Cloud-Native Associate (KCNA)](https://kodekloud.com/courses/kubernetes-and-cloud-native-associate-kcna/) on KodeKloud

### Practice Tests
- [Free test](https://yetmike.com/tests/kcna1)

### Documentation, Tips and Tricks
 - [Kubernetes Overview](https://kubernetes.io/docs/concepts/overview/)
 - [Kubernetes Architecture](https://kubernetes.io/docs/concepts/architecture/)
 - [Kubernetes Objects](https://kubernetes.io/docs/concepts/overview/working-with-objects/kubernetes-objects/)
 - [Pods](https://kubernetes.io/docs/concepts/workloads/pods/)
 - [Deployments](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/)
 - [ReplicaSet](https://kubernetes.io/docs/concepts/workloads/controllers/replicaset/)
 - [StatefulSet](https://kubernetes.io/docs/concepts/workloads/controllers/statefulset/)
 - [DaemonSet](https://kubernetes.io/docs/concepts/workloads/controllers/daemonset/)
 - [Jobs and CronJobs](https://kubernetes.io/docs/concepts/workloads/controllers/job/)
 - [Service](https://kubernetes.io/docs/concepts/services-networking/service/)
 - [Ingress](https://kubernetes.io/docs/concepts/services-networking/ingress/)
 - [Cluster Networking](https://kubernetes.io/docs/concepts/cluster-administration/networking/)
 - [Volumes](https://kubernetes.io/docs/concepts/storage/volumes/)
 - [Persistent Volumes](https://kubernetes.io/docs/concepts/storage/persistent-volumes/)
 - [ConfigMaps](https://kubernetes.io/docs/concepts/configuration/configmap/)
 - [Secrets](https://kubernetes.io/docs/concepts/configuration/secret/)
 - [Kubernetes Scheduler](https://kubernetes.io/docs/concepts/scheduling-eviction/kube-scheduler/)
 - [Taints and Tolerations](https://kubernetes.io/docs/concepts/scheduling-eviction/taint-and-toleration/)
 - [Node Affinity/Anti-Affinity](https://kubernetes.io/docs/concepts/scheduling-eviction/assign-pod-node/)
 - [Security for Kubernetes](https://kubernetes.io/docs/concepts/security/)
 - [RBAC](https://kubernetes.io/docs/reference/access-authn-authz/rbac/)
 - [Platform as a Product: Understanding the Personas](https://tag-app-delivery.cncf.io/blog/paap-personas/)
 - [Container Runtimes](https://kubernetes.io/docs/setup/production-environment/container-runtimes/)
 - [Cluster Networking](https://kubernetes.io/docs/concepts/cluster-administration/networking/)
 - [Cloud Native Landscape](https://landscape.cncf.io/)
 - [Horizontal Pod Autoscaling](https://kubernetes.io/docs/tasks/run-application/horizontal-pod-autoscale/)
 - [CNCF Technical Oversight Committee (TOC)](https://github.com/cncf/toc)
 - [Prometheus](https://prometheus.io/docs/introduction/overview/)
 - [GitOps](https://opengitops.dev/)
 - [CNCF Glossary](https://glossary.cncf.io/)

### Books
- TBD

### Articles
 - [Passing KCNA Exam In 15 Minutes
](https://medium.com/@yetmike/passing-kcna-exam-in-15-minutes-d7d63defe972)

## Kubernetes and Cloud Security Associate (KCSA)
### Courses
 - [Kubernetes and Cloud Native Security Associate (KCSA)]() on KodeKloud

### Practice Tests
- [Free test](https://yetmike.com/tests/kcsa1)

### Documentation, Tips and Tricks
- TBD

### Books
- [Learn Kubernetes Security: Securely orchestrate, scale, and manage your microservices in Kubernetes deployments](https://www.amazon.com/Learn-Kubernetes-Security-orchestrate-microservices/dp/1839216506)

### Articles
- [On how I passed KCSA
](https://medium.com/@yetmike/on-how-i-passed-kcsa-e1ed71cd59ab)

## Certified GitOps Associate (CGOA)

### Courses
 * [GitOps Certified Associate (CGOA)](https://kodekloud.com/courses/gitops-certified-associate-cgoa) on KodeKloud
 * [Introduction to GitOps (LFS169)](https://training.linuxfoundation.org/training/introduction-to-gitops-lfs169/) on Linux Foundation (free)
 * [DevOps and GitOps with Kubernetes](https://www.udemy.com/topic/gitops/) on Udemy

### Practice Tests
- [Free test](https://yetmike.com/tests/cgoa1)

### Documentation, Tips and Tricks
 - [OpenGitOps Principles](https://opengitops.dev/) — the four GitOps principles are central to the exam
 - [CGOA Study Guide (community)](https://github.com/otkd/CGOA-Study-Guide)
 - [Argo CD Documentation](https://argo-cd.readthedocs.io/en/stable/)
 - [Flux Documentation](https://fluxcd.io/flux/)
 - [GitOps Glossary](https://github.com/open-gitops/documents/blob/main/GLOSSARY.md)
 - [CNCF GitOps Working Group](https://github.com/open-gitops/project)
 - The exam is conceptual — focus on the four GitOps principles (Declarative, Versioned & Immutable, Pulled Automatically, Continuously Reconciled) rather than tool syntax

### Books
- TBD

### Articles
 - [How to Ace the CGOA Certified GitOps Associate Exam](https://www.cncf.io/blog/2024/10/30/how-to-ace-the-certified-gitops-associate-cgoa-exam/) on CNCF blog
 - [How to Pass the Certified GitOps Associate (CGOA)](https://medium.com/@keeganjustis/how-to-pass-the-certified-gitops-associate-cgoa-7497b739709b) on Medium
 - [How to Ace the CGOA Exam](https://training.linuxfoundation.org/blog/ace-the-cgoa/) on Linux Foundation blog
 - [Get GitOps Fully Certified: A Practical Guide to Passing CAPA and CGOA](https://medium.com/@talyitzhak/get-gitops-fully-certified-a-practical-guide-to-passing-capa-and-cgoa-6376cef139a7) on Medium

## Certified Argo Project Associate (CAPA)

### Courses
 * [Certified Argo Project Associate (CAPA)](https://kodekloud.com/courses/certified-argo-project-associate-capa) on KodeKloud
 * [DevOps and Workflow Management with Argo (LFS256) + CAPA Exam Bundle](https://training.linuxfoundation.org/certification/lfs256-capa/) on Linux Foundation

### Practice Tests
- [Free test](https://yetmike.com/tests/capa1)

### Documentation, Tips and Tricks
 - [Argo CD Documentation](https://argo-cd.readthedocs.io/en/stable/)
 - [Argo Workflows Documentation](https://argoproj.github.io/argo-workflows/)
 - [Argo Rollouts Documentation](https://argoproj.github.io/argo-rollouts/)
 - [Argo Events Documentation](https://argoproj.github.io/argo-events/)
 - [CAPA Study Guide by DevOpsCube](https://devopscube.com/certified-argo-project-associate/)
 - [CAPA Study Guide by Ravikiran Srinivasulu](https://ravikirans.com/capa-certified-argo-project-associate-study-guide/)
 - The exam covers all four Argo projects — budget extra time for Argo Workflows (36%) and Argo CD (34%)

### Books
- TBD

### Articles
 - [How I Passed the CAPA Exam](https://rafaelmedeiros94.medium.com/how-i-passed-the-capa-certified-argo-project-associate-exam-69075cfdb512) on Medium
 - [CAPA Exam Study Guide by Paul Yu](https://paulyu.dev/article/capa-study-guide/)

## Certified Backstage Associate (CBA)

### Courses
 * [Certified Backstage Associate (CBA)](https://kodekloud.com/courses/certified-backstage-associate-cba) on KodeKloud
 * [Introduction to Backstage: Developer Portals Made Easy (LFS142)](https://training.linuxfoundation.org/training/introduction-to-backstage-developer-portals-made-easy-lfs142/) on Linux Foundation (free)

### Practice Tests
- [Free test](https://yetmike.com/tests/cba1)

### Documentation, Tips and Tricks
 - [Backstage Getting Started](https://backstage.io/docs/getting-started/)
 - [Software Catalog Overview](https://backstage.io/docs/features/software-catalog/)
 - [Catalog Entity Descriptor Format](https://backstage.io/docs/features/software-catalog/descriptor-format)
 - [Well-Known Annotations](https://backstage.io/docs/features/software-catalog/well-known-annotations)
 - [Creating a Frontend Plugin](https://backstage.io/docs/plugins/create-a-plugin)
 - [Creating a Backend Plugin](https://backstage.io/docs/plugins/backend-plugin)
 - [Configuring Backstage](https://backstage.io/docs/conf/)
 - [Deploying Backstage](https://backstage.io/docs/deployment/)
 - [Backstage Architecture Overview](https://backstage.io/docs/overview/architecture-overview)
 - [Backstage Plugin Marketplace](https://backstage.io/plugins)
 - The exam is multiple-choice only — know `catalog-info.yaml` entity kinds (Component, API, System, Domain, Group, User, Resource, Location) cold

### Books
- TBD

### Articles
 - [Awesome Backstage (community resources)](https://github.com/backstage/awesome-backstage)
 - [How we use Backstage at Spotify](https://engineering.atspotify.com/2020/04/how-we-use-backstage-at-spotify/)

## Certified Cloud Native Platform Engineering Associate (CNPA)

### Courses
 * [Certified Cloud Native Platform Engineering Associate (CNPA)](https://kodekloud.com/courses/certified-cloud-native-platform-engineering-associate-cnpa) on KodeKloud
 * [CNPA Certification Prep: Cloud Native Platform Engineering Associate](https://tekanaid.com/course/cnpa-certification-prep) on TeKanAid (26+ hours)
 * [Certified Cloud Native Platform Engineering Associate Boot Camp](https://rx-m.com/training/certified-cloud-native-platform-engineering-associate-cnpa/) on RX-M (2-day instructor-led)

### Practice Tests
- [Free test](https://yetmike.com/tests/cnpa1)

### Documentation, Tips and Tricks
 - [CNCF Platforms White Paper](https://tag-app-delivery.cncf.io/whitepapers/platforms/)
 - [Platform Engineering on Kubernetes (CNCF TAG App Delivery)](https://tag-app-delivery.cncf.io/)
 - [What is Platform Engineering?](https://platformengineering.org/blog/what-is-platform-engineering)
 - [DORA Metrics](https://dora.dev/guides/dora-metrics-four-keys/)
 - [OpenGitOps Principles](https://opengitops.dev/)
 - [Crossplane Documentation](https://docs.crossplane.io/)
 - [Backstage Documentation](https://backstage.io/docs/)
 - [Kubernetes Operators](https://kubernetes.io/docs/concepts/extend-kubernetes/operator/)
 - [Custom Resource Definitions](https://kubernetes.io/docs/tasks/extend-kubernetes/custom-resources/custom-resource-definitions/)
 - [OpenTelemetry Overview](https://opentelemetry.io/docs/what-is-opentelemetry/)

### Books
- [Platform Engineering on Kubernetes](https://www.manning.com/books/platform-engineering-on-kubernetes) by Mauricio Salatino

### Articles
 - [I Passed the CNPA Exam — Here's Everything You Need to Know](https://dev.to/vinujakhatode/i-passed-the-cnpa-exam-heres-everything-you-need-to-know-58c0) on DEV Community
 - [How I Passed the CNPA Exam](https://medium.com/@kienlt.qn/how-i-passed-the-certified-cloud-native-platform-associate-cnpa-exam-e59186e3f669) on Medium

## Cilium Certified Associate (CCA)

### Courses
 * [Complete Cilium Certified Associate (CCA) Exam Prep](https://www.udemy.com/course/complete-cilium-certified-associate-cca-exam-prep/) on Udemy
 * [Cilium Getting Started Labs](https://isovalent.com/labs/) on Isovalent (free interactive labs)
 * [Fundamentals for eBPF](https://isovalent.com/labs/ebpf-fundamentals/) on Isovalent (free)

### Practice Tests
- [Free test](https://yetmike.com/tests/cca1)

### Documentation, Tips and Tricks
 - [CCA Official Study Guide (Isovalent)](https://github.com/isovalent/CCA-Study-Guide)
 - [Cilium Documentation](https://docs.cilium.io/)
 - [Cilium Network Policy](https://docs.cilium.io/en/stable/network/kubernetes/policy/)
 - [Hubble Observability](https://docs.cilium.io/en/stable/observability/hubble/)
 - [Cilium Service Mesh](https://docs.cilium.io/en/stable/network/servicemesh/)
 - [Cilium Cluster Mesh](https://docs.cilium.io/en/stable/network/clustermesh/)
 - [eBPF Introduction](https://ebpf.io/what-is-ebpf/)
 - [Cilium BGP Control Plane](https://docs.cilium.io/en/stable/network/bgp-control-plane/)
 - CKA-level Kubernetes knowledge is assumed — if you don't have CKA yet, get comfortable with Kubernetes networking first
 - Practice reading CiliumNetworkPolicy YAML and reasoning about Layer 3/4/7 intent

### Books
- TBD

### Articles
 - [Preparing for Cilium Certification](https://www.solo.io/blog/preparing-cilium-certification) on Solo.io
 - [The New CNCF Cilium Certified Associate (CCA) Certification](https://isovalent.com/blog/post/cilium-certified-associate-cca/) on Isovalent blog
 - [Prepare for the CCA Exam](https://medium.com/@kienlt.qn/prepare-for-the-cilium-certified-associate-cca-exam-37fcf4bcde79) on Medium
 - [CCA Exam Study Guide by Ravikiran Srinivasulu](https://ravikirans.com/cca-cilium-certified-associate-exam-study-guide/)

## Kyverno Certified Associate (KCA)

### Courses
 * [Kyverno Certified Associate (KCA)](https://kodekloud.com/courses/kyverno-certified-associate) on KodeKloud
 * [Mastering Kubernetes Security with Kyverno (LFS255)](https://training.linuxfoundation.org/training/mastering-kubernetes-security-with-kyverno-lfs255/) on Linux Foundation

### Practice Tests
- [Free test](https://yetmike.com/tests/kca1)

### Documentation, Tips and Tricks
 - [Kyverno Documentation](https://kyverno.io/docs/)
 - [Writing Kyverno Policies](https://kyverno.io/docs/writing-policies/)
 - [Validation Rules](https://kyverno.io/docs/writing-policies/validate/)
 - [Mutation Rules](https://kyverno.io/docs/writing-policies/mutate/)
 - [Generation Rules](https://kyverno.io/docs/writing-policies/generate/)
 - [VerifyImage Rules](https://kyverno.io/docs/writing-policies/verify-images/)
 - [Kyverno CLI](https://kyverno.io/docs/kyverno-cli/)
 - [Policy Reports](https://kyverno.io/docs/policy-reports/)
 - [Kyverno with Helm](https://kyverno.io/docs/installation/methods/)
 - [KCA Study Guide by Ravikiran Srinivasulu](https://ravikirans.com/kca-kyverno-certified-associate-study-guide/)
 - Writing Policies (32%) is the heaviest domain — focus on validate/mutate/generate rules and CEL expressions

### Books
- TBD

### Articles
 - [Prepare for the Kyverno Certified Associate (KCA) exam](https://medium.com/@kienlt.qn/prepare-for-the-kyverno-certified-associate-kca-exam-c144906f9bc2) on Medium
 - [Thoughts on the KCA](https://eugenemdavis.net/archives/2026-03-02-thoughts-on-the-kca/)

## OpenTelemetry Certified Associate (OTCA)

### Courses
 * [OpenTelemetry Certified Associate (OTCA)](https://kodekloud.com/courses/prep-course-opentelemetry-certified-associate-certification-otca) on KodeKloud
 * [Introduction to OpenTelemetry (LFS148)](https://training.linuxfoundation.org/training/introduction-to-opentelemetry-lfs148/) on Linux Foundation (free)

### Practice Tests
- [Free test](https://yetmike.com/tests/otca1)

### Documentation, Tips and Tricks
 - [OpenTelemetry Documentation](https://opentelemetry.io/docs/)
 - [Observability Primer](https://opentelemetry.io/docs/concepts/observability-primer/)
 - [Signals: Traces, Metrics, Logs](https://opentelemetry.io/docs/concepts/signals/)
 - [Context Propagation](https://opentelemetry.io/docs/concepts/context-propagation/)
 - [Semantic Conventions](https://opentelemetry.io/docs/specs/semconv/)
 - [OpenTelemetry Collector](https://opentelemetry.io/docs/collector/)
 - [Collector Configuration](https://opentelemetry.io/docs/collector/configuration/)
 - [Auto-Instrumentation](https://opentelemetry.io/docs/concepts/instrumentation/automatic/)
 - [OpenTelemetry Operator for Kubernetes](https://opentelemetry.io/docs/kubernetes/operator/)
 - [OTel Demo Application](https://opentelemetry.io/docs/demo/) — reference app covering all signals in one deployable service
 - [OTCA Study Guide (community)](https://github.com/rDunn28/OTCA-study-guide)
 - The API and SDK domain is 46% of the exam — understand the difference between API (contracts) and SDK (implementations)

### Books
- [Cloud Native Observability with OpenTelemetry](https://www.packtpub.com/product/cloud-native-observability-with-opentelemetry/9781801077514) by Alex Boten
- [Learning OpenTelemetry](https://www.oreilly.com/library/view/learning-opentelemetry/9781098147174/) by Ted Young & Austin Parker

### Articles
 - [Is the OTCA Exam Right for You?](https://opentelemetry.io/blog/2025/otca-for-newcomers-and-advanced-users/) on OpenTelemetry blog
 - [How I Passed the OTCA Exam in January 2026](https://lime5005.medium.com/how-i-passed-the-opentelemetry-certified-associate-otca-exam-in-january-2026-efe6257be966) on Medium
 - [Prepare for the OTCA exam](https://medium.com/@kienlt.qn/prepare-for-the-opentelemetry-certified-associate-otca-exam-342ea1f574bc) on Medium
 - [How to pass OTCA — Tips](https://cloudificando.medium.com/how-to-pass-opentelemetry-certified-associate-otca-tips-the-best-observability-certification-c64afacfa99a) on Medium

## Prometheus Certified Associate (PCA)

### Courses
 * [Prometheus Certified Associate (PCA)](https://kodekloud.com/courses/prometheus-certified-associate-pca) on KodeKloud
 * [Prometheus Training by PromLabs](https://training.promlabs.com/) — PromQL-focused training by the creators of PromLabs

### Practice Tests
- [Free test](https://yetmike.com/tests/pca1)

### Documentation, Tips and Tricks
 - [Prometheus Documentation](https://prometheus.io/docs/introduction/overview/)
 - [PromQL Basics](https://prometheus.io/docs/prometheus/latest/querying/basics/)
 - [PromQL Functions](https://prometheus.io/docs/prometheus/latest/querying/functions/)
 - [Prometheus Configuration](https://prometheus.io/docs/prometheus/latest/configuration/configuration/)
 - [Alerting Rules](https://prometheus.io/docs/prometheus/latest/configuration/alerting_rules/)
 - [Alertmanager](https://prometheus.io/docs/alerting/latest/alertmanager/)
 - [Prometheus Exporters](https://prometheus.io/docs/instrumenting/exporters/)
 - [Client Libraries](https://prometheus.io/docs/instrumenting/clientlibs/)
 - [Grafana Dashboards](https://grafana.com/docs/grafana/latest/dashboards/)
 - [PCA Study Guide by DevOpsCube](https://devopscube.com/prometheus-certified-associate/)
 - PromQL is 28% of the exam and the hardest part — practice `rate()`, `irate()`, `increase()`, label matchers, and aggregation operators hands-on

### Books
- TBD

### Articles
 - [How to Ace the PCA Exam](https://www.cncf.io/blog/2024/11/07/how-to-ace-the-prometheus-certified-associate-pca-exam/) on CNCF blog
 - [How I Cleared the PCA Exam](https://medium.com/@kedarnath93/how-i-cleared-my-prometheus-certified-associate-pca-exam-221817aca1e9) on Medium
 - [PCA Tips — How to Pass](https://medium.com/@dgoscn/prometheus-certified-associate-pca-tips-on-how-to-pass-the-exam-72cc573e2d06) on Medium
 - [How to Score 93% in the PCA Exam](https://dev.to/monarene/how-to-score-93-in-the-prometheus-certified-associate-exam-1g07) on DEV Community

## Istio Certified Associate (ICA)

### Courses
 * [Istio Certified Associate (ICA)](https://kodekloud.com/courses/istio-certified-associate) on KodeKloud
 * [Introduction to Istio (LFS144)](https://training.linuxfoundation.org/training/introduction-to-istio-lfs144/) on Linux Foundation (free)

### Hands-On Labs
- [killercoda.com Istio scenarios](https://killercoda.com/ica) labs
- [Istio Official Tasks](https://istio.io/latest/docs/tasks/) — work through all tasks before exam day

### Documentation, Tips and Tricks
 - [Istio Documentation](https://istio.io/latest/docs/)
 - [Traffic Management](https://istio.io/latest/docs/concepts/traffic-management/)
 - [VirtualService](https://istio.io/latest/docs/reference/config/networking/virtual-service/)
 - [DestinationRule](https://istio.io/latest/docs/reference/config/networking/destination-rule/)
 - [Gateway](https://istio.io/latest/docs/reference/config/networking/gateway/)
 - [ServiceEntry](https://istio.io/latest/docs/reference/config/networking/service-entry/)
 - [Security: Authorization Policy](https://istio.io/latest/docs/reference/config/security/authorization-policy/)
 - [Security: PeerAuthentication (mTLS)](https://istio.io/latest/docs/reference/config/security/peer_authentication/)
 - [Security: RequestAuthentication (JWT)](https://istio.io/latest/docs/reference/config/security/request_authentication/)
 - [Fault Injection](https://istio.io/latest/docs/tasks/traffic-management/fault-injection/)
 - [Circuit Breaking](https://istio.io/latest/docs/tasks/traffic-management/circuit-breaking/)
 - [Ambient Mode Overview](https://istio.io/latest/docs/ambient/overview/)
 - [istioctl Reference](https://istio.io/latest/docs/reference/commands/istioctl/)
 - [ICA Exam Study Guide (KodeKloud)](https://kodekloud.com/blog/istio-certified-associate-ica-study-guide/)
 - **Important**: ICA is a **hands-on performance-based** exam (2 hours, 15–20 tasks) with access to Istio and Kubernetes docs — practice in a real cluster, not just theory

### Books
- TBD

### Articles
 - [The New Istio Certified Associate Exam Explained](https://medium.com/@maheshshinde.kr/the-new-istio-certified-associate-exam-explained-my-path-from-73-to-success-5607d208c1a1) on Medium
 - [Istio Certified Associate (ICA) Exam Prep](https://medium.com/@wattsdave/istio-certified-associate-ica-exam-prep-51b59bdd372f) on Medium

## Certified Cloud Native Platform Engineer (CNPE)

### Courses
 * [Certified Cloud Native Platform Engineering Associate (CNPA) course](https://kodekloud.com/courses/certified-cloud-native-platform-engineering-associate-cnpa) on KodeKloud — CNPA course serves as strong CNPE foundation
 * [Certified Cloud Native Platform Engineer (CNPE) Boot Camp](https://rx-m.com/training/certified-cloud-native-platform-engineering-cnpe-boot-camp-with-exam/) on RX-M (5-day instructor-led)

### Hands-On Labs
- [killercoda.com CNPE scenarios](https://killercoda.com/course/cnpe) labs
- Practice with the full CNPE toolset in a real cluster: Argo CD, Flux, Crossplane, Kyverno, Prometheus, OpenTelemetry, Tekton, Grafana, Jaeger

### Documentation, Tips and Tricks
 - [CNPE Exam Page — Linux Foundation](https://training.linuxfoundation.org/certification/certified-cloud-native-platform-engineer-cnpe/)
 - [CNPE Study Guide by Ravikiran Srinivasulu](https://ravikirans.com/cnpe-cloud-native-platform-engineer-study-guide/)
 - [Argo CD Documentation](https://argo-cd.readthedocs.io/en/stable/)
 - [Flux Documentation](https://fluxcd.io/flux/)
 - [Crossplane Documentation](https://docs.crossplane.io/)
 - [Kyverno Documentation](https://kyverno.io/docs/)
 - [OpenTelemetry Collector](https://opentelemetry.io/docs/collector/)
 - [Prometheus Documentation](https://prometheus.io/docs/)
 - [Tekton Documentation](https://tekton.dev/docs/)
 - [Grafana Documentation](https://grafana.com/docs/)
 - [OpenCost Documentation](https://www.opencost.io/docs/)
 - [OPA Gatekeeper](https://open-policy-agent.github.io/gatekeeper/website/docs/)
 - [Kubernetes Operators](https://kubernetes.io/docs/concepts/extend-kubernetes/operator/)
 - [Custom Resource Definitions](https://kubernetes.io/docs/tasks/extend-kubernetes/custom-resources/custom-resource-definitions/)
 - **Important**: CNPE is a **hands-on performance-based** exam (2 hours) using a remote Linux desktop — you are expected to complete real tasks using unfamiliar tools with access to documentation. CKA-level Kubernetes proficiency is assumed
 - You will NOT be tested on deep tool-specific knowledge — breadth across the ecosystem matters more than mastery of any single tool

### Books
- [Platform Engineering on Kubernetes](https://www.manning.com/books/platform-engineering-on-kubernetes) by Mauricio Salatino

### Articles
 - [How I Passed the CNPE Exam](https://medium.com/@michatomczak_38795/how-i-passed-the-cloud-native-platform-engineer-cnpe-exam-and-what-you-can-learn-from-my-attempt-69f30f3d1458) on Medium
 - [CNPE Certification Study Guide (YouTube)](https://www.youtube.com/watch?v=7kcTXIqIqiM)
