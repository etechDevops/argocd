## install ArgoCD in k8s
```
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```
## change namespace and switch to it
```
 kubectl config set-context -current-namespace=argocd
 kubectl config set-context --current --namespace=argocd
 kubectl config view | grep namespace
 ```
## aplly your application.yaml file this is the only kubectl apply you'll do
```
vi application.yaml
kubectl apply -f application.yaml
```

## access ArgoCD UI
 selector:
      app.kubernetes.io/name: argocd-server
    sessionAffinity: None
    type: ClusterIP
  status:
    loadBalancer:
      ingress:
## under type, change ClusterIP to  LoadBalancer     

```
kubectl get pod -n argocd
kubectl get svc -n argocd
kubectl edit svc -n argocd
```

## login with admin user and below token (as in documentation):
```
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 --decode && echo
```
## get password and enter in gitlab UI
## username is amin

## you can change and delete init password

==============================================================================================

## Links


## Config repo: https://gitlab.com/nanuchi/argocd-app-config


## Docker repo: https://hub.docker.com/repository/docker/nanajanashia/argocd-app


## Install ArgoCD: https://argo-cd.readthedocs.io/en/stable/getting_started/#1-install-argo-cd


## Login to ArgoCD: https://argo-cd.readthedocs.io/en/stable/getting_started/#4-login-using-the-cli


## ArgoCD Configuration: https://argo-cd.readthedocs.io/en/stable/operator-manual/declarative-setup/

