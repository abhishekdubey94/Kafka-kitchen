## TASK 2

### - To Create, List and Describe Topics

- To **create** a topic, we use **kafka-topics.sh** with create option
  ```
  kafka-topics.sh --bootstrap-server localhost:9092 --create --topic <topicName> --partitions 1 --replication-factor 1
  ```
  - bootstrap server is the ip and port of kafka server
- To **list** the topic, we use kafka-topics.sh with list option
  ```
  kafka-topics.sh --bootstrap-server localhost:9092 --list
  ```
- To **describe** the properties of a topic, we use kafka-topics.sh with describe option
  ```
  kafka-topics.sh --bootstrap-server localhost:9092 --describe --topic <topicName>
  ```
  - The output shows the topic properties. On subsequent lines, it shows each partitions properties of the same topic.

### - To Create Producers

- To **create** a producer, we use **kafka-console-producer.sh**
  ```
  kafka-console-producer.sh --bootstrap-server localhost:9092 --topic <topicName>
  <Add multiple messages>
  ```

### - To Create Consumers

- To **create** a consumer, we use **kafka-console-consumer.sh**
  ```
  kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic <topicName> --from-beginning
  <Shows the message published from beginning>
  ```
  ```
  kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic <topicName> --group myConsumerGroup --from-beginning
  <Shows the message published from beginning>
  ```
- To **list** the consumer groups, we use **kafka-consumer-groups.sh**

  ```
  kafka-consumer-groups.sh --bootstrap-server localhost:9092 --list
  ```

  Note: The consumer details are stored in Kafka cluster in a separate topic named as \_\_consumer-offsets
