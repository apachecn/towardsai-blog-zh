# 使用 Pandas API 的 AWS 红移 ETL

> 原文：<https://pub.towardsai.net/aws-redshift-etl-using-pandas-api-7609be7c9c4f?source=collection_archive---------5----------------------->

## [云计算](https://towardsai.net/p/category/cloud-computing)

这篇博客的目的是用 AWS 红移数据库执行一个简单的 ETL 练习。Oracle 数据库表用作源数据集，使用 Pandas 方法对数据集执行简单的转换，并将数据集写入 AWS 红移表。

![](img/3afdf88d275eaee671c57bdc5e10197f.png)

1.  **导入先决条件和与源 Oracle 的连接:**

```
import pandas as pd
from sqlalchemy import create_engineengine = create_engine(‘oracle://scott:scott@oracle’, echo=False)
```

2 **。从 Oracle 数据库中提取数据集:**

```
#Employee Dataset
emp_df=pd.read_sql_query(‘select * from emp’,engine)
emp_df.head(10)
```

![](img/04c9f6edfaf8b1c9361648f674aca54a.png)

```
#Department Dataset
dept_df=pd.read_sql_query(‘select * from dept’,engine)
dept_df.head(10)
```

![](img/d0e5a10360c8c40d42f25f08d5697187.png)

3.**变换数据集**

使用以下脚本创建 AWS 红移目标表:

```
create table emp (
 empno integer,
 ename varchar(20),
 sal integer,
 comm float,
 deptno integer, 
 dname varchar(20)
);
```

加入 **EMP** 和 **DEPT** 数据集:

```
joined_df=pd.merge(emp_df,dept_df,left_on=’deptno’,right_on=’deptno’,how=’inner’)
joined_df.head(10)
```

![](img/508ab59dcb74ef7b92c2d6e1b56c1ee3.png)

删除目标中不存在的列:

```
joined_df.drop(columns=['job','mgr','hiredate','loc'],inplace=True)
joined_df.head(10)
```

![](img/bee9c436fd2a28686b085dd945130103.png)

**4。创建红移连接并插入数据**

```
#create connection object
conn=create_engine(‘postgresql+psycopg2://<dbuser>:[<dbpassword>@<](mailto:Hasard51@pyspark-redshift.ci5lzce0jb5u.us-east-2.redshift.amazonaws.com)cluster_endpoint_URL>:5439/<dbname>’)joined_df.to_sql(‘emp’, conn, index=False, if_exists=’append’)
```

验证红移表中的数据。

![](img/b43af7feb23e86c7296ddef187982e41.png)

AWS 红移控制台

从 AWS 控制台查询" **emp** "表，我们还可以在本地系统上设置 SQLWorkbench 来查询红移表。

DML 操作成功。

**5。我面临的连接问题**

> OperationalError: (psycopg2。OperationalError)无法连接到服务器:连接超时(0x0000274C/10060)服务器是否在主机" redshift _ cluster _ name . unique _ here . region . redshift . Amazon AWS . com "(<ip address="">)上运行并在端口 5439 上接受 TCP/IP 连接？</ip>

**问题描述**

问题是安全组中的入站规则将一个安全组指定为源。将它更改为包含我的 IP 地址的 CIDR 解决了这个问题。

**怎么修？**

转到群集属性→网络安全

![](img/aec9bc62b24d8badc44ef31ee14f8bde.png)![](img/811162ae141c2925c875bb9d91b6bb04.png)

转到 VPC 安全组→入站规则→编辑入站规则并在下面添加两个规则→单击保存规则。

![](img/16f32e0c5bd01da64fd1a1e5764ca8f6.png)

我们准备好出发了。如果没有第二条规则，可能会出现 AWS 红移数据库的连接问题。因此，请按照上述步骤来避免/解决问题。

感谢大家阅读我的博客。请分享您的观点或反馈。