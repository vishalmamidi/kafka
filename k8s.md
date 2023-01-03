
# 1 replica set 
Apache kafka Installation 
------------------------------------------
`kafka namespace`

```
helm upgrade --install kafka-release bitnami/kafka --set persistence.size=8Gi,logPersistence.size=8Gi,replicaCount=1,volumePermissions.enabled=true,persistence.enabled=true,logPersistence.enabled=true,auth.clientProtocol=plaintext,allowPlaintextListener=true,listeners=PLAINTEXT://0.0.0.0:9092,advertisedListeners=PLAINTEXT://:9092,listenerSecurityProtocolMap=PLAINTEXT:PLAINTEXT,interBrokerListenerName="PLAINTEXT",serviceAccount.create=true,rbac.create=true,image.tag=latest --namespace kafka --create-namespace
```


`default namespace` 
```
helm install kafka-release bitnami/kafka --set persistence.size=8Gi,logPersistence.size=8Gi,replicaCount=1,volumePermissions.enabled=true,persistence.enabled=true,logPersistence.enabled=true,auth.clientProtocol=plaintext,allowPlaintextListener=true,listeners=PLAINTEXT://0.0.0.0:9092,advertisedListeners=PLAINTEXT://:9092,listenerSecurityProtocolMap=PLAINTEXT:PLAINTEXT,interBrokerListenerName="PLAINTEXT",serviceAccount.create=true,rbac.create=true,image.tag=latest
```
```
** Please be patient while the chart is being deployed **

Kafka can be accessed by consumers via port 9092 on the following DNS name from within your cluster:

    kafka-release.default.svc.cluster.local

Each Kafka broker can be accessed by producers via port 9092 on the following DNS name(s) from within your cluster:

    kafka-release-0.kafka-release-headless.default.svc.cluster.local:9092

To create a pod that you can use as a Kafka client run the following commands:

    kubectl run kafka-release-client --restart='Never' --image docker.io/bitnami/kafka:latest --namespace default --command -- sleep infinity
    kubectl exec --tty -i kafka-release-client --namespace default -- bash

    PRODUCER:
        kafka-console-producer.sh \

            --broker-list kafka-release-0.kafka-release-headless.default.svc.cluster.local:9092 \
            --topic test

    CONSUMER:
        kafka-console-consumer.sh \

            --bootstrap-server kafka-release.default.svc.cluster.local:9092 \
            --topic test \
            --from-beginning
WARNING: Rolling tag detected (bitnami/kafka:latest), please note that it is strongly recommended to avoid using rolling tags in a production environment.
+info https://docs.bitnami.com/containers/how-to/understand-rolling-tags-containers/
```







# 3 replica set 
Apache kafka Installation 
------------------------------------------
helm install kafka-release bitnami/kafka --set persistence.size=8Gi,logPersistence.size=8Gi,replicaCount=3,volumePermissions.enabled=true,persistence.enabled=true,logPersistence.enabled=true,auth.clientProtocol=plaintext,allowPlaintextListener=true,listeners=PLAINTEXT://0.0.0.0:9092,advertisedListeners=PLAINTEXT://:9092,listenerSecurityProtocolMap=PLAINTEXT:PLAINTEXT,interBrokerListenerName="PLAINTEXT",serviceAccount.create=true,rbac.create=true,image.tag=latest
helm upgrade kafka-release bitnami/kafka --set externalAccess.enabled=true

Login to kafka pod 
--------------------------------
kubectl exec --tty -i kafka-release-0 --namespace default -- bash

Kafka Topic creation
---------------------------------
kafka-topics.sh --create --topic test1 --bootstrap-server kafka-release-0.kafka-release-headless.default.svc.cluster.local:9092 --replication-factor 3 --partitions 3

Kafka verify the cluster using producer and consumer
------------------------------------------------------------------------------------
kafka-console-producer.sh --broker-list kafka-release-0.kafka-release-headless.default.svc.cluster.local:9092,kafka-release-1.kafka-release-headless.default.svc.cluster.local:9092,kafka-release-2.kafka-release-headless.default.svc.cluster.local:9092 --topic test1

kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic test1 --from-beginning
