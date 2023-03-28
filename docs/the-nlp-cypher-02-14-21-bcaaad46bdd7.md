# NLP 密码| 02.14.21

> 原文：<https://pub.towardsai.net/the-nlp-cypher-02-14-21-bcaaad46bdd7?source=collection_archive---------3----------------------->

![](img/0a0f7f5fea7cebdacac5381841efb6ac.png)

帕特莫斯岛上圣约翰的景象|柯雷乔

## 自然语言处理每周时事通讯

## 事物

欢迎回来！本周，各种来源发布了大量的 Colab 笔记本，有人实际上在 PyTorch 中构建了一个最小化版本的开关变压器。但首先……我们赞助商的一句话:

**如果你喜欢这本书，请帮帮我们👏👏和朋友分享！**

# 神经魔法的持续故事

新年前后，我思考了即将到来的稀疏性的采用及其对推理 w/r/t ML 模型的影响。一家“新”公司出现了，他们刚刚开源了他们的代码。

> “新”用引号括起来，因为它们并不是新的，它们的开源代码才是新的。

公司是神经魔法。

[](https://github.com/neuralmagic) [## 神经魔法

### 神经魔法有 6 个储存库。在 GitHub 上关注他们的代码。

github.com](https://github.com/neuralmagic) 

他们的核心回购协议包括

**SparseML** :一个工具包，包括 API、CLI、脚本和库，将优化算法如[修剪](https://neuralmagic.com/blog/pruning-overview/)和[量化](https://arxiv.org/abs/1609.07061/)应用于任何神经网络。

**SparseZoo** :稀疏模型的模型报告。

**DeepSparse** :稀疏模型的 CPU 推理机。

**稀疏化**:优化深度神经网络的 UI 接口，以获得更好的推理性能。

他们目前支持:PyTorch，Keras 和 TensorFlow V1。🙈

# PyTorch 中开关变压器的实现

已经有一个开关变压器的 PyTorch 实现，但它是一个最小化的版本，不做并行训练。然而，它确实执行了 Google switch 文件中描述的“切换”。你可以在下面的链接中跟随他们的代码片段，并在 Colab 上执行他们的最小化版本。真酷🔥🔥。

[](https://nn.labml.ai/transformers/switch/) [## 开关变压器

### 这是一个微型 PyTorch 实现的纸开关变压器:缩放到万亿参数模型与…

nn.labml.ai](https://nn.labml.ai/transformers/switch/) 

**Colab**

[](https://colab.research.google.com/github/lab-ml/nn/blob/master/labml_nn/transformers/switch/experiment.ipynb) [## 谷歌联合实验室

### 编辑描述

colab.research.google.com](https://colab.research.google.com/github/lab-ml/nn/blob/master/labml_nn/transformers/switch/experiment.ipynb) 

# 微软的多语言拼写检查器

在必应搜索中，客户提交的查询中有 15%有拼写错误。因此，微软从 BART 的架构中获得灵感，帮助扩大他们的搜索业务。阅读微软是如何做到的，以及多语言拼写检查器是如何扩展的。

[](https://www.microsoft.com/en-us/research/blog/speller100-zero-shot-spelling-correction-at-scale-for-100-plus-languages/) [## Speller100 将拼写纠正技术扩展到 100 多种语言

### 在微软必应，我们的使命是为世界各地的用户提供最佳的搜索体验。我们提供多元化的服务…

www.microsoft.com](https://www.microsoft.com/en-us/research/blog/speller100-zero-shot-spelling-correction-at-scale-for-100-plus-languages/) 

# 适用于 Spacy 模型的云 NLP

如果您深入空间领域，并且需要一个存储系统来为您的空间模型提供服务，NLP Cloud 的 peeps 可以助您一臂之力。他们的基础设施建立在 FastAPI 之上，支持 Python、Go 和 Ruby 语言。

**文档**:

[](https://docs.nlpcloud.io/#introduction) [## API 参考

### 使用 en_core_web_sm 预训练模型获取实体:curl " https://API . NLP cloud . io/v1/en _ core _ web _ sm/entities " \ H…

docs.nlpcloud.io](https://docs.nlpcloud.io/#introduction) 

谈论 spaCy……AI2 的 ScispaCy 库基于 spaCy 的 v3 版本发布了一个新版本。如果你想了解 spaCy 的 v3 新特性，可以在这里查看他们的博客文章:

https://explosion.ai/blog/spacy-v3

# 9000 万印度法律案例的大型数据库

> “发展数据实验室使用政府的在线案件管理门户网站-电子法院，处理并取消了 2010 年至 2018 年期间印度所有下级法院提交的法律案件记录。结果是:2，500 万起刑事案件和 6，500 万起民事案件的指控、备案、听证和判决日期、审判结果以及案件类型的详细信息。”

[](https://devdatalab.medium.com/big-data-for-justice-f53e0e14c9c9) [## 大数据促进司法

### 一个包含 8000 万份印度法律案例记录的开放式数据集

devdatalab.medium.com](https://devdatalab.medium.com/big-data-for-justice-f53e0e14c9c9) 

# OCR 库| Azure

Azure 为他们的计算机视觉库带来了新版本的 OCR，它包括:

*   [支持 73 种语言的 OCR](https://docs.microsoft.com/en-us/azure/cognitive-services/computer-vision/language-support#optical-character-recognition-ocr)，包括简体中文、繁体中文、日语、韩语和几种拉丁语言。
*   文本行输出的自然阅读顺序。
*   文本行的手写风格分类。
*   多页文档中所选页面的文本提取。
*   作为内部部署的[分发容器](https://docs.microsoft.com/en-us/azure/cognitive-services/computer-vision/computer-vision-how-to-install-containers?tabs=version-3-2)提供。

[](https://techcommunity.microsoft.com/t5/azure-ai/computer-vision-ocr-read-api-previews-73-human-languages-and-new/ba-p/2121341) [## 计算机视觉 OCR (Read API)预览 73 种人类语言以及云和内部的新功能

### 今天的企业正在应用光学字符识别(OCR)和文档人工智能技术来快速转换他们的…

techcommunity.microsoft.com](https://techcommunity.microsoft.com/t5/azure-ai/computer-vision-ocr-read-api-previews-73-human-languages-and-new/ba-p/2121341) 

# Wav2Vec2

语音转文本功能现在是拥抱人脸库的一部分。脸书 Wav2Vec2 模型本周被上传到他们的模型中心，其中包括用于推理的代码片段。

[](https://huggingface.co/facebook/wav2vec2-base-960h) [## facebook/wav2vec2-base-960h 拥抱脸

### 我们正踏上通过自然语言解决人工智能并使其大众化的旅程。

huggingface.co](https://huggingface.co/facebook/wav2vec2-base-960h) 

## 科拉布🔥

仅供参考，1LittleCoder 已经为您创建了一个不错的 Colab 来开始使用 wav 文件。😎

[](https://colab.research.google.com/drive/1pTkj1HE768-3aM4huTWX5og8GkUKxKRi?authuser=1#scrollTo=741DtETtiW4N) [## 谷歌联合实验室

### 编辑描述

colab.research.google.com](https://colab.research.google.com/drive/1pTkj1HE768-3aM4huTWX5og8GkUKxKRi?authuser=1#scrollTo=741DtETtiW4N) 

# 主题建模

什么要知道跨语言零 sot 话题建模是怎么回事？该模型被称为 ZeroShotTM，基于多语言编码器模型。想象一下，你想让你的模型学习英语中的主题，然后你想让它预测它从未见过的意大利语文档中的未见过的主题。这本质上就是跨语言零拍的全部。你可以看看他们的博客👇其中有一个很好的教程，可以帮助您熟悉他们的库:

[](https://fbvinid.medium.com/contextualized-topic-modeling-with-python-eacl2021-eacf6dfa576) [## 使用 Python 进行上下文化主题建模(EACL2021)

### 在这篇博文中，我讨论了我们最新发表的关于主题建模的论文:

fbvinid.medium.com](https://fbvinid.medium.com/contextualized-topic-modeling-with-python-eacl2021-eacf6dfa576) 

## 本周可乐🏆

[](https://colab.research.google.com/drive/13YhYgJN9EjSQw5bsZYzMaaiNKQpt_SQn?usp=sharing) [## 谷歌联合实验室

### 编辑描述

colab.research.google.com](https://colab.research.google.com/drive/13YhYgJN9EjSQw5bsZYzMaaiNKQpt_SQn?usp=sharing) 

# 回购密码👨‍💻

## 一组最近发布的回购引起了我们的注意👁

## 克利伯特

> CLIPBert 以原始视频/图像+文本作为输入，输出任务预测。
> 
> 支持以下任务的端到端预训练和微调:
> 
> -对 COCO 和 VG 字幕进行图文预处理。
> -文本到视频检索微调 MSRVTT、DiDeMo 和 ActivityNet 字幕。
> -TGIF-QA 和 MSRVTT-QA 上的视频-QA 微调。
> -VQA 2.0 上的图片-质量保证微调。

[**连接论文**](https://www.connectedpapers.com/main/ba4a4d31d2af23eefadbf19e5efd5a7d4fd89143/arxiv) 📈

[](https://github.com/jayleicn/ClipBERT) [## 杰利肯/克利伯特

### 少即是多:通过稀疏采样视频和语言学习的 ClipBERT 官方 PyTorch 代码。

github.com](https://github.com/jayleicn/ClipBERT) 

## 制模工

> 基于 Nystrom 的近似自我注意算法。可以避开编码器模型的 512 个令牌限制，并且在某些情况下，精确度差异极小。

[**连接论文**](https://www.connectedpapers.com/main/6fa1cfc4f97f03a8485692418c7aa1a06c574a85/arxiv) 📈

[](https://github.com/mlpen/Nystromformer) [## mlpen/Nystromformer

### 变形金刚已经成为广泛的自然语言处理任务的强大工具。一把钥匙…

github.com](https://github.com/mlpen/Nystromformer) 

## RpBERT

> 用于多模态名称实体识别的 BERT 模型(NER)

[**连接论文**](https://www.connectedpapers.com/main/b9ad52b670189658851026e03a33063a1b8d47fe/arxiv) 📈

[](https://github.com/Multimodal-NER/RpBERT) [## 多式联运-NER/RpBERT

### RpBERT:基于文本-图像关系传播的多模态 RpBERT 模型 python==3.7 torch==1.2.0…

github.com](https://github.com/Multimodal-NER/RpBERT) 

## 生物医学问答:综述

论文:[https://arxiv.org/abs/2102.05281](https://arxiv.org/abs/2102.05281)

[**连接论文**](https://www.connectedpapers.com/main/1f96539c083d60fa83f7548bc6996cdede1026ee/arxiv) 📈

# 本周数据集:ARC 直接回答问题

## 这是什么？

一个由 2，985 个小学水平的直接回答(“开放式回答”、“自由形式”)科学问题组成的数据集，这些问题来自作为 2018 年 AI2 推理挑战赛一部分发布的 ARC 多项选择问题集。

## 样品

```
{
  "question_id": "ARCEZ_Mercury_7221148",
  "tag": "EASY-TRAIN",
  "question": "A baby kit fox grows to become an adult with a mass of over 3.5 kg. What factor will have the greatest influence on this kit fox's survival?",
  "answers": [
    "food availability",
    "larger predators prevalence",
    "the availability of food",
    "the population of predator in the area",
    "food sources",
    "habitat",
    "availability of food",
    "amount of predators around",
    "how smart the fox is"
  ]
}
```

## 它在哪里？

[](https://allenai.org/data/arc-da) [## ARC 直接回答问题数据集-艾伦人工智能研究所

### 此 1.1 版本修复了一些内容和格式问题，并提供了原始版本的答案。这些问题是…

allenai.org](https://allenai.org/data/arc-da) 

> 每周日，我们都会对来自世界各地研究人员的 NLP 新闻和代码进行一次每周综述。
> 
> *如需完整报道，请关注我们的推特:*[*@ Quantum _ Stat*](http://twitter.com/Quantum_Stat)

![](img/940b7c2dab42511505f20a35b312b258.png)

[量子统计](https://quantumstat.com/)