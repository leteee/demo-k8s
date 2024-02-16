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
[minikube.md](..%2Fwindows%2Fminikube.md)
- 排查问题[minikube.md](..%2Fwindows%2Fminikube.md)
```shell
kubectl logs -n <ingres[minikube.md](..%2Fwindows%2Fminikube.md)s-nginx-namespace> <nginx-ingress-controller-pod-name>
kubectl logs -n demo nginx-ingress-ingress-nginx-controller-fdfc647-cc8xh
```

### 添加bitnami
```shell
helm repo add bitnami https://charts.bitnami.com/bitnami
helm repo update
```
### 安装MySQL
```shell
helm install mysql-demo bitnami/mysql --namespace demo --set auth.rootPassword=1qaz@WSX,architecture=standalone,primary.service.type=NodePort
```
```shell
helm uninstall mysql-demo --namespace demo
```

### 安装redis
```shell
helm install redis-demo bitnami/redis --namespace demo --set auth.password=1qaz@WSX,architecture=standalone,master.service.type=NodePort
```
```shell
helm uninstall redis-demo --namespace demo
```

### 安装kafka
```shell
helm install kafka-demo bitnami/kafka --namespace demo --set service.type=NodePort
```
```shell
helm uninstall kafka-demo --namespace demo
```
### 添加elastic
```shell
helm repo add elastic https://helm.elastic.co
helm repo update
```
### 安装elasticsearch
```shell
helm install elasticsearch-demo elastic/elasticsearch --namespace demo --set service.type=NodePort,secret.password=1qaz2wsx
```
```shell
helm uninstall elasticsearch-demo --namespace demo
```