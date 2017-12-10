# Setup Development Environment

**Prerequisites**

1. Install Eclipse IDE
2. Install Apache Hadoop
3. Install Apache HBase
4. Install Apache Zookeeper

Start all the below mentioned services

```
start-dfs.sh
start-yarn.sh
mr-jobhistory-daemon.sh start historyserver
service zookeeper start
start-hbase.sh
```

![](/assets/start-all-services.png)Once all the above commands are run, check whether all the processes are running.![](/assets/jps.png)

