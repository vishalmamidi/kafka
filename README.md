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
