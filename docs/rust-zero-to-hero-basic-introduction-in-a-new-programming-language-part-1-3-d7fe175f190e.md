# RUST:新编程语言入门(第 1/3 部分)

> 原文：<https://pub.towardsai.net/rust-zero-to-hero-basic-introduction-in-a-new-programming-language-part-1-3-d7fe175f190e?source=collection_archive---------0----------------------->

## [编程](https://towardsai.net/p/category/programming)

## 一种非常适合安全和控制的语言

![](img/31fca07d8f86e94087aa4063f6f2c3c9.png)

[克里斯·迪诺托](https://unsplash.com/@crisdinoto?utm_source=medium&utm_medium=referral)在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 拍摄的照片

## 涵盖的主题:

**第 1 节:**防锈介绍及安装指南

**第 2 部分:**数据类型、变量、常量和字符串

**第三节:**运算符和循环

**第 4 节:**功能

# **第一节:**

> **铁锈介绍**

由 Mozilla 发起并开发的 Rust 编程语言。对其他语言的需求是更快更安全。RUST 在运行时提供了非常好的性能，并在内存问题上提供了安全性。

> **窗户安装生锈**

可以在 visual studio 2013 及更高版本上进行编程。

下载 RUST 64bit — [链接](https://www.rust-lang.org/tools/install)

安装 rust 后，用 admin 打开 cmd，用`rustc`命令检查它与环境变量的连接。

[](https://medium.com/towards-artificial-intelligence/python-zero-to-hero-with-examples-c7a5dedb968b) [## Python:从零到英雄(带示例)

### python 初学者手册指南

medium.com](https://medium.com/towards-artificial-intelligence/python-zero-to-hero-with-examples-c7a5dedb968b) 

# **第二节:**

> **数据类型**

**字符类型**

Char 在编程语言中用于将字符类型值赋给变量。

```
let x = 'a';
let y = 'w';
```

**整数类型**

这种类型在编程语言中用于将整型值赋给变量。整数用有符号(I)和无符号(u)来区分，大小范围从 8 位到 128 位。

```
let a = 3;
let b = 6;
let c = 2143;
```

**浮动式**

浮点类型是那些带有小数的值。

```
let x = 2.3;
let y = 1234.12;
```

**布尔型**

布尔类型是标准类型，在这种类型中我们只能得到两个结果，不是真就是假。

```
let yes = True;
Let no = False;
```

> **变量**

变量在任何编程变量中的作用都是一样的。所有赋值都有一个名称。

变量可以包含数字、字符和下划线。它可以以字母或下划线开头。“sum”和“SUM”是两个不同的变量，表示它区分大小写。变量有两种不同的定义方式，一种是无类型定义，另一种是有类型定义。

```
let a = 40; //without type
let a:i16 = 40.45; //with type
```

变量的值是不可变的，这意味着一旦赋值就不能改变。

> **常数**

常量是指我们在整个程序中定义了常量变量的具体值，它是不可更改的。定义关键字`const`的持续使用。我们必须在常量中指定类型。否则，它会给出错误。

```
const PI:f8 = 3.14; 
const AREA:f16 = 900;let uname=”Amit”;
let uname= uname.len();
println!(“integer length of character : {}”,uname);//output:
integer length of character: 4
```

> **弦**

铁锈中的琴弦分为两种。

**字符串文字(& str)**

当字符串值在编译时已知时，发出这种类型的字符串。这是一种切片类型，指向 UTF-8。

```
let home_name:&str="HAPPYHOME";
```

**字符串对象**

这种类型是标准库的一部分，而不是语言的一部分。此中的字符串存储为字节。

```
let new_string_obj = String::new();
```

有许多字符串对象有它们的工作函数。

*   new() —它创建一个空字符串。
*   replace() —用模式匹配替换字符串。
*   push()-在定义的字符串中追加字符。

# **第三节:**

> **操作员**

rust 中的运算符有各种类型，用于执行算术和计算过程。操作员的类型如下所示:

*   **算术运算符**

示例:

```
let x = 2;
let y = 3;println!("Sum: {}",x+y);
println!("Difference: {}",x-y);
println!("Mul: {}",x*y);
println!("Divide: {}",x/y);

 //output : Sum:5                        
 //output : Difference:-1
 //output : Mul:6
 //output : Divide:0.6666
```

*   **赋值运算符**

示例:

```
let x = 8;
let x = x+2;
println!("x: {}", x)  ;              //output : x:10
println!("x: {}",x += 2);            //output : x:12
println!("x: {}",x *= 2);            //output : x:24
```

*   **关系运算符**

示例:

```
let x = 5;
let y = 6;
println!(x<y);           //output : True
println!(x>y);           //output : False for comparison we use double   equal sign '=='
println!(x=y) ;         //output : False
println!(x<=y);         //output : True
println!(x>=y);         //output : True
println!(x!=y);         //output : True
```

*   **逻辑运算符**

示例:

```
let x = 5;
let y = 4;
if(x<8) && (y<5)
{
    println!("True");
}if(x<8) || (y>5)
{
    println!("True");
} if x!=6
{
    println!("True");
} 
```

*   **按位运算符**

按位运算符用于对整数进行按位计算。

示例:

```
let x:i32 = 12;
let y:i32 = 13;let a:i32 = 10;
let b:i32 = 2;let output:i32;output = x & y;     
println!("(x & y) => {} ",output);output = x | y;          
println!("(x | y) => {} ",output);output = x ^ y;  
println!("(x ^ y) => {} ",output);output = a << b; 
println!("(a << b) => {}",output);output = a >> b; 
println!("(a >> b) => {}",output);//output:
(a & b) => 12
(a | b) => 12
(a ^ b) => 1
(a << b) => 40
(a >> b) => 2
```

> **决策和循环**

***如果*语句**

控制语句用于根据给定的条件执行语句。如果条件为真，那么它将执行 If 部分，否则不执行。

```
let  a:i32 = 3;
if a> 0 
{
   println!("number is greater than zero");
}
```

***if-else* 语句**

控制语句用于根据给定的条件执行语句。如果条件为真，那么它将执行 If 部分；否则，将执行 else 部分。

```
let a = 10;
 if num % 2==0 
{
     println!("Even");
} 
 else 
{
     println!("Odd");
}
```

***为*循环**

它用于序列。for 循环按照定义的次数执行该块。

```
for x in 1..11    // 11 is not inclusive
{ 
    if x==4 
    {
      continue;
    }
      println!("x is  {}",x);
}//output:
x is 1
x is 2
x is 3
x is 5
x is 6
x is 7
x is 8
x is 9
x is 10
```

[](https://medium.com/towards-artificial-intelligence/nlp-zero-to-hero-with-python-2df6fcebff6e) [## NLP——使用 Python 从零到英雄

### 学习自然语言处理基本概念的手册

medium.com](https://medium.com/towards-artificial-intelligence/nlp-zero-to-hero-with-python-2df6fcebff6e) 

# **第四节:**

> 功能

# 功能

*   当我们在做一个大项目时，我们可以分解成更小的任务，然后使用函数。
*   我们必须知道两件主要的事情。

1.  定义函数
2.  调用函数

在 RUST 中，函数是由 ***fn*** 关键字定义的。

句法

```
fn  function_name(arg1,arg2..argN) 
{ 
// statements
}
```

示例:

```
fn main()
{ 
      //calling a function
        sum();
}
//Defining a function
fn  sum()
{
        println!("The sum of the two numbers: ");
}
```

> ***结论:***

RUST 语言是新的，在许多速度和安全更重要的领域非常有用。

我希望你喜欢这篇文章。通过我的 [LinkedIn](https://www.linkedin.com/in/data-scientist-95040a1ab/) 和 [twitter](https://twitter.com/amitprius) 联系我。

# 推荐文章

1.  [NLP —用 Python 从零到英雄](https://medium.com/towards-artificial-intelligence/nlp-zero-to-hero-with-python-2df6fcebff6e?sk=2231d868766e96b13d1e9d7db6064df1)

2. [Python 数据结构数据类型和对象](https://medium.com/towards-artificial-intelligence/python-data-structures-data-types-and-objects-244d0a86c3cf?sk=42f4b462499f3fc3a160b21e2c94dba6)

3. [MySQL:零到英雄](https://medium.com/towards-artificial-intelligence/mysql-zero-to-hero-with-syntax-of-all-topics-92e700762c7b?source=friends_link&sk=35a3f8dc1cf1ebd1c4d5008a5d12d6a3)