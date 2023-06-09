# 西伯特、罗伯塔和伯特:2022 年实施哪一个？

> 原文：<https://pub.towardsai.net/siebert-roberta-and-bert-which-one-to-implement-in-2022-2964cb3a40b6?source=collection_archive---------0----------------------->

## 这些实施管道的介绍和最新更新。

![](img/5f8846129024a27a53ede3da332bb208.png)

来自 Unsplash 的安迪·凯利

# 伯特简介:

BERT 是谷歌为自然语言处理(NLP)设计的深度学习模型。BERT 旨在使机器能够以类似于人类的方式理解文本上下文。为此，BERT 使用了一种叫做双向编码的技术。这意味着它从左到右和从右到左查看文本，以提高几种自然语言理解任务的技术水平。例如，这种分析文本的方法允许 BERT 捕捉单词前后的上下文。因此，BERT 在几个 NLP 任务中非常有效，包括问题回答、文本分类和语言建模。

BERT 基于 Transformer 模型，这是一种用于解析和处理序列数据的神经网络。Transformer 模型最初是在论文“注意力是你所需要的”(Vaswani 等人，2017 年)中介绍的，此后在各种 NLP 任务中取得了成功。BERT 已经被用于构建一些有用的应用程序。例如，拥抱人脸库提供了一组预训练的模型，可用于文本分类、问题回答和其他任务。此外，该模型可以在特定任务上进行微调，如情感分析，以实现更好的性能。

该模型旨在成为自然语言理解的通用模型(NLU)，可用于文本分类等广泛的任务。BERT 的关键优势在于它可以应用于任何语言。此外，该模型是在大型文本语料库(包括整个维基百科)上预先训练的，因此很容易使用少量训练数据针对特定任务对模型进行微调。

使用 BERT 的主要优势之一是，它可以帮助您在处理机器学习模型时避免潜在的陷阱。例如，如果您正在训练一个模型来对文本进行分类，如果训练数据不平衡，您可能会无意中引入偏差。使用 BERT，您可以在平衡的数据集上训练您的模型，这有助于减少偏差。此外，通过提供上下文中单词含义的信息，BERT 可以帮助您提高模型的性能。如果您使用的是低资源语言，这种方法会很有帮助。此外，BERT 可用于预训练您的模型。如果你想使用一个最先进的模型，但是没有资源从头开始训练它，那么预训练可能是有益的。

![](img/5bfd22dc694ab0f4a5ffd1108ca6236f.png)

