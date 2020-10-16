### Argo "Getting started page"
`https://argoproj.github.io/argo-cd/getting_started/`
## To install ArgoCD 
```
cd common\argo_cd
kubectl create namespace argocd
kubectl -n argocd apply -f .\install.yaml
```
## To Access argo CD api (web ui)
##### This is the most secure way to access to argo cd web ui. For other options go by a link on the top of the page
To take initial password
```
kubectl get pods -n argocd -l app.kubernetes.io/name=argocd-server -o name | cut -d'/' -f 2
```
Port forwarding
```
kubectl port-forward svc/argocd-server -n argocd 8080:443
```
Open ``localhost:8080`` and use `admin` login

# Example application
```
kubectl apply -n argocd -f .\common\argo_cd\example\app.yaml
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