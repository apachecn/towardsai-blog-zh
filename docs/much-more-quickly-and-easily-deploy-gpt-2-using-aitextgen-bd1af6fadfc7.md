# 使用 Aitextgen 更快、更轻松地部署 GPT-2

> 原文：<https://pub.towardsai.net/much-more-quickly-and-easily-deploy-gpt-2-using-aitextgen-bd1af6fadfc7?source=collection_archive---------3----------------------->

## 通过集成 PyTorch、拥抱脸变形金刚和使用 Aitextgen 的 GPT-2，更快地解决您的文本生成问题。

![](img/048292e090e6b581eaf2fb9e5c1097cd.png)

来自 Pexels 的 Andrea Piacquadio

# Aitextgen 简介:

Aitextgen 是一个工具，允许开发人员训练和部署人工智能模型来生成文本。它利用 [PyTorch](https://pytorch.org/) 和[拥抱脸变形金刚](https://github.com/huggingface/transformers)使用 GPT-2 生成文本的能力，并可用于在任何类型的文本数据上训练模型。Aitextgen 为训练和部署 AI 模型提供了一个简单的接口，它还包括几个用于监控和优化模型性能的工具。

当 Aitextgen 通过跨神经网络的集成使用训练(如果应用)来生成文本时，它集成了一种称为迁移学习的技术，这种技术允许模型从更大的预训练模型中学习来完成这项任务(文本生成)。

例如，用户可以提供用于训练模型的训练数据集。随后，该模型可用于生成新文本。

## Aitextgen 在 OpenAI 的预训练 124 米/355 米/774 米 GPT-2 模型或 EleutherAI 的 125 米/355 米 GPT 近地天体模型上进行微调。此外，您可以选择创建自己的 GPT-2/GPT 近地天体模型。

Aitextgen 决定与变压器集成，这使得用户可以灵活地实施:

> “通过 Transformers，Aitextgen 保持了与基础包的兼容性，允许您将模型用于其他 NLP 任务，从 HuggingFace 模型库中下载定制的 GPT-2 模型，并上传您自己的模型！此外，它使用包含的 generate()函数来对生成的文本进行大量控制"[2]。

# 一些高级用例:

1.生成与培训数据相似的文本。GPT-2 已经被用于提高其他机器学习模型的性能，例如用于命名实体识别和文本分类的模型。

2.文本分类。通过激活 GPT-2，你可以实现机器翻译，问题回答和摘要。此外，GPT-2 可用于生成文本，这些文本可用于创建新文档或改进现有文档。此外，GPT-2 可用于为其他机器学习模型提供上下文，使它们更加准确。

3.信息提取。GPT-2 已被证明在语言之间的翻译是有效的，因此，可以用来改善机器翻译系统。此外，GPT-2 可用于生成新的翻译，这可用于进一步改善机器翻译系统。

4.产生正面或负面的评价。

5.总结。GPT-2 已被证明在摘要文本方面是有效的，因此，可以用来改进文本摘要系统。此外，GPT-2 可用于生成新的摘要，这可用于进一步改进文本摘要系统。

Aitextgen 是开源软件，可以在 GitHub 上使用(参见参考书目下面的链接)。

![](img/49a90da06451964715fc1f74df789bab.png)

来自 Pexels 的 Tara Winstead

# 实施管道:

## 安装 aitextgen:

aitextgen 的要点文件

## 要在您的计算机上测试 aitextgen，您可以从这里开始:

## 如何加载模型:

以下是生成参数:

*   `n`:要生成的文本数量。
*   `max_length`:生成文本的最大长度。默认情况下，该数字为 200。1024 是 GPT 2 号的长度。2048 年是 GPT 尼奥的长度。
*   `prompt`:本声明将包含在答复中；这条语句将是整个输出的开始。
*   `temperature`:控制文字的“疯狂度”(默认值:0.7)
*   `top_k`:如果非零，将采样的令牌限制为前 *k* 个值。默认值为 0。
*   `num_beams`:如果该数字大于 1，则执行波束搜索。
*   `repetition_penalty`:如果该数字大于 1.0，则存在重复惩罚。

## **生成函数:**

首先，您必须确保有一个对象，如 aitextgen，带有一个加载的模型和一个标记器。然后:

*   `ai.generate()`:生成并打印文本。
*   `ai.generate_one()`:基于生成的文本返回一个字符串。
*   `ai.generate_samples()`:生成多条文本。

Hugging Face 成立于 2015 年，是一家总部位于纽约市的公司，旨在让人们轻松找到、使用和分享人工智能模型。该公司的旗舰产品是一个预训练的自然语言处理模型的开源库，开发人员可以使用它来轻松地将文本分类、实体识别和机器翻译等功能添加到他们的应用程序中。拥抱脸的使命是让开发者更容易构建使用人工智能的应用程序。

PyTorch 是一种开源的机器学习能力，它提供了灵活性，特别是对于使用 GPU 和 CPU 的深度学习。PyTorch 为深度学习提供了广泛的工具，包括自动微分、神经网络和丰富的优化器。PyTorch 也是发展最快的深度学习平台之一，贡献者社区不断增长。(来源:[https://pytorch.org/)](https://pytorch.org/))

创建 Aitextgen 的主要动机是“让这项技术更容易使用，并准确展示它的前景和局限性”[4]。

好了，伙计们。如果你对我的帖子有任何问题或编辑，请联系我。

参考书目:

1.Github 上的 aitextgen。https://github.com/minimaxir/aitextgen

2.aitextgen:[https://docs . aitextgen . io](https://docs.aitextgen.io/)

3.pytorch.org。

4.[https://docs.aitextgen.io/ethics/](https://docs.aitextgen.io/ethics/)

5.语言模型是一次性学习者。预印本 arXiv:2005.14165。

6.语言模型是无人监督的多任务学习者。OpenAI 博客。[https://openai.com/blog/better-language-models/](https://openai.com/blog/better-language-models/)

7.评价阅读理解系统的对立例子。arXiv 预印本 arXiv:1707.07328。

8.小队:机器理解文本的 10 万+题。arXiv 预印本 arXiv:1606.05250。