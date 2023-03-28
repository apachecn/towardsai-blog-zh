# 用 Python 例子充分解释了 P 分布

> 原文：<https://pub.towardsai.net/fully-explained-p-distribution-with-python-example-6f6b4e689e97?source=collection_archive---------0----------------------->

## [数据科学](https://towardsai.net/p/category/data-science)

## 数据科学分析的统计学概念

![](img/2bf419dc617e80da8cea5a3ee27580d8.png)

由[克里斯·利维拉尼](https://unsplash.com/@chrisliverani?utm_source=medium&utm_medium=referral)在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上拍摄

**了解 P 值。**

假设检验是最容易被误解的概念。让我们试着用一个非常简单的例子来理解这个概念。

假设检验不过是根据你的数据记录检查你的假设是否正确。

一个例子让你更清楚的了解情况。

假设我说阿卡什是我班上最好的学生。现在，阿卡什仍然是我班上最好的学生，直到有人声称反对他。现在，我试图收集能够支持我所说的证据，即能够支持阿卡什是最好的学生的证据。现在，如果证据非常支持我，我已经被证明是正确的，我们将不得不相信阿卡什是最好的学生。但是，如果这个证据不能支持我，我们将不得不相信阿卡什不是我班上最好的学生。

现在，谈到术语，我认为正确的是“阿卡什是最好的学生”。这是无效假设。

零假设是被假定为正确的陈述。

有人反对我，说‘阿卡什不是最好的学生’，这是另一种假设。

替代假设是针对原假设的陈述。

我们讨论过，如果证据“非常”支持我，我将被证明是正确的，如果他们不“那么”支持我，我将无法证明我的观点。现在，将出现的问题是“非常多”和“没那么多”的标准。

***p 值:*** p 值是根据证据支持零假设的程度给出的分数。

如果这个值小于 0.05，即 5%，这意味着很少有证据支持零假设，因此，我们将不得不拒绝零假设。也就是说，我们不得不否认阿卡什是我们班最好的学生这一事实。

有时，p 值超过 0.05，这是α值的 5%，因此，它清楚地表明有大量的假设支持零假设，因此，我们不能拒绝零假设。这意味着我们没有拒绝这个事实(我们现在必须接受这个事实)，阿卡什是班上最好的学生。

0.05 可以被认为是一个阈值，根据该阈值来决定拒绝或不拒绝

零假设是基于。

现在，一个问题出现了，为什么只有 0.05 而不是别的？一般来说，0.05 是一个公差值。让我们来看看什么是公差值。

0.05 表示 5%。任何小于或等于 5%的都可以是 1%、2%、3%等等。现在，如果 1%的证据支持我的假设，即零假设，即“阿卡什是最好的学生”，我有两个选择:

为 1%的证据证明我是正确的而战，因此，我是正确的！

容忍和接受这 1%的证据支持可能是由于一些错误，可能是一些巧合，因此接受我可能是错误的，阿卡什可能不是最好的学生。

2%、3%、4%、5%也是如此，但仅此而已！我能容忍的只是 5%,我会假设超过 5%不可能是巧合，也不可能是因为误差。如果超过 5%的证据支持我的假设，我是正确的，因此，这就是为什么，如果 p 值大于 0.05，我们不能拒绝零假设。

所以，一般来说，容忍水平取 5%，但在某些情况下，决策不是很重要，或者我们可以容忍更多，这可以改为 10%或其他。

总结:如果 p 值小于或等于 0.05，我们可以拒绝零假设。如果大于 0.05，我们不能拒绝零假设。

为了更好地理解，让我们尝试实现一个示例。

我们有 32 个人的年龄数据，我们将从这个人群中随机抽取 10 个值作为样本。

对于一个假设，让我们的零假设，即(H0)是'样本和人口的平均年龄没有差异'。

另一个假设，即(Ha)将是“样本平均年龄和总体平均年龄之间存在一些显著差异”。

python 的实用性

```
#Creating a dataages = [10,20,35,50,28,40,55,18,16,55,30,25,43,18,30,28,14,24,
        16,17,32,35,26,27,65,18,43,23,21,20,19,70]#finding the length of the data
len(ages)#output:
32
```

现在，我们将发现时代的意义

```
import numpy as npages_mean = np.mean(ages)
print(ages_mean)#output:
30.34
```

现在，我们将为我们的假设取样本大小。

```
sample_size = 10
age_sample = np.random.choice(ages, sample_size)age_sample#output:
array([21,55,55,17,43,25,43,16,20,32])
```

现在，我们将在统计库的帮助下测试 p 值

```
from scipy.stats import ttest_1sampttest, p_value = ttest_1samp(age_sample, 30)print(p_value)#output:
0.58896
```

为了拒绝或不拒绝零假设，我们将其与标准值(即 0.05)进行比较。

```
#alpha value is 0.05 or 5%if p_value < 0.05:
    print("We reject the null hypothesis")else:
    print("We can not reject the null hypothesis")
```

我们可以看到我们是如何拒绝无效假设的。

我希望你喜欢这篇文章。通过我的 [LinkedIn](https://www.linkedin.com/in/data-scientist-95040a1ab/) 和 [twitter](https://twitter.com/amitprius) 联系我。

# 推荐文章

[1。NLP —零到英雄与 Python](https://medium.com/towards-artificial-intelligence/nlp-zero-to-hero-with-python-2df6fcebff6e?sk=2231d868766e96b13d1e9d7db6064df1)
2。 [Python 数据结构数据类型和对象](https://medium.com/towards-artificial-intelligence/python-data-structures-data-types-and-objects-244d0a86c3cf?sk=42f4b462499f3fc3a160b21e2c94dba6)3 .[Python 中的异常处理概念](/exception-handling-concepts-in-python-4d5116decac3?source=friends_link&sk=a0ed49d9fdeaa67925eac34ecb55ea30)
4。[为什么 LSTM 在深度学习方面比 RNN 更有用？](/deep-learning-88e218b74a14?source=friends_link&sk=540bf9088d31859d50dbddab7524ba35)
5。[神经网络:递归神经网络的兴起](/neural-networks-the-rise-of-recurrent-neural-networks-df740252da88?source=friends_link&sk=6844935e3de14e478ce00f0b22e419eb)
6。[用 Python](https://medium.com/towards-artificial-intelligence/fully-explained-linear-regression-with-python-fe2b313f32f3?source=friends_link&sk=53c91a2a51347ec2d93f8222c0e06402)
7 全面讲解了线性回归。[用 Python](https://medium.com/towards-artificial-intelligence/fully-explained-logistic-regression-with-python-f4a16413ddcd?source=friends_link&sk=528181f15a44e48ea38fdd9579241a78)
充分解释了 Logistic 回归 8。[concat()、merge()和 join()与 Python](/differences-between-concat-merge-and-join-with-python-1a6541abc08d?source=friends_link&sk=3b37b694fb90db16275059ea752fc16a)
的区别 9。[与 Python 的数据角力—第一部分](/data-wrangling-with-python-part-1-969e3cc81d69?source=friends_link&sk=9c3649cf20f31a5c9ead51c50c89ba0b)
10。[机器学习中的混淆矩阵](https://medium.com/analytics-vidhya/confusion-matrix-in-machine-learning-91b6e2b3f9af?source=friends_link&sk=11c6531da0bab7b504d518d02746d4cc)