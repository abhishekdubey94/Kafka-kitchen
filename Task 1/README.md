### TASK 1  - To start and stop ZooKeeper and Kafka

1) Download the zookeeper and apache from the following sites.
    * Zoo Keeper - https://archive.apache.org/dist/zookeeper/
    * Kafka - https://kafka.apache.org/downloads
2) Extract the tar file using command

    ```
    tar -xf <tar file name>
    ```
3) Start the zookeeper by running the script 'zkServer.sh start'.
The zookeeper server searches for zoo.config file in config folder.
4) Start the kafka by running the script 'zkServer.sh ../config/server.properties'.
5) Check the status of running servers using
    ```
    echo stat | nc localhost 2181
    ```
    ```
    echo dump | nc localhost 2181 | grep brokers
    ```
