### 创建名称空间
```shell
kubectl create namespace demo
```
### 更新repo
 ```shell
 helm repo update
 ```

### 安装 Nginx Ingress Controller
```shell
helm repo add ingress-nginx https://kubernetes.github.io/ingress-nginx
helm install nginx-ingress ingress-nginx/ingress-nginx --namespace demo -f ingress-nginx/values.yaml
```

#### 排查问题
```shell
kubectl logs -n <ingress-nginx-namespace> <nginx-ingress-controller-pod-name>
kubectl logs -n demo nginx-ingress-ingress-nginx-controller-fdfc647-cc8xh
```

### 安装WordPress
```shell
helm repo add bitnami https://charts.bitnami.com/bitnami
helm install wordpress-demo bitnami/wordpress --namespace demo -f wordpress/values.yaml
```

#### 创建ingress资源
```shell
kubectl apply -f wordpress/wordpress-ingress.yaml
```

### 安装MySQL
```shell
helm show values bitnami/mysql
helm install mysql-demo bitnami/mysql --namespace demo -f mysql/values.yaml
```

### 安装redis
```shell
helm repo add bitnami https://charts.bitnami.com/bitnami
helm install redis-demo bitnami/redis --namespace demo -f redis/values.yaml
```

### 安装kafka
```shell
helm repo add bitnami https://charts.bitnami.com/bitnami
helm install kafka-demo bitnami/kafka --namespace demo -f kafka/values.yaml
```

### 安装elasticsearch
```shell
helm repo add elastic https://helm.elastic.co
helm install elasticsearch-demo elastic/elasticsearch --namespace demo -f elasticsearch/values.yaml
```