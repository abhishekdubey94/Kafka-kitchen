## Task 3 - To create multi node zookeeper servers and kafka servers

- Zookeeper cluser has multiple nodes (servers).
- The nodes elect one node as their leader.
- The number of nodes in Zookeeper cluster should be odd in number as strongly recommended in documentation, so that election of leader is easy.
- In zoo.cfg file, we have

  - tickTime : 1 unit of time for cluster
  - initLimit : number of tickTime required to connect to a zookeeper cluster
  - syncLimit : number of tickTime required to sync with zookeeper cluster. If not synced, zookeeper will kick it out.
  - dataDir : data regarding zookeeper and clients are kept here.
  - clientPort : port of the zookeeper node
  - maxClientCnxns : maximum number of clients

  Steps to create 'n' nodes of a ZooKeeper cluster:

  1. Copy and extract zookeeper n times in n different folders.
  2. Configure the zoo.cfg file of all the nodes.

     Sample

     ```
     ticktime=2000
     initLimit=10
     syncLimit=5
     dataDir=/tmp/zookeeper1
     clientPort=2181
     maxClientCnxns=60
     4lw.commands.whitelist=*
     server.1=localhost:2788:3788
     .
     .
     server.n=localhost:2789:3789
     ```

3.  To set the unique identifier of each node, add myid file in each /tmp/zookeepern folder with unqiue identifier.

            mkdir /tmp/zookeeper

            echo n >> /tempzookeepern/myid

4.  Start the zookeeper servers.
5.  To check the status of zookeeper nodes, run command
    ```
    echo stat | nc localhost port
    ```
    - the leader node will have mode as leader, others will have followers.

### For multi node kafka

1. Copy the kafka binaries and edit the server.properties.
2. Start the kafka servers.
