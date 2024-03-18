## zookeeper
### 创建zookeeper自启动文件
```shell
sudo vi /lib/systemd/system/zookeeper.service
```
```shell
[Unit]
Description=zookeeperservice
After=network.target

[Service]
WorkingDirectory=/home/light/kafka_2.13-3.6.1/bin 
ExecStart=zookeeper-server-start.sh -daemon /home/light/kafka_2.13-3.6.1/config/zookeeper.properties 
ExecStop=zookeeper-server-stop.sh         
User=root
Group=root

[Install]
WantedBy=multi-user.target
```

### 创建kafka自启动文件
```shell
sudo vi /lib/systemd/system/kafka.service
```
```shell
[Unit]
Description=kafkaservice
After=network.target zookeeper.service

[Service]
WorkingDirectory=/home/light/kafka_2.13-3.6.1     
ExecStart=bin/kafka-server-start.sh -daemon config/server.properties    
ExecStop=bin/kafka-server-stop.sh   
User=root
Group=root
Restart=always
RestartSec=10

[Install]
WantedBy=multi-user.target
```

```shell
sudo systemctl daemon-reload
```

```shell
sudo systemctl start zookeeper.service
sudo systemctl enable zookeeper.service
```

### 启动
```shell
sudo systemctl start kafka.service
sudo systemctl enable kafka.service
```