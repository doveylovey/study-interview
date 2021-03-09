centos7 下启动 zookeeper 和 kafka
=================================

# 进入 $zookeeper_home
### 启动 Zookeeper
./zookeeper-3.4.13/bin/zkServer.sh start

### 查看 Zookeeper 状态
./zookeeper-3.4.13/bin/zkServer.sh status

# 进入 $kafka_home
### 启动 Kafka
./bin/kafka-server-start.sh ./config/server.properties
注，如果要在后台运行 kafka 服务，则可以在启动命令中加入 -daemon 参数或 & 字符，如下：
./bin/kafka-server-start.sh -daemon ./config/server.properties
或者
./bin/kafka-server-start.sh ./config/server.properties &

### 创建一个 Topic
./bin/kafka-topics.sh --zookeeper 127.0.0.1:2181/kafka --create --topic test --replication-factor 1 --partitions 1

### 查看 Topic 详细信息
./bin/kafka-topics.sh --zookeeper 127.0.0.1:2181/kafka --describe --topic test

### Consumer 读取 Topic 的消息
./bin/kafka-console-consumer.sh --bootstrap-server 127.0.0.1:9092 --topic test --from-beginning

### Producer 向 Topic 发送消息
./bin/kafka-console-producer.sh --broker-list 127.0.0.1:9092 --topic test

### 删除 Topic
配置文件新增：delete.topic.enable=true
./bin/kafka-topics.sh --zookeeper 127.0.0.1:2181 --delete --topic test

docker run --name mysql -p 3306:3306 -e MYSQL_ROOT_PASSWORD=root -d mysql:latest
docker exec -it  mysql /bin/bash




