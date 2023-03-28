# ResNeXt:从零开始

> 原文：<https://pub.towardsai.net/resnext-from-scratch-e73110530586?source=collection_archive---------7----------------------->

![](img/c7c0fc3fd0286a830e145a6d888b4ff4.png)

来源: [Unsplash](https://unsplash.com/photos/8bghKxNU1j0)

## [计算机视觉](https://towardsai.net/p/category/computer-vision)，[研究](https://towardsai.net/p/category/research)

ResNeXt 遵循一个简单的概念“分而治之”。ResNeXt 通常被称为“ResNet”的扩展版本。它的一些重要应用是在生物医学工程领域，尤其是在生物成像领域。在这里，我将探索“ResNeXt 的制作:从零开始”

> 模块:PyTorch、CUDA(可选)

如果你对如何在你的系统中安装 PyTorch 感到困惑，那么你可能想看看这里的[链接](https://pytorch.org/)。它会帮助你！向前发展…

# ResNeXt

ResNeXt 体系结构与 ResNet 体系结构非常相似。如果你想了解 ResNet 架构，那么请往[这个方向](https://medium.com/analytics-vidhya/resnet-from-scratch-638e901e0934)走。这是一种基于深度学习的算法，其主要任务是理解图像特征的更深层次的见解。那我们怎么开始呢？…

```
import torch
import torch.nn as nn
```

这是在 Python 环境中初始化 PyTorch 库的初始代码块。这些都是非常庞大的架构，因此需要大量的计算。默认情况下，架构会期望系统具有良好的规格(就 CPU 和 GPU 容量而言),能够在适当的时间内以最高的准确性完成任务。

现在，如果你是 Python 的新手，想要了解这些大型 CNN 架构的基础，那么这可能对你没有什么帮助，因为在“ResNeXt”的定义中，定义了许多继承和类实例，这对有经验的程序员来说甚至很难。这对新手来说可能会很刺眼，因此我会要求你先浏览一下[OOPs](https://www.youtube.com/watch?v=SiBw7os-_zI&ab_channel=freeCodeCamp.org)的基础知识。

> 哎呀够舒服了吧？让我们继续前进…

```
class resnext_block(nn.Module):
    def __init__(self, in_channels, cardinality, bwidth, idt_downsample=None, stride=1):
        super(resnext_block, self).__init__()
        self.expansion = 2
        out_channels = cardinality * bwidth
        self.conv1 = nn.Conv2d(in_channels, out_channels, kernel_size=1, stride=1, padding=0)
        self.bn1 = nn.BatchNorm2d(out_channels)
        self.conv2 = nn.Conv2d(out_channels, out_channels, kernel_size=3, groups=cardinality, stride=stride, padding=1)
        self.bn2 = nn.BatchNorm2d(out_channels)
        self.conv3 = nn.Conv2d(out_channels, out_channels*self.expansion, kernel_size=1, stride=1, padding=0)
        self.bn3 = nn.BatchNorm2d(out_channels*self.expansion)
        self.relu = nn.ReLU()
        self.identity_downsample = idt_downsample
```

从层块的定义开始，在第一个块中，我们定义了继续推进结构所需的后续组件。这只是初始化阶段。每当我们调用该类时，该类要做的第一件事就是初始化这些模块以及它们定义的规范。

如果你已经学习了 ResNet 和 ResNeXt 的[研究论文，你可能会想到的一件事是，我们有在前面的函数中定义的组的基数和基宽。我们没有在 ResNet 中定义它，因为现在我们正在划分整个结构并将它们并排堆叠，然后分析一切。因此,“基数”将定义整个体系结构中的组，而基宽将完全定义体系结构中的“外部通道”。](https://arxiv.org/abs/1611.05431)

> 下一步做什么？…

```
def forward(self, x):
        identity = x
        x = self.conv1(x)
        x = self.bn1(x)
        x = self.relu(x)
        x = self.conv2(x)
        x = self.bn2(x)
        x = self.relu(x)
        x = self.conv3(x)
        x = self.bn3(x)

        if self.identity_downsample is not None:
            identity = self.identity_downsample(identity)

        x += identity
        x = self.relu(x)
        return x
```

初始化后将立即调用“forward”函数。正如研究论文中所描述的，这将有序地包含所有的方法。你可以在 [ResNet](https://medium.com/analytics-vidhya/resnet-from-scratch-638e901e0934) 博客中找到“转发”功能的相似之处。

> 为您呈现全新的架构…

```
class ResNeXt(nn.Module):
    def __init__(self, resnet_block, layers, cardinality, bwidth, img_channels, num_classes):
        super(ResNeXt, self).__init__()
        self.in_channels = 64
        self.conv1 = nn.Conv2d(img_channels, 64, kernel_size=7, stride=2, padding=3)
        self.bn1 = nn.BatchNorm2d(64)
        self.relu = nn.ReLU()
        self.cardinality = cardinality
        self.bwidth = bwidth
        self.maxpool = nn.MaxPool2d(kernel_size=3, stride=2, padding=1)

        # ResNeXt Layers
        self.layer1 = self._layers(resnext_block, layers[0], stride=1)
        self.layer2 = self._layers(resnext_block, layers[1], stride=2)
        self.layer3 = self._layers(resnext_block, layers[2], stride=2)
        self.layer4 = self._layers(resnext_block, layers[3], stride=2)

        self.avgpool = nn.AdaptiveAvgPool2d((1,1))
        self.fc = nn.Linear(self.cardinality * self.bwidth, num_classes)
```

我们来看“ResNeXt”架构的正式定义。同样，这是初始化阶段。人们可能会注意到，有一些' _layers '方法的初始化，但没有定义相同的实例。我们将在接下来的步骤中对其进行定义…

```
def forward(self, x):
        x = self.conv1(x)
        x = self.bn1(x)
        x = self.relu(x)
        x = self.maxpool(x)

        x = self.layer1(x)
        x = self.layer2(x)
        x = self.layer3(x)
        x = self.layer4(x)

        x = self.avgpool(x)
        x = x.reshape(x.shape[0], -1)
        x = self.fc(x)
        return x
```

“前进”功能来了。我们的 ResNeXt 函数被正式定义了。我们按照论文中的定义构建“前进”函数。使用 Conv 层的初始阶段，然后根据需要设置整个层。

```
def _layers(self, resnext_block, no_residual_blocks, stride):
        identity_downsample = None
        out_channels = self.cardinality * self.bwidth
        layers = []

        if stride != 1 or self.in_channels != out_channels * 2:
            identity_downsample = nn.Sequential(nn.Conv2d(self.in_channels, out_channels*2, kernel_size=1,
                                                          stride=stride),
                                                nn.BatchNorm2d(out_channels*2))

        layers.append(resnext_block(self.in_channels,  self.cardinality, self.bwidth, identity_downsample, stride))
        self.in_channels = out_channels * 2

        for i in range(no_residual_blocks - 1):
            layers.append(resnext_block(self.in_channels, self.cardinality, self.bwidth))

        self.bwidth *= 2

        return nn.Sequential(*layers)
```

所以，我们已经定义了一切，是时候来确定我们的推测是否正确了。我们可以实现下面给出的代码块来测试架构。

```
def ResNeXt50(img_channels=3, num_classes=1000, cardinality=32, bwidth=4):
    return ResNeXt(resnext_block, [3,4,6,3],  cardinality, bwidth, img_channels, num_classes)
```

我们完了。那是一项艰巨的工作。谢谢你坚持到最后。这是 CNN 领域中的一个重要架构，理解它确实很困难！如果您需要进一步的帮助，请参阅以下部分…

# 救援马上就到！

如果你仍然觉得你需要完整的代码，那么请点击这里的[链接](https://github.com/tanmaydn/CNNfromScratch/blob/main/ResNeXt.py)。

# 参考

请查阅研究人员的[原创作品。](https://arxiv.org/abs/1611.05431)