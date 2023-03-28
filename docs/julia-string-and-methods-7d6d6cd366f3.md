# Julia“字符串”和方法()

> 原文：<https://pub.towardsai.net/julia-string-and-methods-7d6d6cd366f3?source=collection_archive---------1----------------------->

![](img/d0b56e66f9eb6fbe6d1551e6edda9d68.png)

本文的目标是理解 Julia 编程中的字符串类型变量以及与它们相关的各种操作。

Julia 中的字符串在“*双引号*中定义。

1.  **声明一个字符串变量 s1。**

```
s1=”hello world”
println(s1)
print(typeof(s1)) #to check the datatype of variableOutput:
hello world
String
```

**2。字符串串联**

```
s1=”hello vivek”
s2=”welcome to julia tutorial”#using * operator
println(s1*’ ‘*s2)#using string function
println(string(s1,’ ‘,s2))Output:
"*": hello vivek welcome to julia tutorial
"string": hello vivek welcome to julia tutorial
```

**3。字符串索引和切片**

> Julia 数据类型中的索引从 1 开始，不像 python 从 0 开始

首先，检查如果我们搜索索引为 0 的项目会发生什么。

```
println(s1[0])Output:
BoundsError: attempt to access 40-codeunit String at index [0]

Stacktrace:
 [1] checkbounds
   @ .\strings\basic.jl:216 [inlined]
 [2] codeunit
   @ .\strings\string.jl:102 [inlined]
 [3] getindex(s::String, i::Int64)
   @ Base .\strings\string.jl:223
 [4] top-level scope
   @ In[4]:5
 [5] eval
   @ .\boot.jl:373 [inlined]
 [6] include_string(mapexpr::typeof(REPL.softscope), mod::Module, code::String, filename::String)
   @ Base .\loading.jl:1196
```

在 Julia 字符串中搜索项目的常用方法是:

```
println(“item as pos 5 is“,s1[5])
println(“item as pos 9 is“,s1[9])Output:
item as pos 5 is o
item as pos 9 is v
```

**切片:** Julia 使用关键字" **begin** "和" **end** "从字符串中获取第一个和最后一个项目。

```
s1=”hello vivek welcome to julia programming”println("first item of string s1 is:",s1[begin])
println("last item of string s1 is:",s1[end])Output:
first item of string s1 is: h
last item of string s1 is: g#slicing
println(s1[begin:begin+10])
println(s1[begin+6:begin+18])
println(s1[begin:end-21])                                
println(s1[begin+6:length(s1)-12])Output:
hello vivek
vivek welcome
hello vivek welcome
vivek welcome to julia#negative Indexing
println(s1[end-3])
println(s1[7:end-12])
println(s1[end-10:end])Output:
m
vivek welcome to julia
programming
```

4.**字符串插值**

插值是执行字符串中任何可执行内容的过程，在 Julia 可执行文件中提到了“$”

```
s1=”vivek”
s2=”80"
println(“hello $s1, you scored $s2”)Output:
hello vivek, you scored 80
```

5.**字符串比较**

```
println(cmp(“a”,”a”)) #returns 0 when output is true
println(cmp(“def”,”abc”)) #returns 1 when output is falseOutput:
0
1println(cmp('a',"a")) 
Output:
MethodError: no method matching isless(::Char, ::String)
Closest candidates are:
  isless(::AbstractString, ::AbstractString) at C:\Users\lenovo\AppData\Local\Programs\Julia-1.7.1\share\julia\base\strings\basic.jl:344
  isless(::Any, ::Missing) at C:\Users\lenovo\AppData\Local\Programs\Julia-1.7.1\share\julia\base\missing.jl:88
  isless(::Missing, ::Any) at C:\Users\lenovo\AppData\Local\Programs\Julia-1.7.1\share\julia\base\missing.jl:87
  ...

Stacktrace:
 [1] **cmp(x::Char, y::String)**
   @ Base .\operators.jl:467
 [2] top-level scope
   @ In[22]:2
 [3] eval
   @ .\boot.jl:373 [inlined]
 [4] include_string(mapexpr::typeof(REPL.softscope), mod::Module, code::String, filename::String)
   @ Base .\loading.jl:1196
```

> “单引号”代表字符数据类型
> “双引号”代表字符串类型

6.**字符串搜索操作**

***startswith()***

