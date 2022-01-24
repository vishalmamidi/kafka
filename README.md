## list msk clusters to get arn 
```
aws kafka list-clusters
```

## get kafka BootstrapBrokerString endpoint from arn

```
aws kafka get-bootstrap-brokers --cluster-arn arn
```

## list topics

```
bin/kafka-topics.sh --list --zookeeper localhost:2181
```
```
bin\windows\kafka-topics.bat --list --zookeeper localhost:2181
```

## create topic
```
kafka-topics.sh --create --partitions 10 --replication-factor 2 --topic log --bootstrap-server localhost:2181
```
```
kafka-topics.bat --create --partitions 10 --replication-factor 2 --topic log --bootstrap-server localhost:2181
```

## consumer

```
kafka-console-consumer.sh --topic log --from-beginning --bootstrap-server localhost
```

```
kafka-console-consumer.bat --topic log --from-beginning --bootstrap-server localhost
```

```
kafka-console-consumer.bat --topic jewel-log --from-beginning --bootstrap-server b-2.jewelkafka-dev.guzv65.c21.kafka.us-east-1.amazonaws.com:9092
```

## delete
```
kafka-topics.bat --delete --zookeeper localhost --topic jewel-audit
```
