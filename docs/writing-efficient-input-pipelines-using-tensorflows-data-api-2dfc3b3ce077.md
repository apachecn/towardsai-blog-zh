# 使用 TensorFlow 的数据 API 编写高效的输入管道

> 原文：<https://pub.towardsai.net/writing-efficient-input-pipelines-using-tensorflows-data-api-2dfc3b3ce077?source=collection_archive---------1----------------------->

## [机器学习](https://towardsai.net/p/category/machine-learning)

## 大规模机器学习工程的数据集处理简介

![](img/d7772586532eadb5b9001912e607bfd8.png)

[克劳迪奥·泰斯塔](https://unsplash.com/@claudiotesta?utm_source=medium&utm_medium=referral)在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上拍摄的照片

# 问题陈述

处理非常大的数据集是机器学习工程中的常见场景。通常，这些数据集会太大而不适合内存。这意味着数据必须在训练过程中从磁盘上实时检索。

[磁盘访问比内存访问慢几个数量级](https://en.wikipedia.org/wiki/Memory_hierarchy)，因此高效的检索具有高优先级。

好在 [TensorFlow 的](https://www.tensorflow.org/guide/data) `[tf.data](https://www.tensorflow.org/guide/data)` [API](https://www.tensorflow.org/guide/data) 提供了一个简单直观的接口来加载、预处理，甚至预取数据。

在这篇文章中，我们将学习如何创建一个简单而强大的输入管道来使用`tf.data` API 有效地加载和预处理数据集。

# 使用 TensorFlow 数据 API 的输入管道

> 声明:TensorFlow 为**提供了优秀的**模块和 API 文档。更多详情，请参考[官方网站](https://www.tensorflow.org/api_docs/python/tf/data/)。

本教程的主角是`[tf.data.Dataset](https://www.tensorflow.org/api_docs/python/tf/data/Dataset)`。目标是:

*   使用`tf.data.Dataset.list_files()`静态方法从数据文件创建一个`tf.data.Dataset`
*   在`tf.data.Dataset`实例上应用一系列函数

## 创建数据集

`tf.data.Dataset.list_files()`从提供的文件路径列表或文件模式(正则表达式)中返回一个`tf.data.Dataset`。

> 我们将假设我们的数据集是存储如下的独立文件的集合:

```
datadir/
    file_001.csv
    file_002.csv
    ...
    file_n.csv
```

创建一个`tf.data.Dataset`文件路径:

`filepath_dataset = tf.data.Dataset.list_files(‘./datadir/file_*.csv’)`

文件路径是很好的第一步，但是我们需要在文件中找到实际的数据来学习。我们将链接一系列方法，从文件路径开始，到训练期间使用的实际数据结束。

## 转换数据

一些最常见和最有用的`tf.data.Dataset`方法有:`interleave()`、`shuffle()`、`batch()`和`prefetch()`。在本文中，我们将简要介绍其中的每一个。

## 交错

在模型的训练期间，打乱实例以避免由于训练数据的排序(例如，按字母顺序排序的文件)而学习虚假的模式可能是有益的。`interleave()`函数提供了一种简单的方法来对包含单独的较小文件的数据集进行粗粒度的洗牌。

> **粗粒度**在此上下文中表示在**文件级别**。更细粒度的洗牌将在**进行。csv 行级别**，我们很快就会看到。

通过使用`lambda`函数，我们从每个单独的文件路径生成一个`tf.data.experimental.CsvDataset` *。*

变量`csv_dataset`现在是对由一组`CsvDataset`数据集组成的`tf.data.Dataset` 的引用。`interleave()`方法将所有单独的`CsvDatasets`数据集组合(或*交错*)成一个单独的数据集(在本例中为`csv_dataset`)。

将`num_parallel_calls`设置为`tf.data.experimental.AUTOTUNE`会告诉 TensorFlow 自动选择最佳数量的线程来读取`.csv` 文件。这个**增加了流水线效率**，只要机器有支持多线程的多核处理器(今天大部分机器都有这个)。

## 洗牌

如前所述，混洗数据可以防止学习训练数据中的虚假模式。这也改善了基于梯度的方法的收敛性，例如使用[梯度下降](https://en.wikipedia.org/wiki/Gradient_descent)来训练神经网络。要打乱数据，使用`shuffle()`方法:

`shuffle_buffer_size`值指定缓冲区的大小，用于存储来自原始(未缓冲)数据集的数据。这个值应该根据数据集的大小和可用的内存量来设置。更多详情请参考`shuffle()` [文档](https://www.tensorflow.org/api_docs/python/tf/data/Dataset#shuffle)。

> 注意:验证或测试期间不需要洗牌。事实上，一些场景要求测试集上的预测按照与提供的测试数据相同的顺序发生(例如， [Kaggle](https://www.kaggle.com/) competitions)。请记住这一点，如果需要，请禁用洗牌！

## 一批

另一种常见的数据预处理技术是**批处理**数据，一次处理一小块，而不是一次处理整个数据集。这使得在非常大的数据集上处理和训练成为可能，因为它们不需要一次全部存储在存储器中。

## 预取

高效的深度学习管道利用 GPU 计算进行模型训练，而数据获取和预处理在独立的计算模块(如 CPU)上进行。

如果 GPU 必须等待 CPU 完成加载和预处理，那么它将*闲置*，无所事事地浪费宝贵的周期。**提前预取**数据有助于防止这种情况。这**极大地提高了效率**，因为它最大化了 GPU 的利用率(没有浪费或空闲的周期)。

指定预取数据就像调用`prefetch()`方法一样简单:

# 把所有的放在一起

将所有方法组合到一个函数中，最终的管道可能如下所示:

# 结论

在本文中，我们学习了使用`tf.data` API 创建一个简单而高效的输入管道。我们讲述了如何:

*   使用`tf.data.Dataset.list_files()`静态方法处理分成多个独立文件的非常大的数据集
*   通过利用多线程执行来实现并行
*   使用粗粒度数据洗牌和`interleave()`数据集方法改善收敛
*   使用`shuffle()`方法，通过细粒度的数据混排来改善收敛
*   使用`prefetch()`方法最大化 GPU 利用率
*   将所有这些概念合并到一个函数中，生成一个可供模型使用的数据集

这篇文章的灵感很大程度上来自于[用 Scikit-Learn，Keras & Tensorflow](https://github.com/ageron/handson-ml2) 实践机器学习中第 12 章的一个练习。**我强烈推荐这本书**。

## 来源

*   [使用 Scikit-Learn、Keras 和 TensorFlow 进行机器实践学习](https://www.oreilly.com/library/view/hands-on-machine-learning/9781492032632/)
*   官方 [TensorFlow](https://www.tensorflow.org/api_docs/python/tf/) 文档
*   [https://en.wikipedia.org/wiki/Memory_hierarchy](https://en.wikipedia.org/wiki/Memory_hierarchy)