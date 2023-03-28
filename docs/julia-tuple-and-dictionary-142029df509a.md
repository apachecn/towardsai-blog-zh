# 朱莉娅元组和字典

> 原文：<https://pub.towardsai.net/julia-tuple-and-dictionary-142029df509a?source=collection_archive---------6----------------------->

## 本文的目标是理解 Julia 数据结构 Tuple 和 Dictionary 以及与它们相关的各种操作。

![](img/053d3dacd02e7c108c1ef531185178ca.png)

**元组 *:*** 是由逗号分隔的相同或不同数据类型的不同值的不可变集合。

语法:(项目 1，项目 2，项目 3…)

**字典:**是键-值对的集合，字典中的每个值都可以用它的键来访问。这些键值对不必是相同的数据类型。

语法:Dict(key1 => value1，key2 => value2，…)

# **元组和方法()**

```
#create an empty tuple
t1=()
println(“If a Tuple is empty returns “, isempty(t1))
t1=(“julia”,”python”,”sql”)
println(“If a Tuple is non-empty returns “,isempty(t1))Output:
If a Tuple is empty returns true
If a Tuple is non-empty returns false
```

**索引、切片、迭代和分配**

```
#declare a tuple beverage
beverage= (“coffee”,”tea”,”greentea”,”grrencoffee”,”ginger tea”)#Indexing
println(beverage[1])
Output: coffeeprintln(beverage[0]) #index in julia starts from 1
BoundsError: attempt to access NTuple{5, String} at index [0]

Stacktrace:
 [1] getindex(t::Tuple, i::Int64)
   @ Base .\tuple.jl:29
 [2] top-level scope
   @ In[7]:2
 [3] eval
   @ .\boot.jl:373 [inlined]
 [4] include_string(mapexpr::typeof(REPL.softscope), mod::Module, code::String, filename::String)
   @ Base .\loading.jl:1196#Slicing
println(beverage[2:4])Output:
("tea", "greentea", "grrencoffee")#Iteration
println("iterating over tuple :")
for i in beverage
    println(i)
endOutput:
iterating over tuple :
coffee
tea
greentea
grrencoffee
ginger tea#Tuple manipulation:
beverage[3]="chamomile tea"Output:
MethodError: no method matching setindex!(::NTuple{4, String}, ::String, ::Int64)

Stacktrace:
 [1] top-level scope
   @ In[7]:2
 [2] eval
   @ .\boot.jl:373 [inlined]
 [3] include_string(mapexpr::typeof(REPL.softscope), mod::Module, code::String, filename::String)
   @ Base .\loading.jl:1196
```

> #注意:元组是不可变的，不支持项赋值。

**元组方法()**

```
#reverse a tuple
rev= reverse(beverage)
println(rev)Output:("ginger tea", "grrencoffee", "greentea", "tea", "coffee")#length of tuple
println(“length of tuple “,length(beverage))Output: length of tuple 5#check if empty or not
println(isempty(beverage))Output: false
```

**命名元组:**除了每个元素额外有一个名称之外，就像元组一样！
它们有一个特殊的语法，在元组中使用“=”。
语法:
(name1 = item1，name2 = item2，…)

```
lang= (l1=”julia”,l2=”python”,l3=”SQL”)
println(lang)Output: (l1 = "julia", l2 = "python", l3 = "SQL")println(lang[2])Output: pythonprintln(lang.l1)Output: julia
```

# **字典和方法()**

```
#create a dictionary
empIDs= Dict(“vivek”=>121,”aniket”=>134,”jagdish”=>101)
println(typeof(empIDs))
println(empIDs)Output:
Dict{String, Int64}
Dict("jagdish" => 101, "vivek" => 121, "aniket" => 134)#create dict from tuple
eds=[("vivek",2000),("jagdish",5000),("aniket",3500)]
println(typeof(eds))
println(eds)Output:
Vector{Tuple{String, Int64}}
[("vivek", 2000), ("jagdish", 5000), ("aniket", 3500)]#conver the tuple into dictionary
edict=Dict(eds)
println(typeof(edict))
println(edict)Output:
Dict{String, Int64}
Dict("jagdish" => 5000, "vivek" => 2000, "aniket" => 3500)
```

**访问字典条目**

