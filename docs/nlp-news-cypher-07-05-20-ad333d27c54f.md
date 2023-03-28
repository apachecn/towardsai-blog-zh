# NLP 新闻密码| 07.05.20

> 原文：<https://pub.towardsai.net/nlp-news-cypher-07-05-20-ad333d27c54f?source=collection_archive---------2----------------------->

![](img/dfa7642b38f1f2edbe2eb252686db874.png)

凯尔·格伦在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上的照片

## 自然语言处理每周时事通讯

## 方向

欢迎回来！因此，ACL 2020 今天正式启动，技术窥视者已经开始展示他们的研究。我将在一周内关注 ACL 的所有事情，因此请确保关注我们的 Twitter 更新: [Quantum Stat。](https://twitter.com/Quantum_Stat)

**脸书在 ACL:**

[](https://ai.facebook.com/blog/facebook-research-at-acl-2020/) [## ACL 2020 的脸书研究

### 计算语言学协会(ACL)会议将于今年 7 月 5 日至 7 月 10 日在网上举行…

ai.facebook.com](https://ai.facebook.com/blog/facebook-research-at-acl-2020/) 

**IBM at ACL:**

[](https://www.ibm.com/blogs/research/2020/07/ibm-research-at-acl-2020/) [## IBM 在 ACL 2020 上的研究| IBM 研究博客

### 计算语言学协会(ACL 2020)第 58 届年会，这是…

www.ibm.com](https://www.ibm.com/blogs/research/2020/07/ibm-research-at-acl-2020/) 

哦，最后但同样重要的是，2020 年正式成为有记录以来最奇怪的一年:坎耶·韦斯特正在竞选总统。

埃隆就像:

拜登的竞选经理是这样的:

祝在美国庆祝的人们 7 月 4 日快乐！🎇🎆

# 本周:

> FastAPI 和 Streamlit
> 
> RASA 对话人工智能
> 
> 软件更新
> 
> 文本英雄
> 
> 智能回复来 YouTube
> 
> 羊驼蹼套
> 
> 重整器系列
> 
> 本周数据集:敌对的 NLI

# FastAPI 和 Streamlit

牛逼的新 GitHub，自带全栈后端(fastAPI)和前端(Streamlit)。你可以直接提供这个框架，如果你想跳出 flask WSGI 框架，深入了解 ASGI 的方方面面，这是一个不错的选择。

FastAPI 和 Streamlit 都可以通过 Docker Compose 进行桥接:

```
version: '3'

services:
  fastapi:
    build: fastapi/
    ports: 
      - 8000:8000
    networks:
      - deploy_network
    container_name: fastapi

  streamlit:
    build: streamlit/
    depends_on:
      - fastapi
    ports: 
        - 8501:8501
    networks:
      - deploy_network
    container_name: streamlit

networks:
  deploy_network:
    driver: bridge
```

**博客:**

 [## 使用 FastAPI 和 streamlit 在 Python 中服务的机器学习模型

### 在我目前的工作中，我训练机器学习模型。当实验表明这些模型中的一个可以解决某些需要时…

davidefiocco.github.io](https://davidefiocco.github.io/2020/06/27/streamlit-fastapi-ml-serving.html) 

**Github:**

[](https://github.com/davidefiocco/streamlit-fastapi-model-serving/) [## davidefiocco/streamlit-fastapi-模型服务

### 关于 ML 模型服务使用 streamlit 和 FastAPI 的简单示例，请参见…

github.com](https://github.com/davidefiocco/streamlit-fastapi-model-serving/) 

# 对话式人工智能的 RASA 更新

在讨论对话式人工智能时，RASA 的联合创始人 Alan Nichol 讨论了我们都应该努力实现的聊天机器人技术的 5 个级别，特别是圣杯:级别 5 又称 HAL 9000。对话式人工智能的 5 个层次是从最终用户和开发者的角度来观察的。有趣的阅读可以得到 RASA 认为聊天机器人前进方向的路线图，以及让 HAL 登上 Elon 的星舰需要什么。

**博客:**

[](https://blog.rasa.com/5-levels-of-conversational-ai-2020-update/) [## 对话式人工智能 2020 更新的 5 个层次

### 自从我们第一次发布 5 级人工智能助手，市场和技术已经发生了变化，是时候更新了…

blog.rasa.com](https://blog.rasa.com/5-levels-of-conversational-ai-2020-update/) 

# 软件更新

**张量流:**

[](https://github.com/tensorflow/tensorflow/releases/tag/v2.3.0-rc0) [## 发布 tensor flow 2 . 3 . 0-rc0 tensor flow/tensor flow

### data 添加了两个新的机制来解决输入管道瓶颈和节省资源:此外，checkout

github.com](https://github.com/tensorflow/tensorflow/releases/tag/v2.3.0-rc0) 

**🤗高频:**

[](https://github.com/huggingface/transformers/releases/tag/v3.0.0) [## 发布新的 tokenizer API、TensorFlow 改进、增强的文档和教程…

### 在#4874 中，语言建模 BERT 被一分为二:BertForMaskedLM 和 BertLMHeadModel。BertForMaskedLM…

github.com](https://github.com/huggingface/transformers/releases/tag/v3.0.0) 

**附言**拥抱脸给他们的模型中心添加了一个很棒的端点 API，这样你就可以用社区的模型进行推理了。这里有一个蒸馏瓶的例子:

[](https://huggingface.co/distilbert-base-uncased) [## 无壳拥抱脸

### 这个模型是 BERT 基本模型的一个精华版本。本文对此进行了介绍。蒸馏的代码…

huggingface.co](https://huggingface.co/distilbert-base-uncased) 

**DeepPavlov:**

[](http://deeppavlov.ai/blog/tpost/22tid6u13h-deeppavlov-library-0110-release) [## 走近梦想:宣布我们新的 DeepPavlov🎅0.11.0 发布！

### 大家好，欢迎来到 DeepPavlov 博客！我叫丹尼尔·科尔涅夫，是 DeepPavlov.ai 的产品经理

deeppavlov.ai](http://deeppavlov.ai/blog/tpost/22tid6u13h-deeppavlov-library-0110-release) 

# 文本英雄

一个新的 NLP 数据集库出来了，它被称为文本英雄。您可以使用它进行出色的预处理和数据集可视化。目前它的一些工具:

> 预处理文本数据:它既提供了开箱即用的解决方案，也为定制解决方案提供了灵活性。
> 
> 自然语言处理:关键短语和关键词提取，命名实体识别等等。
> 
> 文本表示:TF-IDF、词频、预训练和自定义单词嵌入。
> 
> 向量空间分析:聚类(K-means，Meanshift，DBSAN 和 Hierarchical)，主题建模(LDA 和 LSI)和解释。
> 
> 文本可视化:关键词可视化，向量空间可视化，地图上地点定位。

仅用 3 行代码就可以可视化数据集的向量空间！

**GitHub:**

[](https://github.com/jbesomi/texthero) [## JB osmi/text hero

### 从零到英雄的文本预处理、表示和可视化。从零到英雄*安装*获取…

github.com](https://github.com/jbesomi/texthero) 

**博客:**

 [## Texthero 文本预处理，从零到英雄的表示和可视化。

### 从零到英雄的文本预处理、表示和可视化。

从零到 hero.texthero.org 的文本预处理、表示和可视化](https://texthero.org/) 

# 智能回复来 YouTube

当你想加快回复邮件的速度时，智能回复功能非常棒。现在，SmartReply 正走向 YouTube，它基于字符/字节级语言建模的最新进展:

论文:[https://www.aaai.org/ojs/index.php/AAAI/article/view/4182](https://www.aaai.org/ojs/index.php/AAAI/article/view/4182)

目前，SmartReply 有英语和西班牙语版本，只会根据谷歌是否认为创作者可能会回复以及他们认为模型何时可以给出合理的评论来选择性地进行提示。🧐

让我们看看这一个是如何进行的:

[](https://ai.googleblog.com/2020/07/smartreply-for-youtube-creators.html) [## YouTube 创建者的智能回复

### 自 SmartReply 推出以来已经有 4 年多了，从那时起，它已经扩展到更多的用户…

ai.googleblog.com](https://ai.googleblog.com/2020/07/smartreply-for-youtube-creators.html) 

# 羊驼蹼套

今年，我偶然发现了一个很棒的金融市场数据 API:羊驼。而我之所以是粉丝，是因为它免费提供实时的市场数据流。我只想说这很少见，我不知道还有其他 API 提供免费的流媒体端点。如果我错了，请在评论里给我爆料。如果你想知道一个设置它的好教程，请看这里:

**文档**:

[](https://alpaca.markets/docs/api-documentation/api-v2/market-data/streaming/) [## 市场数据流-文档|羊驼毛

### 羊驼数据 API 为交易、报价和分钟棒线提供 websocket 流。这有助于接收最新的…

羊驼市场](https://alpaca.markets/docs/api-documentation/api-v2/market-data/streaming/) 

# 重整器系列

如果你想深入了解是什么让改革者成功，看看拥抱脸的这 4 个 Colab 教程。讨论如下:

1.  **改革者自我关注层**——*如何有效地实施自我关注，而不受当地环境的限制？* = >见[本可乐](https://colab.research.google.com/drive/15oP52_7W5dRcAnbgX3tYADsu4R3cjMIf?usp=sharing)。
2.  **分块前馈层** — *对于大型前馈层，如何获得更好的时间-内存平衡？*
3.  **可逆残差层** — *如何通过智能残差架构大幅降低训练中的内存消耗？*
4.  **轴向位置编码** — *如何使位置编码可用于极大的输入序列？*

## 第一部分

[](https://colab.research.google.com/drive/15oP52_7W5dRcAnbgX3tYADsu4R3cjMIf?usp=sharing) [## 谷歌联合实验室

### 编辑描述

colab.research.google.com](https://colab.research.google.com/drive/15oP52_7W5dRcAnbgX3tYADsu4R3cjMIf?usp=sharing) 

## **第二部分**

[](https://colab.research.google.com/drive/1xKK32Yhda-iYgtoA3eCrnCVuy_lraQR9?usp=sharing) [## 谷歌联合实验室

### 编辑描述

colab.research.google.com](https://colab.research.google.com/drive/1xKK32Yhda-iYgtoA3eCrnCVuy_lraQR9?usp=sharing) 

## **第三部分**

[](https://colab.research.google.com/drive/1BLffcRt9LXmM7nKU2UXhtm0PqAG0UE7J?usp=sharing) [## 谷歌联合实验室

### 编辑描述

colab.research.google.com](https://colab.research.google.com/drive/1BLffcRt9LXmM7nKU2UXhtm0PqAG0UE7J?usp=sharing) 

## **第四部分**

[](https://colab.research.google.com/drive/1MYxvC4RbKeDzY2lFfesN-CvPLKLk00CQ?usp=sharing) [## 谷歌联合实验室

### 编辑描述

colab.research.google.com](https://colab.research.google.com/drive/1MYxvC4RbKeDzY2lFfesN-CvPLKLk00CQ?usp=sharing) 

# 本周数据集:敌对的 NLI

# 这是什么？

数据集是一个自然语言推理(NLI)基准，通过人和模型在回路中启用训练(哈姆雷特)创建。

# 样本:

 [## 安利 Demo

### 什么是 NLI？自然语言推理(NLI)的任务是确定，给定一个上下文，一个假设是否…

adversarialnli.com](https://adversarialnli.com/?fbclid=IwAR2vlb3egNu7LEhRQtatHv620CWT_aMeJ20uT291eTFLQfmhzIKS7lpeOkI#) 

# 它在哪里？

[](https://github.com/facebookresearch/anli) [## facebookresearch/anli

### 对立的 NLI:自然语言理解的新基准 1.0 版在这里可用…

github.com](https://github.com/facebookresearch/anli) 

> 每周日，我们都会对来自世界各地研究人员的 NLP 新闻和代码进行一次每周综述。
> 
> 如果你喜欢这篇文章，请帮助我们并与朋友分享！
> 
> 如需完整报道，请关注我们的 Twitter: [@Quantum_Stat](http://twitter.com/Quantum_Stat)

![](img/bfd7b3c617da6d457cc78c78197506dc.png)

www.quantumstat.com