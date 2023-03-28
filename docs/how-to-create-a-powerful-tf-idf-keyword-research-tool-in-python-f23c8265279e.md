# 如何用 Python 创建一个强大的 TF-IDF 关键词研究工具

> 原文：<https://pub.towardsai.net/how-to-create-a-powerful-tf-idf-keyword-research-tool-in-python-f23c8265279e?source=collection_archive---------2----------------------->

## [编程](https://towardsai.net/p/category/programming)

![](img/0c5605aca3497e588ba9b5d2d14189c1.png)

我们正处于数字营销的时代，现在**这个词**比以往任何时候都更重要。数字营销最成功的技术之一是竞争分析和关键词研究。换句话说，我们的竞争对手在谈论什么。这是最有用的搜索引擎优化，但也为博客帖子的想法等。

# 第一步:从网站上获取文本

在这一章中，我们将创建一个从 URL 中提取干净文本的函数，这样我们可以在以后的分析中使用它。

```
import pandas as pd
import numpy as np
import urllib
from fake_useragent import UserAgent
import requests
import re
from urllib.request import Request, urlopen
from sklearn.feature_extraction.text import TfidfVectorizer
from sklearn.feature_extraction.text import CountVectorizer
import math
from nltk.corpus import stopwords
stopWords = list(set(stopwords.words('english')))
from bs4 import BeautifulSoup

def get_text(url):
    try:
        req = Request(url , headers={'User-Agent': 'Mozilla/5.0'})
        webpage = urlopen(req,timeout=5).read()
        soup = BeautifulSoup(webpage, "html.parser")
        texts = soup.findAll(text=True)
        res=u" ".join(t.strip() for t in texts if t.parent.name not in ['style', 'script', 'head', 'title', 'meta', '[document]'])
        return(res)
    except:
        return False
```

我们来举个例子。

```
get_text('https://en.wikipedia.org/wiki/Machine_learning')[0:500]
#It will return the first 500 characters CentralNotice Machine learning From Wikipedia, the free encyclopedia Jump to navigation Jump to search For the journal, see Machine Learning (journal) . "Statistical learning" redirects here. For statistical learning in linguistics, see statistical learning in language acquisition . Scientific study of algorithms and statistical models that computer systems use to perform tasks without explicit instructions Part of a series on Machine learning and data mining Problems Class'
```

成功！现在我们可以从网站上获得干净的文本！但是我们到底该如何使用它呢？让我们进入下一章。

# 第二步:获取竞争对手的网址

