# NLP 新闻密码| 08.23.20

> 原文：<https://pub.towardsai.net/nlp-news-cypher-08-23-20-eb83f076b39d?source=collection_archive---------1----------------------->

![](img/213676f9d97d4e9a1b63e0a7b52e8773.png)

照片由[阿德里安娜·吉奥](https://unsplash.com/@adrigeo_?utm_source=medium&utm_medium=referral)在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 拍摄

## 自然语言处理每周时事通讯

## 狂怒

W 帽子一周。让我们回顾一下。如果你还没听说，我们发布了 NLP 模型伪造🙈，再加上 AI 现在可以在混战中打败你，狂怒行动正在进行中。如果你喜欢这份时事通讯，请在 Medium 上关注我们，也别忘了为它鼓掌👏。

为了进一步评论 Fury，对于那些希望在短期内实习的人，我们有一个职位可以在医疗保健领域的 NLP 深度学习项目中工作。如果您对此感兴趣，并且您有深度学习建模的经验(以及强大的软件工程能力)，请通过 info [at] quantumstat[dot] com 联系我们。

## NLP 模型锻造

所以……NLP 模型伪造了 1，400 个 NLP 代码片段的集合，您可以无缝地选择它们来在 Colab 中运行推理！为什么使用模型锻造？！你可以在我们的博客中找到答案👇：

[](https://medium.com/towards-artificial-intelligence/the-nlp-model-forge-a46faac7b5b0) [## NLP 模型锻造

### 解锁 1，400 个 NLP 模型的推理

medium.com](https://medium.com/towards-artificial-intelligence/the-nlp-model-forge-a46faac7b5b0) 

## 链子

另外，这里有一个叫 chains 的 Colab。我们使用 Forge 的快速多功能性创建了一个笔记本，展示了如何在一个单一的管道中将模型链接在一起进行推理。

[](https://colab.research.google.com/drive/1Py7nyJO_sgOYf8Fh-2Dcn1JmxEJyUUor?usp=sharing) [## 谷歌联合实验室

### 编辑描述

colab.research.google.com](https://colab.research.google.com/drive/1Py7nyJO_sgOYf8Fh-2Dcn1JmxEJyUUor?usp=sharing) 

**DARPA 的空战进化计划:**

人工智能需要速度…

 [## 在 DARPA 试验空军杂志中，人工智能轻松击败人类战斗机飞行员

### 8 月 10 日，在 DARPA 的 AlphaDogfight 试验中，Heron Systems AI 算法在模拟空战中横扫了一名人类 F-16 飞行员

www.airforcemag.com](https://www.airforcemag.com/artificial-intelligence-easily-beats-human-fighter-pilot-in-darpa-trial/) 

本周照片:泰坦尼克号的秘密

![](img/a851792a67ffb57c5a9379f485a29e4d.png)

100 多岁。泰坦尼克号上发现的旧美人鱼钱币🚢

# 本周

> 句子变形金刚
> 
> txtai:人工智能驱动的搜索引擎
> 
> 微调自定义数据集
> 
> 使用 SQL 的数据 API 端点
> 
> 它亮了*🔥*
> 
> 广播公司流 API
> 
> Fast.ai 新发布
> 
> 本周数据集:对话

# 句子变形金刚

如果你希望以一种无人监督的方式使用来自 SOTA 自然语言处理模型的句子嵌入，你可以查看句子变形库。他们微调了 BERT，RoBERTa，DistilBERT，ALBERT，XLNet 模型的暹罗/三元网络结构，以用于几个任务:语义文本相似性，聚类和语义搜索。

(他们也提供代码来训练你自己的模型😎和多语言模型)

**GitHub** :

[](https://github.com/UKPLab/sentence-transformers) [## uk plab/句子-变形金刚

### 伯特/罗伯塔/XLM-罗伯塔生产出开箱即用的相当糟糕的句子嵌入。这个存储库微调 BERT /…

github.com](https://github.com/UKPLab/sentence-transformers) 

# txtai:人工智能驱动的搜索引擎

![](img/14bac1c6bd4f61dccf76c36a5e99c58f.png)

谈句子嵌入…想用句子转换器 AI 搜索并缩放到百万条记录？答案是用[近似最近邻(ANN)](https://en.wikipedia.org/wiki/Nearest_neighbor_search#Approximation_methods) 搜索，即在新的 txtai 库中找到的(建立在变形金刚之上，句子变形金刚)。该库目前支持三个 ANN 搜索库:faiss、airy 和 hnswlib。🔥🔥

除了进行相似性搜索之外，txtai 还可以用于搜索结果中的提取问题回答。例子摘自大卫·梅泽蒂的[博客文章](https://towardsdatascience.com/introducing-txtai-an-ai-powered-search-engine-built-on-transformers-37674be252ec):

```
**sections = ["Giants hit 3 HRs to down Dodgers",
            "Giants 5 Dodgers 4 final",
            "Dodgers drop Game 2 against the Giants, 5-4",
            "Blue Jays 2 Red Sox 1 final",
            "Red Sox lost to the Blue Jays, 2-1",
            "Blue Jays at Red Sox is over. Score: 2-1",
            "Phillies win over the Braves, 5-0",
            "Phillies 5 Braves 0 final",
            "Final: Braves lose to the Phillies in the series opener, 5-0",
            "Final score: Flyers 4 Lightning 1",
            "Flyers 4 Lightning 1 final",
            "Flyers win 4-1"]**

# Add unique id to each section to assist with qa extraction
sections = [(uid, section) for uid, section in enumerate(sections)]

questions = ["What team won the game?", "What was score?"]

execute = lambda query: extractor(sections, [(question, query, question, False) for question in questions])

for query in ["Red Sox - Blue Jays", "Phillies - Braves", "Dodgers - Giants", "Flyers - Lightning"]:
    print("----", query, "----")
    for answer in execute(query):
        print(answer)
    print()

# Ad-hoc questions
**question = "What hockey team won?"**

print("----", question, "----")
print(extractor(sections, [(question, question, question, False)]))
```

**GitHub** :

[](https://github.com/neuml/txtai) [## neuml/txtai

### txtai 在文本部分建立了一个人工智能索引。txtai 支持构建文本索引来执行相似性…

github.com](https://github.com/neuml/txtai) 

**博客**:

[](https://towardsdatascience.com/introducing-txtai-an-ai-powered-search-engine-built-on-transformers-37674be252ec) [## 介绍 txtai，一个基于变形金刚的人工智能搜索引擎

### 为任何应用程序添加自然语言理解

towardsdatascience.com](https://towardsdatascience.com/introducing-txtai-an-ai-powered-search-engine-built-on-transformers-37674be252ec) 

# 微调自定义数据集

拥抱脸有一篇关于如何用 PyTorch 或 TF framework(原生)或他们的训练器类微调你自己的数据集的新文档。现在你可以看到预处理是多么有趣了😁！

这些例子探讨了:

*   [用 IMDb 评论进行序列分类](https://huggingface.co/transformers/master/custom_datasets.html#seq-imdb)
*   [使用 W-NUT 新兴实体的令牌分类](https://huggingface.co/transformers/master/custom_datasets.html#tok-ner)
*   [用 2.0 小队回答问题](https://huggingface.co/transformers/master/custom_datasets.html#qa-squad)

 [## 使用自定义数据集进行微调- transformers 3.0.2 文档

### 注意本教程中使用的数据集是可用的，使用🤗NLP 图书馆。我们确实…

huggingface.co](https://huggingface.co/transformers/master/custom_datasets.html) 

# 使用 SQL 的数据 API 端点

如果你喜欢 SQL 和数据，5432 端口是开放的… Splitgraph 允许用户通过 PostgreSQL 客户端连接到超过 40K 个数据集。👀

[](https://www.splitgraph.com/) [## 分裂图

### 选择剑桥案例。date AS date，Chicago _ cases . cases _ total AS Chicago _ daily _ cases…

www.splitgraph.com](https://www.splitgraph.com/) 

如果您是 Python/PostgreSQL 的狂热爱好者，下面的 pyscopg2 代码可以帮助您入门:

```
import psycopg2

*# Your Splitgraph DDN username/password*
API_KEY = "API_KEY"
API_SECRET = "API_SECRET"

QUERY = """SELECT candidate_normalized, SUM(votes)::integer AS total_votes
    FROM "splitgraph/2016_election:latest".precinct_results
    WHERE state_postal = 'CA'
    GROUP BY candidate_normalized
    ORDER BY total_votes DESC
    LIMIT 5
"""

with psycopg2.connect(
    dsn=f"postgresql://{API_KEY}:{API_SECRET}@data.splitgraph.com:5432/ddn?application_name=psycopg2"
) as conn:
    with conn.cursor() as cur:
        cur.execute(QUERY)
        result = cur.fetchall()
        print(result)
```

**什么样的数据？**

探索 27.2K 主题**👀**

[](https://www.splitgraph.com/explore) [## 分裂图

### 数据操作重新设想:一个 PostgreSQL 端点，40k+数据集。构建、版本化、查询和共享可复制的数据映像。

www.splitgraph.com](https://www.splitgraph.com/explore) 

# 它被点燃了🔥

![](img/b00aebc16d90eb1b8766fec1c8cc8aa1.png)

解密的

谷歌用 LIT 偷袭了我们。除了数据集可视化之外，该工具包还允许开发人员深入研究语言模型。我倾向于把 LIT 看作是原型开发中类固醇的 ML 演示。自带一个现成的用户界面。

它能做什么？

> LIT 支持本地解释(包括显著性地图、注意力和模型预测的丰富可视化)以及聚合分析(包括度量、嵌入空间和灵活切片)，并允许用户在它们之间无缝跳转，以测试本地假设并在数据集上验证它们。

[](https://venturebeat.com/2020/08/14/google-open-sources-lit-a-toolset-for-evaluating-natural-language-models/) [## Google 开源 LIT，一个评估自然语言模型的工具集

### 谷歌附属的研究人员今天发布了语言可解释性工具(LIT)，一个开源…

venturebeat.com](https://venturebeat.com/2020/08/14/google-open-sources-lit-a-toolset-for-evaluating-natural-language-models/) 

**GitHub:**

[](https://github.com/pair-code/lit) [## 成对代码/lit

### 语言可解释性工具(LIT)是一个用于 NLP 模型的可视化、交互式模型理解工具。LIT 是建立在…

github.com](https://github.com/pair-code/lit) 

【https://arxiv.org/pdf/2008.05122.pdf】纸 : [纸](https://arxiv.org/pdf/2008.05122.pdf)

# 广播公司流 API

![](img/5ee695b07a42bbfe187843ac41c1d366.png)

随着流数据的 websockets 在工程师的堆栈中变得越来越流行，关注最新的库是必须的。Broadcaster 是一个简单的 websocket 库，可以与 Redis PUB/SUB、Apache Kafka 和 Postgres LISTEN/NOTIFY 等几个后端一起运行。如果您有使用 FastAPI 的经验，这应该对您很熟悉。

**GitHub** :

[](https://github.com/encode/broadcaster) [## 编码/广播

### Broadcaster 通过提供一个简单的广播 API 来帮助您开发实时流功能

github.com](https://github.com/encode/broadcaster) 

# Fast.ai 新发布

Fast.ai 的粉丝们，有一个新版本有很多好东西。在他们的博客上阅读所有相关内容。(包括一本方便的书)

[](https://www.fast.ai/2020/08/21/fastai2-launch/) [## fast.ai 发布了新的深度学习课程、四个库和 600 页的书

### fast.ai 是一个自筹资金的研究、软件开发和教学实验室，专注于使深度学习更加…

www.fast.ai](https://www.fast.ai/2020/08/21/fastai2-launch/) 

**本周可乐杯:**

[](https://colab.research.google.com/drive/1IWrhwcJoncCKHm6VXsNwOr9Yukhz3B49?usp=sharing) [## 谷歌联合实验室

### 编辑描述

colab.research.google.com](https://colab.research.google.com/drive/1IWrhwcJoncCKHm6VXsNwOr9Yukhz3B49?usp=sharing) 

# 本周数据集:对话

**什么事？**

DialogRE 是第一个基于人类注释的对话的关系抽取数据集，包含 1，788 个来自美国著名电视情景喜剧《老友记》的完整脚本的对话。

**样本**

![](img/48f01ad19ad16e8da4481d01c8a3e6a5.png)

**在哪里？**

 [## dialog:第一个基于人工标注对话的关系抽取数据集

### DialogRE 是第一个人注释的基于对话的关系抽取数据集，包含 1，788 个对话…

dataset.org](https://dataset.org/dialogre/) 

> *每周日，我们都会对来自世界各地研究人员的 NLP 新闻和代码进行一次每周综述。*
> 
> 如果你喜欢这篇文章，请帮助我们并与朋友分享！
> 
> *如需完整报道，请关注我们的推特:*[*@ Quantum _ Stat*](http://twitter.com/Quantum_Stat)

![](img/e34b2da0b2327e82fa233e12150dbe1b.png)

[www.quantumstat.com](http://www.quantumstat.com/)