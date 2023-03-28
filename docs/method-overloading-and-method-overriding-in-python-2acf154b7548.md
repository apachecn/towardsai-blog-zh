# Python 中的方法重载和方法覆盖

> 原文：<https://pub.towardsai.net/method-overloading-and-method-overriding-in-python-2acf154b7548?source=collection_archive---------1----------------------->

## [编程](https://towardsai.net/p/category/programming)

## python 中的一个概念

![](img/de5cd90ac24c0a64057bfbfe5306c61d.png)

照片由[礼萨·南达里](https://unsplash.com/@rezanamdari?utm_source=medium&utm_medium=referral)在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上拍摄

在本文中，我们将讨论方法重载和方法重写。这两个概念都是多态性的类型。多态性是来自面向对象编程(OOPs)的一个概念，即相同的方法表现出不同的特征。

## 方法重载

简单地说，重载意味着我们有相同的方法名，但是参数不同，或者参数的数量或类型不同。但是 python 中没有方法重载的概念，也就是说，我们不能在同一个类中创建两个同名的方法。

我们会让你明白在 python 中实现方法重载

```
class student:

    def sum(self,a, b):
        s = a+b

        return s

s1 = student()
print(s1.sum(2,3))#output:
5
```

这个简单的类方法有一个名为 sum 的方法，它接受两个参数“a”和“b ”,在传递值后我们得到结果“5”。但是如果我们传递这三个值，就会产生错误。

```
class student:

    def sum(self,a, b):
        s = a+b

        return s

s1 = student()
print(s1.sum(2,3,4))#output:
**TypeError**: sum() takes 2 positional arguments but 4 were given
```

另一方面，我们将两个值传递给三个参数，它给出了错误。

```
class student:

    def sum(self, a,b,c):
        s = a+b+c

        return s

s1 = student()
print(s1.sum(2,3))#output:
**TypeError**: sum() missing 1 required positional argument: 'c'
```

因此，我们在其他语言中创建了一个额外的方法来接受三个值，但是在 python 中，我们可以用不同的方法来实现，如下例所示:

我们可以使用“None”作为参数的默认值，也可以使用可变长度的参数。

```
class student:

    def sum(self,a=None, b=None, c=None):
        s = 0

        if a!=None and b!=None and c!=None:
            s = a+b+c

        elif a!=None and b!=None:
            s = a+b

        else:
            s = a

        return ss1 = student()
print(s1.sum(4,2,5))#output:
11
```

即使我们不向参数传递任何值，这个类方法也会工作。

[](/oops-concept-in-python-b5f5833d57db) [## Python 中的 OOPs 概念

### OOPs 是编写程序的一种高效方式

pub.towardsai.net](/oops-concept-in-python-b5f5833d57db) [](/7-beginners-tips-to-help-you-get-better-at-learn-python-33149417b447) [## 帮助你更好地学习 Python 的 7 个初学者技巧

### 成为 python 专家的分步主题

pub.towardsai.net](/7-beginners-tips-to-help-you-get-better-at-learn-python-33149417b447) 

## 方法覆盖

在方法重写中，我们有相同名称的方法，有相同数量的参数，但不在同一个类中，这样继承的概念就出现了。

方法覆盖概念在软件行业中非常重要。

```
class apple:

    def fruit(self):
        print("You are eating Apple")class orange:
    pass

f = orange()
f.fruit()#output:
**AttributeError**: 'orange' object has no attribute 'fruit'
```

在上面的例子中，我们可以观察到 orange 类没有水果方法，所以它给出了一个错误。

如果我们可以用一个继承的概念作为父类和子类来继承父类的所有属性呢？在本例中，我们将 apple 作为父类，orange 作为子类。

```
class apple:

    def fruit(self):
        print("You are eating Apple")class orange(apple):
    pass

f = orange()
f.fruit()#output:
You are eating Apple
```

在上面的例子中，对象首先在 orange 类的方法中搜索句子，没有找到，但是 orange 方法继承了 apple 类的所有属性，然后对象转到 apple 类来检查 fruit 方法。

我们可以在 orange 类中创建相同的水果方法，如下例所示:

```
class apple:

    def fruit(self):
        print("You are eating Apple")class orange:

    def fruit(self):
        print("You are eating Orange")

f = orange()
f.fruit()#output:
You are eating Orange
```

这次对象在 orange 类中找到了水果方法。

## 结论

这两个概念在软件开发中非常有用，可以简化软件的工作功能。

我希望你喜欢这篇文章。通过我的 [LinkedIn](https://www.linkedin.com/in/data-scientist-95040a1ab/) 和 [twitter](https://twitter.com/amitprius) 联系我。

# 推荐文章

1.  [NLP——用 Python 零到英雄](https://medium.com/towards-artificial-intelligence/nlp-zero-to-hero-with-python-2df6fcebff6e?sk=2231d868766e96b13d1e9d7db6064df1)
2.  [用 Python 全面解释层次聚类](/fully-explained-hierarchical-clustering-with-python-ebb256317b50?source=friends_link&sk=7e7113e2a07591a862c77e890fefed10)
3.  [Python 中的异常处理概念](/exception-handling-concepts-in-python-4d5116decac3?source=friends_link&sk=a0ed49d9fdeaa67925eac34ecb55ea30)
4.  [为什么 LSTM 在深度学习方面比 RNN 更有用？](/deep-learning-88e218b74a14?source=friends_link&sk=540bf9088d31859d50dbddab7524ba35)
5.  [神经网络:递归神经网络的兴起](/neural-networks-the-rise-of-recurrent-neural-networks-df740252da88?source=friends_link&sk=6844935e3de14e478ce00f0b22e419eb)
6.  [用 Python 全面解释线性回归](https://medium.com/towards-artificial-intelligence/fully-explained-linear-regression-with-python-fe2b313f32f3?source=friends_link&sk=53c91a2a51347ec2d93f8222c0e06402)
7.  [用 Python 全面解释逻辑回归](https://medium.com/towards-artificial-intelligence/fully-explained-logistic-regression-with-python-f4a16413ddcd?source=friends_link&sk=528181f15a44e48ea38fdd9579241a78)
8.  [Python 中 concat()、merge()和 join()的区别](/differences-between-concat-merge-and-join-with-python-1a6541abc08d?source=friends_link&sk=3b37b694fb90db16275059ea752fc16a)
9.  [与 Python 的数据争论—第 1 部分](/data-wrangling-with-python-part-1-969e3cc81d69?source=friends_link&sk=9c3649cf20f31a5c9ead51c50c89ba0b)
10.  [机器学习中的混淆矩阵](https://medium.com/analytics-vidhya/confusion-matrix-in-machine-learning-91b6e2b3f9af?source=friends_link&sk=11c6531da0bab7b504d518d02746d4cc)
11.  [用 Python 机器学习建模数据](/machine-learning-modeling-data-with-python-92bfebfe4052?source=friends_link&sk=b0f2d74eacefed5843f1e61152513674)