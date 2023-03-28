# 基本预处理技术

> 原文：<https://pub.towardsai.net/essential-preprocessing-techniques-11b0f591bf3a?source=collection_archive---------2----------------------->

## [自然语言处理](https://towardsai.net/p/category/nlp)

文本数据的预处理技术用代码来解释，这些代码只通过预处理数据来改善结果。

![](img/6fe1459c9452b5ae0b9eca35d76a59d2.png)

[苏伦德兰议员](https://unsplash.com/@sure_mp?utm_source=medium&utm_medium=referral)在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上的照片

使用的数据肯定是机器学习任务中最有影响力的元素之一。当然，所使用的技术应该根据**类型的数据**(例如*文本*数据，如在线帖子或对话、*图像*或*音频*)以及项目的**目的(例如*分类*、*分析*)来选择。**

预处理步骤的目标是清除数据并对其进行转换，以使模型具有最佳的可能结果。因为文本数据是自然语言，所以它可能包含不相关和无用的信息，这些信息应该被消除。另一个方面是，模型的数据应该是一致的，以提取尽可能多的信息。

## NLP 的最佳库

首先，为了执行这些技术，必须导入和使用特定的库。或许，NLP 最流行的库之一是自然语言工具包，称为 [**NLTK**](https://www.nltk.org/) 。这是最复杂的自然语言处理库之一。

更新和更侧重于优化， [**spaCy**](https://spacy.io/) 是另一个很好的选择，如果你想处理文本数据。这个库比 NLTK 快得多，也准确得多。

处理文本数据的一种方法是通过称为 **RegEx 的正则表达式。** Python 有一个专门为正则表达式操作创建的内置包，更准确地说是**[**re**](https://docs.python.org/3/library/re.html)**。****

**[**Scikit-learn**](https://scikit-learn.org/stable/index.html)**是使用最多的机器学习库之一。这不是 NLP 的专长，但是它有很多预处理数据的工具。除了用于在分类之前准备数据的许多方法之外，它还具有文本数据方面的专门工具(例如，CountVectorizer、TfidfVectorizer)。****

## ****文本数据的处理方法****

*   ******标记化******

****这是使用自然语言最基本的过程之一，几乎每个项目都有一个标记化步骤。记号化是将文本分割成记号的过程，记号表示更小的文本片段。通常，分隔符是空格“，”甚至一些标点符号如“.”。下面是一个使用 NLTK 库中的 tokenize 包进行标记化的例子。****

```
**from nltk.tokenize import word_tokenizetext = "This is an example of A phrase WIth lowercase and UPPERCASE"
tokens = word_tokenize(text)print(tokens)**[‘This’, ‘is’, ‘an’, ‘example’, ‘of’, ‘A’, ‘phrase’, ‘WIth’, ‘lowercase’, ‘and’, ‘UPPERCASE’]****
```

*   ******小写******

****计算机将单词视为数字，因此同样的单词写成小写或大写会有不同的解释。因为在大多数情况下，每个句子都以大写字母开头，所以可能会出现某些问题。下面是一个如何使用内置 Python 方法将短语转换成小写字母的示例。****

```
**text = "This is an example of A phrase WIth lowercase and UPPERCASE"
text_lower = text.lower() print(text_lower)**"this is an example of a phrase with lowercase and uppercase"****
```

*   ******删除标点符号******

****消除标点符号是最常用的文本预处理技术之一，因为它可以清除数据。在大多数情况下，标点符号是常见的，每个短语至少包含一个或两个。另一方面，在一些任务中，标点符号会带来相关信息。例如，在情绪分析中，许多暂停点*“…”*可能表示抑郁的态度，或者许多感叹号*“！”可能暗示喜悦甚至愤怒。下面你可以看到两个例子，一个使用*字符串*模块，一个使用 *re* 库。*****

```
*****# example 1***
import stringtext = "This is an example; of a phrase with a lot, of punctuation?         marks!!"
text_without_punctuations = text.translate(text.maketrans('', '', string.punctuation))print(text_without_punctuations)**"This is an example of a phrase with a lot of punctuation marks"*****# example 2***
import retext = "This is an example; of a phrase with a lot, of punctuation? marks!!"
text_without_punctuations = re.sub(r'[^\w\s]','',text)print(text_without_punctuations)**"This is an example of a phrase with a lot of punctuation marks"****
```

*   ******删除多余的空格******

****正如我在上一点中解释的，一些短语只是由于错误或在转换空格中的一些字符后有额外的空格，所以，在没有添加信息的情况下，空格的数量会大大增加。和前面的例子一样，我将介绍两种删除多余空格的方法，一种只使用特定于*字符串的*方法，另一种使用 *re* 库。****

```
*****# example 1***
text = "This is  an    example of a phrase    with a  lot of spaces!"
text_without_extra_spaces = " ".join(text.split())print(text_without_extra_spaces)**"This is an example of a phrase with a lot of spaces!"*****# example 2***
import retext = "This is  an    example of a phrase    with a  lot of spaces!"
text_without_extra_spaces = re.sub("\s\s+" , " ", text)print(text_without_extra_spaces)**"This is an example of a phrase with a lot of spaces!"****
```

*   ******删除数字******

****除了数字本身，它们也可能出现在一些单词中，尤其是在在线消息或社交媒体帖子中。比如，“ *ME2* 或者“ *4EVER* ”对于人类来说分别相当于“*我也*”到“*永远*”，但是计算机看它们完全不一样。下面是一个例子，其中只有数字从文本中删除，下面是一个例子，其中数字和包含数字的单词都被删除。对于每种情况，我将给出两个例子，一个只使用特定于*字符串的*方法，另一个使用 *re* 库。****

```
*****# example 1***
text = "Th1s 1s 1 exampl3 of a phras3 conta1n1ng 12 d1g1ts and 11 numb3rs"
text_without_numbers = ''.join([i for i in text if not i.isdigit()])print(text_without_numbers)**"Ths s exampl of a phras contanng dgts and numbrs"*****# example 2***
import retext = "Th1s 1s 1 exampl3 of a phras3 conta1n1ng 12 d1g1ts and 11 numb3rs"
pattern = r'[0-9]'
text_without_numbers = re.sub(pattern, '', text)print(text_without_numbers)**"Ths s exampl of a phras contanng dgts and numbrs"*****# example 3***
text = "Th1s 1s 1 exampl3 of a phras3 conta1n1ng 12 d1g1ts and 11 numb3rs"
text_without_numbers = ' '.join(s for s in words.split() if not any(c.isdigit() for c in s))

print(text_without_numbers)**"of a and"*****# example 4***
import retext = "Th1s 1s 1 exampl3 of a phras3 conta1n1ng 12 d1g1ts and 11 numb3rs"
text_without_numbers = re.sub(r'\w*\d\w*', '', text).strip()print(text_without_numbers)**"of a and"****
```

*   ******删除停止字******

****停用词是一种语言中最常见的词，它们存储在一个列表中，因为它们被频繁使用，所以它们不会带来任何信息。在 stop 的英文例子中，单词可以是: *the* ， *as* ， *of，*等。下面是一个如何使用 NLTK 库中的*语料库*包删除停用词的例子。必须提到的是，NLTK 包含 23 种语言的停用词列表，包括荷兰语、法语或西班牙语。在删除停用词之前，应该对文本进行标记化，以便可以过滤这些词。****

```
**from nltk.tokenize import word_tokenizetext = "This is an example of a phrase with a lot of stop words"
tokens = word_tokenize(text)for word in tokens:
    if word not in stopwords.words("english"):
        without_stop_words.append(word)
text_without_stop_words = ' '.join(without_stop_words)print(text_without_stop_words)**[‘This’, ‘example’, ‘phrase’, ‘lot’, ‘stop’, ‘words’]****
```

****除了数据清理之外，删除所有这些单词、空格或标点符号也可以缩短时间，因为数据量减少了。****

*   ******扩张收缩******

****为了更好地理解和分析文本，计算机需要知道“*不是*”和“*不是*”是同一个意思。缩略词可以用字典来解决，字典里有缩略词和扩展词，比如 [this](https://gist.github.com/nealrs/96342d8231b75cf4bb82) 。一种更方便的方法是使用 Python 库，如下面我介绍的*py constructions*或*constructions*。****

```
**!pip install contractionsimport contractionstext = "This is an example of a phrase with contractions such as: I'll, he'd, and she's."expanded_words = []
for word in text.split():
    expanded_words.append(contractions.fix(word))
text_without_contractions = ' '.join(expanded_words)print(text_without_contractions)**"This is an example of a phrase with contractions such as: I will, he would, and she is."****
```

****最后，我们来解释一下什么是词干化和词干化，它们之间有什么区别。****

*   ******术语化******

****在词元化中，通过从单词中提取词元，将单词替换为根单词或具有相似上下文的单词。它的主要目标是减少一个词的相关屈折和派生形式。在 NLTK 库的 *WordNetLemmatizer* 的帮助下，你可以看到下面的词汇化。****

```
**import nltk
from nltk.stem import WordNetLemmatizer

wnl = WordNetLemmatizer()
words = ['oxen', 'mice', 'cats', 'flying', 'singing', 
         'amazing', 'jumping', 'boring', 'went']
lemmatized_words = []for word in words:
    lemmatized_words.append(wnl.lemmatize(word))print(lemmatized_words)**[‘ox’, ‘mouse’, ‘cat’, ‘flying’, ‘singing’, ‘amazing’, ‘jumping’, ‘boring’, ‘went’]****
```

*   ******词干******

****词干化将单词形式简化为(伪)词干，这意味着它只是消除了单词的最后几个字符，存在含义和拼写错误的风险。在 NLTK 库的 *PorterStemmer* 的帮助下，你可以看到下面的词汇化。****

```
**import nltk
from nltk.stem import PorterStemmerps = PorterStemmer()
words = ['oxen', 'mice', 'cats', 'flying', 'singing', 
         'amazing', 'jumping', 'boring', 'went']
stemmed_words = []for word in words:
    stemmed_words.append(ps.stem((word)))print(stemmed_words)**[‘oxen’, ‘mice’, ‘cat’, ‘fli’, ‘sing’, ‘amaz’, ‘jump’, ‘bore’, ‘went’]****
```

****词汇化的一个优点是，与词干化不同，这种技术考虑了上下文和词性参数，因此具有更好的准确性。从给出的例子可以看出，变元化比词干化具有更精确的结果。另一方面，由于词干提取不考虑上下文，因此更容易实现，运行速度也更快。****

****在一般情况下，尤其是文本情况下，数据的预处理对于所获得的结果是非常相关的。这一步有助于计算机更好地理解文本并从中获得更多信息。****

****感谢阅读！希望你喜欢这篇文章！****