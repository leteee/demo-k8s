### 配置网络
```shell
vim /etc/sysconfig/network-scripts/ifcfg-ens33
service network restart
ping -c4 www.baidu.com
```
> BOOTPROTO=static  
> ONBOOT=yes  
> IPADDR=192.168.7.3  
> GATEWAY=192.168.7.2  
> NETMASK=255.255.255.0  
> DNS1=192.168.7.2  
> DNS2=8.8.8.8  

### 关闭防火墙
```shell
sudo systemctl stop firewalld && systemctl disable firewalld
```

### 配置阿里镜像源
```shell
yum install -y wget
wget -O /etc/yum.repos.d/CentOS-Base.repo http://mirrors.aliyun.com/repo/Centos-7.repo
yum update
```

### 关闭swap
```shell
swapoff -a && sed -i '/ swap / s/^\(.*\)$/#\1/g' /etc/fstab
```

### 时间同步
```shell
yum -y install ntpdate
ntpdate time.windows.com
```

### 将桥接的IPv4流量传递到iptables的链
```shell
cat > /etc/sysctl.d/k8s.conf << EOF
net.bridge.bridge-nf-call-ip6tables = 1
net.bridge.bridge-nf-call-iptables = 1
EOF
sysctl --system  # 生效
```
