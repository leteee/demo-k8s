
### 安装kubectl
```shell
sudo yum install -y kubectl
```

### 安装kind
```shell
curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.20.0/kind-linux-amd64
chmod +x ./kind
sudo mv ./kind /usr/local/bin/kind
```

### 创建集群
```shell
kind create cluster
```


