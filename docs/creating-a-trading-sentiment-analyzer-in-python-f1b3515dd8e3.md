# 用 Python 创建“交易情绪分析器”

> 原文：<https://pub.towardsai.net/creating-a-trading-sentiment-analyzer-in-python-f1b3515dd8e3?source=collection_archive---------0----------------------->

## [自然语言处理](https://towardsai.net/p/category/nlp)

## 使用 Google News API 开发 NLP 驱动的交易工具情绪分析器

![](img/e46541c53130b8c768abc1f20bb01251.png)

[M. B. M.](https://unsplash.com/@m_b_m?utm_source=medium&utm_medium=referral) 在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上的照片

# 介绍

交易情绪分析仪将通过分析互联网上的相关和当前新闻文章来计算任何股票、货币、商品或指数的标准化“情绪”得分。解释这个节目的视频可以在[这里](https://www.youtube.com/watch?v=7c5EzELQ_7c&feature=youtu.be)找到。**源代码**可以在[这里](https://github.com/mkhorasani/Trading_Sentiment_Analyzer)找到。

# 程序的功能是什么？

交易者熟知股票市场和交易中的“情绪”现象。专业交易者在考虑是否购买某个工具时，不仅要参考基本面技术指标，还要观察对该工具的看法。交易情绪分析器将通过从谷歌新闻 API 的新闻文章中检索文本信息来分析用户请求的任何货币、商品、加密货币、股票或指数。随后，在分析各种文章后，该工具将提供该工具的一天、一周、一个月和整体“情绪”的量化分数。完全看涨(积极)的情绪将得到 1.0 分，而完全看跌(消极)的情绪将得到-1.0 分。任何介于两者之间的分数都将表明该交易工具具有积极或消极情绪的程度。情绪值是标准化的，可以用来与市场上的其他交易工具进行比较。

# 谁将从这样的计划中受益？

整个交易社区都可以从这种工具中受益，包括但不限于私人投资者、机构投资者、银行、保险公司等。基本上，任何打算在交易时做出更经验性决策的个人或实体都可以通过了解该交易工具的短期未来而受益，从而增加他们获得回报的可能性。然而，有必要承认，这种技术指标并不总是或完全准确，用户必须始终保持谨慎。

# 在线运行

要在线运行该程序，请访问以下网址[mkhorasani.pythonanywhere.com](https://mkhorasani.pythonanywhere.com/)。

# 本地运行

要在您的本地机器上安装并运行该程序，请按顺序执行以下步骤。

## Python 3.4

如果您尚未安装 Python，请在此处安装 Python 3.4 或更高版本的[。](https://www.python.org/downloads/release/python-340/)

## 工具包:

## 点

首先，通过下载并解压[pip-18.1.tar.gz 来安装 pip 工具包。](https://pypi.org/project/pip/#files)然后在命令提示符(行解释器)中键入以下代码行:

```
set path=%path%;C:/Python34/
cd C:/Users/**/***/pip-18.1/
python setup.py install
```

** *账户用户名*

* * **pip-18.1 安装文件夹的根目录*

## 新闻 api

在命令提示符(行解释器)中键入以下代码行:

```
set path=%path%;C:/Python34/Scripts/
pip install newsapi
```

## 要求

在命令提示符(行解释器)中键入以下代码行:

```
set path=%path%;C:/Python34/Scripts/
pip install requests
```

## tkinter

在命令提示符(行解释器)中键入以下代码行:

```
set path=%path%;C:/Python34/Scripts/
pip install tkinter
```

## metapy

在命令提示符(行解释器)中键入以下代码行:

```
set path=%path%;C:/Python34/Scripts/
pip install metapy
```

## 收集

在命令提示符(行解释器)中键入以下代码行:

```
set path=%path%;C:/Python34/Scripts/
pip install collections
```

要在本地运行此脚本，请将以下文件复制并粘贴到您的根目录中:

1.  [美国运输安全管理局 v1.0.py](https://github.com/mkhorasani/Trading_Sentiment_Analyzer/blob/master/TSA%20v1.0.py)
2.  [lemur-stopwords.txt](https://github.com/mkhorasani/Trading_Sentiment_Analyzer/blob/master/lemur-stopwords.txt)
3.  答。GUI 的 gif 图片。

随后，您必须修改以下代码行以反映根目录的位置:

第 50 行:`logo = PhotoImage(file='C:/Users/**/***/****.gif')`

第 269 行:`logo = PhotoImage(file='C:/Users/**/***/****.gif')`

第 310 行:`logo = PhotoImage(file='C:/Users/**/***/****.gif')`

第 130 行:`tok1 = metapy.analyzers.ListFilter(tok1, "C:/Users/**/***/lemur-stopwords.txt", metapy.analyzers.ListFilter.Type.Reject)`

第 181 行:`tok2 = metapy.analyzers.ListFilter(tok2, "C:/Users/**/***/lemur-stopwords.txt", metapy.analyzers.ListFilter.Type.Reject)`

第 232 行:`tok3 = metapy.analyzers.ListFilter(tok3, "C:/Users/**/***/lemur-stopwords.txt", metapy.analyzers.ListFilter.Type.Reject)`

** *账户用户名*

*** *交易情绪分析仪安装文件夹的根目录*

## 谷歌新闻 API

请在此向谷歌新闻 API [注册，以获得您自己的 API 密钥。随后，在以下代码行中用您自己的密钥替换当前的 API 密钥:](https://newsapi.org/s/google-news-api)

第 113 行:“apiKey= *你的 API 键在这里*

第 164 行:“apiKey= *你的 API 键在这里*”

第 215 行:“apiKey= *您的 API 密钥在这里*”

# 使用

## 在线运行

要在线使用该程序，只需在输入字段中输入交易工具的名称，然后点击“生成报告”按钮。您将被带到显示以下信息的页面:

```
----------------------------------- TRADING SENTIMENT ANALYZER        RESULTS -----------------------------------Sentiment Values Range From -1 to +1             -1 = Negative Sentiment           +1 = Positive SentimentTrading Instrument: aaplOne Day Sentiment: -0.22One Week Sentiment: -0.05One Month Sentiment: -0.13Overall Sentiment: -0.13
```

请注意，我们所说的“交易工具”是指任何股票、货币、商品、指数基金等。请不要在输入字段中输入不相关的单词或短语，因为您将在报告中收到如下所示的“不适用”值。

```
----------------------------------- TRADING SENTIMENT ANALYZER RESULTS -----------------------------------Sentiment Values Range From -1 to +1             -1 = Negative Sentiment           +1 = Positive SentimentTrading Instrument: berlinOne Day Sentiment: N/AOne Week Sentiment: N/AOne Month Sentiment: N/AOverall Sentiment: N/A
```

在特殊情况下，你可能会收到一个不相关条目的分数，但是，分数只会反映关于你的条目的情绪，通常是无目的的。

## 本地运行

在成功安装了上一节中解释的所有必需的工具包和代码修改后，您可以在 Python IDE 打开时通过点击“F5”键来执行 TSA v1.0.py 脚本。随后，将出现一个窗口，提示您输入交易工具的名称，然后您可以点击“生成报告”按钮。将显示一个包含以下信息的新窗口:

```
----------------------------------- TRADING SENTIMENT ANALYZER RESULTS -----------------------------------Sentiment Values Range From -1 to +1             -1 = Negative Sentiment           +1 = Positive SentimentTrading Instrument: aaplOne Day Sentiment: -0.22One Week Sentiment: -0.05One Month Sentiment: -0.13Overall Sentiment: -0.13
```

如果在输入字段中输入了不相关的内容，则会出现另一个窗口，显示以下消息:

```
No information found for this instrument.

                                    Please try another trading instrument.
```

# 解读分数

“情绪”分数范围是从-1 到+1 的相对分数。-1 代表完全消极的情绪，而+1 代表完全积极的情绪，0 代表完全中立的情绪。大多数情况下，分数会介于两者之间，最多显示两位小数。分数如下所示:

一天感悟:(对互联网上一天新闻的感悟)

一周感悟:(对互联网上一周新闻的感悟)

一个月感悟:(对互联网上一个月新闻文章的感悟)

总体情绪:(一天、一周和一个月情绪得分的算术平均值，权重相等)

因此，负的分数表明对交易工具的看法是消极的，也许最好不要购买该工具，或者如果你已经拥有该工具，你可能想卖掉它。反之亦然，正分数表明对交易工具的看法是积极的，也许最好购买该工具，或者如果你已经拥有该工具，你可能希望继续持有。

# 密码

下面的选择将揭示该程序的各个部分，并提供如何修改该程序以满足用户需求的概述。

## 工具包

第 13–22 行:程序的这一部分简单地导入了程序中使用的工具包。目前，使用以下工具包:

1.  newsapi —用于从 Google 新闻 api 中检索文章
2.  日期时间—用于动态生成时间戳，这些时间戳用于检索特定日期的新闻文章
3.  时间—用于更改时间戳，以便检索过去日期的新闻文章
4.  请求—用于发出 http 请求
5.  tkinter —用于设计和执行图形用户界面
6.  metapy —用于对检索到的新闻文章的文本进行分词、词干提取和应用其他过滤器
7.  计数器—用于计算单词数组中单词的出现次数

## 图形用户界面

第 28–77 行:程序的这一部分使用工具包“tkinter”构建一个 GUI 窗口，允许用户输入他们需要的交易工具并相应地生成一个报告。本节还构建了另一个 GUI 窗口，提醒用户他们已经输入了一个空字段。在此部分可以修改的参数包括尺寸、布局、静态图像、静态文本等。GUI 窗口的。

## 日期和查询格式

第 86–97 行:程序的这一部分创建了一个名为 query 的空变量，该变量将被分配给前面部分中 GUI 的输入字段。然后，这个变量将被附加到另一个名为“trading”的字符串上，形成一个查询，如“aapl trading”。然后，这个查询将用于检索以下部分中的相关新闻文章。同样在这部分代码中，日期和时间工具包将用于创建 1 天、1 周和 1 个月的时间戳，这些时间戳将在下面的部分中用于检索这些时间段内的新闻文章。

## 一天的感悟

第 105–149 行:这部分代码使用带有 Google News API 的格式化查询来检索一天内的新闻文章。随后，metapy 工具包将用于对检索到的文本进行解析、标记、词干提取和应用其他过滤器。然后，计数器工具包将用于对标记化列表中的负项`NS1`和正项`PS1`的实例进行计数。情感得分将通过计算正负词语之间的差异`(PS1 - NS1)`来计算，然后将结果除以正负词语的总数`(PS1 - NS1)/(PS1 + NS1)`来归一化。最终分数将四舍五入到小数点后两位。Google 新闻 API 可以修改为包括不同的域(新闻网站)、不同的排序方法，即发布日期/相关性/受欢迎程度、新闻文章语言和页面大小(返回结果的数量)。正面和负面术语的列表也可以被修改，以在“术语频率”计数中添加或删除术语。

## 一周感悟

第 156–200 行:这部分代码使用带有 Google News API 的格式化查询来检索一周内的新闻文章。随后，metapy 工具包将用于对检索到的文本进行解析、标记、词干提取和应用其他过滤器。然后，计数器工具包将用于统计标记化列表中负面术语`NS2`和正面术语`PS2`的实例。情感得分将通过计算正负词语之间的差异`(PS2 - NS2)`来计算，然后将结果除以正负词语的总数`(PS2 - NS2)/(PS2 + NS2)`来归一化。最终分数将四舍五入到小数点后两位。Google 新闻 API 可以修改为包括不同的域(新闻网站)、不同的排序方法，即发布日期/相关性/受欢迎程度、新闻文章语言和页面大小(返回结果的数量)。正面和负面术语的列表也可以被修改，以在“术语频率”计数中添加或删除术语。

## 一个月感悟

第 207–251 行:这部分代码使用带有 Google News API 的格式化查询来检索 1 个月内的新闻文章。随后，metapy 工具包将用于对检索到的文本进行解析、标记、词干提取和应用其他过滤器。然后，计数器工具包将用于对标记化列表中的负项`NS3`和正项`PS3`的实例进行计数。情感得分将通过计算正负词语之间的差异`(PS3 - NS3)`来计算，然后将结果除以正负词语的总数`(PS3 - NS3)/(PS3 + NS3)`来归一化。最终分数将四舍五入到小数点后两位。Google 新闻 API 可以修改为包括不同的域(新闻网站)、不同的排序方法，即发布日期/相关性/受欢迎程度、新闻文章语言和页面大小(返回结果的数量)。正面和负面术语的列表也可以被修改，以在“术语频率”计数中添加或删除术语。

## 出错信息

第 258–288 行:这部分代码构建了一个 GUI 窗口，当检索到的新闻文章中没有足够的正面或负面词汇时，该窗口会向用户发出警告。如果 1 天时间戳内的正项和负项的数量少于 3 `(PS1 + NS1) < 3`，则使用 tkinter 工具包触发错误消息，在新窗口中显示以下消息:

```
No information found for this instrument.

                                    Please try another trading instrument.
```

## 评分和报告图形用户界面

第 295–366 行:这部分代码使用 tkinter 工具包构建了一个 GUI 窗口，显示成功的情感分析结果。它显示交易工具，一天的情绪得分，一周的情绪得分，一个月的情绪得分和整体情绪得分。在此部分可以修改的参数包括尺寸、布局、静态图像、静态文本等。GUI 窗口的。只有在 1 天的时间戳`(PS1 + NS1 > 2)`内有 2 个以上的正项和负项时，GUI 才会被触发，这样做是为了过滤掉任何不相关的查询，这些查询可能有一些正项和负项，但在其他方面是不相关的。最终结果将显示如下:

```
----------------------------------- TRADING SENTIMENT ANALYZER RESULTS -----------------------------------Sentiment Values Range From -1 to +1             -1 = Negative Sentiment           +1 = Positive SentimentTrading Instrument: aaplOne Day Sentiment: -0.22One Week Sentiment: -0.05One Month Sentiment: -0.13Overall Sentiment: -0.13
```

# 放弃

这个程序的结果并不总是或完全准确。建议用户始终保持谨慎。

## 使用 Streamlit 开发 Web 应用程序:

[](https://www.amazon.com/Web-Application-Development-Streamlit-Applications/dp/1484281101?&linkCode=ll1&tag=mkhorasani09-20&linkId=a0cb2bc17df598006fd9029c58792a6b&language=en_US&ref_=as_li_ss_tl) [## 使用 Streamlit 开发 Web 应用程序:开发和部署安全且可伸缩的 Web 应用程序…

### 使用 Streamlit 开发 Web 应用程序:使用……开发安全且可扩展的 Web 应用程序并将其部署到云中

www.amazon.com](https://www.amazon.com/Web-Application-Development-Streamlit-Applications/dp/1484281101?&linkCode=ll1&tag=mkhorasani09-20&linkId=a0cb2bc17df598006fd9029c58792a6b&language=en_US&ref_=as_li_ss_tl) 

## 使用 Python 实现数据可视化:

[](https://www.coursera.org/learn/python-for-data-visualization?irclickid=xgMQ4KWb%3AxyIWO7Uo7Vva0OcUkGQgW2aEwvr1c0&irgwc=1&utm_medium=partners&utm_source=impact&utm_campaign=3308031&utm_content=b2c) [## 用 Python 实现数据可视化

### “一图胜千言”。我们都熟悉这个表达。它尤其适用于试图…

www.coursera.org](https://www.coursera.org/learn/python-for-data-visualization?irclickid=xgMQ4KWb%3AxyIWO7Uo7Vva0OcUkGQgW2aEwvr1c0&irgwc=1&utm_medium=partners&utm_source=impact&utm_campaign=3308031&utm_content=b2c) 

## 面向所有人的 Python 专业化:

[](https://www.coursera.org/specializations/python?irclickid=xgMQ4KWb%3AxyIWO7Uo7Vva0OcUkGQgW16Ewvr1c0&irgwc=1&utm_medium=partners&utm_source=impact&utm_campaign=3308031&utm_content=b2c) [## 面向所有人的 Python

### 学习用 Python 编程和分析数据。开发收集、清理、分析和可视化数据的程序…

www.coursera.org](https://www.coursera.org/specializations/python?irclickid=xgMQ4KWb%3AxyIWO7Uo7Vva0OcUkGQgW16Ewvr1c0&irgwc=1&utm_medium=partners&utm_source=impact&utm_campaign=3308031&utm_content=b2c) 

## GitHub 资源库:

[](https://github.com/mkhorasani/Trading_Sentiment_Analyzer) [## mkhorasani/Trading _ 情操 _ 分析器

### 交易情绪分析仪将通过以下方式计算任何股票、货币、商品或指数的标准化“情绪”得分

github.com](https://github.com/mkhorasani/Trading_Sentiment_Analyzer) 

# 新到中？您可以在此订阅和解锁无限文章[。](https://khorasani.medium.com/membership)