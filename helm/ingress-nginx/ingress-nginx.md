### 下载
```shell
# Get Repo Info
helm repo add ingress-nginx https://kubernetes.github.io/ingress-nginx
helm repo update
# 下载
helm pull ingress-nginx/ingress-nginx --version 4.9.1 --untar
```

### 安装
```shell
helm -n demo install demo-ingress-nginx ingress-nginx -f values.yaml 
```

### 创建ingress
```shell
# 创建ingress资源
kubectl apply -f ingress-nginx.yaml
```