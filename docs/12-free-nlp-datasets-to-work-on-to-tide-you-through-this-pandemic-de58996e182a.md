# 12 个免费的 NLP 数据集帮助你度过这个疫情

> 原文：<https://pub.towardsai.net/12-free-nlp-datasets-to-work-on-to-tide-you-through-this-pandemic-de58996e182a?source=collection_archive---------1----------------------->

![](img/ea82b70c788ea186f8f3575233aac4ad.png)

卢克·切瑟在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上的照片

你可能已经看到，如果不加控制，新冠肺炎的传播速度会有多快。尽管我们都想重新过上正常的生活，但我们现在能做的最好的事情就是尽可能呆在家里。

我们都必须发挥自己的作用，使曲线变平，以免压倒前线医护人员。

> 但是…除了工作，整天呆在家里几个星期或几个月会变得很无聊..

因此，为了帮助你度过这段时期(这样你就不会在家里感到无聊)，我编制了一个免费的 NLP 数据集列表！

**进行情感分析:**

1.  感觉 140 。一个很好的情绪分析数据集，可以处理 16 万条推文。然而，要警惕这种假设。这个数据集假设任何带有正面表情的推文都是正面的，而带有负面情绪的推文都是负面的。
2.  [IMDB 数据集](http://ai.stanford.edu/~amaas/data/sentiment/)。二元情感分类数据集，提供 25，000 条极地电影评论用于训练，25，000 条用于测试/验证。
3.  [标准情感树库](https://nlp.stanford.edu/sentiment/code.html)。这是 2013 年发表的论文“情感树库语义组合递归深度模型”使用的数据集。所使用的数据集包含 10，605 个来自烂番茄的片段。

**文本分类:**

1.  [亚马逊评论](https://snap.stanford.edu/data/web-Amazon.html)。从 1995 年到 2013 年，这个庞大的数据集包含了 34，686，770 篇评论。除了查看用户评分，你甚至可以查看书面评论是如何随时间变化的。写作行为是随时间变化的，还是不变的？
2.  [垃圾短信收集](http://www.dt.fee.unicamp.br/~tiago/smsspamcollection/)。如果您准备好迎接挑战，清理该数据集以做好建模准备是一个很好的练习。这里的收藏由新加坡当地一所大学的短信组成。具有挑战性的部分是处理新加坡人在日常生活中使用的当地俚语。
3.  【Blogger.com 数据集。2004 年来自 Blogger.com 的 681，288 篇博客帖子的语料库。除了尝试按年龄组或性别对博客进行分类之外，这是一个很好的数据集来创建您的单词嵌入，以帮助您更深入地理解和欣赏预先训练的单词嵌入。我写了一篇关于使用翻译向量[嵌入单词的有趣发现的文章。](https://towardsdatascience.com/using-a-generalised-translation-vector-for-handling-misspellings-and-out-of-vocabulary-oov-words-494cd142cd31)

**对于音频语音:**

1.  [IMDA(新加坡)全国演讲语料库](https://www.imda.gov.sg/programme-listing/digital-services-lab/national-speech-corpus)。拥有 1TB 数据的大型数据集。没错。那么大。一般来说，你需要大约 1000 小时的音频才能得到一个好的模型。使用它时面临的问题是磁盘空间。我的服务器没有足够的空间存放所有的音频文件，只能用 300 小时的数据进行训练。老实说，结果并不太好。我可能很快会再做这件事。
2.  [LibriSpeech ASR 语料库](http://www.openslr.org/12/)。有 1000 小时英语演讲的语料库。数据来源于不同人阅读的有声读物。数据被组织成每本书的章节。
3.  [口语维基百科全集](https://nats.gitlab.io/swc/)。这些数据由 3 种语言的维基百科口语页面组成；英语、德语&荷兰语。分别带有 395 小时、386 小时&224 小时的音频数据。在我看来，没有足够的数据来训练一个好的模型，但这是一个好的开始。清理音频数据需要一些专业知识(我还在学习)，所以这是一个很好的开始练习的方法。

**对于命名实体识别:**

1.  [CoNLL-2003](https://www.clips.uantwerpen.be/conll2003/ner/) 。一个典型的 NER 任务提取命名实体，如人，地点，组织和其他给定的句子。
2.  [安然电子邮件](http://www.cs.cmu.edu/~enron/)。一个包含 500，000 封电子邮件的数据集，带有提取姓名、日期和时间的标签。
3.  [麻省理工学院电影文集](https://groups.csail.mit.edu/sls/downloads/movie/)。只是一个简单直接的带标签的数据集，可以帮助您为 NER 任务快速建立模型。对于那些刚刚开始数据科学之旅的人来说，这是很好的实践。

# 回到 Kaggle 从来不会失败

如果上面的列表还不够，Kaggle 是一个重温你的机器学习技能的好地方。

以下是各个 NLP 任务的 Kaggle 数据集的链接:

1.  [情感分析](https://www.kaggle.com/datasets?search=sentiment+analysis)。尝试处理任何社交媒体数据！你会惊讶地发现，仅仅通过在分析之前简单地清理数据，你就可以学到很多东西。在清理过程中，你可能会问自己一些问题:“你应该对表情符号进行编码吗？怎么会？为什么？”“所有的标点符号都是一样的吗？还是说某些标点符号意味着某些东西？全面删除所有标点符号是个好方法吗？”或者“情绪分析最重要的是什么？[语法还是语义](https://towardsdatascience.com/nuances-in-the-usage-of-word-embeddings-semantic-and-syntactic-relationships-780940fe28f)？”。
2.  [文本分类](https://www.kaggle.com/datasets?search=text+classification)。尝试使用不同的输入长度处理分类任务。相对于很长的文本，你的模型在较短的文本上表现如何？有区别吗？如果是，它们是什么？你如何减轻它们？
3.  [语音语音](https://www.kaggle.com/datasets?search=audio+speech)。处理音频数据是一种有趣的体验，我建议您至少尝试一次。我以前并没有从事过多个音频项目，但是有几个要点可以告诉你如何对数据进行降噪，或者通过添加句法背景噪声来增加数据，从而获得更多数据。还有，我看了很多研究论文。端到端的 DL 结构能解决这个问题吗？或者，在继续这项任务之前，你最好先识别语音？
4.  [图像字幕](https://www.kaggle.com/datasets?search=image+captioning)。我只做过一次或者两次图像字幕。这是一个很好的体验，因为它是计算机视觉和自然语言处理的结合。如果你喜欢挑战，这是给你的。
5.  [命名实体识别](https://www.kaggle.com/datasets?search=Named+entity+recognition)。更多的时候，我在从事 NER 或某种形式的信息提取任务。这是业内非常常见的用例，用于将非结构化文本结构化。所以这是一个很好的在你空闲时间温习的机会。

# 结尾注释

就是这样！这不是一个技术性的帖子，但我只是认为为每个人整合一些文本分析数据集会很好！

Well, that’s it then! 再见!

领英简介:[谭震霆](https://www.linkedin.com/in/timothy-tan-97587190/)