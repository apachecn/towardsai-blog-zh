# 你应该知道的 7 个很棒的 Jupyter 工具

> 原文：<https://pub.towardsai.net/7-awesome-jupyter-utilities-that-you-should-be-aware-of-f3afdb75c2b?source=collection_archive---------1----------------------->

## [数据科学](https://towardsai.net/p/category/data-science)

## 一些有用的技巧和窍门，我用在了几乎所有涉及 Jupyter 笔记本的数据科学项目中

![](img/03bff18b797bef40210c153aa5a1223a.png)

[混动](https://unsplash.com/@artbyhybrid?utm_source=medium&utm_medium=referral)在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上拍照

Jupyter 笔记本被认为是任何数据科学实验的支柱，这是有充分理由的。它们允许交互式的、有文化的编程，这是其他平台所不能提供的。

> 编写可运行的代码、提供有意义的文档、开发交互式图表，甚至重新编写和调试您的代码，在继续编写作为导入就绪模块的生产代码之前，首先在 Jupyter 笔记本中要容易得多。

在这篇简短的文章中，我分享了一些我在笔记本上编写数据科学项目时经常使用的技巧和诀窍。

我们开始吧！💥

## 模块自动重装

很多时候，我们需要在运行的中途改变我们在笔记本中导入的一些模块，通常，重启内核不是一个可行的选择。

当在笔记本的第一个单元格中运行时，这个小代码片段将允许您对笔记本外部的任何模块进行更改并保存它，允许它自动重新加载到笔记本中！

```
%load_ext autoreload 
%autoreload 2
```

这是一个非常方便的功能，我怎么强调它对我的重要性都不为过！

## 合并多个笔记本

有一个轻量级的库，可以让你把两个或更多的笔记本合并成一个。

叫 [**nbmerge**](https://pypi.org/project/nbmerge/) 。

```
!pip install nbmerge 
!nbmerge file_1.ipynb file_2.ipynb file_3.ipynb > merged.ipynb
```

在一个细胞中运行它，并看到自己的魔力！

## 信任笔记本

告诉我您在笔记本电脑运行时在您的终端中看到过此输出—***“ABC _ code . ipynb 笔记本不可信。”***

它总是出现。有时候，这就是我无法将笔记本正确导出为 PDF 文件的原因。嗯，有一小段代码可以让信息消失，并消除与笔记本的*不可信*相关的所有问题。

```
!jupyter trust file1.ipynb
```

## 导出交互式 plotly 图形

plotly 最好和最有用的功能之一是，当您与 Plotly plots 共享笔记本时，用户能够与笔记本中嵌入的 plots 进行交互。

好吧，问题是，有好几次当我试图以 PDF 或 HTML 文件的形式分享我的笔记本时，图表就是不显示。经过一番研究，我发现了两行代码可以解决这个烦人的问题，这样你就可以随心所欲地分享你的作品了。

```
import plotly 
plotly.offline.init_notebook_mode()
```

当您想要将笔记本转换为 PDF 或 HTML 文件以便共享时，请在单元格中运行此代码，这意味着此代码应该在笔记本的最后一个单元格中运行。

## 导出到 PDF 和 HTML

我知道，我知道。有一个非常简单的方法可以做到这一点。转到文件菜单，只需点击一个选项。

但是请听我说完。

通过正常方式导出到 PDF 是一个冒险的赌注。换行符被弄乱了。边距格式不正确，一些代码和输出 90%的时间被截断。用通常的简单方法做有它的好处，但是最近我发现它的缺点多于优点。

> 然而，我发现的是一个全新的小库，它不用安装/做任何其他事情，就能以一种很好的 LaTex 格式输出我们的笔记本。

它叫做[笔记本式 pdf](https://pypi.org/project/notebook-as-pdf/) 。

```
!pip install notebook-as-pdf
!pyppeteer-install
```

在这之后，你应该可以走了。只需进入文件菜单，选择导出为→ **PDF via HTML** 。

或者您可以简单地键入:

```
!jupyter-nbconvert --to PDFviaHTML file.ipynb
```

就是这样！它非常好用。试试看。

对于一个 **HTML** 输出，你不需要额外的库。事情是这样的:

```
!jupyter nbconvert my_notebook.ipynb --to html --output my_notebook.html
```

## 测量运行命令所花费的时间

这是一个方便的*魔法命令*(字面上是这么叫的，是的:P)，它使你能够测量**花费的时间:**

*   执行单行代码，如:

```
**%time** my_list = [x for x in all_items]
```

或者，

*   执行整个单元格，如下所示:

```
**%%time**my_list = [x for x in all_items]with open('a.txt') as f:
    '''do something'''
```

我通常利用一些长时间运行的操作，比如**计算一大块文本的句子嵌入，通过 DataLoader 加载数据，**等等，这是 iPython 的一个巧妙的小特性。

最后，

## 通过自定义主题提高您的工作效率

最近，我在 jupyter 笔记本上用了很多黑色主题。它看起来很舒服，总的来说，也很有美感。相信我，如果你的代码编辑器看起来和你喜欢的完全一样，你会更喜欢长时间工作。

开始只需要安装一个库并选择一个主题。

```
pip install jupyterthemes
```

然后，获取主题列表:

```
!jt -t
```

像这样选择一个:

```
!jt -t <theme_name>
```

检查图书馆的官方回购。如果您感兴趣的话，它提供了对特性的详细解释。

我目前选择的主题是海洋。这对我的生产力有好处。找到自己的最爱！:)

感谢您的阅读！😄

> 我定期写下我在数据科学中所学到的东西。独自学习可能会很艰难，[跟我来这里](https://medium.com/@ipom)让我们也让它变得愉快，一次一篇有趣的文章。

[这是我所有数据科学故事的代码库。](https://github.com/yashprakash13/data-another-day)快乐学习！

我还有几个故事让你感兴趣:

[](https://towardsdatascience.com/deploying-an-ml-model-with-fastapi-a-succinct-guide-69eceda27b21) [## 使用 FastAPI 部署 ML 模型——简明指南

### 如何使用 NLP 模型作为 API——智能的、生产就绪的方式。

towardsdatascience.com](https://towardsdatascience.com/deploying-an-ml-model-with-fastapi-a-succinct-guide-69eceda27b21) [](https://towardsdatascience.com/26-datasets-for-your-data-science-projects-658601590a4c) [## 为您的数据科学项目提供 26 个数据集

### 众多基于任务的数据集的汇编，可用于构建您的下一个数据科学项目。

towardsdatascience.com](https://towardsdatascience.com/26-datasets-for-your-data-science-projects-658601590a4c)