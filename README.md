# GitOps App Template Engine

## 📌 What is this project?

This project provides a **reusable GitOps-based Kubernetes deployment template** that can be used to deploy *any application* without rewriting Kubernetes YAML files again and again.

Instead of deploying a single application, this project focuses on **building a deployment standard / platform layer** using:
- Kubernetes manifests
- Kustomize overlays (dev & prod)
- Argo CD (GitOps Continuous Delivery)

The goal is to make deployments **repeatable, consistent, and fully Git-driven**.

---

## 🎯 Problem Statement

In real-world teams:
- Every new service requires writing the same Kubernetes YAML files again
- Dev and Prod environments require different settings
- Deployments are often done manually using `kubectl apply`
- Argo CD applications are frequently created manually from the UI

This leads to:
- Duplication of YAML
- Configuration drift
- Manual mistakes
- Poor reproducibility

---

## ✅ Solution Provided by This Project

This repository solves the above problems by:

1. Creating **generic base Kubernetes templates**
2. Separating **environment-specific configuration** using overlays
3. Managing **Argo CD Applications as code** (not from UI)
4. Enabling **fully automated GitOps deployments**

> Git becomes the **single source of truth**.

---

## 🏗️ Project Structure

```
gitops-app-template/
├── base/
│   ├── deployment.yaml
│   ├── service.yaml
│   └── ingress.yaml
│
├── overlays/
│   ├── dev/
│   │   ├── kustomization.yaml
│   │   └── deployment-patch.yaml
│   │
│   └── prod/
│       ├── kustomization.yaml
│       └── deployment-patch.yaml
│
├── argocd/
│   └── dev-app.yaml
│
└── README.md
```

---

## 🧠 How It Works (High-Level Flow)

```
GitHub Repo
   │
   │  (Base + Overlays + Argo Application YAML)
   ▼
Argo CD
   │
   │  (Continuously watches Git)
   ▼
Kubernetes Cluster
```

### Key Points:
- **Base** contains standard Kubernetes manifests
- **Overlays** modify behavior per environment (dev / prod)
- **Argo CD** continuously reconciles the cluster with Git
- No manual `kubectl apply` is required for application changes

---

## 🔁 GitOps in Action

Example GitOps workflow:

1. Update replicas or image in `overlays/dev/deployment-patch.yaml`
2. Commit & push changes to GitHub
3. Argo CD automatically detects the change
4. Cluster state is updated automatically

No manual intervention is required.

---

## 🚀 Why This Project Matters

This project demonstrates:
- GitOps principles
- Platform engineering mindset
- Separation of concerns (base vs environment)
- Reproducible infrastructure
- Argo CD automation beyond UI-driven setups

It focuses on **system design and delivery automation**, not application code.

---

## 🧪 Notes

- Application images are intentionally placeholders
- The goal is to showcase **deployment patterns**, not application runtime
- Pods running successfully is optional for this project

---

## 🛠️ Tools Used

- Kubernetes
- Kustomize
- Argo CD
- GitHub
- Docker (via kind for local cluster)

---



## 📌 Future Enhancements

- App-of-Apps pattern
- Production Argo CD application
- Secrets management integration
- Monitoring & observability

---

## 👤 Author

**Aayush**  
DevOps / Platform Engineering Enthusiast

