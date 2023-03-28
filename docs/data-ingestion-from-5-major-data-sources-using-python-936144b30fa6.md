# 使用 Python 从 5 个主要数据源获取数据

> 原文：<https://pub.towardsai.net/data-ingestion-from-5-major-data-sources-using-python-936144b30fa6?source=collection_archive---------0----------------------->

## [编程](https://towardsai.net/p/category/programming)

## 了解为什么数据存储在不同的源中，以及如何使用 python 检索它们？

被困在付费墙后面？[阅读这篇文章，我的朋友链接在这里。](https://medium.com/towards-artificial-intelligence/data-ingestion-from-5-major-data-sources-using-python-936144b30fa6?source=friends_link&sk=df29423ffd37d6784bf45685b35e0b69)

![](img/1a0b5c1ae875f05a42121db2423eb59c.png)

[来源](https://unsplash.com/photos/qWwpHwip31M)

您知道在 2020 年每天会产生大约 147 GB 的数据吗？到目前为止，我们已经存储了大约 40 万亿 GB 的数据。所有这些存储的数据甚至都不相同。像文本或数字这样的数据类型有不同的格式。这解释了为什么我们有不同类型的数据源。

当您处理数据时，您应该知道如何从不同的来源获取数据。在本文中，我们将借助 python 库从各种来源获取数据。

我们将浏览以下数据来源。

**1。RDBMS 数据库**

**2。XML 文件格式**

**3。CSV 文件格式**

**4。Apache 拼花文件格式**

**5。微软 Excel**

> 我们是否有一个从所有来源获取数据的 python 库？

不会，因为每个数据源都有自己的数据传输协议。我们有多个 python 库来完成这项工作。请将本文视为了解这些 python 库的一站式平台。

在本文中，我们将解释为什么在不同的源中保存数据，以及如何使用 python 库检索数据。

让我们从我们的数据获取故事开始。

## **1。关系数据库管理系统(RDBMS)数据库**

RDBMS 中的数据以行列格式保存。数据库中的表具有固定的模式。我们可以直接在数据库中使用结构化查询语言(SQL)来更新表。关系数据库管理系统的例子有 oracle、微软 SQL Server 等。

**我们为什么要使用 RDBMS 数据库？**

表格格式便于用户使用。

标准语言 SQL 可用于 RDBMS 操作数据。

如果我们适当地优化 RDBMS，处理速度会提高。

维护很容易。

更多的人可以同时访问数据库。

现在我们可以使用 python 库访问不同的 RDBMS 数据库。

```
import pyodbc
server_name = “SQL instance of your database”
username = “username of your database”
password = “password of your database”
database_name = “name of your database”
port = “connection port for your database”conn=pyodbc.connect(‘DRIVER={PostgreSQL ODBC Driver(UNICODE)};
                    SERVER=’+ server_name + 
                    ‘;UID=’ + username + 
                    ‘;PWD=’ + password + 
                    ‘;DATABASE=’ + database_name + 
                    ‘;PORT=’ + port + ‘;’)
cursor = conn.cursor()
cursor.execute(query)
query_data = cursor.fetchall()
```

我们将在 MySQL 和 Postgress 数据库连接中使用此代码。MySQL 数据库连接不需要端口变量。

对于不同的数据库，驱动变量的内容是不同的。MySQL 和 Postgress 数据库的驱动程序是 SQL Server 和 PostgreSQL ODBC 驱动程序(UNICODE)。此外，请检查您的计算机中有哪些类型的数据库驱动程序。使用 pyodbc.drivers()函数。

将以下代码用于 Oracle 数据库。

```
import cx_Oracledsn_tns = cx_Oracle.makedsn(server_name, 
                            port, 
                            service_name=server_name)conn = cx_Oracle.connect(user=username, 
                         password=password,
                         dsn=dsn_tns)
cursor = conn.cursor()
cursor.execute(query)
query_data = cursor.fetchall()
```

联系您的数据库管理员，获取用户名、密码、服务器名称、端口、服务名称和数据库名称变量的值。

## 2.XML 文件格式

XML 是外部标记语言(XML)文件的文件扩展名。它存储那些人类可读和机器可读的文本数据。XML 的设计方式使得它的格式不会在互联网上改变。

**为什么我们使用 XML 文件格式？**

XML 是一种人和机器都能理解的纯文本文件格式。

XML 有一个简单而通用的语法规则来在应用程序之间交换信息。

我们可以使用编程语言来操作 XML 文件中的信息。

我们可以将多个 XML 文档组合成一个大的 XML 文件，而不需要添加额外的信息。还可以将 XML 分成不同的部分，分别使用。

XML 文件格式在 web 应用程序中更受欢迎。

现在，我们可以使用 xml 库访问 XML 文件。

```
import pandas as pd
import xml.etree.ElementTree as etreexml_tree = etree.parse(“sample.xml”)
xml_root = xml_tree.getroot()
columns = [“A”, “B”]datatframe = pd.DataFrame(columns = columns)
for node in xml_root:
    name = node.attrib.get(“A”)
    mail = node.find(“B”).text if node is not None else None
    datatframe = datatframe.append(pd.Series([A,B], index=columns),
                                   ignore_index = True)
```

您可以使用请求库在 SOAP API 中发布 XML 文件。

## 3.CSV 文件格式。

逗号分隔值(CSV)是一种存储纯文本和表格数据的文件格式。CSV 文件的第一行一般包含各列，并用逗号分隔各列。第二行及以后各列都有内容。它可以是文本、数字或日期。制表符分隔的值文件也有。csv 文件扩展名。它解决了与 CSV 文件格式相关的列分离问题。

**我们为什么使用 CSV 文件格式？**

易于创建和操作数据。

易于阅读和理解数据。

我们可以组织大量的数据。

我们可以轻松地导入和导出 CSV 文件。

现在我们可以使用 pandas 和 CSV 库访问 CSV 文件。

在 pandas 库的帮助下，您可以直接将 CSV 文件导入到数据帧中。

```
# importing Pandas library
import pandas as pd
csv_dataframe = pd.read_csv(“hr_data.csv”, sep=”,”,)
print(csv_dataframe)Name Hire Date Salary Sick Days remaining
0 Graham Chapman 03/15/14 50000.0 10
1 John Cleese 06/01/15 65000.0 8
2 Eric Idle 05/12/14 45000.0 10
3 Terry Jones 11/01/13 70000.0 3
4 Terry Gilliam 08/12/14 48000.0 7
5 Michael Palin 05/23/13 66000.0 8
```

***如果 CSV 文件有' \t '分隔符，则使用 sep="\t "。如果有空间，请使用 sep= " "。*** 访问[此处](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.read_csv.html)了解更多关于 read_csv 函数的信息。

```
import csvwith open(“hr_data.csv”) as csv_file:
    csv_reader = csv.reader(csv_file, delimiter=’,’)
    line_count = 0
    for row in csv_reader:
        if line_count == 0:
            print(f’Column names are {“, “.join(row)}’)
            line_count += 1
        else:
            print(f’\t{row[0]} first column content {row[1]} second
                  row content {row[2]} third row content.’)
            line_count += 1
print(f’Processed {line_count} lines.’)
```

## 4.Apache 拼花地板文件格式

Apache Parquet 是一种面向列的数据存储文件格式。存储在 parquet 文件中的数据得到了有效的压缩。parquet 中使用分解和组装算法来存储数据。它得到了增强，可以批量处理复杂的数据。通常，拼花格式在大数据技术中很有用。

**为什么我们使用 apache parquet 文件格式**

使用高效压缩算法创建的拼花文件比其他文件格式节省大量存储空间。

获取列数据的查询不需要扫描整行，这样可以提高性能。

每一列都有自己的编码技术。

Parquet 文件已经针对处理大量数据的查询进行了优化。

现在我们可以使用 pandas 和 pyarrow 库访问拼花文件。

```
**import** **pyarrow.parquet** **as** **pq**example_table = pq.read_pandas('example.parquet', 
                               columns=['one',’two’]).to_pandas()print(example_table)one two
a foo bar
b bar baz
c baz fooimport pandas as pdpandas_dataframe = pd.read_parquet('example.parquet',
                                   engine='pyarrow')print(pandas_dataframe)one two
a foo bar
b bar baz
c baz foo
```

## 5.微软优越试算表

Excel 是微软开发的电子表格。它以表格形式存储数据。它有一个由单元格组成的网格，这些单元格组合起来就形成了行和列。它有许多内置功能，如计算、绘图工具、数据透视表等。

**为什么我们使用微软的 Excel 文件格式？**

您可以使用图表和图形分析 excel 中的数据。

Excel 擅长对数据进行排序、筛选和搜索。

您可以建立一个数学公式，并将其应用于数据。

Excel 带有密码保护功能。

您可以将 excel 用作日历。

您还可以使用 excel 来自动化与数据相关的作业。

现在，我们可以使用 openpyxl 库访问 Microsoft Excel。

```
from openpyxl import load_workbookworkbook = load_workbook(filename=”sample.xlsx”)
workbook_sheets = workbook.sheetnames
sheet = workbook.activeprint(sheet[“A1”].value)“hello”print(sheet.cell(row=10, column=6).value)“this is hello world store in row 10 and column 6.”import pandas as pd df = pd.read_excel(‘File.xlsx’, sheetname=’Sheet1')print(“Column headings:”)
print(df.columns)[‘A’,’B’,’C’]
```

## 结论

本文帮助您理解为什么我们需要不同的数据源来存储数据，以及如何从这些数据源中检索数据。我们使用了多个 python 库来接收数据。在本文中，我讨论了 5 个数据源。

希望本文能对您的数据处理活动有所帮助。

**作者其他文章**

1.  [EDA 的第一步:描述性统计分析](https://medium.com/analytics-vidhya/first-step-in-eda-descriptive-statistics-analysis-f49ca309da15)
2.  [为 Reddit Post: TextBlob 和 VADER 自动化情感分析流程](https://towardsdatascience.com/automate-sentiment-analysis-process-for-reddit-post-textblob-and-vader-8a79c269522f)
3.  [使用罗伯塔模型发现 Reddit 子群的情绪](https://towardsdatascience.com/discover-the-sentiment-of-reddit-subgroup-using-roberta-model-10ab9a8271b8)