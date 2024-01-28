### 下载mysql
```shell
helm pull bitnami/mysql --version 9.18.0 --untar
```

### 安装mysql
```shell
helm -n demo install demo-mysql mysql -f values.yaml
helm -n demo install demo-mysql mysql --set auth.rootPassword=1qaz@WSX
# 获取设置的值
helm -n demo get values demo-mysql
# 删除
helm -n demo delete demo-mysql
# 更新(操作失败)
helm -n demo upgrade --set auth.rootPassword=1qaz@WS demo-mysql mysql
```

### 连接mysql
```shell
# To connect to your database
kubectl run demo-mysql-client --rm --tty -i --restart='Never' --image  docker.io/bitnami/mysql:8.0.36-debian-11-r0 --namespace demo --env MYSQL_ROOT_PASSWORD=1qaz@WSX --command -- bash
mysql -h demo-mysql.demo.svc.cluster.local -uroot -p"$MYSQL_ROOT_PASSWORD"
```
