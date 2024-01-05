### 安装docker
#### 卸载旧版
```shell
sudo yum remove docker \
                  docker-client \
                  docker-client-latest \
                  docker-common \
                  docker-latest \
                  docker-latest-logrotate \
                  docker-logrotate \
                  docker-engine
```

#### 设置仓库
```shell
sudo yum install -y yum-utils
sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
sudo yum install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
sudo systemctl start docker
```

#### 安装docker
```shell
sudo yum install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
sudo systemctl start docker
```

### 配置Docker仓库
```shell
cat > /etc/docker/daemon.json << EOF
{
  "registry-mirrors": ["https://ij0p9jom.mirror.aliyuncs.com"]
}
EOF
systemctl restart docker
docker info
```


