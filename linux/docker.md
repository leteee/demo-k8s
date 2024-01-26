### 安装docker
#### 卸载旧版[参考](https://docs.docker.com/engine/install/centos/)
```shell
#卸载旧版
 sudo yum remove docker \
                  docker-client \
                  docker-client-latest \
                  docker-common \
                  docker-latest \
                  docker-latest-logrotate \
                  docker-logrotate \
                  docker-engine
#设置仓库
sudo yum install -y yum-utils
sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
#安装docker
sudo yum install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
#启动docker
sudo systemctl restart docker
sudo systemctl enable docker
```

### 配置Docker仓库
```shell
su root 
cat > /etc/docker/daemon.json << EOF
{
  "registry-mirrors": ["https://ij0p9jom.mirror.aliyuncs.com"]
}
EOF
sudo systemctl restart docker
docker info
```
### Enable Non-Root User Access
```shell
#create the docker group on the system
sudo groupadd -f docker
#add the active user to the docker group
sudo usermod -aG docker light
# Apply the group changes to the current terminal session
newgrp docker
#Check if the docker group is in the list of user groups
groups
```