```
s1=”hi geeks enjoying learning julia”
println(startswith(s1,’h’)) 
println(startswith(s1,’g’))println(startswith(s1,”hi”))
println(startswith(s1,”julia”))Output:
true
false
true
false
```

***endswith()***

```
s1=”hi geeks enjoying learning julia”
println(endswith(s1,’a’))
println(endswith(s1,’h’))println(endswith(s1,”julia”))
println(endswith(s1,”learning”))Output:
true
false
true
false
```

> **startswith()** 和 **endswith()** 可以进行字符和模式搜索。

***findfirst()和 findlast():*** 查找该项的出现并返回位置。

```
s1=”hi geeks enjoying learning julia”#findfirst()
println(findfirst(‘j’,s1)) --> 12
println(findfirst(“geeks”,s1)) --> 4:8#findlast()
println(findlast(‘j’,s1))  --> 28
println(findlast(‘e’,s1)) -->20s2="hello vivek, Does vivek like julia?"println("find vivek from first: ",findfirst("vivek",s2)) 
println("find vivek from last: ",findlast("vivek",s2))Output:
find vivek from first: 7:11
find vivek from last: 19:23
```

***findnext():*** 带三个参数 **findnext(模式，字符串，查找位置)**

```
#findnext()
println(findnext(‘e’,s1,7))
println(findnext(‘j’,s1,findfirst(‘j’,s1)))Output:
10
12
```

***findprev()*** -接受三个参数 **findnext(模式、字符串、查找位置)**

```
#findprev()
println(findprev(‘e’,s1,18))Output:
10
```

7.**串条**

***strip()、lstrip()和 rstrip()***

```
#strip()
println("length of string with whitespace: ",length("   vivek  "))
println("length of string without whitespace: ",length(strip("   vivek  ")))
println(strip("   vivek  "))
println(strip("sviveks",'s'))Output:
length of string with whitespace: 10
length of string without whitespace: 5
vivek
vivek#lstrip()
#lstrip
println("length of string with whitespace: ",length("   vivek  "))
println("length of string without whitespace: ",length(lstrip("   vivek  ")))
println(lstrip("  vivek",' '))
println(lstrip("sviveks",'s'))Output:
length of string with whitespace: 10
length of string without whitespace: 7
vivek
viveks#rstrip()
println("length of string with whitespace: ",length("   vivek  "))
println("length of string without whitespace: ",length(rstrip("   vivek  ")))
println(rstrip("  vivek",' '))
println(rstrip("sviveks",'s'))Output:
length of string with whitespace: 10
length of string without whitespace: 8
  vivek
svivek
```

8.**拆分()和合并()**

***split() — s*** 根据分隔符 ***将字符串分隔成一个项数组。***

***join()*** —将数组项连接起来创建一个字符串

```
#split()println(split("vivek#learning#julia#python",'#'))
#split the string into 3 array item
sprintln(split(“vivek learning julia and python”,’ ‘,limit=3))Output:
SubString{String}["vivek", "learning", "julia", "python"]
SubString{String}["vivek", "learning", "julia and python"]#join()#join() similar to pythin join func
#join()- joins array of strings into string
l=["hello","julia","learners"]
println("joined string--> ",join(l,"##"))Output:
joined string--> hello##julia##learners
```

9. **substr()-** 提取字符串的一部分

```
#substring()
s1="hi geeks enjoying learning julia"
println(SubString(s1,4,17))
println(SubString(s1,10,26))Output:
geeks enjoying
enjoying learning
```

10. **sort() —** 方法作用于一个元素数组，以升序或降序方式对项目进行排序。为了对字符串进行排序，使用 ***collect()，*** 将其转换为数组，然后应用 ***sort()*** ，再使用 ***join()将其转换回字符串。***

```
#sort() and collect()
println("output of sort -->",sort(collect("vivek")))println("sorted array converted back to string-->", join(sort(collect("vivek"))))println("sorted array converted back to string reverse-->", join(sort(collect("vivek"),rev=true)))Output:
output of sort -->['e', 'i', 'k', 'v', 'v']
sorted array converted back to string-->eikvv
sorted array converted back to string reverse-->vvkie
```

总结一下:

*   朱莉娅字符串和字符串方法。

感谢您阅读我的博客并支持内容。欣赏总是有助于保持精神。我会尽我所能不断拿出优质的内容。与我联系以获取关于即将推出的新内容的更新。

继续支持。