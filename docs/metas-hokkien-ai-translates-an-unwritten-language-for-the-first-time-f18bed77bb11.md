# Meta 的闽南语:AI 首次翻译一种非书面语言

> 原文：<https://pub.towardsai.net/metas-hokkien-ai-translates-an-unwritten-language-for-the-first-time-f18bed77bb11?source=collection_archive---------3----------------------->

## 主要以口头方式传递的语言的语音到语音模型

![](img/cc985c35b48df130ff5141298526833f.png)

作者使用[稳定扩散](https://arxiv.org/abs/2112.10752)创建的图像

到目前为止，大多数基于人工智能的翻译系统都专注于书面语言。在已知的 7000 种语言中，大多数都没有标准的书写形式。这使得迄今使用的模型难以应用。Meta 最近提出了一个主要用于口语的人工智能翻译模型:闽南语。为什么这很重要？

# **所有没有写下来的单词**

![](img/7624ae4d287d17c75822be68754c6913.png)

作者使用[稳定扩散](https://arxiv.org/abs/2112.10752)创建的图像

40%的已知语言(大约 3500 种)没有标准的书写形式，这些语言中的许多都被广泛使用。能够翻译没有书面形式的语言仍然非常复杂:标准技术需要大量的书面文本来训练模型。

比如[非洲有 2000 多种语言](https://langhotspots.swarthmore.edu/fastfacts.html)，大部分都没有书面形式(80%)。这些语言中有许多濒临灭绝，人们认为它们可能会在本世纪末消失。事实上，在 1991 年，据统计，至少有 180 种语言的使用人数少于 10 人(据估计，每 14 天就有一种语言消亡)。

许多文化和语言仍然是口头流传下来的。口头讲故事代表了社区文化和历史的宝库。当一种语言消失时，一切都消失了。这就是为什么保护它们是重要的。

已经尝试了几项举措来保护它们。收集两种语言的首字母(对于那些有书面形式的语言)并以电子形式记录那些只有口头形式的语言。

典型地，语音到语音翻译(S2ST)是将一种语言翻译成另一种语言的过程。通常，这些系统由三部分组成:自动语音识别(ASR)、机器翻译(MT)和文本到语音合成(TTS)。近年来，人们努力将该过程简化为一个步骤，以避免传播错误并提高效率。此外，传统的方法要求存在大量的书面文本。

例如，一个英语到法语的 S2ST 系统需要有大量两种语言的例子。对于那些被很好地记录并受到研究人员和机构关注的语言来说，这很容易实现。大部分语言都没有这么幸运，翻译的例子很少。此外，这种情况对于没有书面形式的语言是不可行的。

# **梅塔的闽南语**

前几天 Meta 推出了一款新机型，闽南语。闽南语是一个 S2ST 模型，能够在英语和[闽南语](https://en.wikipedia.org/wiki/Hokkien)之间进行翻译。这是一种普遍口头流传下来的语言。闽南语是台湾的官方语言之一，在中国东南部和华人散居的国家(新加坡、印度尼西亚、马来西亚和菲律宾)都有使用。今天，大约有 3000 万 mainland China 人和 1300 万台湾人说英语。这种语言是口头流传下来的，尽管有人试图用汉字(韩吉)来转录它或将其罗马化。

![](img/fe939b8fea43582063caa8eafade3f17.png)

图片来自 Meta AI 博客帖子。图片来源:[此处](https://about.fb.com/news/2022/10/hokkien-ai-speech-translation/)

> “我们的团队首先将英语或闽南语翻译成普通话文本，然后再翻译成闽南语或英语——既有人工注释，也有自动注释，”Meta 研究员胡安·皮诺说。"然后，他们将配对的句子添加到用于训练人工智能模型的数据中."— [来源](https://tech.fb.com/artificial-intelligence/2022/10/ai-translation-unwritten-language/)

正如元研究人员所提到的，他们利用了普通话中有闽南语注释的事实。此外，作为一种语言接近中文有助于模型更好地理解模式。

> 我们专注于语音到语音的翻译。为了做到这一点，我们开发了各种方法，例如使用语音到单元翻译将输入语音翻译成一系列声音，并从中生成波形或依赖于相关语言的文本，在这种情况下是普通话。— Meta AI 博文(来源:[此处)](https://about.fb.com/news/2022/10/hokkien-ai-speech-translation/)

该模型由几个部分组成。第一部分是直接将语音作为输入的编码器。之后，有两个组件，一个直接过渡到目标语言的解码器(单遍解码器)和一个利用注释文本的模型(两遍解码器)。两遍解码器使用翻译成目标文本的模型(如果作为输入的语言是闽南语，则翻译成普通话)。第二个模型允许额外的监督，并使模型更加准确。

![](img/12dd57c1ee98e87ddaafa637ece311db.png)

原始文章中的模型架构。图片来源:[此处](https://scontent-cdt1-1.xx.fbcdn.net/v/t39.8562-6/309184257_1075902092944168_6340948942681513778_n.pdf?_nc_cat=105&ccb=1-7&_nc_sid=ad8a9d&_nc_ohc=_nKnOxWF11AAX9wl7G_&_nc_ht=scontent-cdt1-1.xx&oh=00_AT9EPLVmkQDpykmDgOYox7rz4dT1nVOM9iPXt9BYr_Q8NA&oe=6356E936)

研究人员也使用普通话，因为没有多少人会说英语和闽南语。使用普通话让他们在创建受监督的人类注释数据时有了一种中枢语言。他们使用不同的来源(如福建戏剧，福建抄本，等等)作为数据集。他们还招募了一小组可以在英语和闽南语之间进行翻译的人，让他们把闽南语的一些例子翻译成书面英语。

此外，评估像闽南语这样的非文字语言的口语翻译并不是一个简单的挑战。为了能够评估结果，作者开发了一个将语音内容转录为标准化字母表的系统。在这些转录上，他们然后计算 [BLEU 分数](https://en.wikipedia.org/wiki/BLEU)(考虑音节)。

# 离别的思绪

Meta 的新模型向前迈进了一步，因为它将通常需要几个模型的操作简化为一个步骤。此外，该模型成功地从没有书面形式的语言(如闽南语)进行翻译。所使用的方法也很有趣，例如使用中间语言(普通话)来提高翻译质量。

这些挑战并不容易。对于最广泛使用的语言来说，有一些经过精细管理的大型数据集，而对于大多数语言来说，这些资源并不存在。另一方面，语音到语音甚至更复杂，通常需要文本翻译，而这对于许多语言来说是缺乏的。

![](img/85005cb8a450ea19761b3670e82d5d77.png)

作者使用[稳定扩散](https://arxiv.org/abs/2112.10752)创建的图像

消除语言障碍是迈向包容的另一步。翻译成代表性不足的语言使人们能够利用母语信息。这样可以更好地获取想法和信息。

近年来，Meta 投入了大量资源，将同声翻译扩展到尽可能多的语言。最近他们推出了 [No Language Left Behind](/no-language-left-behind-579afea29e52) ，可以翻译成 100 多种语言(并通过几个例子来学习)。
事实上，许多模型都是双语的，但是扩展到更多语言是相当困难的。

当然，考虑到 Meta 在元宇宙上的投资，可以肯定在这个方向上会有更多的模型。事实上，如前所述:

> “这可能会成为自信、流利和真实的障碍，”布朗说。“我们知道在 Meta，全世界有成千上万的人将他们的界面设置为英语，他们在我们的平台上使用英语——即使他们对其他语言和书写系统更有信心。一旦我们让他们能够用自己的语言制作音频，他们对数字空间的舒适度和信心就会大幅提升。”([来源](https://tech.fb.com/artificial-intelligence/2022/10/ai-translation-unwritten-language/))

就目前而言，元宇宙似乎一点也不成功(对它的成功也有许多怀疑)。不管元宇宙是否失败，Meta 已经将其模型开源，并且可以被社区使用。

# 如果你觉得有趣:

你可以寻找我的其他文章，你也可以 [**订阅**](https://salvatore-raieli.medium.com/subscribe) 在我发表文章时得到通知，你也可以在**[**LinkedIn**](https://www.linkedin.com/in/salvatore-raieli/)**上连接或联系我。**感谢您的支持！**

**这是我的 GitHub 知识库的链接，我计划在这里收集代码和许多与机器学习、人工智能等相关的资源。**

**[](https://github.com/SalvatoreRa/tutorial) [## GitHub - SalvatoreRa/tutorial:关于机器学习、人工智能、数据科学的教程…

### 关于机器学习、人工智能、数据科学的教程，包括数学解释和可重复使用的代码(python…

github.com](https://github.com/SalvatoreRa/tutorial) 

或者随意查看我在 Medium 上的其他文章:

[](https://medium.com/mlearning-ai/reimagining-the-little-prince-with-ai-7e9f68ed8b3c) [## 用艾重新想象小王子

### 人工智能如何从《小王子》中的人物描述中重构他们的形象

medium.com](https://medium.com/mlearning-ai/reimagining-the-little-prince-with-ai-7e9f68ed8b3c) [](https://medium.com/mlearning-ai/nobel-prize-cyberpunk-e1803aa0e087) [## 诺贝尔奖赛博朋克

### 科学发现中人工智能最重要奖项的计算视角

medium.com](https://medium.com/mlearning-ai/nobel-prize-cyberpunk-e1803aa0e087) [](https://towardsdatascience.com/how-artificial-intelligence-could-save-the-amazon-rainforest-688fa505c455) [## 人工智能如何拯救亚马逊雨林

### 亚马逊正处于危险之中，人工智能可以帮助保护它

towardsdatascience.com](https://towardsdatascience.com/how-artificial-intelligence-could-save-the-amazon-rainforest-688fa505c455) [](https://towardsdatascience.com/speaking-the-language-of-life-how-alphafold2-and-co-are-changing-biology-97cff7496221) [## 说生命的语言:AlphaFold2 和公司如何改变生物学

### 人工智能正在重塑生物学研究，并开辟治疗的新领域

towardsdatascience.com](https://towardsdatascience.com/speaking-the-language-of-life-how-alphafold2-and-co-are-changing-biology-97cff7496221)**