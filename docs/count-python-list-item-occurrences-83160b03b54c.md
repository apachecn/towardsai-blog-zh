# 计算 python 列表项目的出现次数

> 原文：<https://pub.towardsai.net/count-python-list-item-occurrences-83160b03b54c?source=collection_archive---------2----------------------->

## [编程](https://towardsai.net/p/category/programming)

从整数列表中，计算每个元素的出现次数，并添加项目，作为子列表计数。

![](img/3dcd1a26bcbef5bdc4c669105642305b.png)

输入列表:inp = [7，9，7，4，3，5，3，6，9，3]
输出列表:out= [[7，2]，[9，2]，[4，1]，[3，3]，[5，1]，[6，1]]

#注意:其中 7 是列表项，2 是出现次数

**使用嵌套循环**

```
def count_items(inp): for i in range(0, len(inp)):
        a = 0
        row =[]
        if i not in l:
            for j in range(0, len(inp)):
                if inp[i]== inp[j]:
                a = a + 1
            row.append(inp[i])
            row.append(a)
            l.append(row)
     for j in l:
        if j not in out:
           out.append(j)return out
```

调用函数并检查输出:

```
#call func() 
inp = [7, 9, 7, 4, 3, 5, 3, 6, 9, 3]
l = []
out = []
print(count_items(inp))Output: [[7, 2], [9, 2], [4, 1], [3, 3], [5, 1], [6, 1]]
```

**使用 count()方法**

```
def count_items(inp): for i in inp:
       row =[]
       ct = 0
       ct = inp.count(i)
       row.append(i)
       row.append(ct)
       l.append(row) for j in l:
       if j not in out:
       out.append(j)
   return out
```

调用函数并检查输出:

```
#call func()
inp = [7, 9, 7, 4, 3, 5, 3, 6, 9, 3]
l = []
out = []
print(count_items(inp))Output: [[7, 2], [9, 2], [4, 1], [3, 3], [5, 1], [6, 1]]
```

**使用计数器()方法**

```
from collections import Counter
def count_items(inp):
     coll = Counter(inp)
     out = []
     for key,val in coll.items():
          out.append([key,val])
 return out
```

调用函数并检查输出:

```
#call func() 
inp = [7, 9, 7, 4, 3, 5, 3, 6, 9, 3]
print(count_items(inp))Output: [[7, 2], [9, 2], [4, 1], [3, 3], [5, 1], [6, 1]]
```

总而言之，我们讨论了几种统计列表项出现次数的方法，如下所示:

*   count()方法
*   嵌套 for 循环
*   集合库计数器()方法

这就是列表项的所有计数事件。

感谢您阅读我的博客并支持内容。欣赏总是有助于保持精神。会尽力不断拿出高质量的内容。与我联系以获取关于即将推出的新内容的更新。