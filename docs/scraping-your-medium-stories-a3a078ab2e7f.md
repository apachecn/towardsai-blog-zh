# 刮掉你的媒介故事

> 原文：<https://pub.towardsai.net/scraping-your-medium-stories-a3a078ab2e7f?source=collection_archive---------2----------------------->

## [数据挖掘](https://towardsai.net/p/category/data-mining)，[编程](https://towardsai.net/p/category/data-mining)

## 在了解和探索 web 抓取功能的同时

![](img/acb0faa44f569c8cb341033cf8f82e8b.png)

在“过去的好时光”中，媒体允许我们为自己的出版物定制网站。不幸的是，这一功能最近已被否决。

尽管如此，作为开发人员，我们足智多谋，不那么容易气馁。

我们可以使用网络抓取来获取每个媒体报道的细节(标题、描述、链接、特写图片，甚至标签！)并在单独的网站上展示。

这个过程将分为两篇文章。第一部分将只关注抓取文章，在这里我们可以发现网络抓取的力量。在第二篇文章中，我们将使用我们收集的数据向数据库添加和更新条目，并自动化甚至安排收集过程。

# 网页抓取

网络抓取是从网站提取数据的过程。我们可以用它来“收集”社交媒体上的帖子、新闻文章，就我们而言，还有媒体报道。为了帮助我们，我们可以使用几个库，包括 BeautifulSoup 和 requests。有了这些，只需要三到四行代码就可以完成几乎所有的事情:

```
url='[https://medium.com'](https://medium.com/feed/@joaquindecastro')
response = requests.get(url)
content = BeautifulSoup(response.content, 'html.parser')
some_tag = content.find_all('tag')
```

第一行只是定义了我们将从中获取数据的 URL。第二行实际访问 URL，就像人们在搜索引擎中粘贴 URL 一样。第三行解析从第二行返回的响应对象，并给出我们实际可以阅读的 HTML 内容。最后，第四行在内容中搜索特定的 HTML 标记。

当然，一个网络刮刀很少只有四行。我们可能希望搜索分散在整个网页中的不同标签，并对它们进行格式化，以便人们能够阅读。但是整个过程是一样的。

# 用代码弄脏我们的手

因此，不再拖延，让我们进入实际的代码。同样，我们的目标是收集作者的中间故事，并提供每个故事的相关信息。

## 网址

