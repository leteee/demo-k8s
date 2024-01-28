### 创建名称空间
```shell
kubectl apply -f demo-namespace.yaml
```


### 安装nginx
```shell
helm repo add stable https://charts.helm.sh/stable
helm repo update
# 使用 Helm 安装 Nginx
helm install demo-nginx stable/nginx-ingress -n demo
```
