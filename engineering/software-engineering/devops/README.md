# DevOps & Infrastructure

Modern ML systems don't live in notebooks — they run in containers, scale with orchestration platforms, and ship through automated pipelines. This track covers the infrastructure skills needed to deploy, operate, and monitor production ML systems.

---

## Goal

By the end of this track you will be able to:
- Containerize any application with Docker correctly and efficiently
- Deploy and manage services on Kubernetes
- Build CI/CD pipelines that automate testing, building, and deployment
- Provision and manage cloud infrastructure using code (Terraform)
- Operate ML systems with proper monitoring and alerting

---

## Prerequisites

- Linux command line fluency
- Basic Python and Go (for the services being deployed)
- Understanding of HTTP and networking basics

---

## Learning Path

### 1. Docker
- [ ] Containers vs. VMs: namespace isolation, cgroups, what a container actually is
- [ ] Dockerfile best practices: layer caching, multi-stage builds, minimal base images
- [ ] Image size optimization: why it matters for ML images (CUDA images are enormous)
- [ ] Docker networking: bridge, host, overlay networks
- [ ] Docker Compose: multi-service local development environments
- [ ] **Project:** Containerize an ML inference service — write an optimized multi-stage Dockerfile for a PyTorch model server. Use a CUDA base image. Minimize final image size. Run with Docker Compose alongside a Redis sidecar for caching.

### 2. Kubernetes Fundamentals
- [ ] Core objects: Pod, Deployment, Service, ConfigMap, Secret
- [ ] Namespaces, labels, selectors
- [ ] ReplicaSets: desired state reconciliation
- [ ] Services: ClusterIP, NodePort, LoadBalancer
- [ ] Storage: PersistentVolumes, PersistentVolumeClaims, StorageClasses
- [ ] **Project:** Deploy the inference service on Kubernetes (use minikube or kind locally) — write Deployment and Service manifests, configure resource requests/limits (CPU, memory, GPU), expose via a LoadBalancer

### 3. Kubernetes — Advanced
- [ ] ConfigMaps and Secrets: externalizing configuration
- [ ] Health checks: liveness probes, readiness probes, startup probes
- [ ] Horizontal Pod Autoscaler (HPA): scale on CPU, memory, or custom metrics
- [ ] Jobs and CronJobs: batch workloads (useful for training runs)
- [ ] Helm: chart structure, templating, values files
- [ ] **Project:** Package the inference service as a Helm chart — parameterize image tag, replica count, resource limits, and environment config. Deploy two environments (staging, production) from the same chart with different values.

### 4. CI/CD Pipelines
- [ ] CI/CD concepts: triggers, stages, artifacts, environments
- [ ] GitHub Actions: workflow syntax, jobs, steps, actions marketplace
- [ ] Building and pushing Docker images in CI
- [ ] Running tests in CI: unit tests, integration tests, linting
- [ ] GitOps: declarative deployment, ArgoCD (conceptual overview)
- [ ] **Project:** Build a full CI/CD pipeline for the inference service — on push to main: run tests, build Docker image, push to registry, deploy to a staging Kubernetes cluster. On tag: promote to production.

### 5. Infrastructure as Code
- [ ] Why IaC: reproducibility, version control, drift detection
- [ ] Terraform: providers, resources, state, modules
- [ ] Terraform workflow: `init`, `plan`, `apply`, `destroy`
- [ ] Managing Kubernetes resources with Terraform
- [ ] **Project:** Provision a Kubernetes cluster and supporting infrastructure (VPC, subnets, node pools) using Terraform on a cloud provider (GCP GKE or AWS EKS). Store state in a remote backend (GCS or S3).

### 6. Monitoring and Observability for ML
- [ ] The three pillars: metrics, logs, traces
- [ ] Prometheus: scraping, PromQL, alerting rules
- [ ] Grafana: dashboards, alerting, data sources
- [ ] Distributed tracing: OpenTelemetry, trace propagation
- [ ] ML-specific monitoring: data drift, prediction distribution shift, model performance degradation
- [ ] **Project:** Full observability stack for the inference service — Prometheus + Grafana deployed on Kubernetes, scraping model server metrics. Dashboards for latency, throughput, error rate. Alerts on p99 latency breach and error rate spike.

---

## Projects

| Project | Description | Key concepts |
|---|---|---|
| Containerized ML service | Multi-stage Docker + Compose with CUDA image | Docker, image optimization |
| Kubernetes deployment | K8s manifests for inference service with autoscaling | Deployments, Services, HPA |
| Helm chart | Parameterized chart for multi-environment deployment | Helm, templating |
| CI/CD pipeline | GitHub Actions: test → build → push → deploy | CI/CD, GitOps |
| Terraform infrastructure | K8s cluster + networking provisioned with Terraform | IaC, Terraform |
| Observability stack | Prometheus + Grafana + alerting on K8s | Monitoring, PromQL |

---

## Resources

**Books**
- *The DevOps Handbook* — Kim, Humble, Debois (culture and practices)
- *Kubernetes: Up and Running* — Burns, Beda, Hightower (practical K8s reference)
- *Terraform: Up and Running* — Brikman (hands-on IaC)

**Documentation**
- Kubernetes docs — kubernetes.io/docs (excellent official docs)
- Terraform docs — developer.hashicorp.com/terraform
- GitHub Actions docs — docs.github.com/actions

**Courses / Guides**
- *Cloud Native Patterns* — Cornelia Davis (patterns for container-native systems)
- Kelsey Hightower's *Kubernetes the Hard Way* — set up K8s from scratch to understand internals

---

## Progress

- [ ] Docker
- [ ] Kubernetes fundamentals
- [ ] Kubernetes advanced
- [ ] CI/CD pipelines
- [ ] Infrastructure as code
- [ ] Monitoring and observability for ML
- [ ] Project: Containerized ML service
- [ ] Project: Kubernetes deployment
- [ ] Project: Helm chart
- [ ] Project: CI/CD pipeline
- [ ] Project: Terraform infrastructure
- [ ] Project: Observability stack
