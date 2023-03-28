# 用 Neattext 管道预处理推文

> 原文：<https://pub.towardsai.net/preprocessing-tweets-with-neattext-pipeline-cce8ce173ce7?source=collection_archive---------2----------------------->

## 使用 python 创建管道来高效清理 tweets

![](img/fa786eaa150e3c03ba5f30fb177e64f5.png)

丹尼尔·索罗金在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上拍摄的照片

## 介绍

如果使用得当，文本数据可以保存如此多的信息。然而，原始文本数据通常是杂乱的。它将**【联合国】**置于**【非结构化】**之中，处理起来可能会非常令人生畏。

> 对我来说，另一件让清理文本数据变得困难的事情是使用不同的包并下载其依赖项来清理文本。

老实说，文本清理的程度取决于需要。

例如:如果您的目标是从文本中提取有用的信息，如电子邮件、URL 或姓名，那么您需要做的就是找到一种方法来获取这些组件，并丢弃文本中的其余单词

如果你的目标是建立一个主题模型并对文档进行分类，那么首先要做的两件事是停用词和标点符号。此外，电子邮件、网址和姓名可能无关紧要，因为它们最终对目标没有价值。

**假设我们想要从推文数据中构建一个文本情感模型。在这种情况下，停用词对于这样的模型理解句子是非常有用的。因为像“not”这样的停用词可能是判断一个句子是肯定句还是否定句的关键。**

让我们思考一下对我们的目标没有用的 tweet 文本的一些细微差别

*   用户名，如 **@anitaokoh、**等。
*   标签，如**#有用词、**等。
*   推文语言，如**“Retweet”、“Re-ping”**等。
*   像 **I'd，let's，**等单词缩写。
*   用户可能提供的其他信息，如**电子邮件、URL 等**
*   其他潜在的干扰，如 Html 标签、表情符号、标点符号等

> 不言而喻，将文本数据小写作为预处理步骤通常是明智的

这个列表并不详尽，因为 tweets 中可能有其他对模型没有价值的噪声。此外，你可以清理短信的范围是有限的，因为短信可以很狡猾地使用缩写、缩写等。这就是为什么 EDA(探索性数据分析)的力量和决定在哪里停止发挥作用。

**在下面的代码演示中，我们将尝试使用简洁的文本管道函数有效地从 tweets 中删除上面突出显示的那些组件。**

> **关于 NeatText 库**
> 
> 这是一个简单的 NLP 包，用于清理文本数据和文本预处理。
> 
> 它提供了 5 个主要的处理文本数据的类
> 
> - TextFrame:一个类似框架的对象，用于清理文本
> 
> - TextCleaner:删除或替换细节
> 
> - TextExtractor:提取不需要的文本数据
> 
> - TextMetrics:单词统计和度量
> 
> - TextPipeline:在一个管道中组合多个函数
> 
> 更多关于它的细节[这里](https://pypi.org/project/neattext/)

## 代码演示

使用的数据是推特的集合，可以在 Kaggle [这里](https://www.kaggle.com/datasets/pashupatigupta/emotion-detection-from-text)找到。

> (附注:这些数据有公共许可证，所以也可以自由探索这些数据)

1.  **将数据读入数据帧**

```
import pandas as pddf = pd.read_csv("tweet_emotions.csv")df.head()
```

数据帧预览如下所示

使用 Deepnote 的作者代码

**2。根据上面**突出显示的要删除的内容列表，导入 NeatText 库和函数

```
from neattext.pipeline import TextPipelinefrom neattext.functions import  remove_emails, fix_contractions, remove_numbers,remove_emojis,remove_special_characters, remove_stopwords, remove_html_tags, remove_urls, remove_puncts,remove_custom_pattern
```

**3。为函数**创建函数

我们的渠道将分为三个功能

*   用于**删除 Tweets** 中特定细微差别的函数，如用户名、标签等

```
def remove_specific_patterns(text, pattern): return remove_custom_pattern(text, pattern)
```

*   该功能用于**去除典型文本消息(如电子邮件、表情符号、URL 等)中的特定噪声**

```
def specific_cleaning(text):
    specific_cleaning = TextPipeline(steps=[fix_contractions, remove_emails,remove_emojis, remove_html_tags, remove_urls]) return specific_cleaning.fit(text)
```

*   该功能用于去除文本中的**一般噪声**，如标点符号、数字和特殊字符(如果存在且未从之前的功能中去除)。

> 如果需要，这个函数也可以删除停用词。但是在这种情况下，需要停用词。

```
def final_cleaning(text, pattern):
    msg = remove_specific_patterns(text, pattern)
    almost_clean_text = specific_cleaning(msg)
    general_cleaning = TextPipeline(steps=[remove_numbers,remove_special_characters, remove_puncts])
    return general_cleaning.fit(almost_clean_text)
```

> 注意:第三个函数也调用前面的两个函数

我们可以只有一个功能而不是三个功能吗？

是的，你可以

**这样做的唯一原因是避免一种方法在清理文本时与另一种方法冲突，从而造成混乱，例如，将电子邮件删除功能和标点符号删除功能放在同一个功能中可能会转换，也可能不会转换**

> 我的电子邮件是 anita@gmail.com

**到此**

> 我的邮箱是 anitagmailcom

这对我们来说毫无意义。

**4。调用函数并打印数据帧预览**

在调用数据帧上的函数之前，下面是调用数据帧第一行上的函数的输出。所以下面这段文字:

> `@tiffanylue i know i was listenin to bad habit earlier and i started freakin at his part =[`

成为

> `i know i was listenin to bad habit earlier and i started freakin at his part`

现在，我们调用数据帧上的函数

```
df["clean_message"] = df.apply(lambda x: final_cleaning(x.content, r'@\w+|#\w+|Re-pinging'), axis=1)
```

输出如下所示

使用 Deepnote 的作者代码

## 结论

有了这个数据集，您可以通过可视化/分析文本进行更多的探索，看看是否有任何模式噪声可以消除，或者是否有一些重要的东西可以添加到文本中。或者，您可以使用此文本构建模型，并评估结果。

> 使用此[链接](https://anitaokoh.medium.com/membership)订阅媒体，并获取媒体上的所有报道