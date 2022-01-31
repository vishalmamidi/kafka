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
bin/kafka-topics.sh --list --bootstrap-server localhost:2181
```
```
bin\windows\kafka-topics.bat --list --bootstrap-server localhost:2181
```

## create topic
```
kafka-topics.sh --create --partitions 10 --replication-factor 2 --topic log --bootstrap-server localhost:2181
```
```
kafka-topics.bat --create --partitions 10 --replication-factor 2 --topic log --bootstrap-server localhost:2181
```

## producer

```
bin/kafka-console-producer.sh --topic quickstart-events --bootstrap-server localhost:9092
```

## consumer

```
kafka-console-consumer.sh --topic log --from-beginning --bootstrap-server localhost
```

```
kafka-console-consumer.bat --topic log --from-beginning --bootstrap-server localhost
```


## delete
```
kafka-topics.bat --delete --bootstrap-server localhost --topic jewel-audit
```
