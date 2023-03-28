# 通过代码示例了解 JAVA Basic

> 原文：<https://pub.towardsai.net/understand-java-basic-with-code-examples-cf9beeea9553?source=collection_archive---------3----------------------->

## [编程](https://towardsai.net/p/category/programming)

## 开源编程和面向对象编程语言

![](img/0b27434dbaa5358d7d5d04de7618ba72.png)

由[克里斯托弗·高尔](https://unsplash.com/@cgower?utm_source=medium&utm_medium=referral)在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上拍摄的照片

> ***简介***

Java 是世界上最流行和最强大的编程语言之一，用于设计移动应用程序、桌面应用程序、游戏、数据库连接等等。

*   Java 是一种独立于平台的语言，也就是说，它可以在任何平台上工作，如 Windows、Linux、Mac 等。
*   它是一种开源编程语言。
*   它是一种面向对象的编程语言。

> ***Java 标识符***

Java 标识符是用来标识类、方法、变量等的标识符。

```
**public** **class** Student1
{
    **public** **static** **void** main(String[] args)
    {
        // **TODO** Auto-generated method stub
        **int** roll_no=45;
        String Student_name=”Arpita Sinha”
    }
}
```

在这段代码中，标识符有: ***学生*** ， ***主*** ， **int** ， ***字符串*** ， ***args***

> ***定义 java 标识符的规则***

*   java 标识符的名称应该包含字母数字字符和美元符号($)以及特殊字符中的下划线(_)。不允许使用其他特殊字符。
*   保留字和关键字不得用作标识符的名称。
*   它不应该以任何数字开头。

> ***变量***

在 java 中，必须定义变量的数据类型，如 Int、String、float、double 等。并且应该相应地分配该值。

*   **字符串** —它存储单词
*   **Int** —它存储整数
*   **Float** —存储十进制数字
*   **char** -它存储字符

> ***变量类型***

*   局部变量:总是在方法中的变量
*   实例变量:这些变量定义在方法之外，但在类之内。
*   静态方法:这些方法也在方法外部和类内部定义。它以 static 关键字开始。静态变量的值在整个执行过程中保持不变。
*   循环变量:变量是在循环内部声明的，当循环终止时，变量的作用域也随之结束。

当方法有一个同名的参数时，这个关键字可以用来引用当前的类变量。

任何在类中方法之外定义的变量都可以被该类的所有成员访问。

```
**class** employee
{
    **static** **int** *id_no=4567*; //static variable
    String name=”Ramesh shah”; //Instance variable
}
```

> ***Java 中的循环***

**Java 中循环的类型**

1.  While 循环:

在执行之前的 while 循环中，它有一个条件语句，如果语句的条件得到满足，它将继续执行，除非条件变为 false。

```
**public** **class** Demo{
    **public** **static** **void** main(String[] args)
    {
        **int** x=10;
        **while**(x!=0)
        {
          print(x); //it would print integers from 10 to 1
          x — ;
        }
    }
}
```

2.Do while 循环:

在这个循环中，循环执行一次，然后检查条件，如果条件为真，则循环进一步执行，否则执行。

**代码**

```
**public** **class** Demo{
    **public** **static** **void** main(String[] args) 
    {
        **int** x=0;
        **do** {
            System.***out***.println(“ the value of x:”);
            x++;
           }
       **while**(x!=10);
    }
}
```

> ***Java 选择语句***

它控制程序的执行。

*   如果
*   如果-否则
*   如果-否则-如果
*   开关盒
*   跳转-中断、继续、返回

在 **If** 语句中，检查语句的条件，如果语句为真，则允许循环执行，否则，跳过循环执行，编译器转到代码的下一条语句。

**代码**

```
**public** **class** demoIf {
    **public** **static** **void** main(String[] args) {
        // **TODO** Auto-generated method stub
        **int** arr[]= {1,6,9,8};
        i=0;
        **if** (arr[i]%3==0) {
            System.***out***.println(arr[i]);
    }
  }
}
```

在 **If-else** 语句中，检查条件语句，如果语句为真，则执行 If 部分，否则执行 else 部分。

**代码**

```
**public** **class** demoIfElse {
    **public** **static** **void** main(String[] args) {
        // **TODO** Auto-generated method stub
        **int** arr[]= {1,6,9,8};
        **int** i=0;
        **if** (arr[i]%2==0) {
            System.***out***.println(arr[i]+”is an even number”);
            i++;
        }
        **else** System.***out***.println(“not an even number”);
            i++;
    }
  }
}
```

在 **if-else-if** 中，首先检查“if”语句，如果为真，则执行循环，如果为假，则检查“else-if”部分，如果语句为真，则循环执行，否则不执行。

**代码**

```
**public** **class** demoIfElse {
    **public** **static** **void** main(String[] args) {
        // **TODO** Auto-generated method stub
        **int** arr[]= {1,6,9,8};
        **int** i=0;
        **if** (arr[i]%2==0) {
            System.***out***.println(arr[i]+”is an even number”);
            i++;
        }**else

        if**(arr[i]%2==0) {
            System.***out***.println(arr[i]+”is an Odd number”);
            i++;
   }
  }
}
```

**Switch-case**:Switch case 是一个多分支语句。这是一种基于执行值来执行代码不同部分的方法。

```
Switch(expression)
{
case value1:
    Instruction1;
    breakcase value2:
    Instruction2;
    break;
    …….default:
    Default statement;
    break;
```

> ***跳转语句***

有三个跳转语句:

**Break:** Break 语句用于终止/退出循环。

例如:如果我们想执行一个搜索活动，键值是 10，条件是如果发现一个负值，我们需要停止搜索操作

```
**public** **class** demoIfElse {
    **public** **static** **void** main(String[] args) {
        // **TODO** Auto-generated method stub
        **int** arr[]= {4,6,9,8,0,5,-2, 10};
        **int** key=10;
        **int** i=0;
        **if** (arr[i]==key) {
             System.***out***.println(arr[i]+”is the value of key”);
             i++;
        }**else

        if**(arr[i]<0) {
            System.***out***.println(arr[i]+”the searching is stopped as a 
            negative number is found in the path”);
            **break**;
            i++;
   }
 }
}
```

**继续:**有时你可能想继续循环，但停止循环中的特定处理，在这种情况下，我们使用继续循环

例如:如果我们想做上述活动，但在这里我们不想停止，如果我们发现一个负值，在这种情况下，代码将如下:

```
**public** **class** demoIfElse {
    **public** **static** **void** main(String[] args) {
        // **TODO** Auto-generated method stub
        **int** arr[]= {4,6,9,8,0,5,-2, 10};
        **int** key=10;
        **int** i=0;
        **if** (arr[i]==key) {
            System.***out***.println(arr[i]+”is the value of key”);
            i++;
            **continue**;
        }**else** **if**(arr[i]<0) {
            System.***out***.println(arr[i]+”the searching is stopped as a
            negative number is found in the path”);
            **break**;
            i++;
    }
   }
 }
```

> ***为循环***

*   在 for 循环中，有一个初始化条件，一个测试条件，然后是一个递增或递减语句

**代码**

```
**public** **class** Demo{
     **public** **static** **void** main(String[] args) {
         **for**(**int** i=0;i<5;i++){
             // It would print the integers from 0 to 4
             System.***out***.println(“ the value of x is”+i);
   }
  }
}
```

*   对于每个循环:

这是一个增强的“for”循环，用于元素的迭代。

```
**public** **class** Student1 {
    **public** **static** **void** main(String[] args) {
        // **TODO** Auto-generated method stub
        **int** arr[]= {1,6,6,8};
        **for** (**int** i:arr) {
            System.***out***.println(i);
   }
  }
}
```

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