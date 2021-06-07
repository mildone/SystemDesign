# Overview
## HDFS (file system)
NameNode and DataNode
## YARN
ResourceManager, NodeManager, ApplicationManager, Container
scheduler strategy: FIFO, FAIR, 
## MapReduce
## ZooKeeper
## Hive (sql like client)
## HBASE (distributed Database)
## Spark
framework

## Hadoop start-all.sh can't have datanode 
root cause: the cluster id is different if you compare data/current/VERSION and name/current/VERSION. 
fix: copy clusterid in name/current/VERSION to /data/current/VERSION 
it's caused by running format twice or several times. 
to locate VERSION file. 
```
1. find it in core-default.xml where those info are recorded as configuraiton when starting HADOOP
2. find / -name VERSION -print|grep -i current
```





