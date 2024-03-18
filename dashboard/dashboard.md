## [Deploying the Dashboard UI](https://kubernetes.io/docs/tasks/access-application-cluster/web-ui-dashboard/)
```shell
kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v2.7.0/aio/deploy/recommended.yaml
```

```shell
kubectl apply -f dashboard.yaml
```


## [创建 ServiceAccount and ClusterRoleBinding](https://github.com/kubernetes/dashboard/blob/master/docs/user/access-control/creating-sample-user.md)
```shell
kubectl apply -f dashboard-adminuser.yaml
```

## Command line proxy

```shell
kubectl proxy
```
- [Dashboard available](http://localhost:8001/api/v1/namespaces/kubernetes-dashboard/services/https:kubernetes-dashboard:/proxy/)
  
- Getting a Bearer Token for ServiceAccount
```shell
kubectl -n kubernetes-dashboard create token admin-user
```
- Getting a long-lived Bearer Token for ServiceAccount
```shell
kubectl get secret admin-user -n kubernetes-dashboard -o jsonpath={".data.token"} | base64 -d
```