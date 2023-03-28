# 用句子变形库嵌入句子

> 原文：<https://pub.towardsai.net/sentence-embeddings-with-sentence-transformers-library-7420fc6e3815?source=collection_archive---------0----------------------->

## [数据科学](https://towardsai.net/p/category/data-science)，[机器学习](https://towardsai.net/p/category/machine-learning)

## 使用伯特/罗伯塔/XLM-罗伯塔公司和 PyTorch 的多语言句子嵌入

![](img/a755c1a7d85b8ef0c7fedcbb8768b658.png)

照片由[肯德尔·胡普斯](https://www.pexels.com/@ken123films)在 [Unsplash](https://www.pexels.com/photo/silhouette-photography-of-people-2901134/) 上拍摄

当我最近致力于实现语义搜索功能时，我偶然发现了这个简单易用的库。作为其中的一部分，我必须将每个文档的密集向量表示索引到 Elasticsearch 中，以便语义搜索能够工作。有了这个库，我能够快速有效地实现这个功能。我希望这篇文章对你有所帮助。

这篇文章需要嵌入的知识(单词嵌入或句子嵌入)。你可以参考[这篇](https://towardsdatascience.com/why-do-we-use-embeddings-in-nlp-2f20e1b632d2)文章，快速刷新你的记忆。如果你已经了解了嵌入，你可以继续阅读。

# 装置

```
pip install -U sentence-transformers
```

# 使用

## 1.句子嵌入

```
from sentence_transformers import SentenceTransformer
model = SentenceTransformer('model_name_or_path')
```

在下面的例子中，我们将一个预先训练好的模型`distilbert-base-nli-stsb-mean-tokens`传递给`SentenceTransformer` 来计算句子嵌入。预训练模型的完整列表见[此处](https://www.sbert.net/docs/pretrained_models.html)。请注意，没有一个嵌入可以适用于所有的任务，因此我们应该尝试这些模型中的一些，并选择最有效的一个。

> **注意** : `sentence-transformers`模型也托管在 Huggingface 存储库中。所以我们可以直接使用 Hugginface 的`Transformers`库来生成句子嵌入，而不需要安装`sentence-transformers`库。这里给出了[的示例代码](https://www.sbert.net/docs/usage/computing_sentence_embeddings.html#sentence-embeddings-with-transformers)。

## 2.语义文本相似度

现在我们已经了解了如何生成句子嵌入，下一步是比较句子的语义文本相似性，并根据余弦相似性对它们进行排序。

下面列出了句子相似度的推荐模型。这些模型在&[STS](https://www.sbert.net/docs/pretrained-models/sts-models.html)数据上训练，在 STSbenchmark 数据集上评估。作者推荐型号`distilbert-base-nli-stsb-mean-tokens`，因为它在速度和性能之间达到了完美的平衡。

**Roberta-large-nli-STSb-mean-tokens**—STSb 性能:86.39
**Roberta-base-nli-STSb-mean-tokens**—STSb 性能:85.44
—Bert-large-nli-STSb-mean-tokens—STSb 性能:85.29
**distilbert-base-nli-STSb-mean-tokens**

让我们看一个我们在前面的例子中使用的句子之间的余弦相似性的例子:

该方法使用强力方法来寻找得分最高的对，其具有二次复杂度。对于较长的句子，这种方法不可行。下面讨论的释义挖掘是最佳方法。

## 3.释义挖掘

当我们需要处理大量的句子集合(10，000 个或更多)时，会使用复述挖掘。在这里可以找到[对释义挖掘的更详细的解释。](https://www.sbert.net/docs/usage/paraphrase_mining.html#paraphrase-mining)

让我们看一个使用释义挖掘的例子:

## 4.语义搜索

传统的搜索引擎是为基于词汇的搜索而设计的，但是使用语义搜索，我们可以基于同义词来查找文档。使用我们上面学到的技术，我们可以实现语义搜索功能。语义搜索试图通过理解搜索查询的内容来提高搜索的准确性。

语义搜索最常用于 Elasticsearch 等搜索引擎。如果你对 Elasticsearch 有一个基本的了解，并通过这个[链接](https://www.sbert.net/docs/usage/semantic_search.html#elasticsearch)了解语义搜索是如何实现的。

# 结论

希望你已经理解了如何使用`sentence-transformers`库来计算句子嵌入，如何获得句子之间的相似度，以及最后我们如何确定句子嵌入来实现语义搜索。

*阅读更多关于 Python 和数据科学的此类有趣文章，* [***订阅***](https://pythonsimplified.com/) *到我的博客*[***【www.pythonsimplified.com】***](http://www.pythonsimplified.com/)***。*** 你也可以通过 [**LinkedIn**](https://www.linkedin.com/in/chetanambi/) 联系我。

# 参考

[](https://github.com/UKPLab/sentence-transformers) [## uk plab/句子-变形金刚

### 这个框架提供了一个简单的方法来计算句子和段落的密集向量表示(也称为…

github.com](https://github.com/UKPLab/sentence-transformers)  [## 句子变压器文件-句子-变压器文件

### 编辑描述

www.sbert.net](https://www.sbert.net/index.html)