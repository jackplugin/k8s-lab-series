# Kubernetes Lab Series on Windows 11 Home with Docker Desktop, WSL2, and Minikube

Welcome to the **Kubernetes Lab Series** — a hands-on, experiment-driven guide to learning Kubernetes from scratch on a Windows 11 Home environment. This series is tailored for developers, students, and enthusiasts who want to explore Kubernetes using **WSL2**, **Minikube**, **Docker Desktop**, and a **local web proxy**, all without needing Windows Pro or a cloud subscription.

Each lab is a self-contained exercise focusing on a key concept in Kubernetes, from cluster setup to DevOps workflows.

---

## 🚀 Lab Index

| Part | Title | Description |
|------|-------|-------------|
| ✅ 1 | [Set Up a Local Multi-Node Kubernetes Cluster](#) | Install and configure Minikube in WSL2 with Docker Desktop and a local proxy to run Kubernetes on Windows 11 Home. |
| ⏳ 2 | [Deploy Your First Pod with YAML](#) | Understand the anatomy of a Pod and practice deploying a basic containerized app. |
| ⏳ 3.1 | [Deployments 101: Rolling Updates](#) | Learn how Deployments provide scaling and self-healing capabilities. |
| ⏳ 3.2 | [Health Checks with Probes](#) | Add readiness and liveness probes to your apps. |
| ⏳ 3.3 | [Autoscaling Deployments Using Metrics](#) | Set up Horizontal Pod Autoscaler (HPA) and monitor performance. |
| ⏳ 4 | [Expose Your Applications with Services](#) | Use ClusterIP, NodePort, and LoadBalancer services to make your apps accessible. |
| ⏳ 5 | [Persistent Storage with PV and PVC](#) | Explore how to manage data in Kubernetes using PersistentVolumes and PersistentVolumeClaims. |
| ⏳ 6 | [Install Monitoring with Prometheus and Grafana](#) | Deploy and configure a local monitoring stack for your cluster. |
| ⏳ 7 | [Ingress and HTTPS for Local Development](#) | Set up Ingress Controller and TLS certs for clean routing and local HTTPS. |
| ⏳ 8 | [Cloud-Native DevOps Lab: GitOps with ArgoCD](#) | Automate your deployments and manage config using GitOps principles. |

---

## 🔧 Technologies Used

- **Operating System**: Windows 11 Home
- **Linux Distro**: Ubuntu 24.04 (via WSL2)
- **Kubernetes Tooling**: Minikube (Linux version), kubectl, Helm
- **Runtime**: Docker Desktop with WSL2 integration
- **Networking**: Local web proxy (Privoxy + SSH Dynamic Port Forwarding)
- **Optional DevOps Tools**: ArgoCD, Prometheus, Grafana, Kustomize

---

## 🧭 How to Use This Series

1. Follow each lab in order — or jump to the part you're interested in.
2. All labs are hands-on and include explanations, YAML manifests, and screenshots.
3. You can clone the example files and scripts from the [GitHub repo](#) (coming soon).
4. Bookmark this page as your **entry point** to the full series!

---

## 📌 Stay Tuned

More labs and improvements will be added over time. Feel free to leave comments, ask questions, or suggest topics you'd like to see.

---

Happy K8s hacking! 🚀  
