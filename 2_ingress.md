#
https://kubernetes.io/docs/tasks/access-application-cluster/ingress-minikube/

# MINIKUBE first step. We want to enable ingress addon (if you didnt do that on "kubectl start..." command)
minikube addons enable ingress
# If you want disable, then use:
minikube addons disable ingress

# HELLO WORLD
kubectl create deployment web --image=gcr.io/google-samples/hello-app:1.0
kubectl expose deployment web --type=NodePort --port=8080
kubectl get service web
minikube service web --url
# Visit url and you will see "Hello, world! Version...."
# To delete all these stuff, use delete deployment and service commands