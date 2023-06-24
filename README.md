## Follow this link to create an EKS cluster
```
https://github.com/etechDevops/kube-EKS
```
## install ArgoCD in k8s
```
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```
## change namespace and switch to it
```
 kubectl config set-context --current --namespace=argocd
 kubectl config view | grep namespace
 ```
## aplly your application.yaml file this is the only kubectl apply you'll do
```
vi application.yaml
kubectl apply -f application.yaml
```

## `access ArgoCD UI`
## `selector:`
##      `app.kubernetes.io/name: argocd-server`
##    `sessionAffinity: None`
##    `type: ClusterIP`
##  `status:`
##    `loadBalancer:`
##      `ingress:`
## `under type, change ClusterIP to  LoadBalancer`    

```
kubectl get pod 
kubectl get svc 
kubectl edit svc argocd-server
```

## login with admin user and below token (as in documentation):
```
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 --decode && echo
```
## get password and enter in gitlab UI
## username is admin

## you can change and delete init password

==============================================================================================

## Links


## https://github.com/etechDevops/argocd


## Docker repo: engr Elvis add please


## Install ArgoCD: https://argo-cd.readthedocs.io/en/stable/getting_started/#1-install-argo-cd


## Login to ArgoCD: .......


## ArgoCD Configuration: https://argo-cd.readthedocs.io/en/stable/operator-manual/declarative-setup/

