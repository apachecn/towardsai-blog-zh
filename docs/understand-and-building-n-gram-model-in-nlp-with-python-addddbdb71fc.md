# 用 Python 理解和构建自然语言处理中 N 元语法模型

> 原文：<https://pub.towardsai.net/understand-and-building-n-gram-model-in-nlp-with-python-addddbdb71fc?source=collection_archive---------1----------------------->

## 自然语言处理中的文本建模技术

![](img/83db6d75df13a96e7fede02378ddf522.png)

洛根·韦弗在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上拍摄的照片

## **简介 **

本文向您介绍了自然语言处理中 N 元语法技术的基本建模。这里，N 是指文本的不完整部分，即一系列字符、单词或句子等。状态的不同部分可以表述为马尔可夫链。

马尔可夫链用于基于序列进行预测的情况，即在遗传学中是 DNA 序列，在通信中是数据序列，等等。这是一个基于当前状态预测/预报值的过程。马尔可夫链中的状态根据概率规则变化。

例如:

```
**X** is a state and **Y** is also a state.These states are based on probability rules:
1\. State **X** to state **X** only - 50% probability
2\. State **X** to state **Y** only - 50% probability
3\. State **Y** to state **X** only - 50% probability
4\. State **Y** to state **Y** only - 50% probabilitylet's assume the initial state is **X** does to **X** itself then goes to **Y** and then goes to **X**.**XXYX** - we made a sequence based on rules.
```

[](https://medium.com/analytics-vidhya/understand-nlp-model-building-approach-with-python-b9c2d7ef8577) [## 了解使用 Python 构建 NLP 模型的方法

### 所有 NLP 分析技术的便捷概念

medium.com](https://medium.com/analytics-vidhya/understand-nlp-model-building-approach-with-python-b9c2d7ef8577) 

## 双字母和三字母

*   二元语法:当文本中的部分是 2 时，n 的平均值。
*   三元组:当文本中的部分是 3 时，表示 n 的值。

我们举个例子。

```
India is a beautiful country.Finding the grams in the text.When N=2 
Bi-grams = 'In', 'nd', 'di', 'ia', 'a ', ' i', 'is', 's ', etcWhen N=3
Tri-grams = 'Ind', 'ndi', 'dia', 'ia ', 'a i', ' is', etc.
```

在二字格和三字格中，空格是作为字符包含在内的。

就文字而言

```
When N = 2
Bi-grams = 'India is', 'is a', 'a beautiful', etcWhen N = 3
Tri-grams = 'India is a', 'is a beautiful', etc 
```

现在，实现 N-gram

导入随机库

```
import random 
```

现在，获取样本文本数据

```
text = """Fruits are important among common cultivation crops around
          the world because of its significance of good nutrition
          and health benefits"""
```

现在，从样本数据中创建 N-grams

```
n = 3ngrams = {}#creating ngrams
for i in range(len(text) - n):
    gram = text[i:i+n]
    if gram not in ngrams.keys():
        ngrams[gram] = []
    ngrams[gram].append(text[i+n])
```

查看数据的 N 元模型

```
ngrams#Output:{'Fruit': ['s'],
 'ruits': [' '],
 'uits ': ['a'],
 'its a': ['r'],
 'ts ar': ['e'],
 's are': [' '],
        .
        .
        .
 'h ben': ['e'],
 ' bene': ['f'],
 'benef': ['i'],
 'enefi': ['t'],
 'nefit': ['s']}
```

现在，是时候测试我们的模型来生成有意义的句子了

```
#testing ngram model
current_gram = text[0:n]
result = current_gram
for i in range(100):
    if current_gram not in ngrams.keys():
        break
    possibilities = ngrams[current_gram]
    next_item = possibilities[random.randrange(len(possibilities))]
    result = result + next_item
    current_gram = result[len(result) - n:len(result)]print(result)
```

“n”值的数量不同，结果也不同

```
#result with n = 3Fruits around the world because
   of its are important among common cultivation cultivation and the#result with n = 5Fruits are important among common cultivation and health benefits
```

[](/word-cloud-with-python-82e833d8c636) [## 使用 Python 的词云

### 文本注释转换为词云可视化

pub.towardsai.net](/word-cloud-with-python-82e833d8c636) 

## 结论:

本文给出了自然语言处理领域中 N 元语法的基本概念。

我希望你喜欢这篇文章。通过我的 [LinkedIn](https://www.linkedin.com/in/data-scientist-95040a1ab/) 和 [twitter](https://twitter.com/amitprius) 联系我。

# 推荐文章

[1。NLP —零到英雄与 Python](https://medium.com/towards-artificial-intelligence/nlp-zero-to-hero-with-python-2df6fcebff6e?sk=2231d868766e96b13d1e9d7db6064df1)
2。 [Python 数据结构数据类型和对象](https://medium.com/towards-artificial-intelligence/python-data-structures-data-types-and-objects-244d0a86c3cf?sk=42f4b462499f3fc3a160b21e2c94dba6)3 .[Python 中的异常处理概念](/exception-handling-concepts-in-python-4d5116decac3?source=friends_link&sk=a0ed49d9fdeaa67925eac34ecb55ea30)
4。[用 Python 进行主成分分析降维](/principal-component-analysis-in-dimensionality-reduction-with-python-1a613006d531?source=friends_link&sk=3ed0671fdc04ba395dd36478bcea8a55)
5。[用 Python 全面讲解 K-means 聚类](https://medium.com/towards-artificial-intelligence/fully-explained-k-means-clustering-with-python-e7caa573176a?source=friends_link&sk=9c5c613ceb10f2d203712634f3b6fb28)
6。[用 Python](https://medium.com/towards-artificial-intelligence/fully-explained-linear-regression-with-python-fe2b313f32f3?source=friends_link&sk=53c91a2a51347ec2d93f8222c0e06402)
7 全面讲解了线性回归。[用 Python](https://medium.com/towards-artificial-intelligence/fully-explained-logistic-regression-with-python-f4a16413ddcd?source=friends_link&sk=528181f15a44e48ea38fdd9579241a78)
充分解释了 Logistic 回归 8。[concat()、merge()和 join()与 Python](/differences-between-concat-merge-and-join-with-python-1a6541abc08d?source=friends_link&sk=3b37b694fb90db16275059ea752fc16a)
的区别 9。[与 Python 的数据角力—第一部分](/data-wrangling-with-python-part-1-969e3cc81d69?source=friends_link&sk=9c3649cf20f31a5c9ead51c50c89ba0b)
10。[机器学习中的混淆矩阵](https://medium.com/analytics-vidhya/confusion-matrix-in-machine-learning-91b6e2b3f9af?source=friends_link&sk=11c6531da0bab7b504d518d02746d4cc)