```
println(edict)
Output:
Dict("jagdish" => 5000, "vivek" => 2000, "aniket" => 3500)key=keys(edict)
println(“keys are :”,key)
Output: keys are :["jagdish", "vivek", "aniket"]val=values(edict)
println(“values are :”, val)
Output: values are :[5000, 2000, 3500]#Iterate over dictionary using for loop 
for (key,val) in edict
    println(key,"=>",val)
endOutput:
jagdish=>5000
vivek=>2000
aniket=>3500
```

**字典法()**

**get()和 getkey()**

```
#get() method: Return the value stored for the given key
#syntax: get(collection, key, default)println(edict)
Output:
Dict("jagdish" => 5000, "vivek" => 2000, "aniket" => 3500)println(get(edict,"vivek",-1))
Output: 2000#default value is mandatory otherwise it throws error
println("Key not found ",get(edict,"viv",0))
Output: Key not found 0#wihtout default value
println("Key not found ",get(edict,"viv"))Output:
MethodError: no method matching get(::Dict{String, Int64}, ::String)
Closest candidates are:
  get(::Dict{K, V}, ::Any, ::Any) where {K, V} at C:\Users\lenovo\AppData\Local\Programs\Julia-1.7.1\share\julia\base\dict.jl:506
  get(::IJulia.IJuliaStdio, ::Any, ::Any) at C:\Users\lenovo\.julia\packages\IJulia\e8kqU\src\stdio.jl:21
  get(::Test.GenericDict, ::Any, ::Any) at C:\Users\lenovo\AppData\Local\Programs\Julia-1.7.1\share\julia\stdlib\v1.7\Test\src\Test.jl:1800
  ...

Stacktrace:
 [1] top-level scope
   @ In[57]:7
 [2] eval
   @ .\boot.jl:373 [inlined]
 [3] include_string(mapexpr::typeof(REPL.softscope), mod::Module, code::String, filename::String)
   @ Base .\loading.jl:1196#getkey()
Return the key matching argument key if one exists in collection, otherwise return default.println(getkey(edict,"aniket",-1))
Output: aniketprintln(getkey(edict,"viv",-1))
Output: -1
```

**删除()项**

```
println(edict)
Output:
Dict("jagdish" => 5000, "vivek" => 2000, "aniket" => 3500)delete!(edict,”vivek”)
println(edict)
Output:
Dict("jagdish" => 5000, "aniket" => 3500)#delete a non-existing item
delete!(edict,"viv")
Output: 
Dict{String, Int64} with 2 entries:
  "jagdish" => 5000
  "aniket"  => 3500
```

**合并()字典**

```
#merge dictionaries using merge()
d1 = Dict(“a”=>1, “b”=>9, “c”=>3)
d2 = Dict(“e”=>7, “f”=>2, “h”=>5)
println(merge(d1,d2))
Output:
Dict("f" => 2, "c" => 3, "e" => 7, "b" => 9, "a" => 1, "h" => 5)#common keys present
d1 = Dict("a"=>1, "b"=>9, "c"=>3)
d2 = Dict("e"=>7, "b"=>2, "h"=>5)
println(merge(d1,d2))
Output:
Dict("c" => 3, "e" => 7, "b" => 2, "a" => 1, "h" => 5)#merge dictionaries using mergewith()
d1 = Dict("a"=>1, "b"=>9, "c"=>3)
d2 = Dict("e"=>7, "b"=>2, "h"=>5)
println(mergewith!(+,d1,d2))
Output:
Dict("c" => 3, "e" => 7, "b" => 11, "a" => 1, "h" => 5)
```

**添加和更改字典项目**

```
#add new item to a dict
println(edict)
Output: Dict("jagdish" => 5000, "aniket" => 3500)edict[“vivek”]=2700
println(edict)
Output: Dict("jagdish" => 5000, "vivek" => 2700, "aniket" => 3500)#change dict vaue for a key
println(edict)
Output: Dict("jagdish" => 5000, "vivek" => 2700, "aniket" => 3500)edict["vivek"]=4000
println(edict)
Output: Dict("jagdish" => 5000, "vivek" => 4000, "aniket" => 3500)
```

总结一下:

*   Julia 元组和元组方法。
*   字典和方法。

感谢您阅读我的博客并支持内容。欣赏总是有助于保持精神。我会尽我所能不断拿出优质的内容。与我联系以获取关于即将推出的新内容的更新。

继续支持。