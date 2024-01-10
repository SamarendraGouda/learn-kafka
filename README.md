## Kafka - Setup using docker

1. Initialize zookeeper container from the `zookeeper` docker image (expose PORT `2181`):
```bash
docker run -p 2181:2181 zookeeper
```

2. Start confluent/kafka container from the `confluentinc/cp-kafka` docker image (expose PORT `9092`):
```bash
docker run -p 9092:9092 \
-e KAFKA_ZOOKEEPER_CONNECT=<PRIVATE_IP>:2181 \
-e KAFKA_ADVERTISED_LISTENERS=PLAINTEXT://<PRIVATE_IP>:9092 \
-e KAFKA_OFFSETS_TOPIC_REPLICATION_FACTOR=1 \
confluentinc/cp-kafka
```

Now, Kafka is up and running on PORT `9092`.
