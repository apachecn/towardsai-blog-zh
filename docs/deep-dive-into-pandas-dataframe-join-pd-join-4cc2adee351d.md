# 深入了解熊猫数据帧连接— pd.join()

> 原文：<https://pub.towardsai.net/deep-dive-into-pandas-dataframe-join-pd-join-4cc2adee351d?source=collection_archive---------1----------------------->

![](img/9826d60c6298fc530d2cae203056f6f2.png)

图片由作者| **除特别注明外，所有图片均来自作者。**

## [数据科学](https://towardsai.net/p/category/data-science)，[编辑](https://towardsai.net/p/category/editorial)，[编程](https://towardsai.net/p/category/programming)

## 关于如何在 pandas 中将列与其他数据框连接的深度可视化教程

**作者:** [普拉蒂克·舒克拉](https://www.linkedin.com/in/pratik-shukla28/)，[罗伯特·伊里翁多](https://mktg.best/vguzs)

[](https://members.towardsai.net/) [## 加入我们吧↓ |面向人工智能成员|数据驱动的社区

### 加入人工智能，成为会员，你将不仅支持人工智能，但你将有机会…

members.towardsai.net](https://members.towardsai.net/) 

pandas 库的函数用于连接另一个数据帧的列。它可以有效地将列与索引或键列上的另一个数据帧连接起来。我们也可以通过传递一个列表来连接多个 DataFrame 对象。让我们从理解它的语法和参数开始。本教程的配套资料可以在我们的 [**资源部分**](#dc64) 中找到。

## 目录:

1.  [语法](#0538)
2.  [创建数据帧](#e8c6)
3.  [了解 lsuffix 和 rsuffix 参数](#a343)
4.  [通过索引值连接数据帧](#a475)
5.  [设置索引以连接数据帧](#ad00)
6.  [了解 on 参数](#da7f)
7.  [连接多个数据帧](#8285)
8.  [用数据帧连接一个系列](#de10)
9.  [了解“如何”参数](#2069)
10.  [了解“排序”参数](#0d9e)
11.  [关键要点](#8129)
12.  [资源](#dc64)
13.  [参考文献](#e18d)

# 熊猫。DataFrame.join()

**调用者数据帧:** 主数据帧，我们想用它来连接其他数据帧或系列。

**其他数据框:**
我们希望与主数据框连接的数据框。

## 语法:

*DataFrame.join(other，on=None，how="left "，lsuffix= " "，rsuffix = " "，sort=False)*

## 参数:

> 1.其他→数据帧、数据帧系列或数据帧列表
> 我们希望连接到主对象的其他对象(数据帧或系列)。
> 该参数是必需值。
> 
> 2.on → string、字符串列表或类似数组的
> 来设置调用数据帧中的列，以连接其他数据帧的索引。
> 该参数是可选值。默认值为无。
> 
> 3.how →{“左”、“右”、“外”、“内”}
> 如何处理对象的拼接操作。
> A. left:使用调用框架的索引。
> B .右:使用别人的指数。
> C. outer:将调用框架的索引与其他框架的索引形成并集。
> D. inner:形成调用框架的索引与其他框架的索引的交集。
> 这是一个可选值。默认值为左。
> 
> 4.lsuffix → string
> 它指定用于左框架重叠列的后缀值。
> 该参数是可选值。默认值为“”。
> 
> 5.rsuffix → string
> 它指定用于右框架重叠列的后缀值。
> 该参数为可选值。默认值为“”。
> 
> 6.sort → boolean
> 它指定结果数据帧的顺序结果。如果为 False，则顺序取决于“how”关键字的值。
> 该参数为可选值。默认值为 False。

## 退货:

它将返回一个 DataFrame，其中包含来自调用者和其他人的列。

## A.导入所需的库:

![](img/6a69d76af569a53dbd8aec32ce07081c.png)

图 1:导入所需的库

## B.创建数据帧:

## B1。第一个数据帧:

![](img/2f71e244092d49970f3e4e191aa5225e.png)

图 2:数据帧 1 (df1)

## Python 实现:

![](img/9af44e3ddf3473bd926df94c26285a95.png)

图 3: Python 代码

![](img/58f5cb20f82d1d22230c70b2b691b33f.png)

图 4:输出

## B2。第二个数据帧:

![](img/acaf63e1efbcc443e16fa0ebee11a93c.png)

图 5:数据帧 2 (df2)

## Python 实现:

![](img/7e457704995588c11f1c45101a080f63.png)

图 6: Python 代码

![](img/8a4ce9b46f1c64a92ca98bf04b9afc61.png)

图 7:输出

## B3。第三个数据帧:

![](img/5ab9e30ecef818e8d482af3d7e2aec84.png)

图 8:数据帧 3 (df3)

## Python 实现:

![](img/b0d41cce8b25b98731f8ccbbbccb8d0a.png)

图 9: Python 代码

![](img/ca909846db30ed7480187692c8ac3bc7.png)

图 10:输出

## B4。第四个数据帧:

![](img/74e6e0f1973ff559370daa0f97fcad4e.png)

图 11:数据帧 4 (df4)

## Python 实现:

![](img/9634a471167e36c65d90ea97bf92908a.png)

图 12: Python 代码

![](img/43a9c9d3b957bc040dda47115c8dea2b.png)

图 13:输出

## B5。第五个数据帧:

![](img/0b8ec068eb7ad4ee7bdbea4d9059e46c.png)

图 14:数据帧 5 (df5)

## Python 实现:

![](img/2abd14b49f545f239f13a153184b7f53.png)

图 15: Python 代码

![](img/c962c45e33ce97de4d6a4c56138f22d0.png)

图 16:输出

## B6。第六个数据帧:

![](img/a9696e25218175d03fcd6675664691ce.png)

图 17:数据帧 6 (df6)

## Python 实现:

![](img/79085a78f25b1f5ec31af44acb12ccd0.png)

图 18: Python 代码

![](img/d8ede53d82e4327b86556a40803a452f.png)

图 19:输出

## B7。第七个数据帧:

![](img/50b4239b5ad130769530103fd16a52ba.png)

图 20:数据帧 7 (df7)

## Python 实现:

![](img/b48df3d6e64b4bd68c60af45bae5f312.png)

图 21: Python 代码

![](img/9ad9a4a4cc1f4e34eb9fe1a634344123.png)

图 22:输出

# 了解 lsuffix 和 rsuffix 参数:

## A.示例 1:

如果我们在数据帧中有重叠的列，并且没有指定`“lsuffix”`或`“rsuffix”`的值，那么就会产生一个错误。请注意，我们必须指定`“lsuffix”`或`“rsuffix”`的值，或两者都指定，以避免此错误。在下面的例子中，我们有一个名为`“Name”`的重叠列，因为我们既没有指定`“lsuffix”`也没有指定`“rsuffix”`，所以它会产生一个错误。

![](img/2f71e244092d49970f3e4e191aa5225e.png)

图 23:数据帧 1 (df1)

![](img/acaf63e1efbcc443e16fa0ebee11a93c.png)

图 24:数据帧 2 (df2)

![](img/8a4992b207969b68b9489bfa2dbdd297.png)

图 25:使用 join()函数

![](img/5dcc5a60c8e474edc3adfad53f895be7.png)

图 26:输出

## Python 实现:

![](img/15424f284014bc67ca123a84be807b42.png)

图 27: Python 代码

![](img/dd79d17b025527f3ed6a98794be3712e.png)

图 28:输出

## B.示例 2:

## 使用的参数:

> lsuffix = "_Left "
> 
> rsuffix = "_Right "

![](img/2f71e244092d49970f3e4e191aa5225e.png)

图 29:数据帧 1 (df1)

![](img/acaf63e1efbcc443e16fa0ebee11a93c.png)

图 30:数据帧 2 (df2)

![](img/810cef6ef488b247c63097ec12e26369.png)

图 31:使用 join()函数

![](img/0e10fd3e4050ead13a14e15dd260c727.png)

图 32:最终输出

## Python 实现:

![](img/c4a2300a03f29e231b1321195199d86d.png)

图 33: Python 代码

![](img/c6a55083ba155d482bbf94c3285a9962.png)

图 34:输出

## C.示例 3:

## 使用的参数:

> lsuffix = "_Left "

![](img/2f71e244092d49970f3e4e191aa5225e.png)

图— 35:数据帧 1 (df1)

![](img/acaf63e1efbcc443e16fa0ebee11a93c.png)

图— 36:数据帧 2 (df2)

![](img/a0e0704c9d3579376cbbedaa654308ab.png)

图— 37:使用 join()函数

![](img/7b5e2ea303460b8fb213e3bf37e34dfd.png)

图 38:最终输出

## Python 实现:

![](img/6128e61982bcdb90b7e8bcb46e162511.png)

图 39: Python 代码

![](img/8eef0c5ce079200bd4ffe64539c55230.png)

图 40:输出

## D.示例 4:

## 使用的参数:

> rsuffix = "_Right "

![](img/2f71e244092d49970f3e4e191aa5225e.png)

图— 41:数据帧 1 (df1)

![](img/acaf63e1efbcc443e16fa0ebee11a93c.png)

图 42:数据帧 2 (df2)

![](img/3975fdafea13f17e772e889a58c523af.png)

图 43:使用 join()函数

![](img/405276bce739bda5281de35d5e3944b1.png)

图 44:输出

## Python 实现:

![](img/5256d5f535db560561ad05361028a8bf.png)

图 45: Python 代码

![](img/2bedd10d990f708561bb4cb9ed13b53c.png)

图 46:输出

# 通过索引值连接数据帧:

## A.示例 1:

默认情况下，数据帧将由索引值连接。

![](img/74e6e0f1973ff559370daa0f97fcad4e.png)

图— 47:数据帧 4 (df4)

![](img/0b8ec068eb7ad4ee7bdbea4d9059e46c.png)

图 48:数据帧 5 (df5)

![](img/fff7d9b88fc7c7da6839133235988853.png)

图-49:使用 join()函数

![](img/32f82fbed434b1e9d7fba4b47ac7e7a4.png)

图 50:输出

## Python 实现:

![](img/5593fa1fc2acfa65ce46963c3f7cdde7.png)

图 51: Python 代码

![](img/5b40d74a49f9f3eb6854688875633c44.png)

图 52:输出

# 设置索引以连接数据帧:

## A.示例 1:

我们可以使用`“set_index”`来设置数据帧的索引，然后连接数据帧。

![](img/2f71e244092d49970f3e4e191aa5225e.png)

图— 53:数据帧 1 (df1)

![](img/acaf63e1efbcc443e16fa0ebee11a93c.png)

图— 54:数据帧 2 (df2)

![](img/70af0b10363d265616885c618f2d7d5f.png)

图-55:使用 join()函数

![](img/7f7ce290e01663a91b9817b4662c84ec.png)

图 56:输出

## Python 实现:

![](img/30732fd507a0d49373207d0930544871.png)

图 57: Python 代码

![](img/74be838f0a42a517e49d6ddca43138f3.png)

图 58:输出

# 理解“开”参数:

## A.示例 1:

## 使用的参数:

> on = "Name "

![](img/2f71e244092d49970f3e4e191aa5225e.png)

图— 59:数据帧 1 (df1)

![](img/acaf63e1efbcc443e16fa0ebee11a93c.png)

图 60:数据帧 2 (df2)

![](img/ea7cb6a69f7d70b6d01972250963a550.png)

图-61:使用 join()函数

![](img/7f7ce290e01663a91b9817b4662c84ec.png)

图 62:输出

## Python 实现:

![](img/0a45c6ae210f771e3a56f92d28db3f9c.png)

图 63: Python 代码

![](img/6f5299739c3649b7f5cc04bd248bf9a4.png)

图 64:输出

# 连接多个数据帧:

## A.示例 1:

我们可以通过使用数据帧列表来连接多个数据帧。

![](img/2f71e244092d49970f3e4e191aa5225e.png)

图— 65:数据帧 1 (df1)

![](img/acaf63e1efbcc443e16fa0ebee11a93c.png)

图-66:数据帧 2 (df2)

![](img/5ab9e30ecef818e8d482af3d7e2aec84.png)

图-67:数据帧 3 (df3)

![](img/66875315f9b2661506ef72e7226e928d.png)

图-68:使用 join()函数

![](img/8e9d68d18177b25adbb53f1423d1b49e.png)

图 69:输出

## Python 实现:

![](img/bc3ff5b889670aeee311afa41025c02a.png)

图 70: Python 代码

![](img/7eee61177a5f0d888231485d5e7f1cd0.png)

图 71:输出

# 将系列与数据框连接起来:

## A.创建系列:

![](img/877f859b93585ddd73256a046f03db64.png)

图— 71:创建系列图像

## Python 实现:

![](img/7755e606d55574ee5f4cde4befa11036.png)

图 72: Python 代码

![](img/6a0dba6a1835ea1a3e9c1725204cbddc.png)

图-73:输出

## B.示例 1:

将一个系列与一个数据帧连接时，必须指定该系列的`name` ，它将在输出中用作列名。

![](img/2f71e244092d49970f3e4e191aa5225e.png)

图— 74:数据帧 1 (df1)

![](img/877f859b93585ddd73256a046f03db64.png)

图-75:系列

![](img/b977752f3859ae87b59a5e3264577497.png)

图-76:使用 join()函数

![](img/0e81967a590803f02361071fef6815c6.png)

图— 77:输出

## Python 实现:

![](img/e86b45c3837f77e1230105f721d10119.png)

图 78: Python 代码

![](img/56816767bb7231d27b546a0645b95f94.png)

图-79:输出

# 了解“如何”参数:

## A.示例 1:

如果我们使用`“how” = “left”`，那么它将使用调用框架的索引(或列名)来执行连接操作。*在这种情况下，调用数据帧中的任何一行都不会在最终输出中丢失。*

## 使用的参数:

> how = "左"

![](img/2f71e244092d49970f3e4e191aa5225e.png)

图 80:数据帧 1 (df1)

![](img/acaf63e1efbcc443e16fa0ebee11a93c.png)

图-81:数据帧 2 (df2)

![](img/069db15d26d0bfc2457a71e072ea3de9.png)

图-82:使用 join()函数

![](img/c71180024a42ff3690c309745d840521.png)

图 83:输出

## Python 实现:

![](img/fc28737c9a011f784b27e67ea1ee8e03.png)

图 84: Python 代码

![](img/766ace2a9d24aa4994c314e4f639c9c0.png)

图 85:输出

## B.示例 2:

如果我们使用`“how” = “right”`，那么它将使用另一个框架的索引(或列名)来执行连接操作。*在这种情况下，来自另一个数据帧的任何一行都不会在最终输出中丢失。*

## 使用的参数:

> how = "right "

![](img/2f71e244092d49970f3e4e191aa5225e.png)

图— 86:数据帧 1 (df1)

![](img/acaf63e1efbcc443e16fa0ebee11a93c.png)

图-87:数据帧 2 (df2)

![](img/a2db6e975efc7f82809d3b4616fbd377.png)

图-88:使用 join()函数

![](img/d36b7504d584ee935775df255e37ce29.png)

图-89:输出

## Python 实现:

![](img/4c07c28e34207ea7d041da5811110ba0.png)

图 90: Python 代码

![](img/25624a8c34a3683689e94d0ab9a6f3bf.png)

图 91:输出

## C.示例 3:

如果我们使用`“how” = “outer”`，它将调用框架的索引(或列名)与其他框架的索引结合起来。这里需要注意的重要一点是，即使我们没有指定`sort`参数，输出也将按字典顺序排序。*在这种情况下，来自调用和其他数据帧的行都不会丢失。*

## 使用的参数:

> how = "outer "

![](img/2f71e244092d49970f3e4e191aa5225e.png)

图— 92:数据帧 1 (df1)

![](img/acaf63e1efbcc443e16fa0ebee11a93c.png)

图— 93:数据帧 2 (df2)

![](img/a1eed0919bd90b0ff995c78a0d96d54f.png)

图-94:使用 join()函数

![](img/b2af718343d11797164600224bfad3d1.png)

图 95:输出

## Python 实现:

![](img/eb45a04f7c52cca0a9daba55db87c114.png)

图 96: Python 代码

![](img/6f43f6d5204d45a3347be355d474aeea.png)

图 97:输出

## D.示例 4:

如果我们使用`“how” = “inner”`，那么它形成了调用框架的索引(或列名)与其他索引的交集。输出将保持调用数据帧的顺序。

## 使用的参数:

> how = "内心"

![](img/2f71e244092d49970f3e4e191aa5225e.png)

图— 98:数据帧 1 (df1)

![](img/acaf63e1efbcc443e16fa0ebee11a93c.png)

图— 99:数据帧 2 (df2)

![](img/d62b47229f2c902523cae1dbb05d2cdb.png)

图 100:使用 join()函数

![](img/b0030263d0e93d023468445f60d676d5.png)

图 101:输出

## Python 实现:

![](img/d7f1db092f9e5a440becc0ee988f2d55.png)

图 102: Python 代码

![](img/75f315a2f7a89049622e708b8d91fd7d.png)

图 103:输出

## 总结:

![](img/01f0ce1e2b5640e7eaa0df5ba524bb23.png)

# 了解“排序”参数:

## A.示例 1:

## 使用的参数:

> how = "左"
> 
> 排序=假

输出将**而不是**按字典顺序排序。

![](img/a9696e25218175d03fcd6675664691ce.png)

图— 104:数据帧 6 (df6)

![](img/50b4239b5ad130769530103fd16a52ba.png)

图— 105:数据帧 7 (df7)

![](img/94cdce4bb477117d75c0774dc30286bb.png)

图-106:使用 join()函数

![](img/927525168d00d6d0ea76028956cb008a.png)

图 107:输出

## Python 实现:

![](img/498d661d17896d9359045a57a987f689.png)

图 108: Python 代码

![](img/459fdd719aab2035a9cc1cb4a405db79.png)

图 109:输出

## B.示例 2:

## 使用的参数:

> how = "左"
> 
> 排序=真

输出将按字典顺序排序。

![](img/a9696e25218175d03fcd6675664691ce.png)

图 110:数据帧 6 (df6)

![](img/50b4239b5ad130769530103fd16a52ba.png)

图— 111:数据帧 7 (df7)

![](img/0fbb646a8d5aa2c2512c08b9dc796b96.png)

图-112:使用 join()函数

![](img/ae50841d4141544504f544c35d463ce0.png)

图 113:输出

## Python 实现:

![](img/e7c429bfaebf291de1f79415c52b5d79.png)

图 114: Python 代码

![](img/6ebdf826d855a44915b95943de61cfb9.png)

图 114:输出

## C.示例 3:

## 使用的参数:

> how = "right "
> 
> 排序=假

输出将**而不是**按字典顺序排序。

![](img/a9696e25218175d03fcd6675664691ce.png)

图— 115:数据帧 6 (df6)

![](img/50b4239b5ad130769530103fd16a52ba.png)

图— 116:数据帧 7 (df7)

![](img/df578c2315b84b9c72164411ccc1b4a6.png)

图-117:使用 join()函数

![](img/57e1c2f700b9282fa7eb54b244f43bd0.png)

图 118:输出

## Python 实现:

![](img/62a4d45d8028a5943335536acb211320.png)

图 119: Python 代码

![](img/08b07bfbf759dd45a6623fb7a8a2626f.png)

图 120:输出

## D.示例 4:

## 使用的参数:

> how = "right "
> 
> 排序=真

输出将按字典顺序排序。

![](img/a9696e25218175d03fcd6675664691ce.png)

图— 121:数据帧 6 (df6)

![](img/50b4239b5ad130769530103fd16a52ba.png)

图— 122:数据帧 7 (df7)

![](img/496e34706f6824fbfb338303eb65d5a8.png)

图-123:使用 join()函数

![](img/7c771d4ec3df04f195eec61567d2426a.png)

图 124:输出

## Python 实现:

![](img/49843862f56f6a84fae1b3bb7ed77163.png)

图 125: Python 代码

![](img/13eb1aafaa4e1e201ac010e83be10ef1.png)

图 126:输出

## E.示例— 5:

## 使用的参数:

> how = "outer "
> 
> 排序=假

如果我们指定了`how = “outer”`，那么不管我们是否指定了`sort = True or False`，输出总是按字典顺序排序。

![](img/a9696e25218175d03fcd6675664691ce.png)

图— 127:数据帧 6 (df6)

![](img/50b4239b5ad130769530103fd16a52ba.png)

图— 128:数据帧 7 (df7)

![](img/ce10e7043d8ea777ebb1aeeb8e527a17.png)

图-129:使用 join()函数

![](img/a7d206fc627a0419c103eceb14a8f81f.png)

图 130:输出

## Python 实现:

![](img/231bb115965468c0ea9b80f8ee0c85c9.png)

图 131: Python 代码

![](img/2222350f2bf31b6cc78c2c46d004026e.png)

图 132:输出

## F.示例— 6:

## 使用的参数:

> how = "outer "
> 
> 排序=真

输出将按字典顺序排序。

![](img/a9696e25218175d03fcd6675664691ce.png)

图— 133:数据帧 6 (df6)

![](img/50b4239b5ad130769530103fd16a52ba.png)

图— 134:数据帧 7 (df7)

![](img/ab8abfe72a104c7ffbc61b0f88ee242f.png)

图-135:使用 join()函数

![](img/a7d206fc627a0419c103eceb14a8f81f.png)

图 136:输出

## Python 实现:

![](img/34d4e6370a638fb4dc88fa5f676fb11e.png)

图 137: Python 代码

![](img/3ee96d5961b1ef7351d84151d025da60.png)

图 138:输出

## G.示例— 7:

## 使用的参数:

> how = "内心"
> 
> 排序=假

如果我们指定`how = “inner”`，那么默认情况下，输出将保持调用数据帧的顺序。输出将**而不是**按字典顺序排序。

![](img/a9696e25218175d03fcd6675664691ce.png)

图— 139:数据帧 6 (df6)

![](img/50b4239b5ad130769530103fd16a52ba.png)

图— 140:数据帧 7 (df7)

![](img/ebdd5851b3f954bae00110d37f2661ef.png)

使用 join()函数

![](img/17242207fc99b04d4fa58569127b23f6.png)

图 141:输出

## Python 实现:

![](img/a43c06a150899549f9fe74b760789fb0.png)

图 142: Python 代码

![](img/03b0d5ea7a994efe231abec488b43509.png)

图 143:输出

## H.示例— 8:

## 使用的参数:

> how = "内心"
> 
> 排序=真

输出将按字典顺序排序。

![](img/a9696e25218175d03fcd6675664691ce.png)

图— 144:数据帧 6 (df6)

![](img/50b4239b5ad130769530103fd16a52ba.png)

图— 145:数据帧 7 (df7)

![](img/dfd05e8823cab3ff8faa57b30c9ebafe.png)

图-146:使用 join()函数

![](img/1592a360fe83b708652548ad9646f05d.png)

图 147:输出

## Python 实现:

![](img/2629ae3b463b2ac04938b79740316b1b.png)

图 148: Python 代码

![](img/60c4ba28387bee179a41dfde4c4f2c75.png)

图 149:输出

## 总结:

![](img/dcafc8fd46b522b64f9e2a7a363685b3.png)

图 150:总结

## 关键要点:

1.  当两个数据帧中有相同标签的列时，我们希望连接。我们必须使用`“lsuffix”`或`“rsuffix”`值来避免错误。
2.  默认情况下，数据帧将通过其索引值进行连接。
3.  我们可以通过使用数据帧列表来连接多个数据帧。
4.  我们可以使用`“how”`参数来处理连接操作。
5.  我们可以使用`“sort”`参数按字典顺序对结果数据帧进行排序。

[![](img/7ba4f2d6d12c187d5442ad1a88605fe8.png)](https://www.buymeacoffee.com/pratu)

给普拉蒂克买杯咖啡！

**免责声明:**本文所表达的观点均为作者个人观点，不代表与作者(直接或间接)相关的任何公司的观点。这项工作并不打算成为最终产品，而是当前思想的反映，同时也是讨论和改进的催化剂。

**除非另有说明，所有图片均来自作者。**

经由[发布**走向 AI** 发布](https://towardsai.net/)

## 资源:

[](https://colab.research.google.com/drive/10nYP81Ya3Z_pCEhjxaDXE8-wTXsR8mPt?usp=sharing) [## 熊猫数据框架连接— pd.join() |谷歌联合实验室

colab.research.google.com](https://colab.research.google.com/drive/10nYP81Ya3Z_pCEhjxaDXE8-wTXsR8mPt?usp=sharing) 

[**Github 资源库。**](https://github.com/towardsai/tutorials/blob/master/pandas/pd_join().py)

[](https://ws.towardsai.net/shop) [## 店铺↓ |走向 AI

### 发布最好的技术、科学和工程|社论→https://towardsai.net/p/editorial |订阅→…

ws.towardsai.net](https://ws.towardsai.net/shop) [](https://members.towardsai.net/) [## 加入我们吧↓ |面向人工智能成员|数据驱动的社区

### 加入人工智能，成为会员，你将不仅支持人工智能，但你将有机会…

members.towardsai.net](https://members.towardsai.net/) [](https://sponsors.towardsai.net/) [## 赞助商|了解如何成为《走向人工智能》的赞助商

### 无论你是想以一种吸引读者的方式突出你的产品，吸引高度相关的利基受众，还是…

sponsors.towardsai.net](https://sponsors.towardsai.net/) 

## 进一步阅读

[](/handling-missing-values-in-pandas-f87cec928937) [## 处理熊猫中缺失的值

### 一个关于如何检测和处理熊猫丢失数据的实践视频教程

pub.towardsai.net](/handling-missing-values-in-pandas-f87cec928937) [](https://news.mktg.best/natural-language-in-search-engine-optimization-seo-how-what-when-and-why-b390364b5d3d) [## 搜索引擎优化(SEO)中的自然语言——如何、做什么、何时以及为什么

新闻网](https://news.mktg.best/natural-language-in-search-engine-optimization-seo-how-what-when-and-why-b390364b5d3d) [](/understanding-pandas-melt-pd-melt-362954f8c125) [## 了解熊猫融化— pd.melt()

### 了解重塑 Pandas 数据框的最有效和最灵活的函数

pub.towardsai.net](/understanding-pandas-melt-pd-melt-362954f8c125) 

## 参考资料:

[1]“熊猫。data frame . Join-Pandas 1 . 2 . 4 文档”。2021.Pandas.Pydata.Org。[https://pandas . pydata . org/docs/reference/API/pandas . data frame . join . html](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.join.html.)