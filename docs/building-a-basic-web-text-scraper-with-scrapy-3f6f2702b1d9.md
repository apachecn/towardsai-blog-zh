# 用 Scrapy 构建一个基本的 Web 文本刮刀

> 原文：<https://pub.towardsai.net/building-a-basic-web-text-scraper-with-scrapy-3f6f2702b1d9?source=collection_archive---------0----------------------->

![](img/0f72f4a9e3ac3d50a333af037749fbb4.png)

在 [Unsplash](https://unsplash.com/s/photos/html?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) 上 [Sai Kiran Anagani](https://unsplash.com/@_imkiran?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) 拍摄的照片

## [编程](https://towardsai.net/p/category/programming)，[网页抓取](https://towardsai.net/p/category/web-scraping)

## 如何从 web 中提取文本数据？

***免责声明:*** *本文仅出于教育目的。我们不鼓励任何人抓取网站，尤其是那些可能有条款和条件反对此类行为的网站。*

crapy 是一个开源库，旨在实现快速简单的网络抓取和抓取。我将用它来提取哥伦比亚宪法法院的所有判决，大约 20000 份。这样做的目的是能够使用 NLP 技术分析大量的非结构化数据。但是现在，这里是如何使用 Scrapy 设置一个刮刀。

## 装置

使用 pip 就像使用 pip 一样简单(尽管我更喜欢使用 [pipenv](https://pipenv.pypa.io/en/latest/) ，这是一个非常酷的包管理器，通过虚拟环境来避免令人头疼的问题)。

```
pip install scrapy#orpipenv install scrapy
```

## 目录

首先，你需要进入你的终端，导航到你选择的工作目录(wd ),输入以下内容，创建 Scrapy 需要的所有必要的实例:

```
# let's call it 'tutorial' for the next cell to make sensescrapy startproject <project name> 
```

这将在你的 wd 中创建一系列文件，一个新的 Scrapy 工作目录。来自 Scrapy 文档:

```
"
tutorial/
    scrapy.cfg            *# deploy configuration file*

    tutorial/             *# project's Python module, you'll import your code from here*
        __init__.py

        items.py          *# project items definition file*

        middlewares.py    *# project middlewares file*

        pipelines.py      *# project pipelines file*

        settings.py       *# project settings file*

        spiders/          *# a directory where you'll later put your spiders*
            __init__.py
"
```

在那里，你会看到一个名为*蜘蛛的目录。*那是你的蜘蛛将要生活的地方。从技术上讲，蜘蛛是您创建的类，但它继承了蜘蛛子类。在其中，您可以设置蜘蛛要遵循的各种规则，比如从哪些链接开始，允许哪些域，等等。

## 剧本

现在，转到您选择的 IDE 并创建一个空白 python 脚本(any_name.py)，在这里您将创建第一个蜘蛛。首先，导入 Scrapy 和 LinkExtractor，因为我们将处理一系列链接:

```
import scrapyfrom scrapy.linkextractors import LinkExtractor
```

现在，创建一个存储每个 URL 及其内容的项目类:

```
class VeredictItem(scrapy.Item): url= scrapy.Field() content = scrapy.Field()
```

然后，创建 Spider 类(继承自 scrapy。蜘蛛，如下):

```
class SentspiderSpider(scrapy.Spider): name = 'verdictspider' allowed_domains = ['corteconstitucional.gov.co'] start_urls =
       ['https://www.corteconstitucional.gov.co/relatoria/radicador/buscar.php?vs=26184&pg=0&ponente=&demandado=&Sentencia=&Tipo=Sentencias&busqueda=&conector=AND&segundotema=&anios=Todos&proceso='] base_url = "https://www.corteconstitucional.gov.co"
```

请注意，我设置了四个不同的变量:蜘蛛的名称、允许蜘蛛爬行到哪些域、应该从哪里开始以及基本 URL 是什么，依次排列。接下来，我们需要定义方法来告诉蜘蛛到底要做什么。让我们一个接一个地创建三个不同的方法。

第一种方法将允许您的蜘蛛解析页面(读取组成页面的 HTML，更多信息请参见此处的):

```
def parse(self, response): """Method to parse the HTML table and extract the link to each              verdict """ links =       LinkExtractor(allow_domains=self.allowed_domains).extract_links(response) for link in links: if not self.use_link(link.url): continue request = response.follow(link, callback=self.parse_links) yield request
```

这里是您将使用 LinkExtractor 的地方。因为您正在搜索一个主页，并且您所寻找的信息在各个链接中被引用，所以您需要识别它们并提取它们。一旦你有了它们，就建立一个检查点(下一个单元格中的方法)，用它来评估你拥有的链接是否是感兴趣的。如果不是，蜘蛛会继续它的路线，不会看它。如果是，蜘蛛将接受服务器的响应，并按照链接，产生请求，即链接包含的内容。

如上所述，第二种方法是健全性检查:

```
def use_link(self, url): return '/relatoria/' in url
```

它所做的就是创建一个方法，通过这个方法你可以评估一个关键词是否出现在你的蜘蛛提取的链接中。在他的例子中，如果链接中包含模式 *'/relatoria/'* ，那么这个链接将是感兴趣的，这个方法将返回一个逻辑断言( *True* )。

最后，最后一个方法将使用解析方法提取每个链接的响应中包含的所有非结构化数据。它将获取在相应的 HTML 标签中找到的所有文本，并将其提取出来，以便保存在“content”变量中。提取将使用 XPath(更多关于 XPath 做什么[这里](https://www.w3schools.com/xml/xpath_intro.asp))来指导，它将告诉蜘蛛哪些标签是目标和读取的。在这种情况下，*'//div/p[@ class = ' MsoNormal ':*

```
def parse_links(self, response): """Method to request a new HTML link to the server, extracted     with the parse method""" content = ' '.join(response.xpath('//div/p[@class = 'MsoNormal'][not(contains(normalize-space(), '\u00a0'))]//text()").extract()) content = content.replace('\r\n', ' ') yield VeredictItem(url= response.url, content= content)
```

提取之后，该方法将删除换行符(' \n ')，并用空格替换它们，最终生成我们之前在 VerdictItem 类中创建的变量的总体结果: *URL* 和*内容*。

## 运行脚本

用您选择的文件名(当然，扩展名是. py)保存整个文件，您就可以开始了。

要运行蜘蛛脚本，请再次进入终端，键入以下内容:

```
scrapy crawl <spider_name> # verdictspider in this case
```

最后，如果您想要设置所有数据将存放的文件，请像这样运行脚本:

```
scrapy crawl verdictspider -O all_verdicts.json
```

给你。该蜘蛛将抓取 20 多个链接，提取 20000 多个司法判决的相关文本，并将其全部保存到一个 JSON 文件中。一个真正的 NLP 天堂！