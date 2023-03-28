# 综合生成基线标记数据

> 原文：<https://pub.towardsai.net/synthetically-generating-a-baseline-labeled-data-b11e346498dc?source=collection_archive---------3----------------------->

## 如何生成乱码和非乱码电子邮件的标签数据集

![](img/90aa357fae37bb59830da9d76ac22543.png)

照片由[海伦娜·赫兹](https://unsplash.com/@imperiumnordique?utm_source=medium&utm_medium=referral)在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上拍摄

## 介绍

关于数据的一些流行说法是

> 数据无处不在

或者

> 大数据正在兴起

***的微妙和，在我看来*** ，最重要的是

> 相关的现实生活数据通常不容易获得，并且通常是杂乱的、非结构化的，并且在大多数情况下是没有标记的。

这句话在商业场景中非常适用。监督模型的一个关键要素是**训练的先验标记数据。**

业务团队找到创造性的方法来标记可用于训练模型的数据。

三种主要方式

*   人类标记
*   基于规则的标注
*   合成数据标记

*不要误会，上面的列表并不详尽，因为还有其他方法，如* ***无监督/半监督模型标记*** *。但就像上面提到的方法一样，它们只是代理标记，因为即使是人类标记也会有错误。*

我们今天要关注的一种方法是**合成数据标记**。这涉及到人工生成的数据，既有正面的也有负面的情景要识别。反过来，这可以用于训练/建立基线模型，该模型可以随着时间的推移得到改进和监控。

*(通常建议在生产初期以影子模式实现此类模型)*

假设我们想知道一封进入数据库的电子邮件是不是乱码。我们没有现成的标记数据来进行分类，而且人工标记很昂贵。实事求是地说，预计数据库中的乱码邮件和非乱码邮件的类别会不平衡。该团队决定综合生成带有电子邮件标签的电子邮件类型，因为这似乎比其他选项更容易。

为此，我们需要两样东西。

*   获取无意义的文本或单词
*   访问令人信服、格式正确的电子邮件

所有这些都将在 python 中完成

**对于乱码文本数据集**，[这个](https://www.kaggle.com/datasets/johnwdata/gibberish-text-classification?select=Gibberish.csv)数据集来源于 Kaggle。

**为了让人相信格式正确的电子邮件**，我们将使用一个名为 **Faker** 的库来生成它们。Pip 安装库，以便继续。

*为了简单起见，我们将只考虑三个最受欢迎的域名的电子邮件:gmail.com、yahoo.com 和 hotmail.com*

关于数据集，乱码文本来源于此，它是通过汇编成千上万个糟糕的亚马逊调查回复创建的。

## 代码演示

代码步骤可以总结为 4 个步骤

*   读那些胡言乱语
*   创建类似胡言乱语的电子邮件和看起来真实的电子邮件
*   标记两种电子邮件类型并合并数据
*   转换为 Pandaframe 并存储/保存数据

## **1。念着胡言乱语的文字**

```
import pandas as pddf = pd.read_csv('/work/Gibberish.csv')df['Response'] = df['Response'].str.replace(' ', '')focus_df = df[df['Response'].str.len() <= 21]
gibberish_text = list(focus_df['Response'])
```

上面的代码读取乱码文本数据，删除文本之间的所有空格，而**为了简单起见**，只获取长度小于或等于 21 的文本。然后将乱码文本列转换为列表。

输出列表如下所示。

## 2.创建类似胡言乱语的电子邮件和看起来真实的电子邮件

```
from faker import Fakerimport randomfake = Faker()def transform(number, text_list=None): domain_list = ['gmail.com', 'yahoo.com', 'hotmail.com'] if text_list is not None: result = [random.choice(text_list) for i in range(number)] result = [i+'@'+random.choice(domain_list) for i in result] else: result = [fake.profile()['mail'] for _ in range(2000)] return resultgibberish_list = transform(2000, gibberish_text)email_list = transform(2000)
```

上面的代码

*   实例化 **Faker** 类，该类用于在创建的函数中生成 2000 封看起来令人信服的电子邮件
*   该功能还用于随机选择 2000 个乱码文本，并将每个文本与随机选择的域连接起来。

乱码邮件的输出如下所示。

## 3.标记两种电子邮件类型并合并

```
def label_and_zip_list(label_constant, list_name): tag = [label_constant] * len(list_name) return list(zip(list_name, tag)) gibberish_zip = label_and_zip_list(1,gibberish_list )email_zip = label_and_zip_list(0,email_list)email_zip.extend(gibberish_zip)
```

从上面的代码中，两种电子邮件类型都被标记并存储在 python zip 中

## 4.将压缩数据转换为 Pandaframe 并存储/保存数据

```
data = pd.DataFrame(email_zip, columns=['email', 'label'])
data.to_csv('labelled_email_types.csv',index=False)
```

数据帧的输出如下所示

## 结论

恭喜你，你现在有了乱码邮件标记的数据，可以用作基线数据集来训练和建立基线模型。这并不需要很多资源。当然，这种方法也有一些问题，其中一个明显的问题就是样本偏差。然而，这是构建一个基线模型的良好开端，可以对其进行分析、监控、评估和改进。这就是数据科学和机器学习的美妙之处。这是一个迭代的过程，一开始总会有“不那么完美”的模型。

> 你不能改进还没有建成或完成的东西。总会有一个**版本 1**

> 使用此[链接](https://anitaokoh.medium.com/membership)订阅媒体，并获取媒体上的所有报道