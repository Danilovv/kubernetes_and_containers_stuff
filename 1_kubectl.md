# PODS list for current namespace
`kubectl get pods`

# PODS list for all namespaces
`kubectl get pods --all-namespaces`

# APPLY yaml file
`kubectl apply -f <file_name>.yaml`

# DELETE service/deployment/pod
`kubectl delete <service|deployment|pod> <name>`

# DASHBOARD deployment.
`kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v2.0.4/aio/deploy/recommended.yaml`
### Also, we should create user and role for access to UI
Go to this_repo/common/kubernetes_dashboard and run this commands:
`kubectl apply -f 1_dashboard-adminuser.yaml`
`kubectl apply -f 2_dashboard_cluster_role_binding.yaml`
### Then we will take user access token with help of this: (copy token property value)
##### POWERSHELL
`kubectl -n kubernetes-dashboard describe secret $(kubectl -n kubernetes-dashboard get secret | sls admin-user | ForEach-Object { $_ -Split '\s+' } | Select -First 1)`
##### BASH
`kubectl -n kubernetes-dashboard describe secret $(kubectl -n kubernetes-dashboard get secret | grep admin-user | awk '{print $1}')`
### PROXY your cluster endpoint to local machine.
`kubectl proxy`
### Then you will have access via link
`http://localhost:8001/api/v1/namespaces/kubernetes-dashboard/services/https:kubernetes-dashboard:/proxy/`