# 算法的最差、最佳和平均性能

> 原文：<https://pub.towardsai.net/worst-best-and-average-performance-of-algorithms-7535c43cee05?source=collection_archive---------2----------------------->

## 算法给计算机一组特定的指令

![](img/8d715780a677ec8483ba7f26c4bc8bb5.png)

马库斯·斯皮斯克在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上的照片

我们已经意识到，通过互联网或书籍，任何文本信息都可以在世界各地获得。在互联网的情况下，我们所要做的就是输入我们想要搜索的文本查询，瞧！似乎是。这些都是从计算机科学角度来看的字符串。搜索引擎使用许多算法来理解所有这些信息，使搜索更加有效。现在问题来了:**什么是算法**？

你们中有些人知道这个词，有些人不知道。算法是在计算或其他解决问题的操作中应该遵循的一组规则(**或**)，通常通过递归操作，在有限的步骤中解决数学问题的过程。

算法分析的基础包括以下内容:

1.  框架分析
2.  输入大小的测量
3.  测量运行时间的单位。
4.  最坏情况、最好情况和一般情况
5.  渐近符号

> ***框架分析***

有两种效率-

*   时间效率表示给定算法的运行速度。
*   空间效率—处理算法所需的额外空间。

> ***输入尺寸的测量***

该算法的效率是某个参数 n 的函数，该参数表示该算法的输入大小。在大多数情况下，这样一个参数的选择是非常简单的。例如，它将是排序问题、搜索、查找最小列表元素和大多数其他列表问题的列表大小。对于计算多项式 p(x) = an x n +…和 n 次 0 的问题，这将是多项式的次数或其系数的数量，比其次数大 1。在某些情况下，指示输入大小的参数的选择很重要。例如，计算两个 n 乘 n 矩阵的乘积。

这个问题的两个自然衡量标准是:

1.  矩阵的顺序 ***n***
2.  矩阵中要相乘的元素总数 N。

*   由于有一个简单的公式将这两个度量联系起来，我们可以很容易地从一个转换到另一个。但是关于算法有效性的答案将会有质的不同，这取决于我们使用两种度量中的哪一种。
*   适当度量大小的选择会受到算法操作的影响。例如，我们应该如何测量拼写检查算法的输入大小？如果一个算法检查其输入中的单个字符，我们应该通过字符的数量来衡量大小；如果它通过处理单词来工作，我们应该在输入中计算它们的数量。
*   对于涉及数字属性的算法，应该特别注意测量输入的大小(例如，检查给定的整数 n 是否是质数)。
*   计算机专家更喜欢用 n 的二进制表示中的 b 位数来衡量大小:

```
**by b=|log2n|+1**
```

这种度量通常能更好地反映相应算法的效率。

> ***测量运行时间的单位***

*   为了测量实现算法的程序的运行时间，我们可以简单地使用一些标准的时间单位——一秒、一毫秒等等。这种方法有明显的缺点。
*   依赖于特定计算机的速度。
*   这依赖于程序中实现的算法的质量。
*   编译器用于生成机器码。
*   很难测量程序的实际运行时间。既然需要衡量算法效率，就应该有一个不依赖于这些外部因素的度量。一种可能的方法是计算每个算法操作已经执行的次数。这种方法既困难又不必要。

主要目标是确定算法中最重要的操作(称为基本操作，对总运行时间贡献最大的操作),并计算基本操作的执行次数。

> ***最差、最好和一般情况下的表现***