正如我们在上面看到的，我们需要一个真正的网页，在那里我们可以获得所有这些有趣的数据。我们可以尝试我们的中型个人资料页面(像 https://medium.com/@joaquindecastro 的 T4 T5)，但是那里的信息隐藏在混乱的源代码中，解析起来很麻烦。相反，我们可以使用 Medium 为每个作者提供的 RSS 提要(比如[https://medium.com/feed/@joaquindecastro)](https://medium.com/feed/@joaquindecastro))。

当我们打开这个页面时，我们可以看到信息已经在 XML 标记中显示出来了。这不仅更容易刮擦，而且我们可以完全避免检查任何源代码！

```
url='[https://medium.com/feed/@joaquindecastro'](https://medium.com/feed/@joaquindecastro')
```

## 使用请求和 BeautifulSoup 解析

接下来，我们可以简单地按照上面概述的过程来获取 URL 的内容:

```
response = requests.get(url)
content = BeautifulSoup(response.content, 'html.parser')
```

现在，在我们开始检索信息之前，注意一些文本嵌套在 XML 字符数据块()中。让我们删除它，因为我们将把提要解析为 HTML。

```
content = str(content).replace('<![CDATA[','').replace(']]>','')
content = BeautifulSoup(content, 'html.parser')
```

> *💡*记得先将内容变量转换成一个**字符串**，然后再转换回一个 BeautifulSoup **对象**，否则我们会遇到属性和类型错误

## 获取最近文章的列表

查看 RSS 提要，我们看到每篇文章的信息都在一个<item>标签中。</item>

```
A snippet of my RSS feed**<item>**
<title>
<![CDATA[ The Powers of Two: Why Is 1 + 2 + 4 + 8 + … = -1 ]]>
</title>
<description>
<![CDATA[ <div class="medium-feed-item"><p class="medium-feed-image"><a href="[https://medium.com/cantors-paradise/the-powers-of-two-why-is-1-2-4-8-1-19d8f00be228?source=rss-46b79b6c143b------2](https://medium.com/cantors-paradise/the-powers-of-two-why-is-1-2-4-8-1-19d8f00be228?source=rss-46b79b6c143b------2)"><img src="[https://cdn-images-1.medium.com/max/2048/1*geeybYiAeCd1vFkKuO75lA@2x.jpeg](https://cdn-images-1.medium.com/max/2048/1*geeybYiAeCd1vFkKuO75lA@2x.jpeg)" width="2048"></a></p><p class="medium-feed-snippet">On calculating infinite divergent series sums</p><p class="medium-feed-link"><a href="[https://medium.com/cantors-paradise/the-powers-of-two-why-is-1-2-4-8-1-19d8f00be228?source=rss-46b79b6c143b------2](https://medium.com/cantors-paradise/the-powers-of-two-why-is-1-2-4-8-1-19d8f00be228?source=rss-46b79b6c143b------2)">Continue reading on Cantor’s Paradise »</a></p></div> ]]>
</description>
<link>[https://medium.com/cantors-paradise/the-powers-of-two-why-is-1-2-4-8-1-19d8f00be228?source=rss-46b79b6c143b------2](https://medium.com/cantors-paradise/the-powers-of-two-why-is-1-2-4-8-1-19d8f00be228?source=rss-46b79b6c143b------2)</link>
<guid isPermaLink="false">[https://medium.com/p/19d8f00be228](https://medium.com/p/19d8f00be228)</guid>
<category>
<![CDATA[ science ]]>
</category>
<category>
<![CDATA[ infinity ]]>
</category>
<category>
<![CDATA[ math ]]>
</category>
<category>
<![CDATA[ education ]]>
</category>
<category>
<![CDATA[ numbers ]]>
</category>
<dc:creator>
<![CDATA[ Joaquin de Castro ]]>
</dc:creator>
<pubDate>Wed, 01 Jul 2020 08:36:11 GMT</pubDate>
<atom:updated>2020-07-01T10:45:28.172Z</atom:updated>
**</item>**
```

由于我们想要获得每篇文章的信息**，我们应该遍历所有这些条目标签。**

要获得一个“可迭代”对象，我们可以使用 BeautifulSoup 的 find_all 属性，如下所示:

```
articles = content.find_all('item')
```

然后，我们可以循环这个:

```
for a in articles:
   # GET TITLE
   # GET SUBTITLE
   # GET DATA
...
```

## 标题

首先，获取每篇文章的标题是有意义的。扫描 XML 文档，我们可以发现所有的标题都在一个<title>标签中</title>

```
<item>
**<title><![CDATA[ The Powers of Two: Why Is 1 + 2 + 4 + 8 + … = -1 ]]></title>**
...
```

要检索它，我们所要做的就是使用 BeautifulSoup 的‘find’属性(每篇文章只有一个标题，所以不需要使用 find_all)

```
title = a.find('title').text
```

> *💡*这个。文本只是删除标签，在本例中是<标题>和</标题>，只留下我们需要的文本

## 小标题

```
<item>
...
<description>
<![CDATA[ <div class="medium-feed-item"><p class="medium-feed-image"><a href="https://medium.com/cantors-paradise/the-powers-of-two-why-is-1-2-4-8-1-19d8f00be228?source=rss-46b79b6c143b------2"><img src="https://cdn-images-1.medium.com/max/2048/1*geeybYiAeCd1vFkKuO75lA@2x.jpeg" width="2048"></a></p>**<p class="medium-feed-snippet">On calculating infinite divergent series sums</p>**<p class="medium-feed-link"><a href="https://medium.com/cantors-paradise/the-powers-of-two-why-is-1-2-4-8-1-19d8f00be228?source=rss-46b79b6c143b------2">Continue reading on Cantor’s Paradise »</a></p></div> ]]>
</description>
...
```

在我们的中型文章上加一个副标题是一个很好的做法，这样读者就知道从一篇文章中可以期待什么。回头看看我们的 RSS 提要，我们可以在一个段落标签中找到我们的副标题。但是页面中有多个段落标签，所以我们需要一种方法来区分它和其他的。这可以通过唯一的 class = " medium-feed-snippet "--我们可以看到它只分配给了副标题-和 attrs 参数来实现。

```
for subtitle in a.find_all('p', attrs={'class':'medium-feed-snippet'}):
  subtitle = subtitle.text
```

我们在这里使用 find_all 是因为使用 find 会导致属性错误:

```
subtitle = a.find('subtitle').text
   AttributeError: 'NoneType' object has no attribute 'text'
```

## 特征图像

```
<item>
...
<description>
...
**<img src="https://cdn-images-1.medium.com/max/2048/1*geeybYiAeCd1vFkKuO75lA@2x.jpeg" width="2048">**
...
```

提要还为我们提供了图像源。我们可以应用到目前为止我们所做的，除了我们使用一个['src']键来获得图像的链接:

```
for img in a.find_all('img', src=True):
  img = img['src']
```

## 链接到实际的媒体文章

```
<item>
...
**<link>https://medium.com/cantors-paradise/the-powers-of-two-why-is-1-2-4-8-1-19d8f00be228?source=rss-46b79b6c143b------2</link>**
...
```

长话短说，我们不会抓取整篇文章的内容，但是我们可以获得中间文章的链接。当我们将这些文章列在一个单独的网站(比如博客或作品集)上时，这是很有帮助的，我们可以在那里将浏览者重定向到完整的文章。同样，除了我们使用['href']键之外，它几乎与特征图像完全相同。

```
for link in a.find_all('a', href=True):
  link = link['href']
```

## 出版者

找到发表该故事的出版物可能会有点棘手。没有直接指定发布名称。但是只要稍微动动脑筋，我们就可以看到，通过文章链接可以找到该出版物。因此，给定用户提交的出版物以及相应的出版物 slug(medium.com/的“走向人工智能”部分**走向人工智能**)，我们可以如下运行可能的出版物:

```
if 'towards-artificial-intelligence' in link:
  publisher = "Towards AI"
 elif 'cantors-paradise' in link:
  publisher = "Cantor's Paradise"
 elif 'mindreform' in link:
  publisher = 'MindReform'
```

## 标签

```
<category>
<![CDATA[ **science** ]]>
</category>
<category>
<![CDATA[ **infinity** ]]>
</category>
<category>
<![CDATA[ **math** ]]>
</category>
<category>
<![CDATA[ **education** ]]>
</category>
<category>
<![CDATA[ **numbers** ]]>
</category>
```

刮中等标签可以帮助是在我们的网站后来纳入搜索功能。扫描文档时，我们看到一篇文章的标签都嵌套在一个<category>标签中。由于一篇文章可以有多个标签，我们将使用 find_all 并将每个标签附加到一个列表中，如下所示</category>

```
tags = []
 for tag in a.find_all('category'):
  tag = tag.text
  tags.append(tag)
```

## 日期

```
<item>
...
**<pubDate>Wed, 01 Jul 2020 08:36:11 GMT</pubDate>**
...
```

最后但同样重要的是，日期。我们在解析日期时必须小心。我们不仅要注意文档中的日期格式，还要注意我们希望将其转换成的格式(尤其是在处理数据库时)。我们将使用`datatime`模块来完成这项工作。

```
import datetime # DON'T FORGET!date = a.find('pubdate').text
 date = str(date).replace(' GMT','') # REMOVE GMT STRING
 date = datetime.strptime(date, '%a, %d %b %Y %H:%M:%S') # CONVERT date TO DATETIME OBJECT
 date = date.strftime('%Y-%m-%d') # CONVERT TO DJANGO DateField FORMAT
```

正如我们在<pubdate>标签中看到的，日期的格式是“工作日，日，月，年，小时，分钟，秒，GMT”。GMT 可以忽略，所以我们将完全删除它。有了这些，让我们把剩下的数据转换成`strptime()`可以理解的代码(查看[这个链接](https://www.programiz.com/python-programming/datetime/strftime#format-code)获取完整的日期格式代码)。</pubdate>

```
'%a, %d %b %Y %H:%M:%S'
```

> *💡*注意 RSS 提要中的十进制数字是用零填充的(例如 01 而不是 1)

最后，让我们将它转换成我们想要的格式，我只是遵循了 Django 的默认日期字段格式，即“年-月-日”或

```
'%Y-%m-%d'
```

## 组织数据

仅此而已！

现在我们有了每篇媒体文章的精彩数据。不幸的是，提要并没有给出我们所有的文章，但这在将来应该不是问题，因为我们会定期收集这些文章。

为了保持输出清晰，让我们将所有这些数据传递到每篇文章的字典中，然后再传递到一个列表中:

```
 ... # EVERYTHING WE DID UP THERE
   # PUT ALL INFO IN A DICTIONARY
   article_info = {
   'title':title,
   'img':img,
   'date':date,
   'subtitle':subtitle,
   'publisher':publisher,
   'link':link,
   'tags':tags 
   }
   # PUT article_info IN article_all
   articles_all.append(article_info)
print(articles_all)
```

# 最终代码

这是我们所有的代码。最终结果是我们所有文章的列表——每篇文章都由包含标题、副标题、图像、链接、日期、出版商和标签的字典表示。

```
import requests
from bs4 import BeautifulSoup
import pandas
from datetime import datetime# GET ACTUAL CONTENT
url='[https://medium.com/feed/@joaquindecastro'](https://medium.com/feed/@joaquindecastro')
response = requests.get(url)
content = BeautifulSoup(response.content, 'html.parser')# REMOVE UNNECESSARY STRINGS
content = str(content).replace('<![CDATA[','').replace(']]>','')
content = BeautifulSoup(content, 'html.parser')# GET LIST OF ALL ARTICLES 
# FOUND IN <item> TAG
articles = content.find_all('item')# CREATE ARRAY FOR ALL article_info
articles_all = []# GET ARTICLE INFO PER ARTICLE
for a in articles:
 # GET TITLE
 title = str(a.find('title').text)
 # GET SUBTITLE
 for subtitle in a.find_all('p', attrs={'class':'medium-feed-snippet'}):
  subtitle = subtitle.text
 # GET IMG SOURCE
 for img in a.find_all('img', src=True):
  img = img['src']
 # GET DATE
 date = a.find('pubdate').text
 date = str(date).replace(' GMT','') # REMOVE GMT STRING
 date = datetime.strptime(date, '%a, %d %b %Y %H:%M:%S') # CONVERT date TO DATETIME OBJECT
 date = date.strftime('%Y-%m-%d') # CONVERT TO DJANGO DateField FORMAT
 # GET LINK TO MEDIUM ARTICLE
 for href in a.find_all('a', href=True):
  link = href['href']
 # GET PUBLISHER BASED ON LINK (eg medium.com/my-publication/article-slug)
 if 'towards-artificial-intelligence' in link:
  publisher = "Towards AI"
 elif 'cantors-paradise' in link:
  publisher = "Cantor's Paradise"
 elif 'mindreform' in link:
  publisher = 'MindReform'
 # GET LIST OF TAGS
 tags = []
 for tag in a.find_all('category'):
  tag = tag.text
  tags.append(tag)
 # PUT ALL INFO IN A DICTIONARY
 article_info = {
 'title':title,
 'img':img,
 'date':date,
 'subtitle':subtitle,
 'publisher':publisher,
 'link':link,
 'tags':tags 
 }
 # PUT article_info IN article_all
 articles_all.append(article_info)
print(articles_all)
```

这里是 Github 库:[https://github.com/JoaquindeCastro/medium_scraper](https://github.com/JoaquindeCastro/medium_scraper)