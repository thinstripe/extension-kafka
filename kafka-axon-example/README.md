# Kafka Axon Springboot Example

This is an example SpringBoot application using the Kafka Axon extension. 
It configures a simple Kafka message publishing using Kafka infrastructure run locally. 

## How to run

### Preparation

You will need `docker` and `docker-compose` to run this example.

Please run:

```bash 
docker-compose -f ./kafka-axon-example/docker-compose.yaml up -d
```

This will start [Zookeeper](https://zookeeper.apache.org/), [Kafka](https://github.com/wurstmeister/kafka-docker), 
 [KafkaCat](https://github.com/edenhill/kafkacat), [Kafka Rest](https://github.com/nodefluent/kafka-rest) and [Kafka Rest UI](https://github.com/nodefluent/kafka-rest-ui).
KafkaCat can be used to investigate the setup, whereas the UI (accessed through localhost:8000, user `admin` and password `admin`) provides visualization of the internals.

Now build the application by running:

```bash
mvn clean package -f ./kafka-axon-example 
``` 

### Running example application
 
You can start the application by running `java -jar ./kafka-axon-example/target/axon-kafka-example.jar`.

From a Kafka Message Source perspective, there are several options you have, as both consumption and production of 
event messages can be Subscribing or Streaming (aka push or pull).
Thus, the application can run in six different modes due to the possibility to define a producer
 and consumer event processing mode.
At this stage the following profiles can be used:

  * `subscribing-producer`
  * `tracking-producer`
  * `pooled-streaming-producer`
  * `subscribing-consumer`
  * `tracking-consumer`
  * `pooled-streaming-consumer`
 
If not specified, a `subscribing` producer and `tracking` consumer will be used.
To activate these modes, please use Spring profiles in the run configuration like so:
 `--spring.profiles.active=tracking-producer,subscribing-consumer`
