## MySQL
- 安装
```shell
docker run --name demo-mysql -p 3306:3306 -e MYSQL_ROOT_PASSWORD=1qaz@WSX  --restart=always -d mysql:8
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
docker run --name demo-redis -p 6379:6379 --restart=always -d redis --requirepass "1qaz@WSX"
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

## RabbitMQ
- 安装
```shell
docker run-d --name demo-rabbitmq --hostname my-rabbit -p 15672:15672 -p 5672:5672 rabbitmq
```
- 安装插件
```shell
docker exec -it demo-rabbitmq /bin/bash
rabbitmq-plugins enable rabbitmq_management
```
- 卸载
```shell
docker rm demo-rabbitmq
```

## [ElasticSearch](https://www.elastic.co/guide/en/elasticsearch/reference/8.13/docker.html#run-kibana-docker)
- 网络
```shell
docker network create elastic
```
- 安装
```shell
docker run -d --name demo-es --net elastic -p 9200:9200 -m 1GB docker.elastic.co/elasticsearch/elasticsearch:8.12.2
```
- Kibana
```shell
docker run -d --name demo-kib --net elastic -p 5601:5601 docker.elastic.co/kibana/kibana:8.12.2
```

- enrollment token
```shell
docker exec -it demo-es /usr/share/elasticsearch/bin/elasticsearch-create-enrollment-token -s kibana
```
- bin\kibana-verification-code.bat
```shell
docker exec -it demo-kib /usr/share/kibana/bin/kibana-verification-code
```
- password
```shell
docker exec -it demo-es /usr/share/elasticsearch/bin/elasticsearch-reset-password -u elastic
```
- 分词器
```shell
docker cp ubuntu/ik demo-es:/usr/share/elasticsearch/plugins
docker restart demo-es
```

- 删除
```shell
# Remove the Elastic network
docker network rm elastic

# Remove Elasticsearch containers
docker rm demo-es

# Remove the Kibana container
docker rm demo-kib
```



