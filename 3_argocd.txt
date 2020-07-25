https://argoproj.github.io/argo-cd/

# Create namespace for argocd
kubectl create namespace argocd

# Deploy argocd cluster
# Use first command, if you want to make argocd-server acces - insecure (http).
kubectl apply -n argocd -f ./common/argo_cd/1_deployment.yaml
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml

# Forwar port of argocd to local 8888
kubectl port-forward svc/argocd-server -n argocd 8888:443