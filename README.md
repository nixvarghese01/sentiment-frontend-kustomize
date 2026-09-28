# project-coit-frontend: Kustomize Manifests for the COIT Frontend

Kubernetes manifests, managed with Kustomize, that deploy the COIT sentiment-analysis frontend. Each branch holds the configuration for one environment.

## Contents
| File | Purpose |
|---|---|
| `kustomization.yaml` | Entry point: namespace, name prefix and suffix, labels, image, config map generators |
| `frontend-deployment.yaml`, `frontend-patch.yaml` | Deployment and environment-specific patch |
| `service-frontend-lb.yaml`, `frontend-ingress.yaml` | LoadBalancer service and ingress |
| `frontend-hpa.yaml` | Horizontal Pod Autoscaler |
| `backend1-pvc.yaml`, `fast-good-for-db.yaml` | PersistentVolumeClaim and StorageClass |
| `frontend-service-account.yaml`, `frontend-clusterrolebinding-list-pods.yaml`, `Roles/` | RBAC |
| `Issuers/` | cert-manager Let's Encrypt staging and production issuers |
| `config.properties`, `provider.properties` | Turned into ConfigMaps (placeholder values only) |

## Deploy
```bash
kubectl kustomize .     # preview the rendered manifests
kubectl apply -k .
```

## Branches
| Branch | Environment |
|---|---|
| `prod` (default) | Production |
| `main` | Base |
| `dev` | Development |

Application source: [coit-frontend](https://github.com/nixvarghese01/coit-frontend)
