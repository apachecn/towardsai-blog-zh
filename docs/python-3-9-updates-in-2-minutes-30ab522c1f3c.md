# Python 3.9 在 2 分钟内更新

> 原文：<https://pub.towardsai.net/python-3-9-updates-in-2-minutes-30ab522c1f3c?source=collection_archive---------4----------------------->

## [编程](https://towardsai.net/p/category/programming)

## Python 3.9 的稳定版本在这里

![](img/2c8d5880a7e3f8e8f1accd255d3b789d.png)

由[马库斯·温克勒](https://unsplash.com/@markuswinkler?utm_source=medium&utm_medium=referral)在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上拍摄

Python 3.9.0 的稳定版已于 2020 年 10 月 5 日发布。让我们看看新的主要功能。

# 词典合并

考虑两个字典具有相同的键-值对，除了一个字典中的一个值。例如，一个人的电子邮件 id 最近已被更改，它位于新字典(b)中，而您希望更新包含其他详细信息的原始字典(a)中的电子邮件 id。

在 Python 3.9 中有两种方法可以做到(**更新字典 a** )。

```
**Output**: {'id' : 10, 'username' : 'python3.9', 'email' : 'newpython@gmail.com'}
```

# 类型提示

Python 现在支持原生类型提示。你只能有一个**整数列表**，如果你试图向列表中添加一个字符串，它会抛出一个错误。

# 删除前缀/后缀

假设我有一个医生的名字列表，其中一个名字前面没有“医生”。现在我想去掉前缀，这样我的名单上就只有这些名字了。

我们先来看看 Python 3.9 之前的**是怎么做的。**

```
**Output**: ['Leonard McCoy', 'Beverly Crusher', 'Julian Bashir', 'The Doctor', 'Phlox']
```

Python 3.9 提供了两个移除前缀和后缀的函数:

1.  removeprefix()
2.  removesuffix()

现在我们来看看 Python 3.9 后如何进行上述作业**。**

```
**Output**: ['Leonard McCoy', 'Beverly Crusher', 'Julian Bashir', 'The Doctor', 'Phlox']
```

# 时区

Python 3.9 提供了本机功能来**指定时区**。以前，我们必须通过安装名为 pytz 的第三方库来做到这一点。

下面的代码显示了印度时区的时间。

还有更多更新，更多细节请参考[文档](https://docs.python.org/release/3.9.0/whatsnew/3.9.html)。

![](img/de291cbd6a4a90bc4da9228eb93d61eb.png)

凯文·薛在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上的照片

视频参考

[Python 3.9 中的一些新特性](https://www.youtube.com/watch?v=NvxI07dl7gY)由[漂亮地打印出来](https://www.youtube.com/channel/UC-QDfvrRIDB6F0bIO4I4HkQ)

让我们连接

[](https://www.linkedin.com/in/sujan-shirol/) [## Sujan Shirol - Python 开发人员- Kaggle 专家| LinkedIn

### 我相信教学是最好的学习方式。技术作家在媒体的最大出版物的启动，走向人工智能&…

www.linkedin.com](https://www.linkedin.com/in/sujan-shirol/)