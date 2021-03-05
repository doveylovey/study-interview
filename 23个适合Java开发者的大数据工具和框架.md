23 个适合 Java 开发者的大数据工具和框架
==================================

本文参考(2017-02-18)：https://www.cnblogs.com/stm32stm32/p/6413557.html

### 概述
目前，编程人员面对的最大挑战就是复杂性，硬件越来越复杂，OS 越来越复杂，编程语言和 API 越来越复杂，我们构建的应用也越来越复杂。根据外媒的一项调查报告，以下列出了 Java 程序员在过去 12 个月内一直使用的一些工具或框架，或许会对你有意义。

先来看看大数据的概念。根据维基百科，大数据是庞大或复杂的数据集的广义术语，因此传统的数据处理程序不足以支持如此庞大的体量。

在许多情况下，使用 SQL 数据库存储/检索数据都是很好的选择。而现如今的很多情况下，它都不再能满足我们的目的，这一切都取决于用例的变化。

现在来讨论一些不同的非 SQL 存储/处理数据工具，例如 NoSQL 数据库、全文搜索引擎、实时流式处理、图形数据库等。

### 1、MongoDB -- 最受欢迎的，跨平台的，面向文档的数据库。
MongoDB 是一个基于分布式文件存储的数据库，使用 C++ 语言编写。旨在为 Web 应用提供可扩展的高性能数据存储解决方案。应用性能高低依赖于数据库性能，MongoDB 则是非关系数据库中功能最丰富，最像关系数据库的，随着 MongoDB 3.4 版本发布，其应用场景适用能力得到了进一步拓展。

MongoDB 的核心优势就是灵活的文档模型、高可用复制集、可扩展分片集群。你可以试着从几大方面了解 MongoDB，如实时监控 MongoDB 工具、内存使用量和页面错误、连接数、数据库操作、复制集等。

### 2、Elasticsearch -- 为云构建的分布式RESTful搜索引擎。
ElasticSearch 是基于 Lucene 的搜索服务器。它提供了分布式多用户能力的全文搜索引擎，基于 RESTful web 接口。Elasticsearch 是用 Java 开发的，并作为 Apache 许可条款下的开放源码发布，是比较流行的企业级搜索引擎。

ElasticSearch 不仅是一个全文本搜索引擎，还是一个分布式实时文档存储，其中每个 field 均是被索引的数据且可被搜索；也是一个带实时分析功能的分布式搜索引擎，并且能够扩展至数以百计的服务器存储及处理 PB 级的数据。ElasticSearch 在底层利用 Lucene 完成其索引功能，因此其许多基本概念源于 Lucene。

### 3、Cassandra -- 开源分布式数据库管理系统，最初是由 Facebook 开发的，旨在处理许多商品服务器上的大量数据，提供高可用性，没有单点故障。
Apache Cassandra 是一套开源分布式 NoSQL 数据库系统。集 Google BigTable 的数据模型与 Amazon Dynamo 的完全分布式架构于一身。于 2008 年开源，此后，由于 Cassandra 良好的可扩展性，被 Digg、Twitter 等 Web 2.0 网站所采纳，成为了一种流行的分布式结构化数据存储方案。

因 Cassandra 是用 Java 编写的，所以理论上在具有 JDK6 及以上版本的机器中都可以运行，官方测试的 JDK 还有 OpenJDK 及 Sun 的 JDK。 Cassandra 的操作命令，类似于我们平时操作的关系数据库，对于熟悉 MySQL 的朋友来说，操作会很容易上手。

### 4、Redis -- 开源(BSD 许可)内存数据结构存储，用作数据库，缓存和消息代理。
Redis 是一个开源的使用 ANSI C 语言编写的、支持网络、可基于内存亦可持久化的日志型、Key-Value 数据库，并提供多种语言的 API。Redis 有三个主要使其有别于其它很多竞争对手的特点：Redis 是完全在内存中保存数据的数据库，使用磁盘只是为了持久性目的；Redis 相比许多键值数据存储系统有相对丰富的数据类型；Redis 可以将数据复制到任意数量的从服务器中。

