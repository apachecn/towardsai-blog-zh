# 构建 ML 或 DNN 模型的技巧

> 原文：<https://pub.towardsai.net/tricks-of-building-an-ml-or-dnn-model-b2de54cf440a?source=collection_archive---------1----------------------->

## [机器学习](https://towardsai.net/p/category/machine-learning)

![](img/dcdd34392428305d7562a436f179facd.png)

[马志威](https://unsplash.com/@makcedward?utm_source=medium&utm_medium=referral)在 [Unsplash](https://unsplash.com/?utm_source=medium&utm_medium=referral) 上拍照

每个人都可以轻松地将数据放入任何模型机器学习或深度学习框架中。遵循最佳实践可能有助于您区分他人。此外，您可以考虑以下技巧。以下是我在数据科学家之旅中应用的一些方法。

# 目录

***数据准备***

*   处理您自己的数据
*   使用张量
*   数据扩充
*   采样相同的数据

***模特培训***

*   保存中间检查点
*   虚拟纪元
*   简单就是美
*   简化问题

***调试***

*   简化问题
*   使用评估模式进行培训
*   数据移位
*   解决拟合不足问题
*   解决过度拟合问题

***制作***

*   元数据关联
*   切换到推理模式
*   缩放成本
*   无国籍的
*   分批法
*   使用 C++

# 数据准备

## 处理您自己的数据

![](img/39acc34b6a1f8016814f83a0946bcdb4.png)

[奥利弗·黑尔](https://unsplash.com/@4themorningshoot?utm_source=medium&utm_medium=referral)在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上拍摄的照片

建议在模型内(或预测服务内)处理数据。原因是消费者可能不知道如何做到这一点，并使特征工程对他们透明。

*   以一个 ***文本分类*** 问题为例，你正在使用 [BERT](https://towardsdatascience.com/how-bert-leverage-attention-mechanism-and-transformer-to-learn-word-contextual-relations-5bbee1b6dbdb) 进行分类。您不能要求您的客户端进行令牌化和功能对话(将文本转换为令牌 ID)。
*   以一个 ***回归问题*** 为例，日期(如 10/31/2019)是特征之一。在您的初始模型中，您可能只使用一周中的某一天(即星期四)作为一个特性。经过几次迭代之后，星期几不再是一个好的特性，您希望只使用 day(即 31)。如果您的客户仅通过日期(即 2019 年 10 月 31 日)，而不是从第 1 天开始的一周中的某一天(即 31 日)，则您不需要为了推出新模型而更改 API 接口。
*   以 ***自动语音识别*** 为例，消费者只能向你发送音频，而不能发送梅尔频率倒谱系数(MFCC)等经典特征。

因此，建议将数据预处理嵌入到您的管道中，而不是要求您的客户端去做。

## 使用张量

张量是一个 N 维数组，为多维计算而优化。它比使用 Python 字典或数组更快，深度学习框架(例如 PyTorch 或 TensorFlow)的预期数据格式是张量。

## 数据扩充

缺乏标记数据是从业者通常处理的挑战之一。迁移学习是克服的方法之一。可以考虑用 ResNet(计算机视觉)，BERT(自然语言处理)。另一方面，可以生成合成数据来增加标注数据。[图释](https://github.com/albumentations-team/albumentations)和 [imgaug](https://github.com/aleju/imgaug) 帮助生成图像数据，而 [nlpaug](https://github.com/makcedward/nlpaug) 生成文本数据。

如果你了解你的数据，你应该量身定做增强方法。请记住，数据科学的黄金法则是垃圾进垃圾出。

## 采样相同的数据

![](img/b1118503268fa50ef9b6c66530b32629.png)

杰里米·毕晓普在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上拍摄的照片

大多数时候，我们希望随机抽取数据，以便保持样本数据在训练集、测试集和验证集中的分布。同时，您希望一直保持这种“随机”行为，这样您就可以获得相同的训练集、测试集和验证集。

*   如果数据带有日期属性，您可以很容易地按该列拆分数据。
*   否则，您可以更改种子，以便获得一致的随机行为。

```
import torch
import numpy as np
import randomseed = 1234
random.seed(seed)
np.random.seed(seed)
torch.manual_seed(seed)
torch.cuda.manual_seed(seed)
```

# 模特培训

## 保存中间检查点

重新升级到保存已训练的模型，一种更简单的方法是在完成整个训练过程后保存它。然而，有几个缺点。让我们一起经历吧。

*   由于 ***模型的复杂性、计算资源以及训练*数据**的大小，整个模型训练过程可能需要几天或几周的时间。如果没有持久的中间检查点，那就太危险了，因为机器可能会被意外关闭。
*   一般来说，较长的训练模型导致较好的结果(例如，较少的损失)。然而，过度拟合可能会发生。***e****最后一个关卡在大部分时间里并没有交出最好的成绩。大多数时候，我们需要使用中间检查点进行生产。*
*   ****使用提前停止机制*** 省钱。注意到一个模型在几个时期内没有改进，我们可以更早地停止它以节省时间和资源。你可能会争辩说，最好的模型可能是在几个时代之后训练出来的。这是你如何平衡它。*

*那么我们能做到吗？理想情况下，您可以持久化所有检查点(例如，在每个时期后保存模型)，但是这需要大量存储。事实上，我们建议只保留最佳模型(或最佳三个模型)和最后一个模型。*

## *虚拟纪元*

*历元是模型训练中非常常见的参数。如果初始化不正确，可能会影响模型性能。*

*例如，如果我们有 100 万条记录，并且我们为训练设置了 5 个时期，则总共有 500 万(1M *5)个训练数据。三周后，我们又获得了 50 万张唱片。如果我们使用相同的历元(即 5)进行模型训练，则总训练数据变成 750 万(1.5M *5)。这些问题是:*

*   *可能不容易知道模型的改进是由增加唯一训练数据还是增加总训练数据引起的。*
*   *新的 0.5M 将训练时间延长到一个小时甚至几天。它增加了机器故障的风险。*

*代替使用静态时期，建议使用虚拟时期来代替原始时期。虚拟时期可以基于训练数据的大小、期望时期、批量大小来计算。*

*这是我们通常的设置:*

```
*#original
num_data = 1000 * 1000
batch_size = 100
num_step = 14 * 1000 * 1000
num_checkpoint = 20
steps_per_epoch = num_step//num_checkpoint#TensorFlow/ Keras
model.fit(x, epoch=num_checkpoint, steps_per_epoch=steps_per_epoch,
  batch_size=batch_size
)*
```

*事实上，您可以使用以下设置:*

```
*num_data = 1000 * 1000
num_total_data = 14 * 1000 * 1000
batch_size = 100
num_checkpoint = 20
steps_per_epoch = num_total_data // (batch_size*num_checkpoint)#TensorFlow/ Keras
model.fit(x, epoch=num_checkpoint, steps_per_epoch=steps_per_epoch,
  batch_size=batch_size
)*
```

## *简单就是美*

*![](img/cc5574c6981e8672bc3e61cffd9afb54.png)*

*[LUM3N](https://unsplash.com/@lum3n?utm_source=medium&utm_medium=referral) 在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上拍照*

*从业者打算使用最先进的模型来构建一个初始模型。事实上，总是建议构建一个足够简单的模型作为基线模型。原因是:*

*   *我们总是需要一个 ***基线模式* l** 来证明所提出的模型。很难告诉客户我们惊人的深度神经网络模型比其他模型更好。*
*   *基准模型在性能方面不需要很好，但必须是 ***可解释*** 。商业用户总是想知道预测结果的原因。*
*   ****容易实现* t** 很重要。客户不能为了得到一个足够好的模型而等待一年。我们需要建立一套模型，以便从投资者那里获得动力，在初始模型的基础上建立您的精彩模型。*

*以下是不同领域的一些建议基线模型:*

*   ****声学*** :您可以使用经典特征，例如梅尔倒谱系数(MFCC)或梅尔频谱图特征，而不是训练模型来获得矢量表示(即嵌入层)。将这些特征传递给单层长短期记忆(LSTM)或卷积神经网络(CNN)和完全连接的层，用于分类或预测。*
*   ****计算机视觉*** (CV): TODO*
*   ****自然语言处理(NLP)*** :使用[单词袋](https://towardsdatascience.com/3-basic-approaches-in-bag-of-words-which-are-better-than-word-embeddings-c2cbc7398016)或[经典单词嵌入](https://towardsdatascience.com/3-silver-bullets-of-word-embedding-in-nlp-10fa8f50cc5a)与 LSTM 是一个很好的起点，以后再转移到基于 transformer 的模型，如 [BERT](https://towardsdatascience.com/how-bert-leverage-attention-mechanism-and-transformer-to-learn-word-contextual-relations-5bbee1b6dbdb) 或 [XLNet](https://medium.com/dataseries/why-does-xlnet-outperform-bert-da98a8503d5b) 。*

# *排除故障*

## *简化问题*

*有时，分类问题包括 1000 个类别的 100 万个数据。当模型性能低于您的异常时，调试您的模型就太难了。糟糕的性能可能由 ***模型复杂性、数据质量或***bug 造成。因此，建议简化问题，这样我们可以保证它没有 bug。我们利用 ***过拟合*** ***问题*** 来实现这个目标。*

*您可以对 10 个类别(每个类别 100 条记录)进行采样，并训练您的模型，而不是对 1000 个类别进行分类。通过使用相同的训练数据集(或子集)作为评估数据集，您应该能够 ***过度拟合您的模型，并获得良好的*结果**(例如，80 甚至 90+精度)。如果没有，你的模型开发可能存在一些 bug。*

## *使用评估模式进行培训*

*如果评估设置精度在前几个时期没有变化，您可能会忘记在评估后重置“训练”模式*

*在 [PyTorch](https://pytorch.org/docs/stable/nn.html?highlight=module%20eval#torch.nn.Module.eval) 中，训练和评估时需要切换`train`和`eval`模式。如果启用了训练模式，批标准化、丢弃或其他层将受到影响。有时，您可能会在评估后忘记启用它。*

```
*model = MyModel() # Default mode is training modefor e in range(epoch):
  # mode.train() # forget to enable train mode
  logits = model(x_train)
  loss = loss_func(logits, y_train)
  model**.**zero_grad()
  loss.backward()
  optimizer.step()mode.eval() # enable eval mode
  with torch.no_grad():
    eval_preds = model(x_val)*
```

## *数据移位*

*当训练数据集不同于评估/测试数据集时，会发生数据移动。在计算机视觉(CV)任务中，可能大多数训练数据是白天的图片，而测试数据是晚上的图片。*

*![](img/a1204fd0249113c297b7b3bcb9a8ffee.png)*

*日日夜夜在同一个地方([来源](https://petapixel.com/2015/11/17/a-time-lapse-of-hong-kong-that-bounces-between-day-and-night/))*

*如果您发现训练损失/准确性和测试损失/准确性之间有很大差异，您可以从两个数据集中随机选取一些样本进行检查。要解决这个问题，您可以考虑:*

1.  *确保 ***在训练、测试和在线预测数据集之间的***数据上保持相似的分布。*
2.  *如有可能，添加 ***更多训练数据*一个**。*
3.  *利用库添加 ***合成数据*和**。考虑使用 [nlpaug](https://github.com/makcedward/nlpaug) (用于自然语言处理和声学任务)和 [imgaug](https://github.com/aleju/imgaug) (用于计算机视觉任务)。*

## *解决拟合不足问题*

*欠拟合意味着训练误差大于预期误差。换句话说，模型不能达到预期的性能。造成大误差的因素很多。要解决这个问题，您可以从一个更简单的方法开始，看看它是否可以解决。如果这个问题能够在早期阶段得到解决，您可以节省更多的时间，因为它更容易减少人力。*

1.  *执行错误分析。 ***通过[石灰](https://towardsdatascience.com/3-ways-to-interpretate-your-nlp-model-to-management-and-customer-5428bc07ce15)、 [SHAP](https://towardsdatascience.com/interpreting-your-deep-learning-model-by-shap-e69be2b47893) 或[主播](https://towardsdatascience.com/anchor-your-model-interpretation-by-anchors-aa4ed7104032)来解读你的模型*、T25，这样你就能对问题有所感悟。***
2.  *初始模型可能过于简单。 ***增加模型复杂度*** 如增加长短期记忆(LSTM)层，卷积神经网络(CNN)层，或全连接(FC)层。*
3.  *通过 ***减少正则化图层*** 一点点过度拟合模型。脱落和重量衰减旨在防止过度拟合。你可以试着移除那些规则布局，看看是否能解决问题。*
4.  *采用 ***最先进的模型架构*。**考虑在自然语言处理(NLP)中使用变形器(如 [BERT](https://towardsdatascience.com/how-bert-leverage-attention-mechanism-and-transformer-to-learn-word-contextual-relations-5bbee1b6dbdb) 或 [XLNet](https://medium.com/dataseries/why-does-xlnet-outperform-bert-da98a8503d5b) )。*
5.  ****介绍合成数据*** 。生成更多数据有助于提高模型性能，无需任何人工操作。理论上，生成的数据应该共享同一个标签。它允许模型“看到”更多不同的数据，并最终提高稳健性。你可以利用 [nlpaug](https://github.com/makcedward/nlpaug) (用于自然语言处理和声学任务)和 [imgaug](https://github.com/aleju/imgaug) (用于计算机视觉任务)来执行 ***数据增强* n** 。*
6.  *分配更好的超参数和优化器。您可以考虑执行超参数调整，而不是使用默认/通用学习速率、时期、批量大小。考虑使用波束搜索、网格搜索或随机搜索来 ***确定更好的超参数和优化器*** 。这种方法相对简单，只需改变超参数，但可能需要较长的时间。*
7.  *重新访问您的数据并引入额外功能。*

## *解决过度拟合问题*

*除了拟合不足，你还可能面临拟合过度的问题。过度拟合意味着您的模型太适合您的训练，而对于其他数据不够一般化。换句话说，你的训练损失/准确性比验证损失/准确性更好。考虑以下方法来解决它*

1.  *执行错误分析。 ***通过[石灰](https://towardsdatascience.com/3-ways-to-interpretate-your-nlp-model-to-management-and-customer-5428bc07ce15)、 [SHAP](https://towardsdatascience.com/interpreting-your-deep-learning-model-by-shap-e69be2b47893) ，或者[主播](https://towardsdatascience.com/anchor-your-model-interpretation-by-anchors-aa4ed7104032)来解读你的模型*** 这样你就能对问题有所感悟。*
2.  *如果可能，添加更多培训数据。*
3.  ****介绍*** ***正则化和归一化图层*** 。丢弃(正则化层)和批量归一化(归一化层)通过移除一些输入和平滑输入来帮助减少过度拟合。*
4.  ****介绍合成数据*** 。生成更多数据有助于提高模型性能，无需任何人工操作。理论上，生成的数据应该共享同一个标签。它允许模型“看到”更多不同的数据，并最终提高稳健性。你可以利用 [nlpaug](https://github.com/makcedward/nlpaug) (用于自然语言处理和声学任务)和 [imaug](https://github.com/aleju/imgaug) (用于计算机视觉任务)来执行 ***数据扩充* n** 。*
5.  *分配更好的超参数和优化器。您可以考虑执行超参数调整，而不是使用默认/通用学习速率、时期、批量大小。考虑使用波束搜索、网格搜索或随机搜索来 ***确定更好的超参数和优化器*** 。这种方法相对简单，只需改变超参数，但可能需要较长的时间。*
6.  *使用提前停止机制来寻找最佳模型。*
7.  ****清除特征*** 。*
8.  *模型可能过于复杂。 ***减少*** ***模型复杂度*** 。*

# *生产*

## *元数据关联*

*在你的模型被展示之后，你需要检查一些例外的情况。一种方法是生成 ID 并将其保存到数据库中。但是，它带来了几个问题，增加了故障排除的难度。以下是一些缺点:*

*   *耦合问题影响了系统的灵活性。从架构设计的角度来看， ***解耦是构建高灵活性系统*** 的途径之一。如果我们生成一个 ID 并将带有这个 ID 的预测结果传递给一个客户机，客户机需要将它保存在数据库中。如果我们改变了格式或数据类型，你需要通知所有消费者更新他们的数据库方案。*
*   *我们可能需要根据消费者的主键收集更多的元数据。额外的主键 ***增加了连接复杂度和存储消耗*** 。相反。*

*为了克服这个问题，预测结果应该直接与消费者的主键相关联。*

## *切换到推理模式*

*使用 PyTorch 时，在将模型部署到生产环境中时，有几个设置需要注意。前面提到的 PyTorch 中的`eval`,它使那些层(例如 dropout、BatchNorm)以推理模式工作，例如在推理时间不应用任何 Dropout 动作。它不仅加快了你的过程，而且将所有信息输入神经网络。`detach`和`torch.no_grad`将帮助你从一个图形中得到一个结果，并且使用更少的内存。*

```
*mode.eval() # enable eval mode
with torch.no_grad():
  eval_preds = model(x_val)*
```

## *缩放成本*

*当您尝试向外扩展 API 以处理更多吞吐量时，有时可以考虑使用 GPU。GPU VM 确实比 CPU 贵很多。但是 GPU 给你带来了一些优势，比如计算时间更少，维持同样的服务水平需要更少的 VM。试着评价一下，看 GPU 是不是省点钱。*

## *无国籍的*

*尽量让你的 API 无状态，这样你的 API 服务就可以很容易的伸缩。无状态意味着不在 API 服务器中保存任何中间结果(内存或本地存储)。只要保持 API 服务器简单，并将结果返回给客户机，而不在内存或本地存储中存储任何东西。*

## *分批法*

*预测一组记录通常比逐个记录要快。大多数现代机器学习或深度学习框架优化了预测性能(在速度方面)。您可能会注意到切换到批处理模式预测有很大的改进。*

## *使用 C++*

*虽然 Python 是机器学习领域的一等公民，但与 C++等其他编程语言相比，它可能太慢了。如果你想要低延迟推理时间，你可以考虑使用 [TorchScript](https://pytorch.org/docs/stable/jit.html) 。总的想法是，您仍然可以用 Python 训练您的模型，并通过使用它来生成 C++兼容的模型。*

# *参考*

*   *[机器学习设计模式](https://medium.com/@lakshmanok/machine-learning-design-patterns-58e6ecb013d7)*
*   *[深度神经网络故障排除](http://josh-tobin.com/assets/pdf/troubleshooting-deep-neural-networks-01-19.pdf)*
*   *[PyTorch 投入生产](https://tarasmatsyk.com/posts/4-how-to-pytorch-in-production/)*
*   *[NLP 增强库](https://github.com/makcedward/nlpaug)*