# Apache Spark 工具哪个最好？

> 原文：<https://pub.towardsai.net/devops-639e377fffc5?source=collection_archive---------2----------------------->

## [数据工程](/object-storage-521d5454d2d?source=false---------2)

提供使用 Apache Spark 的不同工具的背景知识

![](img/9fcb2ce5f57a5af779f388261e159ee7.png)

[王华伦](https://unsplash.com/@wflwong?utm_source=medium&utm_medium=referral)在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上的照片

在您将代码推向舞台以在云中测试它之前，您是在最后一次注视您的代码运行。您会看到一个弹出的错误，显示“连接丢失”“又来了？”你心里想。这还不到我在这些 Python 作业中需要处理的数据的十分之一。

这种情况对我来说非常熟悉，可能对你也是如此。在今天的文章中，我想讨论 Apache Spark —它是什么？我为什么要用它？还有最重要的，我该挑哪个味道的 spark 平台？

**背景**

在我们谈论 Spark 之前，我需要先谈谈 MapReduce 框架。

MapReduce 是一种编程范式，能够在 Hadoop 集群中的数百或数千台服务器之间实现巨大的可伸缩性。术语“MapReduce”指的是 Hadoop 程序执行的两个独立且截然不同的任务。第一个是映射作业，它获取一组数据并将其转换为另一组数据，其中各个元素被分解为元组(键/值对)。reduce 作业将映射的输出作为输入，并将这些数据元组组合成一个更小的元组集。尽管这种模式确实大大减少了处理数据集的时间，特别是在 Google 的 PageRank 算法和类似的算法中，但是 MapReduce 的主要限制是它需要在运行每个作业后将整个数据集保存在 HDFS 中。这个原因激发了 Apache Spark 的产生。

Apache Spark 于 2009 年作为加州大学伯克利分校的一个研究项目启动，并于 2010 年初开源。Apache Spark 并不仅仅使用映射和简化函数，而是拥有一大组称为转换的操作。Apache Spark 还会在每次操作之间将数据缓存在内存中，从而加快后面的处理。

**火花的内部工作原理**

我们已经介绍了一些关于 Spark 及其优势的历史。现在让我们来谈谈 Apache Spark 是如何工作的。下面是一个过于简化的图表，展示了 Spark 的基础设施。

![](img/79e1c81559c09891a9cae41e50a994c0.png)

design⁴星火建筑

您有一个与集群管理器对话的 SparkContext，集群管理器调度作业。根据您的喜好，集群管理器可以是独立的、Apache Mesos、Hadoop Yarn 或 Kubernetes。集群管理器将作业分配给工作节点，然后执行。非常类似于现代分布式系统的样子。

# 设置 Spark 的方法

在您设置这些集群之前，我强烈建议您只设置一个单节点(您的本地笔记本电脑，等等。)使用 spark 集群并自己完成安装。我知道这是乏味的，但你会看到火花的特点。

**火花独立集群**

在这种类型的设置中，您将自己设置 spark 服务器并维护其所有奇妙的复杂性，无论是在云上还是在数据中心。此外，如果您想要使用这种类型的设置，您将不得不投入大量资源来设置这个基础架构和维护这些服务器。

设置这个的最好方法是使用 [Cloudera](https://docs.cloudera.com/) 。他们做了大量的工作，尽可能地使指令简单明了。

**云中托管 Spark 集群(Azure HDInsight、亚马逊 Web 服务 EMR、谷歌云平台 Dataproc)**

第二种类型的设置是我所说的中间设置。在这些实例中已经处理了安装和设置，但是这些并不是云不可知的。

您可以在设置时添加其他参数或包。

**亚马逊网络服务**

这是 AWS 的。我注意到这个服务没有很好地与 AWS 中的其他服务集成。如果你计划使用任何其他服务作为 EMR 包的一部分，他们在包升级上落后了。

[](https://aws.amazon.com/emr/) [## 大数据平台-亚马逊 EMR -亚马逊网络服务

### Amazon EMR 运行大数据应用程序和 Pb 级数据分析的速度更快，成本不到……

aws.amazon.com](https://aws.amazon.com/emr/) 

Redshift 是 AWS 的数据仓库，也不容易通过 EMR 访问；相反，您应该使用 Databricks 产品，这将在下面讨论。

**谷歌云平台**

Dataproc 是 Google 云平台中的托管 Spark 服务。这是三个服务中与其他服务集成程度最高的一个。

[](https://cloud.google.com/dataproc) [## Dataproc |谷歌云

### 发送反馈了解如何在 Google Cloud 上的开放式集成数据分析中简化企业分析…

cloud.google.com](https://cloud.google.com/dataproc) 

**微软 Azure**

最后，Azure HDInsight。这是三个中我用得最少的一个。

[](https://azure.microsoft.com/en-us/services/hdinsight/#overview) [## Azure HDInsight - Hadoop、Spark 和 Kafka |微软 Azure

### Myntra 加速其数字化转型 Myntra 与微软密切合作，将其平台从…

azure.microsoft.com](https://azure.microsoft.com/en-us/services/hdinsight/#overview) 

**数据砖块平台**

这是一整套。说实话，这个平台本身就要求满岗。但是我在本地计算机或虚拟机上使用 spark 的大部分经验表明，使用 Databricks 是非凡的，值得付出额外的成本。我是做一站式的，所以什么都做。Databricks 允许我在这个平台上做任何事情。当然，当时也有一些小问题，比如 git 集成和安全性。幸运的是，他们现在增加了增量共享和更紧密的 git 集成。这是他们最令人钦佩的特点之一——他们如何与其他开源项目紧密集成，并将这些新功能快速实现到他们的代码库中。

老实说，出于这些原因，我肯定会选择 Databricks 及其价格标签，而不是任何其他选择。

在这里，我写了一个 Apache Spark 生态系统的快速概述和一些利用这种设置的工具。

```
**Resources
1\.** [https://spark.apache.org/history.html](https://spark.apache.org/history.html)
2\. [https://www.ibm.com/topics/mapreduce](https://www.ibm.com/topics/mapreduce)
3\. [https://patents.google.com/patent/CN103279328A/en](https://patents.google.com/patent/CN103279328A/en)
4\. [https://spark.apache.org/docs/latest/cluster-overview.html](https://spark.apache.org/docs/latest/cluster-overview.html)
```