找到最佳竞争对手的最好方法是在谷歌搜索中获得我们感兴趣的关键词的顶部结果。我们将使用前一篇文章中的代码，[如何使用 Python](https://predictivehacks.com/how-to-scrape-google-results-for-free-using-python/) 免费抓取谷歌结果。

```
def google_results(keyword, n_results):
    query = keyword
    query = urllib.parse.quote_plus(query) # Format into URL encoding
    number_result = n_results
    ua = UserAgent()
    google_url = "https://www.google.com/search?q=" + query + "&num=" + str(number_result)
    response = requests.get(google_url, {"User-Agent": ua.random})
    soup = BeautifulSoup(response.text, "html.parser")
    result_div = soup.find_all('div', attrs = {'class': 'ZINbbc'})
    results=[re.search('\/url\?q\=(.*)\&sa',str(i.find('a', href = True)['href'])) for i in result_div if "url" in str(i)]
    links=[i.group(1) for i in results if i != None]
    return (links)
```

比方说，我们希望看到“机器学习博客”这个关键词的“竞争对手”。让我们使用 google results 函数来获取排名靠前的 URL，其中第一个变量是关键字，第二个变量是结果的数量。

```
google_results('machine learning blog',10)['https://towardsai.net/p/machine-learning/best-machine-learning-blogs-6730ea2df3bd', 'https://machinelearningmastery.com/blog/', 'https://towardsdatascience.com/how-to-start-a-machine-learning-blog-in-a-month-7eaf84692df9', 'http://ai.googleblog.com/', 'https://www.springboard.com/blog/machine-learning-blog/', 'https://blog.ml.cmu.edu/', 'https://blog.feedspot.com/machine_learning_blogs/', 'https://aws.amazon.com/blogs/machine-learning/', 'https://neptune.ai/blog/the-best-regularly-updated-machine-learning-blogs-or-resources', 'https://www.stxnext.com/blog/best-machine-learning-blogs-resources/']
```

# 第三步:分析课文，找出最重要的单词。

让我们想想。最重要的词是什么？在我们的分析中，我们将使用 3 个指标。**平均 TF-IDF、最大 TF-IDF** 和**频率。**管道如下。我们将获得每个网站的文本(在我们的例子中是前 12 个结果),并将它们用作 TF-IDF 矢量器的语料库。然后从这个矩阵中，我们将得到每个单词的平均和最大 TF-IDF 分数。然后，我们可以很容易地从 TF-IDF 矩阵中获得频率，方法是说如果这个词在这一行中不等于零，它就包含在 URL 中，我们正在计算它的百分比。完整的函数如下。

```
def tf_idf_analysis(keyword):
    links=google_results(keyword,12)
    text=[]
    for i in links:
        t=get_text(i)
        if t:
            text.append(t)

    v = TfidfVectorizer(min_df=2,analyzer='word',ngram_range=(1,2),stop_words=stopWords)
    x = v.fit_transform(text)

    f = pd.DataFrame(x.toarray(), columns = v.get_feature_names())
    d=pd.concat([pd.DataFrame(f.mean(axis=0)),pd.DataFrame(f.max(axis=0))],axis=1)

    tf=pd.DataFrame((f>0).sum(axis=0))

    d=d.reset_index().merge(tf.reset_index(),on='index',how='left')

    d.columns=['word','average_tfidf','max_tfidf','frequency']

#you can comment the following part if you want the number of URLs #that the word occurs. The percentage makes sense
#when we have a lot of URLs to check

    d['frequency']=round((d['frequency']/len(text))*100)

    return(d)
```

现在我们的最终函数已经准备好了，让我们通过使用**机器学习博客**关键字来看看我们在机器学习方面的竞争对手。

![](img/0586950f38efcea9ebbe04b06efd9046.png)

```
x= tf_idf_analysis('machine learning blog')

#remove the numbers and sort by max tfidf and get the top20 words
x[x['word'].str.isalpha()].sort_values('max_tfidf',ascending=False).head(20)word  average_tfidf  max_tfidf  frequency
929      google       0.098790   0.626160       67.0
254         aws       0.052512   0.550785       25.0
171      amazon       0.060131   0.537993       33.0
1472      model       0.058276   0.521179       33.0
307        blog       0.131429   0.385008      100.0
133          ai       0.109516   0.358522       83.0
1222   learning       0.191090   0.352528      100.0
717         end       0.036682   0.304649       58.0
1332    machine       0.158022   0.295191      100.0
525     cookies       0.023013   0.263509       17.0
1980        see       0.030134   0.255031       58.0
439         cmu       0.028235   0.253162       17.0
2242    towards       0.035054   0.245614       42.0
862   followers       0.022837   0.245576       17.0
1949    science       0.057179   0.240060       58.0
670      domain       0.021410   0.236214       25.0
739       entry       0.022586   0.233097       17.0
944    gradient       0.019838   0.233097       17.0
377    brownlee       0.021105   0.226498       25.0
537     courses       0.024935   0.218224       25.0
```

我们可以看到，其中一个热门词汇是亚马逊 AWS。嗯，也许我们也应该写点什么😉。这可能是数字营销的一个强大工具，有许多付费服务正在这样做。所以开始尝试吧！

*原载于*[*https://predictivehacks.com*](https://predictivehacks.com/how-to-create-a-powerful-tf-idf-keyword-research-tool/)*。*