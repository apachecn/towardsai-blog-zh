# 自然语言处理初学者指南

> 原文：<https://pub.towardsai.net/natural-language-processing-beginners-guide-461d569b70e3?source=collection_archive---------0----------------------->

## [自然语言处理](https://towardsai.net/p/category/nlp)

![](img/8cf16519acd1220eab25d50dec417c15.png)

版权:[波会计](https://www.google.com/url?sa=i&url=https%3A%2F%2Fwww.waveapps.com%2Fblog%2Faccounting-and-taxes%2Fempower-yourself-with-our-fearless-accounting-guide&psig=AOvVaw08FaRn0SxCTlOvPK4Oj8Dh&ust=1593002624651000&source=images&cd=vfe&ved=0CAMQjB1qFwoTCOCHpbL7l-oCFQAAAAAdAAAAABAD)

我发表了一篇关于自然语言处理的文章。在浏览这篇文章之前，我建议你先浏览一下上一篇文章。

[](https://medium.com/analytics-vidhya/nlp-made-easy-with-these-libraries-3fe4b1ac49a1) [## 有了这些库，NLP 变得简单了

### 什么是自然语言处理？

medium.com](https://medium.com/analytics-vidhya/nlp-made-easy-with-these-libraries-3fe4b1ac49a1) 

# 几乎每个 NLP 问题的通用过程

1.  标记化
2.  堵塞物
3.  词汇化
4.  位置标签
5.  命名实体识别
6.  组块

# 让我带你经历每一个步骤

对于一篇信息更丰富的文章，我会在中间使用一些片段，以便您可以跟随。

[***安装指南此处***](https://nltk.readthedocs.io/en/latest/install.html)

## **1。标记化**

将句子分解成单词的过程，在此过程中，标点符号将从标记中删除。

示例:-

```
# import and download the required library data
import nltknltk.download()# sentence
text = "Don't forget to follow my profile"#import the tokenization library
from nltk.tokenize import word_tokenize#Tokenization
print(word_tokenize(text)
```

**输出:**

```
['Do', "n't", 'forget', 'to', 'follow', 'my', 'profile']
```

如果你看看输出，单词“不”被分成“做”和“不”。这个函数正确地将单词分块。

**注:**

在词干提取之前，我们需要执行一个额外的步骤，即删除停用词。这一步是去掉句子中没有意义和没有任何信息的词。

```
#Import Required Library
from nltk.corpus import stopwords#Now store all the stopwords into a variable
stop_words = set(stopwords.words('english'))#Sentence
tokens = word_tokenize(text)#Create an empty list to store the filtered words
filtered_sentence = []#Removal of stopwords
for w in tokens:
    if w not in stop_words:
        filtered_sentence.append(w)#Printing the output
print(tokens)
print(filtered_sentence)
```

**输出:**

```
['Do', "n't", 'forget', 'to', 'follow', 'my', 'profile']
['Do', "n't", 'forget', 'follow', 'profile']
```

单词“to”和“my”从令牌中移除。如果你清楚地看到输出，有另一个词是没有意义的。在这种情况下，您可以创建自己的停用字词表。流程是这样的:

```
#Own Stop words list
stop_words_own = ["n't","if","by"]#Create an empty list to store the filtered words
filtered_sent = []#Removal of stopwords
for w in filtered_sentence:
    if w not in stop_words_own:
        filtered_sent.append(w)#printing the output
print(filtered_sentence)
print(filtered_sent)
```

**输出:**

```
['Do', "n't", 'forget', 'follow', 'profile']
['Do', 'forget', 'follow', 'profile']
```

## 2.**炮泥**

这是一种单词规范化技术。这个单词被转换成它的词根形式。

这是官方网站上关于词干的文档。在下面的例子中，我将使用斯特梅尔港。

```
#Import required library
from nltk.stem import PorterStemmer#Initialize the Class 
ps = PorterStemmer()#Stemmer
for w in filtered_sent:
    print(ps.stem(w))
```

**输出:**

```
Do
forget
follow
profil
```

如果您查看输出，单词“profile”被分成“profile”。每个词干分析器都有不同的工作方式。你所需要做的就是使用你的问题所需要的词干分析器。

## 3.**词汇化**

这个过程非常类似于词干。

```
#Import the required library
from nltk.stem import WordNetLemmatizer#Initialize the class
lemmatizer = WordNetLemmatizer()#Few examples
print(lemmatizer.lemmatize("cats"))
print(lemmatizer.lemmatize("cacti"))
print(lemmatizer.lemmatize("geese"))
print(lemmatizer.lemmatize("rocks"))
print(lemmatizer.lemmatize("python"))
print(lemmatizer.lemmatize("better", pos="a"))
print(lemmatizer.lemmatize("best", pos="a"))
print(lemmatizer.lemmatize("run"))
print(lemmatizer.lemmatize("run",'v'))
```

**输出:**

```
cat
cactus
goose
rock
python
good
best
run
run
```

## 4. **POS 标签**

将单词分类成它们的词性的过程被称为词性标注。

```
tags = nltk.pos_tag(filtered_sent)
print(tags)
```

**输出**

```
[('Do', 'NNP'), ('forget', 'VB'), ('follow', 'VB'), ('profile', 'NN')]
```

5.**命名实体识别**

提取人、地点、位置等实体的过程。

```
#Import the required libraries
from nltk import word_tokenize, pos_tag, ne_chunk#Sentence
sentence = "Mark and John are working at Google."# Named Entity Recognition
print(ne_chunk(pos_tag(word_tokenize(sentence))))
```

**输出:**

```
(S
  (PERSON Mark/NNP)
  and/CC
  (PERSON John/NNP)
  are/VBP
  working/VBG
  at/IN
  (ORGANIZATION Google/NNP)
  ./.)
```

# 结论:

我希望现在您已经熟悉了所有 NLP 应用程序的基本和常见步骤。不要忘记关注我，因为未来还有许多其他有趣的文章。

# 联系人:

欢迎在 LinkedIn Davuluri he manth chow dary 上与我联系