由[阿森托古列夫](https://unsplash.com/@tetrakiss?utm_source=medium&utm_medium=referral)在[的 Unsplash](https://unsplash.com/?utm_source=medium&utm_medium=referral)

# 以下是 BERT 的 7 大优势:

1.最先进的自然语言处理:BERT 为许多自然语言处理任务的准确性设立了新的标准，包括问题回答、文本分类和序列标记。

2.更少的假设:大多数以前的 NLP 模型对输入文本的结构做了强有力的假设，例如它是一个结构良好的句子。BERT 做了更少的假设，使得它更加灵活和准确。

3.双向:BERT 是一个双向模型，这意味着它从两个方向(左和右)考虑单词的上下文。这一点很重要，因为许多单词根据上下文可能有不同的意思。

4.预训练:BERT 是在大型文本语料库上进行预训练的，可以快速适应任何新任务。

5.迁移学习:BERT 可以用于各种任务，只需很少或不需要特定任务的培训。这使得训练和部署非常有效。

6.可伸缩性:BERT 是高度可伸缩的，可以在大型数据集上进行训练。

7.开源:BERT 是开源的，任何人都可以使用和改进。

BERT 是自然语言处理中的一个重要突破，因为它首次代表了一个模型可以从无标签文本中预训练深度双向表示。这是一项重大成就，因为它允许模型用于各种任务，而不需要特定任务的训练数据。随着 NLU 的使用越来越广泛，BERT 可能会成为开发人员越来越流行的工具。此外，该模型的灵活性和易用性使其成为那些希望创建复杂的 NLP 应用程序的人的宝贵资产。

# 罗伯塔简介:

RoBERTa 是脸书为自然语言处理(NLP)模型开发的训练和评估工具。它被设计成流行的 BERT NLP 模型的一个更加健壮和灵活的版本。RoBERTa 在几项自然语言处理任务上的表现超过了 BERT，包括句子分类、问题回答和自然语言推理。

# RoBERTa 可用于 NLP 任务的 10 个示例:

1.情感分析

2.主题分类

3.文本摘要

4.问题回答

5.对话生成

6.文本到语音转换

7.图像字幕

8.语音识别

9.机器翻译

10.自然语言理解

# 与 BERT 相比，RoBERTa 及其灵活性和稳健性的 10 种解释:

1.它使用了比 BERT 更广泛的训练数据集，包含超过 1.6 亿个句子。

2.它使用比 BERT 更深的变压器模型，有 24 个变压器层，而不是 12 个。

3.使用屏蔽语言建模目标而不是像 BERT 那样的下一句预测目标来训练它。这使得 RoBERTa 能够更好地模拟句子中单词的上下文。

4.它使用的词汇量比 BERT 大得多，超过 100 万个单词。

5.它使用子词标记化，这允许它更好地处理词汇表外的词。

6.它使用动态屏蔽进行训练，动态屏蔽随机屏蔽一定比例的输入标记，而不是总是屏蔽相同的标记。

7.它在比 BERT 更长的序列上被训练，多达 512 个记号。

8.它使用一种称为似然比训练的技术，旨在鼓励模型预测更加自信。

9.它包括一个句子级目标，鼓励模型保持句子之间的衔接。

10.它建立在流行的 PyTorch 深度学习框架之上，更易于使用和扩展。

# 关于罗伯塔内部运作的 9 个解释:

1.这是一个更新的模型，因此受益于 Transformer 架构的进步(例如，它使用更大的训练语料库和更多的层)。

2.它更能抵抗训练数据的过拟合。

3.它在几个自然语言理解任务上取得了较好的性能。

4.它使用字节对编码(BPE ),而不是像 BERT 那样的单词块编码，这有助于它更好地处理词汇表以外的单词。

5.它有一个更有效的训练动态掩蔽方案。

6.它集成了来自变压器(BERT)和 OpenAI GPT(单向变压器模型)的双向编码器表示的思想。

7.它被设计为对敌对输入(例如，被操纵来欺骗机器学习模型的文本数据)更加鲁棒。

8.它可以处理比 BERT 更长的序列，这使它更适合于回答需要更多上下文的问题等任务。

9.它使用一种叫做知识蒸馏的技术来提高下游任务的性能。

# 西伯特简介:

1.它能够对各种类型的英语文本进行可靠的二元情感分析。对于每一种情况，它预测积极(1)或消极(0)情绪[3]。

2.该模型在许多任务上取得了最先进的结果，包括情感分析、问题回答和文本分类。

3.该模型是开源的，可以在 GitHub 上获得。

# SiEBERT 的 7 大优势:

1.它是一个预先训练的语言模型，可以针对各种 NLP 任务进行微调，如文本分类、序列标记和问题回答。

2.在各种 NLP 任务中，它已经被证明优于其他预先训练的语言模型，例如 BERT。

3.它比其他预先训练的语言模型需要更少的数据，这使它成为低资源语言的理想选择。

4.它对不在词汇表中的单词是健壮的，并且可以处理输入文本中的拼写错误和错误。

5.它在大型数据语料库上训练，比其他在较小数据集上训练的模型更准确。

6.它有英语和德语两种版本，是多语言应用的好选择。

7.它是开源的，可以免费使用。

## 这是对伯特、罗伯塔和西伯特的高层次介绍。请 pm 我，如果你有任何主题，你想让我涵盖这些实施。

# 另外，请考虑订阅我的每周简讯:

[](https://pventures.substack.com/) [## 周日报告#1

### 设计思维与 AI 的共生关系设计思维能向 AI 揭示什么，AI 又能如何拥抱…

pventures.substack.com](https://pventures.substack.com/) 

参考资料:

1.facebook/opt-30b 拥抱脸。https://huggingface.co/facebook/opt-30b

2.GRUBERT:一种基于 GRU 的方法来融合 Twitter 的 BERT 隐藏层。【https://aclanthology.org/2020.aacl-srw.19.pdf 

3.[https://hugging face . co/siebert/sensation-Roberta-large-English](https://huggingface.co/siebert/sentiment-roberta-large-english)

4.[https://huggingface.co/xlm-roberta-base](https://huggingface.co/xlm-roberta-base)

5.塞伯特研究:[https://deliverypdf.ssrn.com/delivery.php?ID = 29702408500410202702507808608008109902402700305902103809312201100902512209103020220202102602902118061047123124112040640640112112121212121212120202020404121212040406404012121212](https://deliverypdf.ssrn.com/delivery.php?ID=297024085004102027025078086080081099024027003059021038093122011009025122091030102022021026029022118061047123124111121104064093044038034079014003025084066093096104076035053051120118024001007126089099083086107123025087027022014096015111089068067019082106&EXT=pdf&INDEX=TRUE)