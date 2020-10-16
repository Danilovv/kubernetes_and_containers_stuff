# 1. Argo "Getting started page"
`https://argoproj.github.io/argo-cd/getting_started/`
# 1.1
```
kubectl create namespace argocd

```


# ** IN PROGRESS **

`https://argoproj.github.io/argo-cd/`

# Create namespace for ArgoCD
`kubectl create namespace argocd`

# Deploy ArgoCD cluster
# Use first command, if you want to make ArgoCD-server access - insecure (http).
```
kubectl apply -n argocd -f ./common/argo_cd/1_deployment.yaml
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```

# Forward port of ArgoCD to local 8888
`kubectl port-forward svc/argocd-server -n argocd 8888:443`