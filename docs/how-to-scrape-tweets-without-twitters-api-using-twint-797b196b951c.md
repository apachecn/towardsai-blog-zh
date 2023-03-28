# 如何使用 TWINT 在没有 Twitter 的 API 的情况下抓取推文

> 原文：<https://pub.towardsai.net/how-to-scrape-tweets-without-twitters-api-using-twint-797b196b951c?source=collection_archive---------0----------------------->

## [编程](https://towardsai.net/p/category/programming)

## 使用 Twitter 智能工具 TWINT，在没有 Twitter API 的情况下抓取任何人的推文的实践指南

![](img/506b7192563dcbecba34f24b411e2a2d.png)

来源: [Unsplash](https://unsplash.com/photos/6vw_O9R4zf4)

# 什么是 Twint

Twint 是一个高级的 Twitter 报废工具。我们可以使用这个工具来收集任何用户的关注者、跟随者、推文等。而不必使用 Twitter API。

## 以下是一些好处

*   Twitter API 限制只能抓取最后 3200 条推文。但是 Twint 可以获取几乎所有的推文。
*   设置真的很快，因为没有设置 Twitter API 的麻烦。
*   无需 Twitter 注册即可匿名使用。
*   免费的！！没有价格限制。
*   提供易于使用的选项，将抓取的推文存储为不同的格式——CSV、JSON、SQLite 和 Elasticsearch。

# 装置

## 使用画中画

```
!pip3 install twint
```

## 直接来自 Git

```
!git clone --depth=1 https://github.com/twintproject/twint.git
%cd twint
!pip3 install . -r requirements.txt
```

# 建立

让我们先看看使用 Twint 工具的最基本语法，然后再讨论更高级的功能。

首先，我们创建一个名为`c`的 Twitter 配置对象，然后将不同的参数传递给该对象。这些参数将定义我们将如何抓取推文。在下面的例子中，我们只传递了两个参数`Username`和`Limit`。Username 是用户的 twitter id，Limit 是要抓取的 tweets 的数量。限制以 100 为增量，因此限制 1 意味着 100 条推文。最后，`twint.run.Search`会抓取推特，并返回推文。

```
import twint# Configure
c = twint.Config()
c.Username = “narendramodi”
c.Limit = 1# Run
twint.run.Search(c)
```

如果您在笔记本上尝试此操作，您可能会遇到错误*“runtime error:This event loop is has running”*。要解决此错误，请按照下列步骤操作:

```
!pip install nest_asyncio
import nest_asyncio
nest_asyncio.apply()
```

让我们看看下面的一些例子。

# 例子

## 1.特定日期的推文

```
import twint# Configure
c = twint.Config()
c.Username = "narendramodi"
c.Limit = 1
c.Since = "2020–10–12"# Run
twint.run.Search(c)
```

## 2.特定搜索字符串的推文

```
import twint# Configure
c = twint.Config()
c.Username = "narendramodi"
c.Limit = 1
c.Search = ["India"]# Run
twint.run.Search(c)
```

## 3.带有图片、视频或媒体的推文(图片或视频)

```
import twint# Configure
c = twint.Config()
c.Username = "narendramodi"
c.Limit = 1
#c.Images= True
#c.Vidoes = True
c.Media = True# Run
twint.run.Search(c)
```

## 4.用户的热门推文

```
import twint# Configure
c = twint.Config()
c.Username = "narendramodi"
c.Limit = 1
c.Popular_tweets = True# Run
twint.run.Search(c)
```

## 5.基于最低点赞数、最低转发数和最低回复数的推文

```
import twint# Configure
c = twint.Config()
c.Username = "narendramodi"
c.Limit = 1
c.Min_likes = 50000
#c.Min_replies = 1000
#c.Min_retweets = 1000# Run
twint.run.Search(c)
```

## 6.追随者

```
import twint# Configure
c = twint.Config()
c.Limit = 1
c.Username = "narendramodi"# Run
twint.run.Followers(c)
```

## 7.将推文存储为熊猫数据帧

```
import twint# Configure
c = twint.Config()
c.Limit = 1
c.Username = ‘narendramodi’
c.Pandas = True# Run
twint.run.Search(c)Tweets_df = twint.storage.panda.Tweets_df
```

**Twint** 提供了很多这样的配置，所有配置的列表都列在官方页面[这里](https://github.com/twintproject/twint/wiki/Configuration)。您可以使用这些选项的组合来过滤出您感兴趣的推文，以供进一步分析。

# 完整的代码

# 结论

在本文中，我们介绍了 Twint 为废弃 tweets 提供的一些功能。它还提供了一些高级功能[](https://github.com/twintproject/twint/wiki)**，比如将推文存储到数据库、内存(python 列表)和弹性搜索。使用这里获得的知识，你可以快速抓取推文，并开始使用它进行进一步的分析。**

**【阅读更多关于 Python 和数据科学的此类有趣文章， [***订阅***](https://pythonsimplified.com/) *到我的博客*[***www.pythonsimplified.com***](http://www.pythonsimplified.com/)***。*** 你也可以通过 [**LinkedIn**](https://www.linkedin.com/in/chetanambi/) 联系到我。**

# ****参考文献****

**[](https://github.com/twintproject/twint) [## twintproject/twint

### 没有认证。没有 API。没有限制。Twint 是一个用 Python 编写的高级 Twitter 抓取工具，它允许…

github.com](https://github.com/twintproject/twint)**