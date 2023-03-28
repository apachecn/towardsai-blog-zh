# 用抽象的方法概括新闻

> 原文：<https://pub.towardsai.net/summarizing-news-by-abstractive-approach-358b715a4038?source=collection_archive---------3----------------------->

## [自然语言处理](https://towardsai.net/p/category/nlp)

## 抽象概括

在自然语言处理中，有两种方法可以进行文本摘要。第一种是[提取方法](https://towardsdatascience.com/text-summarization-extractive-approach-567fe4b85c23)，这是一种从文章中提取关键词或句子的简单方法。有一些局限性，证明了性能不是很好。这种方法存在不相关和冗余的问题。第二种是抽象方法，即根据给定的文章生成新的句子。它需要更先进的技术，但要达到更好的效果。

![](img/87c2744d91fdb4b48b9ce9ab1dc51d0e.png)

由[凯利·西克玛](https://unsplash.com/@kellysikkema?utm_source=medium&utm_medium=referral)在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上拍摄的照片

> 这主要应用于文本。抽象方法构建原始内容的内部语义表示，然后使用该表示创建更接近人类可能表达的摘要。抽象可以通过[解释源文档的](https://en.wikipedia.org/wiki/Automated_paraphrasing)部分来转换提取的内容，从而比提取更有力地压缩文本。然而，这种转换在计算上比提取更具挑战性，既涉及[自然语言处理](https://en.wikipedia.org/wiki/Natural_language_processing)，在原始文档涉及特定知识领域的情况下，通常还涉及对原始文本领域的深入理解。

# 日常使用

我们在日常生活中有很多利用文本摘要的用例。有效的用法之一是新闻摘要。详细的新闻可能包括几个段落和超过 1000 字。通读整个新闻大约需要几分钟。人们很难消化大量的本地和国际新闻，包括许多话题，如金融、体育等。因此，新闻摘要有助于人们快速对其有一个高层次的理解。与其花 5 分钟阅读可能与我们无关的新闻，我们可能只需要 30 秒钟就能从新闻摘要中得到大概的想法。

![](img/716f4656bfc888d77f03d1d33f7c806a.png)

[奥比·奥尼耶德](https://unsplash.com/@thenewmalcolm?utm_source=medium&utm_medium=referral)在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上拍照

另一种用法是查找相关的研究论文。抽象部分帮助我们大致了解实践者想要解决什么问题，解决方案是什么。否则，我们可能需要通读 10 页才能决定这篇论文是否相关。

# 我们可以通过机器学习模型来总结新闻吗？

受益于 NLP 中的新技术，摘要新闻肯定是可以的。我们可以利用最先进的 NLP 架构，如序列到序列和变压器。此外，你需要一个包括摘要和详细新闻文章的数据集。最后，你需要一个强大的机器来训练一个新闻摘要模型。

另一种方法是利用 API 来获取新闻摘要。你只需要提供新闻的内容，不需要任何机器学习代码就可以得到摘要。

最近，我训练了一个新闻摘要模型，用于总结最新的新闻。下面是这个 API 服务的演示。

## 疫情的工作时间

这是从我的 API 中生成的这个[新闻](https://www.cnn.com/2021/02/05/business/working-from-home-hours-pandemic-scli-intl-gbr/index.html)的摘要

![](img/676eaa8a27e596abd8e14ee00a90938d.png)

API 展示

> 自上周疫情袭击欧洲以来，英国、澳大利亚、加拿大和美国的工作时间都有所增加。根据一项新的研究，在家工作的员工现在比以前更有可能投入更多的时间。

## 拉丁裔企业增长

这是另一个从我的 API 生成的关于这个[新闻](https://www.nbcnews.com/news/latino/latino-owned-businesses-are-seeing-record-growth-big-banks-are-n1256884)的摘要

![](img/edea4e264c2a10ee61e3f34126de52ed.png)

API 展示

> 根据一项新的研究，拉丁美洲人从国家银行获得资本所面临的挑战。拉丁裔拥有的企业在几个行业的增长速度超过了全国平均水平，在过去 10 年中增长了 34%，相比之下，所有其他小企业的增长率仅为 1%。

# 拿走

我训练了一个新闻摘要深度学习模型，建立了一个 web 服务器来提供这个服务。如果你想尝试这个 API 服务，请给我发邮件或信息。

# 喜欢学习？

我是湾区的数据科学家。专注于数据科学、人工智能，尤其是 NLP 和平台相关领域的最新发展。在 [LinkedIn](https://www.linkedin.com/in/edwardma1026) 或 [Github](https://github.com/makcedward) 上随时联系 [me](https://makcedward.github.io/) 。

# 延伸阅读

*   [通过结合提取和抽象步骤对文档进行总结](https://medium.com/dataseries/summarize-document-by-combing-extractive-and-abstractive-steps-40295310526)
*   [摘要提取方式说明](https://towardsdatascience.com/text-summarization-extractive-approach-567fe4b85c23)