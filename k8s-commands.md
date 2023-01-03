```
kubectl run kafka-release-client --image docker.io/bitnami/kafka:latest --namespace kafka --command -- sleep infinity
```
```
kubectl exec --tty -i kafka-release-client --namespace kafka -- bash
```
```
kafka-console-producer.sh \
    --broker-list kafka-release-0.kafka-release-headless.kafka.svc.cluster.local:9092 \
    --topic test
```
```
kafka-console-consumer.sh \
    --bootstrap-server kafka-release.kafka.svc.cluster.local:9092 \
    --topic test \
    --from-beginning
```
