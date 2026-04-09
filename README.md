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
