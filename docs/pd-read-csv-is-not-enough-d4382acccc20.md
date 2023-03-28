# pd.read_csv()还不够(*)

> 原文：<https://pub.towardsai.net/pd-read-csv-is-not-enough-d4382acccc20?source=collection_archive---------1----------------------->

## [编程](https://towardsai.net/p/category/programming)

![](img/1e2bec50c9cded77d64de892a1d13368.png)

[西格蒙德](https://unsplash.com/@sigmund?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)在 [Unsplash](https://unsplash.com/s/photos/load?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) 上拍照

作为初学者，你可能只知道一种加载数据(通常是 CSV 格式)的方法，那就是使用 *pandas.read_csv* 函数读取数据。这是最成熟和最强大的功能之一，但其他方法非常有用，有时肯定会派上用场。

几十年前，最有价值的资源是石油。数据被比作石油。因此有一句名言“数据是新的石油”。

因此，让我们了解一下各种装油方法(😆)

> **读取文本文件(。txt)**

```
With open(“filename.txt”, r) as file:
     print(file.read())
```

> **使用 Numpy [loadtxt()，genfromtxt()]**导入平面文件

**loadtxt()**

导入 numpy 作为 np
data = np.loadtxt(文件名，分隔符= "，")

**genfromtxt()**

```
import numpy as np
data = np.genfromtxt(filename, delimiter = “,”)
```

何时使用 loadtxt()以及何时使用 genfromtxt()

*   当我们的数据中有相同类型时，比如全整型、全分类或全浮点型，那么就使用 loadtxt()
*   但是当我们有混合数据类型时，比如我们有 int 列、categorical 列和所有其他类型的列，那么我们应该使用 genfromtxt()

> **读取 CSV 文件:**

**利用熊猫**

```
import pandas as pd
data = pd.read_csv(‘file.csv’, **kwargs)
```

> **读取泡菜文件:**

*   Pickle 文件是序列化的(将一个对象转换成字节流)

```
import pickle
with open(“file.pkl”, ‘rb’) as file:
     data = pickle.load(file)
print(data)
```

> **读取 Excel 文件:**

```
import pandas as pd
data = pd.excelfile(“file.xlsx”)
print(data.sheet_name)
```

> **导入 SAS 和 Stata 文件**

*   **SAS:-** 统计分析系统
*   **Stata:-** 统计分析数据

> **SAS 文件是用来干什么的？**

*   高级/多元分析
*   商业智能
*   数据管理
*   预测分析

> **导入 SAS 文件**

```
import pandas as pd
from sas7bdat import SAS7DBATwith SAS7DBAT(“file.sas7bdat”) as file:
     df_sas = file.to_data_frame()
```

> **Stata 文件用于**

*   DTA 文件是 IWIS 链条工程(一种汽车传动链计算程序)使用的数据库文件。它包含的数据可能包括发动机扭矩、链条负载和传动链所支持的摩擦力。DTA 文件用于计算所需的驱动能力，以确定适合汽车的驱动链。

> **导入 STATA 文件**

```
import pandas as pd
data = pd.read_state(‘file.dta”)
```

> **导入 HDF5 文件**

*   分层数据格式版本 5
*   存储大量数字数据的标准
*   数据集可能有数百 GB 或 TB
*   HDF5 可扩展至 1 EB

```
import h5py
data = h5py.File(“file.hdf5”, ‘r’)
print(type(data))//The Structure of HDF5 file
for key in data.keys():
    print(key)
```

> **导入 MATLAB 文件**

*   Matlab 代表矩阵实验室。
*   数据文件另存为”。垫子"

**使用 scipy.io**

```
import scipy.io
mat = scipy.io.loadmat(‘file.mat’)
print(type(mat))
```

暂时就这样了👏👏。下一篇文章再见。

**在我的 YouTube 上查看更多有趣的机器学习、深度学习、数据科学项目👉:-**[**YouTube**](https://www.youtube.com/c/himanshutripathi)**(👍)**

****还有，我们来连线一下**[**Linkedin**](https://www.linkedin.com/in/iamhimanshu0/)**[**Twitter**](https://twitter.com/iam_himanshu0)**[**insta gram**](https://instagram.com/iamhimanshu0/)**[**Github**](https://github.com/iamhimanshu0)**，以及** [**脸书**](https://www.facebook.com/iamhimanshu0) **。**********