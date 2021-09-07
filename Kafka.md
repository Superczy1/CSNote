## 概念

* 消息：record （key， value，时间戳）
* producer： 生产者， 生产鸡蛋（消息/记录 record）
* consumer：消费者， 吃鸡蛋
* topic：队列， 鸡蛋的标签，每类消息成为一个主题
* broker：kafka ， 装鸡蛋的篮子，已发布的消息保存在一组服务器中，称之为Kafka集群。集群中的每一个服务器都是一个代理（Broker）。 消费者可以订阅一个或多个主题（topic），并从Broker拉数据，从而消费这些已发布的消息。

## 分布式的流平台

* 发布和订阅消息，类似消息队列
* 以容错(故障转移) 的方式存储消息 (流)
* 在消息流发生时处理

## kafka-API

* Producer API: 发布消息到 一个或多个 topic中
* Consumer API: 订阅 一个或多个 topic ，并处理消息
* Stream API: 1 ~ n topic  ---> 1 ~ n topic 将输入流转换到输出流
* Connectot API: 可构建或运行可重用的生产者或消费者，将topic连接到现有的应用程序或数据系统。例如，连接到关系数据库的连接器可以捕获表的每个变更

## Topic 

* 消息的类别名
* 每个 Topic 有分区 log ，每个 partition 是不可变的，顺序的消息队列，可持续增加
* 每个 parition 中的消息都有偏移量，且唯一，（ps：类似索引）
* 分区的目的：处理更多的消息，不受单台服务器的限制； 分区作为并行处理单元
* **分布式**：log 的分区分布在集群中的多个服务器上，每个服务器处理自己的分区
  * 根据配置每个分区还可以复制到其他服务器作为备份容错
  * 每个分区有 leader ， 0 或多个 follower
  * leader 处理分区的读写请求，而 follow 被动复制
  * 若leader 泵机，其中的follower 会成为新的 leader
  * 平衡负载，一个服务器可能是一个分区的 leader ，又是另外一个分区的 follower

![img](https://img.orchome.com/group1/M00/00/01/KmCudlf7DsaAVF0WAABMe0J0lv4158.png)

<img src="https://img.orchome.com/group1/M00/00/01/KmCudlf7D2iALXG_AAIhinsLf_Q676.png" alt="img" style="zoom: 25%;" />

## 架构

* 存在消费者组，