# 在不同笔记本之间共享代码的实用策略

> 原文：<https://pub.towardsai.net/a-practical-strategy-to-share-the-code-among-different-notebooks-9f9bd78aa3a7?source=collection_archive---------0----------------------->

## [德沃普斯](https://towardsai.net/p/category/devops)

## 关于如何通过结合 Jupyter 笔记本和 Visual Studio 代码来提高编码效率的一些提示

![](img/240db50fa59bc3a1544c6b520ed5658e.png)

照片由 [Kostiantyn 李](https://unsplash.com/@leekos?utm_source=medium&utm_medium=referral)在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上拍摄

程序员肯定会面临的问题之一是重用编写的代码。这个问题可以通过编写包含重用代码的类和函数来轻松解决。**但是在使用笔记本的时候，你是如何重用代码的呢？**

在这篇文章中，我试图描述一种在不同笔记本之间共享代码的策略。

文章组织如下:

*   动机
*   一个可能的策略
*   实际例子。

# 动机

在编写 Jupyter 笔记本时，您可能需要重用以前的笔记本中编写的代码。显然，最快的策略可能是**将代码从一个笔记本复制并粘贴到另一个**。

然而，从长远来看，这种策略可能会适得其反。事实上，如果您更新笔记本中的代码，那么您应该在复制该代码的所有其他笔记本中更新它。

**结果是管理和维护更新代码的时间过载。😧**

因此，问题是:

> 如何只写一次代码，然后在不同的笔记本之间共享？

![](img/8fd4078daa363e37c3d1613d563ebcfd.png)

由 [Towfiqu barbhuiya](https://unsplash.com/@towfiqu999999?utm_source=medium&utm_medium=referral) 在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上拍摄的照片

# 一个可能的策略

前一个问题的可能答案是 Jupyter 笔记本和 Visual Studio Code (VSC)或任何其他 Python IDE 的组合。

在实践中， **VSC 被用来编写核心函数或类，这些函数或类可以在不同的笔记本上重用。**

要使这一策略奏效，您需要采取两项预防措施:

*   将类或函数转换成包；
*   告诉 Jupyter 在运行每个单元时重新加载包。

要将类或函数转换成可以由其他 Python 脚本导入的包，应该在类和函数所在的目录下创建一个名为`__init__.py`的空文件。然后，如果所有的类都包含在与 Jupyter 笔记本相同的文件夹中，您可以简单地在 Jupyter 单元格中导入包，如下所示:

```
from file_directory.file_name import class_name
```

然后，您可以像通常对其他 Python 包那样使用它。

其次，您应该告诉 Jupyter 在运行每个单元时重新加载您的包。这可以通过在第一个 Jupyter 单元格中写下以下魔字来实现:

```
%autoreload 2
```

所描述的策略允许你保持你的代码是最新的和有序的。😃

![](img/c932aed1e59b1022991508f156b4f7c0.png)

照片由 [Mollie Defibaugh](https://unsplash.com/@molliedefibaugh?utm_source=medium&utm_medium=referral) 在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上拍摄

# 实际例子

作为一个实际的例子，我实现了一个 scraper，它从任何 HTML 页面中提取列表元素，然后将它们转换成 Pandas 数据帧。刮刀利用了`selenium`包。在我之前的文章中，我描述了如何通过 selenium 从零开始提取数据，因此您可以参考它进行`selenium`安装和配置。

我假设具有以下目录结构:

```
data_extraction
|__ Web_Site1.ipynb
|__ Web_Site2.pynb
|__ extractor
   |__ scraper.py
   |__ _init__.py
```

在主目录(`data_extraction`)中，有两个笔记本，它们利用 scraper 从两个不同的网站提取数据。scraper 主函数位于`extractor`目录中，在那里我还创建了一个名为`__init__.py`的空文件。

## scraper.py

现在，我用 VSC 打开`scraper.py`，并在其中创建了一个类，实现了 scraper。构造函数接收 URL 作为输入。在构造函数中，我将驱动程序配置为在无头设备中工作。或者，我可以添加另一个输入参数来指定选项。然而，在这个例子中，我定义了一个预配置的选项。

```
import pandas as pd
from selenium import webdriver
from selenium.webdriver.chrome.options import Optionsclass Scraper:
   def __init__(self,url):
       self.options = Options()
       self.options.add_argument("--headless")
       self.options.add_argument("--lang=it");
       self.driver = webdriver.Chrome(options=self.options)
       self.url = url
       self.driver.get(url)
```

然后，我定义了另外两个函数，分别返回和关闭驱动程序:

```
def get_driver(self):
   return self.driverdef close(self):
   self.driver.close()
```

这些是铲运机非常基本的功能。我可以通过添加任意多的功能来定制它😃

## 网站 1.ipynb 和网站 2.ipynb

现在，我可以利用我的刮板在两个笔记本如下。首先，设置自动重新加载模式:

```
%autoreload 2
```

然后，我导入包:

```
from extractor.scraper import Scraper
```

最后，我开发了我的刮刀:

```
url = '[http://www.myexample.com'](https://myjewishitaly.it/')
scraper = Scraper(url)
```

请注意，如果我需要向 scraper 添加一个新函数，我可以直接在 VSC 中完成，保存更改并在 Jupyter 单元格中调用该函数😎

# 摘要

恭喜你！现在你已经学会了如何在不同的 Jupyter 笔记本之间共享代码！这可以通过简单的预防措施来实现。快乐编码😄

如果你已经走了这么远来阅读，对我来说今天已经很多了。谢谢！你可以在[这篇文章](https://alod83.medium.com/which-topics-would-you-like-to-read-c68314dc6813)中读到更多关于我的信息。

# 相关文章

[](https://towardsdatascience.com/how-to-run-r-scripts-in-jupyter-15527148d2a) [## 如何在 Jupyter 中运行 R 脚本

### 关于如何在 Jupyter 中安装并运行 R 内核的简短教程

towardsdatascience.com](https://towardsdatascience.com/how-to-run-r-scripts-in-jupyter-15527148d2a) [](https://towardsdatascience.com/scraping-data-from-nested-html-pages-with-python-selenium-c5f23065841f) [## 用 Python Selenium 从嵌套的 HTML 页面中抓取数据

towardsdatascience.com](https://towardsdatascience.com/scraping-data-from-nested-html-pages-with-python-selenium-c5f23065841f) [](https://towardsdatascience.com/have-you-ever-thought-about-using-python-virtualenv-fc419d8b0785) [## 有没有想过用 Python virtualenv？

### 在终端和 Jupyter 笔记本上安装和使用 Python virtualenv 的实用指南。

towardsdatascience.com](https://towardsdatascience.com/have-you-ever-thought-about-using-python-virtualenv-fc419d8b0785)