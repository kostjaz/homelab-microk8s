# homelab-gitops

GitOps repo for my microk8s homelab.

## Goals

- manage cluster from git
- bootstrap Argo CD cleanly
- keep kubectl for debugging, not for primary deployments

## Structure

- `bootstrap/argocd` — Argo CD installation manifests
- `clusters/homelab/argocd` — root app and Argo CD config
- `clusters/homelab/infra` — infrastructure components
- `clusters/homelab/apps` — applications

## 🧱 Argo CD Bootstrap

Argo CD is installed from manifests stored in this repository.

---

### ⚠️ Important Notes

- Installation **must use server-side apply**
- Namespace must be created **before applying manifests**
- Do **NOT** use plain `kubectl apply` (client-side) — it causes field ownership conflicts
- Manifests are **not self-contained** — namespace must be specified via `-n`

---

### 🚀 Installation

```bash
kubectl apply -f bootstrap/argocd/namespace.yaml

kubectl apply -n argocd -f bootstrap/argocd/install.yaml \
  --server-side \
  --force-conflicts
