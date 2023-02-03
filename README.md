# KAFKA

- Kafka is a **distributed message streaming platform** that uses **publish and subscribe** mechanism to stream the records.
- **Messaging Systems** : A messaging system is responsible for transferring data from one application to another so that application can focus on data without bogged down on data transmission and sharing.
- There are two types of messaging system

  - **Point to Point** -
    a) Messages are persisted in Queue.
    b) A particular message can be consumed by a maximum of one receiver.
    c) There is no time dependency laid for the receiver to receive the message.
    d) When receiver receives the message, it sends back an acknowledgement to the sender.
  - **Publish-Subscribe Messaging System**
    a) Messages are persisted in a Topic (It is a type of queue with additional features).
    b) A particular message can be consumed by any number of consumers.
    c) There is time dependency laid for the consumer to consume the message.
    When the subscriber receives the message, it does not send any acknowledgement.

### Terminology

- **Topic** : A stream of messages belonging to a particular category. Similar to table in database.Unique name of a data stream.
- **Partition**: Topics are split in Partitions. These are small and independent portion of topics. All messages in the partition are ordered and immutable. Each message within a partition has a unique id known as Offset. Offsets are local to a partition. When we create a topic, we need to mention the number of partition we need. Partition is the smallest unit and will be sitting on a single machine. **So to locate a message record, we need Topic, partition and offset.**
- Replicas: These are the backups of a partition. Replicas are never read or write data. They are used to prevent data loss (Fault tolerance).
- **Producers** are the applications which write/publish data to the topics within a cluster using the Producing APIs. They can write data either on the topic level or specific partitions of the topic.
- **Message Record** are the data produced by the producers. 
- **Consumers** are the applications which read/consume data from the topics within a cluster using the Consuming APIs. They can write data either on the topic level or specific partitions of the topic. Consumers are associated with exactly one Consumer Group. Kafka doesn't allow more than one consumer to read and process data from the same partition simultaneously. This is necessary to avoid double reading of the records.
- **Brokers or Kafka Servers**: These are simple software process which maintain and manage the published messages also known as Kafka Servers. They are also manage the consumer-offsets and are responsible for the delivery of messages to the right consumers. A set of brokers which are communicating with each other to perform the management and maintenance task are collectively known as Kafka Cluster. We can add more brokers in an already running kafka cluster without any downtime (Horizontal Scaling).
- **Zookeeper**: It is used to monitor kafka cluster and co-ordinate with each broker. It keeps all the metadata information related to kafka cluster in the form of a key-value pair. The metadata includes configuration information and health status of each broker. It is used for the controller election within kafka cluster. A set of zookeeper nodes working together to manage other distributed systems is known as Zookeeper Cluster or Zookeeper Ensemble.

### Architecture

![Architecture](./resources/Architecture.PNG?raw=true "Architecture")

### Core APIs

1. Producer APIs
2. Consumer APIs
3. Admin APIs
4. Stream APIs
5. Connector APIs

![APIs](./resources/APIs.jpg?raw=true "APIs")

Task 1 - To start and stop the zookeeper and kafka
Task 2 - To create topics, producers and consumers

### Features

- Scalable
- Fault Tolerance
- Durable
- Performance
- No Data Loss
- Zero Down Time
- Reliable

## Kafka Connect Framework
- Useful when we do not have access to producer/consumer code to embed Producer API/Consumer API.
- Implement 2 Java classes Source Connector (SourceConnector and SourceTask) and Sink Connector (SinkConnector and SinkTask). Kafka Connect is a cluster. 
- We can have a single Kafka Connect cluster to work as source and sink.

### Architecture
Kafka Connect has three components
 - Worker
 - Connector
 - Task

- Kafka Connect is a cluster and it runs one or more workers.
- Workers of same cluster have same GroupId.
- Workers are fault tolerant and self managed.