*   将算法的效率作为指示算法输入大小的参数的函数来测量是合理的。
*   然而，有许多算法的运行时间不仅取决于输入大小，还取决于特定输入的细节。
*   例如，顺序搜索。这是一种简单的算法，通过检查列表中出现的连续元素，在 n 个元素的列表中搜索给定的项目(某个搜索关键字 K)。该算法继续检查，直到找到与搜索关键字匹配的内容，否则，列表将被用尽。
*   下面是算法伪代码，为了简单起见，列表是作为一个数组实现的。(它还假设，如果检查数组索引不超过上限的第一个条件失败，则不会检查第二个条件 A[i] i= K。

> ***渐近符号***

步骤数用于比较计算相同函数的两个程序的时间复杂度，并预测实例特征改变时运行时间的增加。确定精确的步骤数是困难的，也是不必要的，因为值不是精确的量。我们只需要像 ***c1n2 tp(n) c2n2*** 这样的比较语句。

比如考虑复杂度 ***c1n2 + c2n*** 和 ***c3n*** 的两个程序。对于较小的 n 值，复杂度取决于 c1、c2 和 c3 的值。但是也会有 n，超过 n 复杂度 c3n 比复杂度 ***c1n2 + c2n*** 要好。这个 n 值叫做临界点。

**注意: *c3n*** 在临界点为零的情况下永远快。

> ***结论***

在寻找逻辑的世界中，算法是一种需要。它构成了操场的主干。在计算机科学中，算法给计算机一组特定的指令，允许它做任何事情，无论是运行计算器还是火箭。

算法思维，或定义解决问题的清晰步骤的能力，在许多不同的领域都是必不可少的。即使我们没有意识到，我们也一直在使用算法和算法思维。算法思维允许我们分解问题，并以离散的步骤概念化解决方案。理解和实现一个算法需要学生练习结构化思维和推理。

我希望你喜欢阅读这篇文章。你可以在下一篇文章中评论你想让我讲的内容。读者们，下一个话题再见。

我希望你喜欢这篇文章。通过我的 [LinkedIn](https://www.linkedin.com/in/data-scientist-95040a1ab/) 和 [twitter](https://twitter.com/amitprius) 联系我。

# 推荐文章

[1。用 Python](/15-most-usable-numpy-methods-with-python-4d20eb93e149?sk=911d2bebf042b148be8f366b907af158)
2 最有用的 NumPy 方法。 [NumPy:图像上的线性代数](/numpy-linear-algebra-on-images-ed3180978cdb?source=friends_link&sk=d9afa4a1206971f9b1f64862f6291ac0)3。[Python 中的异常处理概念](/exception-handling-concepts-in-python-4d5116decac3?source=friends_link&sk=a0ed49d9fdeaa67925eac34ecb55ea30)
4。[熊猫:处理分类数据](/pandas-dealing-with-categorical-data-7547305582ff?source=friends_link&sk=11c6809f6623dd4f6dd74d43727297cf)
5。[超参数:机器学习中的 RandomSeachCV 和 GridSearchCV](/hyper-parameters-randomseachcv-and-gridsearchcv-in-machine-learning-b7d091cf56f4?source=friends_link&sk=cab337083fb09601114a6e466ec59689)
6。[用 Python](https://medium.com/towards-artificial-intelligence/fully-explained-linear-regression-with-python-fe2b313f32f3?source=friends_link&sk=53c91a2a51347ec2d93f8222c0e06402)
7 全面讲解了线性回归。[用 Python](https://medium.com/towards-artificial-intelligence/fully-explained-logistic-regression-with-python-f4a16413ddcd?source=friends_link&sk=528181f15a44e48ea38fdd9579241a78)
充分解释了 Logistic 回归 8。[数据分发使用 Numpy 与 Python](/data-distribution-using-numpy-with-python-3b64aae6f9d6?source=friends_link&sk=809e75802cbd25ddceb5f0f6496c9803)
9。 [40 种 Python 中最疯狂可用的方法](https://medium.com/pythoneers/40-most-insanely-usable-methods-in-python-a983c78f5bfd?sk=07df9058ea3e8c2fce4318a73cd8fce9)
10。[Python 中最常用的 20 种熊猫快捷方式](https://medium.com/pythoneers/20-most-usable-pandas-shortcut-methods-in-python-c9bc065ce11e?sk=1faf673d0cdfb46234975cbdeed12beb)