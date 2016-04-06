---
layout: post
title: storm学习笔记
category : 技术分享
tagline: "Supporting tagline"
tags : [storm,基础]
published: true
---
{% include JB/setup %}
# storm学习笔记
---

Storm的现实模型就是水流的处理，例如小区供水。

- 数据来源定义为Spout，`源源不断` 的供给水流。
- 水流在管道中流行，定义为Stream。
- 每个住户都会消费水，是Stream中的一个节点，定义为Bolt。`可能会将消费的水排放，也或许不排。`
- 一个小区的Spout、Stream、Bolt组合在一起，即一个拓扑结构，定义为Topology。

强调部分，在Storm的实现中，真的就是这么做的。我会在后面的文章中去解释。

Storm实现：

- Spout：        数据源，源源不断的发送元组数据 Tuple
- Tuple：         元组数据的抽象接口，可以是任何类型的数据。但是必须要可序列化。
- Stream：      Tuple的集合。一个 Stream内的 Tuple拥有相同的源。
- Bolt：             消费Tuple的节点。消费后可能会排出新的 Tuple到该 Stream上，也可能会排到到其他 Stream，也或者根本不排。可并发。
- Topology： 将 Spout、 Bolt整合起来的拓扑图。定义了 Spout和 Bolt的结合关系、并发数量、配置等等。



