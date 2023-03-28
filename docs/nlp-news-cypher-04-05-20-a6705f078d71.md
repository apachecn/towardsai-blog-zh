# NLP 新闻密码| 04.05.20

> 原文：<https://pub.towardsai.net/nlp-news-cypher-04-05-20-a6705f078d71?source=collection_archive---------0----------------------->

![](img/21a0caf7fad1e9a4cec73a0dc92bc035.png)

吉米·科诺弗在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上的照片

## 自然语言处理每周时事通讯

## 沉思

当莱克斯不穿着阴沉的深色西装采访人工智能先驱时，他会在推特上质疑真空空间中的交流物理学。

我在这条推特上得到了 1 个赞，它来自 HAL 9000。

你这周过得怎么样？😎

我们已经更新了[大坏 NLP 数据库](https://datasets.quantumstat.com/)。我们增加了 38 个新数据集，总数超过了 350 个！感谢托马索·帕西尼、亨利·达什伍德、比尔·林、里德·普里赞特、帕斯·帕里克和克里斯蒂安·哈德曼的贡献！

有数据集要共享吗？然后，“突破到另一边”(又名:请通过点击 BBND 网页上的“联系”链接并发送详细信息来共享数据集。)

顺便说一句，下周我们会给你一个惊喜。敬请期待！🧐

# 本周:

> 视觉叙事
> 
> 狼人来了
> 
> Matplotlib 为黄金时间做好准备
> 
> 分解冗余
> 
> 斯坦萨的笔记本
> 
> 边缘上的 ML 推理
> 
> 加强自然语言处理
> 
> 本周数据集:阿尔弗雷德

# 视觉叙事

最近发布了一个新的模型，讨论通过强化学习的视觉讲故事的主题！什么是视觉叙事？

> “给定一个照片流，机器经过训练，可以用自然语言生成一个连贯的故事来描述照片。”

ReCo-RL 模型根据三个新标准对“相关”故事进行奖励:*相关性、连贯性和表现力*。酷的是，这个模型在传统和新的标准上取得了优异的表现。

**GitHub** :

[](https://github.com/JunjieHu/ReCo-RL) [## 胡俊杰/法国

### 如果你在回购中使用代码，请引用我们的 AAAI2020 论文…

github.com](https://github.com/JunjieHu/ReCo-RL) 

**论文**:

[链接](https://arxiv.org/pdf/1909.05316.pdf)

# 狼人来了

T5 是谷歌的大型型号，它既是编码器又是解码器，现在可以通过 Transformer 库访问。如果您想试用 T5 的摘要或翻译功能，请查看以下我的 Colab 笔记本🤗的原始笔记本。

**Colab:**

[](https://colab.research.google.com/drive/1O4ebooFLBKSnUuCgKqs8WI1bzjh0KN6S) [## 谷歌联合实验室

### 编辑描述

colab.research.google.com](https://colab.research.google.com/drive/1O4ebooFLBKSnUuCgKqs8WI1bzjh0KN6S) 

# Matplotlib 为黄金时间做好准备

我对 Matplotlib 的图形可视化最大的不满之一是，它看起来像是在 windows 95 上运行。但最近，我发现了这个博客，它展示了如何在 Matplotlib 上用一些令人印象深刻的可视化来打动你的数据科学朋友。包含代码！

[](https://matplotlib.org/matplotblog/posts/matplotlib-cyberpunk-style/) [## Matplotlib 赛博朋克风格

### 让我们编造一些数字，将它们放入熊猫数据框架并绘制它们:import Pandas as PD import matplotlib . py plot…

matplotlib.org](https://matplotlib.org/matplotblog/posts/matplotlib-cyberpunk-style/) 

# 分解冗余

我以前在以前的时事通讯中讨论过这个模型。但这次他们带着 Github 回购回来了！我不会再深入讨论，但本质上，这个模型将多跳问题分解为更简单的问题，以帮助回答问题:

**GitHub** :

[](https://medium.com/@ethanperez18/unsupervised-question-decomposition-for-question-answering-9b81c5f7a71d) [## 面向问答的无监督问题分解

### 我们通过将困难的问题分解成更容易的子问题来改进自动问答

medium.com](https://medium.com/@ethanperez18/unsupervised-question-decomposition-for-question-answering-9b81c5f7a71d) 

**博客**:

[](https://medium.com/@ethanperez18/unsupervised-question-decomposition-for-question-answering-9b81c5f7a71d) [## 面向问答的无监督问题分解

### 我们通过将困难的问题分解成更容易的子问题来改进自动问答

medium.com](https://medium.com/@ethanperez18/unsupervised-question-decomposition-for-question-answering-9b81c5f7a71d) 

# 斯坦萨的笔记本

您可能听说过斯坦福的 Stanza:一个新的多语言 NLP Python 库。

你可能不知道的是，他们有很棒的巧克力让你快速入门。

**初学者指南**:

[](https://colab.research.google.com/github/stanfordnlp/stanza/blob/master/demo/Stanza_Beginners_Guide.ipynb) [## 谷歌联合实验室

### 编辑描述

colab.research.google.com](https://colab.research.google.com/github/stanfordnlp/stanza/blob/master/demo/Stanza_Beginners_Guide.ipynb) 

**CoreNLP 指南**:

[](https://colab.research.google.com/github/stanfordnlp/stanza/blob/master/demo/Stanza_CoreNLP_Interface.ipynb) [## 谷歌联合实验室

### 编辑描述

colab.research.google.com](https://colab.research.google.com/github/stanfordnlp/stanza/blob/master/demo/Stanza_CoreNLP_Interface.ipynb) 

# 边缘上的 ML 推理

来自 TensorFlow 博客:对于梦想有一天将 ML 模型部署到移动设备的人来说，这是一个新的代理版本😁。

> 今天，我们很高兴地宣布一个新的 [TensorFlow Lite delegate](https://www.tensorflow.org/lite/performance/delegates) ，它使用苹果的核心 ML API，通过神经引擎在 iPhones 和 iPads 上更快地运行浮点模型。对于像 MobileNet 和 Inception V3 这样的模型，我们可以看到高达 14 倍的性能提升(详见下文)。

**博客**:

[](https://blog.tensorflow.org/2020/04/tensorflow-lite-core-ml-delegate-faster-inference-iphones-ipads.html) [## TensorFlow Lite Core ML delegate 可在 iPhones 和 iPads 上实现更快的推理

### 2020 年 4 月 2 日——由 Tei Jeong 和 Karim Nosseir 发布，软件工程师 TensorFlow Lite 为代表提供选项…

blog.tensorflow.org](https://blog.tensorflow.org/2020/04/tensorflow-lite-core-ml-delegate-faster-inference-iphones-ipads.html) 

# 加强自然语言处理

想了解 NLP 中强化学习的最新情况吗？我们找到了一份回购协议，让你在家期间有事可做。

[](https://github.com/jiyfeng/rl4nlp) [## 吉风/rl4nlp

### 自然语言处理阅读小组的强化学习

github.com](https://github.com/jiyfeng/rl4nlp) 

# 本周数据集:阿尔弗雷德

**什么事？**

> “ALFRED 数据集包含 8k+专家演示，每个演示带有 3 种或更多语言注释。这是学习从自然语言指令和以自我为中心的视觉到家务行动序列映射的基准。”

**样本:**

[](https://ai2thor.allenai.org/ithor/demo/) [## 演示

### 控件来启用或禁用游戏的控件。用你的鼠标四处看看。/键移动。左键点击互动…

ai2thor.allenai.org](https://ai2thor.allenai.org/ithor/demo/) 

**在哪里？**

[](https://github.com/askforalfred/alfred/tree/master/data) [## askforalfred/阿尔弗雷德

### ALFRED 数据集包含 8k+专家演示，每个演示都有 3 种或更多语言注释。轨迹包括…

github.com](https://github.com/askforalfred/alfred/tree/master/data) 

> 每周日，我们都会对来自世界各地研究人员的 NLP 新闻和代码进行一次每周综述。
> 
> 如果你喜欢这篇文章，请帮助我们并与朋友分享！
> 
> 如需完整报道，请关注我们的 Twitter: [@Quantum_Stat](http://twitter.com/Quantum_Stat)

![](img/2caf071852ba9a194777d8e1e52e4d9a.png)

www.quantumstat.com