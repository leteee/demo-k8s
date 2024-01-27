### 将桥接的IPv4流量传递到iptables的链
```shell
su root
cat > /etc/sysctl.d/k8s.conf << EOF
net.bridge.bridge-nf-call-ip6tables = 1
net.bridge.bridge-nf-call-iptables = 1
EOF
sysctl --system  # 生效
exit
```

### 安装kubectl
```shell
# This overwrites any existing configuration in /etc/yum.repos.d/kubernetes.repo
cat <<EOF | sudo tee /etc/yum.repos.d/kubernetes.repo
[kubernetes]
name=Kubernetes
baseurl=https://pkgs.k8s.io/core:/stable:/v1.29/rpm/
enabled=1
gpgcheck=1
gpgkey=https://pkgs.k8s.io/core:/stable:/v1.29/rpm/repodata/repomd.xml.key
EOF
sudo yum install -y kubectl
```

### kubesphere
```shell
#下载 KubeKey
export KKZONE=cn
curl -sfL https://get-kk.kubesphere.io | VERSION=v3.0.13 sh -
chmod +x kk
#依赖
sudo yum install -y conntrack socat ebtables ipset
#安装
sudo ./kk create cluster [--with-kubernetes version] [--with-kubesphere version]
sudo ./kk create cluster --with-kubernetes v1.22.12 --with-kubesphere v3.4.1
#验证结果
kubectl logs -n kubesphere-system $(kubectl get pod -n kubesphere-system -l 'app in (ks-install, ks-installer)' -o jsonpath='{.items[0].metadata.name}') -f
```
- [访问](192.168.7.3:30880)  admin/P@88w0rd





