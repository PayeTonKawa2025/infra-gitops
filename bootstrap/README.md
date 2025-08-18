# How to bootstrap this cluster

Here's the doc for deploying the PayeTonKawa production cluster.
This cluster is managed by ArgoCD. All you have to do is install it and argo will take care of deploying the rest.

## Requirements
- kubectl

```
kubectl apply -f ./argocd/namespace.yaml
```

```
kubectl -n argocd apply -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```

```
kubectl -n argocd apply -f ./argocd/repository-secret.yaml
```

```
kubectl -n argocd apply -f ./bootstrap/argocd/resources/application.yaml
```

```
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d
```