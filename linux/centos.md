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

### 配置sudo
```shell
#修改文件
vi /etc/sudoers
#文件内容
light  ALL=(ALL) NOPASSWD:ALL
light ALL=(ALL) NOPASSWD:/usr/bin/du,/usr/bin/ping
#一行命令
echo "light  ALL=(ALL) NOPASSWD:ALL" | sudo tee /etc/sudoers.d/username
```

### 关闭防火墙
```shell
sudo systemctl stop firewalld && sudo systemctl disable firewalld
```

### 配置阿里镜像源
```shell
sudo mv /etc/yum.repos.d/CentOS-Base.repo /etc/yum.repos.d/CentOS-Base.repo.backup
sudo curl -o /etc/yum.repos.d/CentOS-Base.repo http://mirrors.aliyun.com/repo/Centos-7.repo
sudo yum clean all
sudo yum makecache
sudo yum -y  update
```

### 关闭swap
```shell
sudo swapoff -a && sudo sed -i '/ swap / s/^\(.*\)$/#\1/g' /etc/fstab
```

### 时间同步
```shell
sudo yum -y install ntpdate
sudo ntpdate time.windows.com
```

### 修改主机名
```shell
sudo hostnamectl set-hostname a
```

