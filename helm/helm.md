### 创建名称空间
```shell
kubectl create namespace demo
```
- 更新repo
 ```shell
helm repo add bitnami https://charts.bitnami.com/bitnami
helm repo update
 ```

- 查看配置信息
```shell
helm show values bitnami/mysql
```

### 安装 Nginx Ingress Controller
```shell
helm repo add ingress-nginx https://kubernetes.github.io/ingress-nginx
helm repo update
helm install nginx-ingress ingress-nginx/ingress-nginx --namespace demo
```

- 排查问题
```shell
kubectl logs -n <ingress-nginx-namespace> <nginx-ingress-controller-pod-name>
kubectl logs -n demo nginx-ingress-ingress-nginx-controller-fdfc647-cc8xh
```

### 安装MySQL
```shell
helm repo add bitnami https://charts.bitnami.com/bitnami
helm install mysql-demo bitnami/mysql --namespace demo --set auth.rootPassword=1qaz@WSX,architecture=standalone,primary.service.type=NodePort
```

### 安装redis
```shell
helm install redis-demo bitnami/redis --namespace demo --set auth.password=1qaz@WSX,architecture=standalone,master.service.type=NodePort
```