### 5、Hazelcast -- 基于 Java 的开源内存数据网格。
Hazelcast 是一种内存数据网格 in-memory data grid，提供 Java 程序员关键任务交易和万亿级内存应用。虽然 Hazelcast 没有所谓的 Master，但是仍然有一个 Leader 节点(the oldest member)，这个概念与 ZooKeeper 中的 Leader 类似，但是实现原理却完全不同。同时，Hazelcast中的数据是分布式的，每一个 member 持有部分数据和相应的 backup 数据，这点也与 ZooKeeper 不同。

Hazelcast 的应用便捷性深受开发者喜欢，但如果要投入使用，还需要慎重考虑。

### 6、EHCache -- 广泛使用的开源 Java 分布式缓存。主要面向通用缓存、Java EE 和轻量级容器。
EhCache 是一个纯 Java 的进程内缓存框架，具有快速、精干等特点，是 Hibernate 中默认的 CacheProvider。主要特性有：快速简单，具有多种缓存策略;缓存数据有两级，内存和磁盘，因此无需担心容量问题;缓存数据会在虚拟机重启的过程中写入磁盘；可以通过 RMI、可插入 API 等方式进行分布式缓存；具有缓存和缓存管理器的侦听接口；支持多缓存管理器实例，以及一个实例的多个缓存区域；提供 Hibernate 的缓存实现。

### 7、Hadoop -- 用 Java 编写的开源软件框架，用于分布式存储，并对非常大的数据集进行分布式处理。
用户可以在不了解分布式底层细节的情况下，开发分布式程序。充分利用集群进行高速运算和存储。Hadoop 实现了一个分布式文件系统(Hadoop Distributed File System)，简称 HDFS。Hadoop 的框架最核心的设计就是：HDFS 和 MapReduce。HDFS 为海量的数据提供了存储，MapReduce 则为海量的数据提供了计算。

### 8、Solr -- 开源企业搜索平台，用 Java 编写，来自 Apache Lucene 项目。
Solr 是一个独立的企业级搜索应用服务器，它对外提供类似于 Web-service 的 API 接口。用户可以通过 http 请求，向搜索引擎服务器提交一定格式的 XML 文件，生成索引；也可以通过 Http Get 操作提出查找请求，并得到 XML 格式的返回结果。

与 ElasticSearch 一样，同样是基于 Lucene，但它对其进行了扩展，提供了比 Lucene 更为丰富的查询语言，同时实现了可配置、可扩展并对查询性能进行了优化。

### 9、Spark -- Apache Software Foundation 中最活跃的项目，是一个开源集群计算框架。
Spark 是一种与 Hadoop 相似的开源集群计算环境，但是两者之间还存在一些不同之处，这些不同之处使 Spark 在某些工作负载方面表现得更加优越，换句话说，Spark 启用了内存分布数据集，除了能够提供交互式查询外，它还可以优化迭代工作负载。

Spark 是在 Scala 语言中实现的，它将 Scala 用作其应用程序框架。与 Hadoop 不同，Spark 和 Scala 能够紧密集成，其中的 Scala 可以像操作本地集合对象一样轻松地操作分布式数据集。

### 10、Memcached -- 通用分布式内存缓存系统。
Memcached 是一套分布式快取系统，当初是 Danga Interactive 为了 LiveJournal 所发展的，但被许多软件(如：MediaWiki)所使用。Memcached 作为高速运行的分布式缓存服务器，具有以下的特点：协议简单，基于 libevent 的事件处理，内置内存存储方式。

### 11、Apache Hive -- 在 Hadoop 之上提供类似 SQL 的层。
Hive 是一个基于 Hadoop 的数据仓库平台。通过 hive，可以方便地进行 ETL 工作。hive 定义了一个类似于 SQL 的查询语言，能够将用户编写的 SQL 转化为相应的 Mapreduce 程序基于 Hadoop 执行。目前，已经发布了 Apache Hive 2.1.1 版本。

### 12、Apache Kafka -- 最初是由 LinkedIn 开发的高吞吐量，分布式订阅消息系统。
Apache Kafka 是一个开源消息系统项目，由 Scala 写成。该项目的目标是为处理实时数据提供一个统一、高通量、低等待的平台。Kafka 维护按类区分的消息，称为主题(topic)。生产者(producer)向 kafka 的主题发布消息，消费者(consumer)向主题注册，并且接收发布到这些主题的消息。kafka 以一个拥有一台或多台服务器的集群运行着，每一台服务器称为 broker。

