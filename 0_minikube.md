# SETUP MINIKUBE_HOME env variable first,
if you dont want to store virtual drive and other vm stuff in your home directory.

# INSTALL minikube into hyper-v VM.
## Setup 8 cores, 12Gb of memory and 50Gb of storage for VM.
##### Switch name = my manual created switch, which has an access to host machine networ.
`minikube start --driver='hyperv' --cpus=12 --memory='15g' --disk-size='150g' --hyperv-virtual-switch='Net_1'`
# INSTALL minikube into docker inside your VM.
`minikube start --driver='docker' --cpus=9 --memory='14g' --disk-size='150g'`
# STOP minukube
`minikube stop`
# START minikube
##### If no minikube instance been created, then new minikube vm will start, using default parameters
`minikube start`


# ADDON enable/disable
`minikube addons enable <addon_name>`
`minikube addons disable <addon_name>`

# DELETE existing VM with kubernetes
`minikube delete`

# To point your shell to minikube's docker daemon
### Use the last command from output of
`docker ps`
### OR use one of theese:
#### Windows shell:
`& minikube -p minikube docker-env | Invoke-Expression`
#### Windows terminal:
`@FOR /f "tokens=*" %i IN ('minikube -p minikube docker-env') DO @%i`
#### Linux:
`eval $(minikube docker-env)`