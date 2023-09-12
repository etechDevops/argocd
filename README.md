## Follow this link to create an EKS cluster
```
https://github.com/etechDevops/kube-EKS
```
## Create a namespace in your k8s and install ArgoCD  
```
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```
## Switch to the namespace created above
```
 kubectl config set-context --current --namespace=argocd
 kubectl config view | grep namespace
 ```
## aplly your application.yaml file this is the only kubectl apply you'll do
```
vi application.yaml
kubectl apply -f application.yaml -n argocd
```
```
kubectl get pod 
kubectl get svc
```
### accessing ArgoCD UI

### Edit the service and change type from ClusterIP to LoadBalancer
   

```
 
kubectl edit svc argocd-server
```

### login with admin user and below token (as in documentation):
```
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 --decode && echo
```
### get password and enter in gitlab UI
### username is admin

### you can change and delete init password

==============================================================================================

## Links


## https://github.com/etechDevops/argocd


## Docker repo: engr Elvis is going to add it


## Install ArgoCD: https://argo-cd.readthedocs.io/en/stable/getting_started/#1-install-argo-cd


## Login to ArgoCD: .......


## ArgoCD Configuration: https://argo-cd.readthedocs.io/en/stable/operator-manual/declarative-setup/

## NOTE: to delete your k8s cluster first delete argocd and myapp namespace

