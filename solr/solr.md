# Apache Solr

Solr is enterprise search platform built on Apache Lucene. 
Highly reliable, scalable and fault tolerant, providing distributed indexing, replication and load-balanced querying, automated failover and recovery, centralized configuration and more.

## Resources

* Website: [Apache Solr](https://lucene.apache.org/solr/)
* [Hortonworks Solr Website](https://hortonworks.com/hadoop/solr/)
* [Solr Tutorial](https://lucene.apache.org/solr/guide/7_3/solr-tutorial.html)
* [Analyzing Social Media and Customer Sentiment With Apache NiFi and HDP Search](https://github.com/hortonworks/data-tutorials/blob/master/tutorials/hdp/analyzing-social-media-and-customer-sentiment-with-apache-nifi-and-hdp-search/) - Hortonworks tutorial on HDP & NiFi

## Solr Basics

### Install Solr (Windows)

[Download latest Solr](https://lucene.apache.org/solr/mirrors-solr-latest-redir.html) package. Unpack into a directory `$SOLR_HOME`. I used `SOLR_HOME=C:\Sandbox\Solr\solr-7.3.0`

### Start Solr for the First Time

Recommend to use older version of Java. E.g. JDK 1.8, installed in `C:\Program Files\Java\jdk1.8.0_172`.

```cmd
C:\Sandbox\Solr\solr-7.3.0>set PATH=C:\Program Files\Java\jdk1.8.0_172\bin;%PATH%

C:\Sandbox\Solr\solr-7.3.0>java -version
java version "1.8.0_172"
Java(TM) SE Runtime Environment (build 1.8.0_172-b11)
Java HotSpot(TM) 64-Bit Server VM (build 25.172-b11, mixed mode)
```

Start Solr. This will start two node cluster on ports 8983 and 7574.
It will ask also a few questions for setting up your first collection.

```cmd
C:\Sandbox\Solr\solr-7.3.0>bin\solr.cmd -e cloud

Welcome to the SolrCloud example!

This interactive session will help you launch a SolrCloud cluster on your local workstation.
To begin, how many Solr nodes would you like to run in your local cluster? (specify 1-4 nodes) [2]:

Ok, let's start up 2 Solr nodes for your example SolrCloud cluster.
Please enter the port for node1 [8983]:

Please enter the port for node2 [7574]:

Creating Solr home directory C:\Sandbox\Solr\solr-7.3.0\example\cloud\node1\solr
Cloning C:\Sandbox\Solr\solr-7.3.0\example\cloud\node1 into
   C:\Sandbox\Solr\solr-7.3.0\example\cloud\node2

Starting up Solr on port 8983 using command:
"C:\Sandbox\Solr\solr-7.3.0\bin\solr.cmd" start -cloud -p 8983 -s "C:\Sandbox\Solr\solr-7.3.0\example\cloud\node1\solr"

Waiting up to 30 to see Solr running on port 8983
Started Solr server on port 8983. Happy searching!

Starting up Solr on port 7574 using command:
"C:\Sandbox\Solr\solr-7.3.0\bin\solr.cmd" start -cloud -p 7574 -s "C:\Sandbox\Solr\solr-7.3.0\example\cloud\node2\solr" -z localhost:9983

Waiting up to 30 to see Solr running on port 7574
Started Solr server on port 7574. Happy searching!
INFO  - 2018-05-12 21:54:54.357; org.apache.solr.client.solrj.impl.ZkClientClusterStateProvider; Cluster at localhost:9983 ready

Now let's create a new collection for indexing documents in your 2-node cluster.
Please provide a name for your new collection: [gettingstarted]
techproducts
How many shards would you like to split tutorial into? [2]

How many replicas per shard would you like to create? [2]

Please choose a configuration for the tutorial collection, available options are:
_default or sample_techproducts_configs [_default]
sample_techproducts_configs
Created collection 'tutorial' with 2 shard(s), 2 replica(s) with config-set 'tutorial'

Enabling auto soft-commits with maxTime 3 secs using the Config API

POSTing request to Config API: http://localhost:8983/solr/tutorial/config
{"set-property":{"updateHandler.autoSoftCommit.maxTime":"3000"}}
Successfully set-property updateHandler.autoSoftCommit.maxTime to 3000


SolrCloud example running, please visit: http://localhost:8983/solr
```

### Index Examples

Execute following in `$SOLR_HOME`:

```cmd
java -jar -Dc=techproducts -Dauto example\exampledocs\post.jar example\exampledocs\*
```

### Start Solr

```cmd
bin\solr.cmd start -cloud -p 8983 -s "C:\Sandbox\Solr\solr-7.3.0\example\cloud\node1\solr"
bin\solr.cmd start -cloud -p 7574 -s "C:\Sandbox\Solr\solr-7.3.0\example\cloud\node2\solr" -z localhost:9983
```

To view solr web interface, navigate to [http://localhost:8983/solr](http://localhost:8983/solr).

### Stop Solr

To stop all ports:
```cmd
bin\solr.cmd stop -all
```

To stop particular port:
```cmd
bin\solr.cmd stop -p <port-number>
```

