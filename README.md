## Argocd Installation Steps

[Follow this link to create an EKS cluster](https://github.com/etechDevops/kube-EKS)

Create a namespace in your k8s and install ArgoCD  
```
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```
Switch to the namespace created above
```
 kubectl config set-context --current --namespace=argocd
 kubectl config view | grep namespace
 ```
aplly your application.yaml file this is the only kubectl apply you'll do
```
vi application.yaml
```
```

kubectl apply -f application.yaml -n argocd
```

```
kubectl get pod,svc
```
To accessing ArgoCD UI, Edit the service and change type from ClusterIP to LoadBalancer

```
kubectl edit svc argocd-server
```
Execute the command below to get the password, UserName is admin
```
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 --decode && echo
```
you can optionally change and delete init password

Links

[Argocd](https://github.com/etechDevops/argocd)

[Argocd official website](https://argo-cd.readthedocs.io/en/stable/getting_started/#1-install-argo-cd)

[ArgoCD Configuration](https://argo-cd.readthedocs.io/en/stable/operator-manual/declarative-setup/)

note: to delete your k8s cluster first delete argocd and myapp namespace
```
kubectl delete ns myapp
```
Docker repo To be added by Engr Elvis