### 13、Akka -- 用于在 JVM 上构建高并发，分布式和弹性消息驱动应用程序的工具包。
Akka 是一个用 Scala 编写的库，用于简化编写容错的、高可伸缩性的 Java 和 Scala 的 Actor 模型应用。它已经成功运用在电信行业，系统几乎不会宕机。

### 14、HBase -- 开放源代码，非关系型，分布式数据库，采用Google的BigTable建模，用Java编写，并在HDFS上运行。
与FUJITSU Cliq 等商用大数据产品不同，HBase 是 Google Bigtable 的开源实现，类似 Google Bigtable 利用 GFS 作为其文件存储系统，HBase 利用 Hadoop HDFS 作为其文件存储系统；Google 运行 MapReduce 来处理 Bigtable 中的海量数据，HBase 同样利用 Hadoop MapReduce 来处理 HBase 中的海量数据；Google Bigtable 利用 Chubby 作为协同服务，HBase 利用 Zookeeper 作为对应。

### 15、Neo4j -- 在 Java 中实现的开源图形数据库。
Neo4j 是一个高性能的 NOSQL 图形数据库，它将结构化数据存储在网络上而不是表中。它是一个嵌入式的、基于磁盘的、具备完全事务特性的 Java 持久化引擎。

### 16、CouchBase -- 开源分布式的 NoSQL 面向文档数据库，针对交互式应用程序进行了优化。
如果以前没有 NoSQL 的使用经验，那么理解 couchbase 的时候关键有两点：延后写入和松散存储。该产品基于 Apache CouchDB，并整合了 GeoCouch(一个基于 Erlang、紧密集成的地理空间索引系统，可支持 LBS 应用)。

### 17、Apache Storm -- 开源分布式实时计算系统。
Apache Storm 是一个能近实时地在数据之上运行用户代码片段的流式数据处理框架。它实际上是一系列连在一起的管道。通常用于简单的分析任务，诸如计算，以及清洗，使其常规化，并且准备摄入用于长期存储的数据。

### 18、CouchDB -- 开源的面向文档的NoSQL数据库，使用JSON存储数据。
CouchDB 是一个开源的面向文档的数据库管理系统，可以通过 RESTful JavaScript Object Notation (JSON) API 访问。CouchDB 落实到最底层的数据结构就是两类 B+Tree 。

### 19、Oracle Coherence -- 内存数据网格解决方案，通过提供对常用数据的快速访问，使企业能够可预测地扩展关键任务应用程序。
简单来说，Coherence 仅支持 Java、.NET 和 C++ 三种语言的 API，这三个都是面向对象的语言，这也说明 Coherence 和应用开发的亲和性。

### 20、Titan -- 可扩展的图形数据库，优化用于存储和查询包含分布在多机集群上的数百亿个顶点和边的图形。
支持不同的分布式存储层：Cassandra 1.1 和 HBase 0.92。原生实现 Blueprints graph API，Gremlin graph traversal language，Frames graph-to-object mapper，Rexster graph server。

### 21、Amazon DynamoDB -- 快速，灵活的全面管理 NoSQL 的数据库服务，适用于任何规模的要求一致性，单位毫秒延迟的应用程序。
Amazon DynamoDB 是一种完全托管的 NoSQL 数据库服务，提供快速而可预测的性能，能够实现无缝扩展。

### 22、Amazon Kinesis -- AWS 上的实时流式传输数据平台。
Web 应用程序、移动设备、可穿戴设备、行业传感器和许多软件应用程序和服务都可能生成大量的流数据(有时达到每小时数 TB)，需要对其进行连续地收集、存储和处理。Amazon Kinesis 就是针对这种需求产生的。

### 23、Datomic -- 完全事务，云就绪，分布式数据库，用 Clojure 编写。
Datomic 是一个灵活的、基于时间因子的数据库，支持联合查询，具有弹性的可扩展性以及支持 ACID 事务性。Datomic 提供高可用的、分布式存储服务。
