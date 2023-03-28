# NLP:使用 Python 的正则表达式综合指南

> 原文：<https://pub.towardsai.net/a-comprehensive-guide-of-regular-expressions-using-python-6ff8de3d1a67?source=collection_archive---------0----------------------->

## [编程](https://towardsai.net/p/category/programming)

## NLP 文本分析中“re”模块的概念

![](img/a53844df077e55e3a3cdcb501247bed8.png)

照片由[詹姆斯·哈里逊](https://unsplash.com/@jstrippa?utm_source=medium&utm_medium=referral)在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上拍摄

> ***什么是正则表达式？***

正则表达式，也称为 RegEx，是一个独特的字符序列，有助于匹配或查找一组字符串、一个单词、一个字母甚至一个数字。我们可以通过使用一个特殊的语法后跟一个模式来实现这一点。“re”python 模块类似于“Perl”——类似于 python 中的正则表达式。

这些表达式完全在特殊符号上起作用，因为这些符号中的每一个都有它们的含义。这些符号用在搜索引擎中，取代文字处理器、文本编辑器、文本处理工具和词法分析的对话框。

> ***涵盖的主题:***

```
**1.** **RegEx functions
2\. Using r as a prefix before a String
3\. Metacharacters
4\. Special Sequences
5\. Using SETS
6\. Match Objects**
```

> ***用 python 写正则表达式程序之前要知道什么***

RegEx 程序由一个模块和包含函数、元字符、集合和序列的语句组成。现在让我们来详细看看这些主题。

> ***正则表达式模块***

Python 由一个名为“re”的内置包组成。所以每当我们使用正则表达式时，总是需要导入这个函数。

```
**Example**: import re
```

> ***正则函数***

在 python 中，re 模块提供了一组内置函数，允许我们在字符串中搜索匹配项。其中一些功能如下所示:

1.re.search():如果字符串中有匹配项，该函数返回一个匹配对象。

**程序:**

```
import restring = "Happy vaccine to us"
result = re.search( "to", string)
print(result)**Output:** <re.Match object; span=(14, 16), match='to'>
```

**解释:**这里，我们使用内置函数 search()在字符串中查找“bad”的匹配项。因为单词“to”与字符串匹配，所以显示单词的位置。如果不匹配，则返回“无”。

**2。re.findall()** :该函数返回字符串中所有匹配项的列表。

**程序:**

```
import restring = "Happy vaccine to us"
result = re.findall( "t", string)
print(result)**Output:** [‘t’]
```

**解释:**在这里，findall 函数根据字母“t”在句子中出现的次数来搜索并打印它。

**3。re.split()** :该函数返回一个列表，在该列表中，字符串在每次匹配时都被拆分。

**程序:**

```
import restring = "Happy vaccine to us"
result = re.split( "\s", string, 1)
print(result)**Output:** ['Happy', 'vaccine to us']
```

**解释:**这里，split 函数被编程为在第一次出现空白字符时进行分割。(\s 表示空白字符)

**4。re.sub()** :该函数用我们的选择替换指定的文本。

**节目:**

```
import restring = "Happy vaccine to us"
result = re.sub( "\s", "-", string)
print(result)**Output:** Happy-vaccine-to-us
```

**解释:**在这个程序中，我们使用 sub()函数将每个空白字符替换为符号'-'。

> ***在字符串前使用 r 作为前缀***

让我们用一个例子来看看这个概念。

**程序:**

```
import restring = 'Happy vaccine to us'
result = re.findall(r "\AHappy", string)
print(result)
```

**解释:**在这个程序中，行，' r "\AHappy " '表示' \ '，' A' 'The '都作为普通字符处理。而如果不使用“r ”,则在字母成为元字符之前使用符号“\”作为前缀。

[](/understand-and-building-n-gram-model-in-nlp-with-python-addddbdb71fc) [## 用 Python 理解和构建自然语言处理中 N 元语法模型

### 自然语言处理中的文本建模技术

pub.towardsai.net](/understand-and-building-n-gram-model-in-nlp-with-python-addddbdb71fc) [](/programming-14b6b5c43a5d) [## Python 中的字符串方法有助于文本处理

pub.towardsai.net](/programming-14b6b5c43a5d) 

> ***元字符***

在正则表达式中，我们知道符号起着主要作用，因为这些符号中的每一个都包含特殊的含义。元字符就是这样一种东西。他们是具有特殊意义的人物。让我们看看其中的一些符号，并理解它们的含义。

1. **[]:** 该字符表示字符串中是否存在一组字符。

**程序:**

```
import retring = "Happy vaccine to us"
result = re.findall( "[a-h]", string)
print(result)**Output:** ['a', 'a', 'c', 'c', 'e']
```

**解释:**这个程序找到所有出现在‘a’和‘h’之间的字母。如果没有字母，输出将显示为“无”。

**2。。** : 这个字符是表示换行符以外的一个字符。

**程序:**

```
import restring = "Happy vaccine to us"
r = re.findall( "v..", string)
s = re.findall( "v.", string)print(r)
print(s)**Output:** ['vac']
['va']
```

**解释:**这个程序搜索是否有匹配的字符串。如果根据出现的点的数量有一个匹配，剩余的字母将被填充。因此，输出显示为“v”。这个过程适用于下一次搜索。

**3。^:** 这个字符显示一个字符串是否以一个特定的单词/字符开始。

**程序:**

```
import restring = "Happy vaccine to us"
result = re.findall( "^The", string)
if result:
    print("The string starts with 'The' ")
else:
    print("Not matching")**Output:** Not matching
```

**解释:**这里，程序搜索字符串是否以单词‘The’开头。为此，我们使用'^'字符。如果字符串与搜索匹配，它将打印 true 语句，否则 false 语句将显示为输出。

**4。*:** 这个字符查找一个字符串是否包含一个特定的字符零次或多次。

**程序:**

```
import restring = "Happy vaccine to us"
result = re.findall( "to*", string)
print(result)**Output:** ['to']
```

**解释:**程序在后跟 0 个或多个“到”字符的字符串中搜索“到”。

**5。+:** 这个字符查找一个字符串是否包含一个特定的字符零次或多次。

**程序:**

```
import restring = "Happy vaccine to us"
result = re.findall( "a+", string)
print(result)**Output:** ['a', 'a']
```

**解释:**程序搜索字符串中的“a ”,后跟一个或多个“a”字符。

**6。{}:** 该字符查找精确指定的出现次数。

**程序:**

```
import restring = "Happy vaccine to us"
result = re.findall( "vac{2}", string)
print(result)**Output:** ['vacc']
```

**解释:**这个程序搜索一个字符串‘vacc’，后跟两个‘cc’字符。

**7。\:** 这个字符表示一个独特的序列。

**程序:**

```
import restring = "Happy 2 vaccine to us"
result = re.findall( "\d", string)
print(result)**Output:** ['2']
```

**解释:**在这里，程序查找字符串中出现的所有数字，即‘2’。

**8。|:** 该字符查找是否至少有一个匹配的定义字符串为真。

**程序:**

```
import restring = "Happy vaccine to us"
result = re.findall( "hap | vac", string)
print(result)
if result:
    print("There is a match")
else:
    print("Not matching")**Output:** [' vac']
There is a match
```

**解释:**这个程序查找是否至少有一个我们正在搜索的单词匹配(“hap | vac”)”。程序搜索字符串中的两个单词。因为只有单词“vac”存在，所以它同样返回输出。

9。$: 这个字符显示一个字符串是否以一个特定的单词/字符结尾。

**程序:**

```
import restring = "Happy vaccine to us"
result = re.findall( "us$", string)
print(result)
if result:
    print("The string ends with 'us'")
else:
    print("Not matching")**Output:** ['us']
The string ends with 'us'
```

**解释:**上面的程序显示匹配的搜索是否出现在字符串的末尾。这里，单词“friends”在字符串的末尾(匹配搜索)。因此打印第一条语句。

> ***特殊序列***

1. **\d:** 这种序列返回一个字符串中所有数字的列表。

**程序:**

```
import restring = "Happy 2 vaccine to us"
result = re.findall( "\d", string)
print(result)**Output:** [‘2’]
```

**2。\D:** 这种序列返回字符串中除数字以外的所有字符的列表。

**程序:**

```
import restring = "Happy 2 vaccine to us"
result = re.findall( "\D", string)
print(result)**Output:** ['H', 'a', 'p', 'p', 'y', ' ', ' ', 'v', 'a', 'c', 'c', 'i', 'n', 'e', ' ', 't', 'o', ' ', 'u', 's']
```

**3。\s:** 这种序列返回包含字符串中出现的空白字符的列表。

**程序:**

```
import restring = "Happy 2 vaccine to us"
result = re.findall( "\s", string)
print(result)**Output:** [' ', ' ', ' ', ' ']
```

**4。\S:** 这种序列返回字符串中除空白字符以外的字符列表。

**程序:**

```
import restring = "Happy 2 vaccine to us"
result = re.findall( "\S", string)
print(result)**Output:** ['H', 'a', 'p', 'p', 'y', '2', 'v', 'a', 'c', 'c', 'i', 'n', 'e', 't', 'o', 'u', 's']
```

**5。\w:** 这种序列返回字符串中出现的每个单词字符(a-z，0–9&_)的列表。

**程序:**

```
import restring = "Happy 2 vaccine to us"
result = re.findall( "\w", string)
print(result)**Output:** ['H', 'a', 'p', 'p', 'y', '2', 'v', 'a', 'c', 'c', 'i', 'n', 'e', 't', 'o', 'u', 's']
```

**6。\W:** 这种序列返回字符串中除单词以外的所有字符的列表。

**程序:**

```
import restring = "Happy 2 vaccine to us"
result = re.findall( "\W", string)
print(result)**Output:** [' ', ' ', ' ', ' ']
```

**7。\Z:** 如果指定的字符出现在字符串的末尾，该序列将返回一个列表。

**程序:**

```
import restring = "Happy 2 vaccine to us"
result = re.findall( "us\Z", string)
print(result)
if result:
    print("There is a match")
else:
    print("Not matching")**Output:** ['us']
There is a match
```

**8。\A:** 这个序列返回一个列表，指定出现在字符串开头的字符。

**程序:**

```
import restring = "Happy 2 vaccine to us"
result = re.findall( "\AHap", string)
print(result)
if result:
    print("There is a match")
else:
    print("Not matching")**Output:** ['Hap']
There is a match
```

**9。\b:** 这个序列返回一个列表，指定出现在一个单词的开头或结尾的字符。

**节目:**

```
import restring = "Happy 2 vaccine to us"
result = re.findall(r"\bat", string)
output = re.findall(r"at\b", string)
print(result)
print(output)**Output:** []
[]
```

**10。\B:** 该序列返回指定字符的列表，除了字符串的第一个和最后一个单词。

**程序:**

```
import restring = "Happy 2 vaccine to us"
result = re.findall(r"\Bac", string)
output = re.findall(r"ap\b", string)
print(result)
print(output)**Output:** ['ac']
[]
```

> ***使用套***

1. **[ahf]:** 这个集合返回一个包含指定字符的列表，字符串中出现“a”、“h”或“f”。

**程序:**

```
import restring = "Happy 2 vaccine to us"
result = re.findall("[act]", string)
print(result)**Output:** ['a', 'a', 'c', 'c', 't']
```

**2。[a-n]:** 此集合返回“a”和“n”之间的字符串中所有小写字符的列表。

**程序:**

```
import restring = "Happy 2 vaccine to us"
result = re.findall("[a-h]", string)
print(result)**Output:** ['a', 'a', 'c', 'c', 'e']
```

**3。[^arn]:** 这个集合返回字符串中除了‘a’、‘r’和‘n’之外的所有字符的列表。

**程序:**

```
import restring = "Happy 2 vaccine to us"
result = re.findall("[^ahf]", string)
print(result)**Output:** ['H', 'p', 'p', 'y', ' ', '2', ' ', 'v', 'c', 'c', 'i', 'n', 'e', ' ', 't', 'o', ' ', 'u', 's']
```

**4。[0123]:** 该集合返回字符串中出现的指定数字“0123”的列表。

**程序:**

```
import restring = "Happy 2 vaccine to us"
result = re.findall("[015]", string)
print(result)**Output:** []
```

**5。[0–9]:**此集合返回字符串中 0 到 9 之间任何数字的列表。

**程序:**

```
import restring = "Happy 2 vaccine to us"
result = re.findall("[0-9]", string)
if result:
    print("There is a match")
else:
    print("No match")**Output:** There is a match
```

**6。[0–5][0–9]:**此集合返回字符串中 00 到 59 之间的任何两位数的列表。

**程序:**

```
import restring = "Happy 22 vaccine to us"
result = re.findall("[0-6][0-5]", string)
print(result)**Output:** [‘22’]
```

**7。[a-za-z]:** 该集合返回字符串中出现的大写和小写字母的列表(从 A-Z 或 A-Z 开始)。

**程序:**

```
import restring = "Happy 2 vaccine to us"
result = re.findall("[a-zA-Z]", string)
print(result)**Output:** ['H', 'a', 'p', 'p', 'y', 'v', 'a', 'c', 'c', 'i', 'n', 'e', 't', 'o', 'u', 's']
```

**8。[+]:** 这个集合返回一个包含“+”符号的列表。这个概念也适用于' * '，', '|', '()', '$', '{}'.

**程序:**

```
import restring = "Happy 2 + vaccine to us"
result = re.findall("[+]", string)
print(result)**Output:** ['+']
```

> ***匹配对象***

匹配对象是包含搜索和结果信息的对象。

1. **match.group()**

group 方法()用于仅在搜索匹配时打印字符串的一部分。

**程序:**

```
import restring = "The book is on the box"
x = re.search(r"\bb\w+", string)
print(x.group())**Output:** book
```

**解释:**这里，我们已经执行了查找字母‘b’的程序。如果搜索匹配，这个单词将作为结果打印出来。

**2。match.span()**

span()方法打印第一个匹配项的开始到结束位置。让我们看看下面的例子:

**程序:**

```
import restring = "The book is on the box"
x = re.search(r"\bb\w+", string)
print(x.span())**Output:** (4, 8)
```

**解释:**这里，我们执行了搜索字母‘b’在‘字符串’中的位置的程序。输出将显示为(4，8)，因为字母“b”位于 8 个字符(包括空白字符)中的第 4 个位置。

**3。match.string**

string 属性返回我们搜索过的字符串。

**程序:**

```
import restring = "The book is on the box"
x = re.search(r"\bb\w+", string)
print(x.string)**Output:** The book is on the box
```

**解释:**上面的程序声明，如果搜索的字符与传递给函数的字符串匹配，则返回整个字符串。

> ***结论***

嘿，读者们！！本文涵盖了正则表达式的所有基本概念。我鼓励你通过执行程序来探索这个主题，并希望你在阅读这篇文章时感到有趣。

我希望你喜欢这篇文章。通过我的 [LinkedIn](https://www.linkedin.com/in/data-scientist-95040a1ab/) 和 [twitter](https://twitter.com/amitprius) 联系我。

# 推荐文章

[1。NLP —零到英雄与 Python](https://medium.com/towards-artificial-intelligence/nlp-zero-to-hero-with-python-2df6fcebff6e?sk=2231d868766e96b13d1e9d7db6064df1)
2。 [Python 数据结构数据类型和对象](https://medium.com/towards-artificial-intelligence/python-data-structures-data-types-and-objects-244d0a86c3cf?sk=42f4b462499f3fc3a160b21e2c94dba6)3 .[Python 中的异常处理概念](/exception-handling-concepts-in-python-4d5116decac3?source=friends_link&sk=a0ed49d9fdeaa67925eac34ecb55ea30)
4。[为什么 LSTM 在深度学习方面比 RNN 更有用？](/deep-learning-88e218b74a14?source=friends_link&sk=540bf9088d31859d50dbddab7524ba35)
5。[神经网络:递归神经网络的兴起](/neural-networks-the-rise-of-recurrent-neural-networks-df740252da88?source=friends_link&sk=6844935e3de14e478ce00f0b22e419eb)
6。[用 Python](https://medium.com/towards-artificial-intelligence/fully-explained-linear-regression-with-python-fe2b313f32f3?source=friends_link&sk=53c91a2a51347ec2d93f8222c0e06402)
7 全面讲解了线性回归。[用 Python](https://medium.com/towards-artificial-intelligence/fully-explained-logistic-regression-with-python-f4a16413ddcd?source=friends_link&sk=528181f15a44e48ea38fdd9579241a78)
充分解释了 Logistic 回归 8。[concat()、merge()和 join()与 Python](/differences-between-concat-merge-and-join-with-python-1a6541abc08d?source=friends_link&sk=3b37b694fb90db16275059ea752fc16a)
的区别 9。[与 Python 的数据角力—第一部分](/data-wrangling-with-python-part-1-969e3cc81d69?source=friends_link&sk=9c3649cf20f31a5c9ead51c50c89ba0b)
10。[机器学习中的混淆矩阵](https://medium.com/analytics-vidhya/confusion-matrix-in-machine-learning-91b6e2b3f9af?source=friends_link&sk=11c6531da0bab7b504d518d02746d4cc)