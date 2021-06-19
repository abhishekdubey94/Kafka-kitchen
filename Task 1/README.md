## TASK 1 - To start and stop ZooKeeper and Kafka

### To strat the ZooKeeper

1. Download the zookeeper and apache from the following sites.
   - Zoo Keeper - https://archive.apache.org/dist/zookeeper/
   - Kafka - https://kafka.apache.org/downloads
2. Extract the tar file using command

   ```
   tar -xf <tar file name>
   ```

3. Start the zookeeper by running the script 'zkServer.sh start'.

   ```
   zkServer.sh start
   ```

- The zookeeper server searches for zoo.config file in config folder. If not present copy the sample and configure.
- zookeeper has blacklisted four letter word commands. To enable that add following line in zoo.config

  ```
  4lw.commands.whitelist=*
  ```

### To strat the Kafka

1. Kafka uses configuration file in conf folder of kafka named server.properties. Update the listeners and other configuration.

2. Start the kafka by running the script from bin

   ```
   kafka-server-start.sh config/server.properties
   ```

   - To run in background, use -daemon

3. Check the status of running servers using.
   ```
   echo stat | nc localhost 2181
   ```
   ```
   echo dump | nc localhost 2181 | grep brokers
   ```
   Note : As kafka servers are managed by zookeeper, we are checking port 2181.
   - Kafka server logs is present inside kafka/logs/server.log
4. To stop the kafka server
   ```
   kafka-server-stop.sh
   ```

Note : Kafka uses ZooKeeper so you need to first start a ZooKeeper server if you don't already have one. You can use the convenience script packaged with kafka to get a quick-and-dirty single-node ZooKeeper instance.
