## TASK 2 - To create topics, producers and consumers

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
- To **delete** the topic, we use kafka-topics.sh with delete option
  ```
  kafka-topics.sh --bootstrap-server localhost:9092 --delete --topic <topic name>
  ```

### - To Publish A Message by Producers

- To **publish** a message by producer, we use **kafka-console-producer.sh**
  ```
  kafka-console-producer.sh --bootstrap-server localhost:9092 --topic <topicName>
  <Add multiple messages>
  ```

  - With Acknowledgement
  ```
  kafka-console-producer.sh --bootstrap-server localhost:9092 --topic <topicName> --producer-property acks=all
  <Add multiple messages>
  ```

  - If a topic is not present and still producer passes it in above command, the topic will be created after retry attempts.
- To publish using key
   ```
  kafka-console-producer.sh --bootstrap-server localhost:9092 --topic <topicName> --property parse.key=true --property key.separator=:
  <Add multiple messages>
  ```

### - To consume message by Consumers

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

  Note: The consumer offset details are stored in Kafka cluster in a separate topic named as \_\_consumer-offsets
- To display key, value and timestamp in consumer
  ```
  kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic <topic_name> --formatter kafka.tools.DefaultMessageFormatter --property print.timestamp=true --property print.key=true --property print.value=true --property print.partition=true --from-beginning
  ```