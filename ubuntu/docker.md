## MySQL
- 安装
```shell
docker run --name demo-mysql -p 3306:3306  -e MYSQL_ROOT_PASSWORD=1qaz@WSX -d mysql:8
```
- 停止
```shell
docker stop demo-mysql
```
- 删除
```shell
docker rm demo-mysql
```
## Redis
- 安装
```shell
docker run --name demo-redis -p 6379:6379 -d redis --requirepass "1qaz@WSX"
```
- 停止
```shell
docker stop demo-redis
```
- 删除
```shell
docker rm demo-redis
```

## Kafka 
- zookeeper
```shell
docker run --name demo-zookeeper --publish 2181:2181 -d zookeeper:latest
```
- kafka
```shell
docker run --name kafka -p 9092:9092 -e KAFKA_BROKER_ID=0 -e KAFKA_ZOOKEEPER_CONNECT=localhost:2181 -d wurstmeister/kafka:latest
```


