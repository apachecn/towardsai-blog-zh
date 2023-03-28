# SQL 和 PySpark 中的窗口函数(笔记本)

> 原文：<https://pub.towardsai.net/window-functions-in-sql-and-pyspark-notebook-9145ae96beec?source=collection_archive---------2----------------------->

如果你是一名数据工程师，窗口函数是你几乎每天在工作中都会用到的东西。窗口功能使工作变得非常简单。它们有助于解决一些复杂的问题，并有助于轻松执行复杂的操作。

让我们深入了解窗口函数的用法以及使用它们可以执行的操作。

**注**:下面的一切，我都在 Databricks 社区版中实现了。这不是一篇书面文章；把笔记本贴在这里。以此作为我前进的参考。

**数据砖块笔记本—**

本笔记本将向您展示如何创建和查询您上传到 DBFS 的表格或数据框架。DBFS 是一个数据块文件系统，允许你在数据块内部存储查询数据。这个笔记本假设你有一个文件已经在 DBFS，你想阅读。

这个笔记本是用**Python**编写的，所以默认的单元类型是 Python。但是，您可以通过使用`%LANGUAGE '语法来使用不同的语言。Python，Scala，SQL，R 都支持。

```
# File location and type
file_location = "/FileStore/tables/wage_data.csv"
file_type = "csv"
# CSV options
infer_schema = "true"
first_row_is_header = "true"
delimiter = ","
# The applied options are for CSV files. For other file types, these will be ignored.
df = spark.read.format(file_type) \
.option("inferSchema", infer_schema) \
.option("header", first_row_is_header) \
.option("sep", delimiter) \
.load(file_location)
display(df)
```

从 Pyspark 数据框架创建视图或表格

```
temp_table_name = "wage_data_csv"
df.createOrReplaceTempView(temp_table_name)
```

从表中检索数据

```
select * from `wage_data_csv`
```

将它注册为临时视图后，它将只对该特定笔记本可用。如果您希望其他用户能够查询该表，您也可以从 DataFrame 创建一个表。

一旦保存，该表将在集群重启后保持不变，并允许不同笔记本电脑上的不同用户查询该数据。

```
permanent_table_name = "wage_data_csv"
df.write.format("parquet").saveAsTable(permanent_table_name)
```

有三种类型的窗口功能:

1.  聚合— (AVG、最大值、最小值、总和、计数)

**在 SQL 中—**

```
%sql

 -- 1\. Aggregate

 -- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
 -- Limitations of GroupBy and normal aggregate functions

 select distinct(region) from wage_data_csv
 select distinct(education) from wage_data_csv
 select distinct(jobclass) from wage_data_csv
 select region, year, education, jobclass, avg(wage) from wage_data_csv group by region, education, jobclass order by avg(wage) desc
 -- Here if we want to select year then we have to use nested queries and then select as above sql statement will throw an error.

 -- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
 -- Aggregate AVG function

 select *, avg(wage) over() as average_salary from wage_data_csv
 select region, education, jobclass, avg(wage) over( partition by region, education, jobclass) as avg_wage from wage_data_csv
 select *, avg(wage) over( partition by region, education, jobclass) as avg_wage from wage_data_csv
 select region, education, jobclass, age, avg(wage) over( partition by region, education, jobclass order by age) as avg_wage from wage_data_csv

-- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - 
 --Functionaltites:

 select distinct region, education, jobclass, avg(wage) over( partition by region, education, jobclass) as avg_wage from wage_data_csv
 select distinct region, education, jobclass, max(wage) over( partition by region, education, jobclass) as max_wage from wage_data_csv
 select distinct region, education, jobclass, count(wage) over( partition by region, education, jobclass) as count_wage from wage_data_csv
 select distinct region, education, jobclass, min(wage) over( partition by region, education, jobclass) as min_wage from wage_data_csv
 select distinct region, education, jobclass, sum(wage) over( partition by region, education, jobclass) as sum_wage from wage_data_csv

-- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
```

在 Pyspark —

```
#Pyspark
#reading data
df = spark.sql("select * from wage_data_csv")
df.display()

# Aggregate Window Functions
from pyspark.sql.functions import col,avg,sum,min,max,count
from pyspark.sql import Window

df = df.withColumn("avg_salary", avg(col("wage")).over(Window.partitionBy("region", "education", "jobclass").orderBy("wage")))
df = df.withColumn("max_salary", max(col("wage")).over(Window.partitionBy("region", "education", "jobclass")))
df = df.withColumn("min_salary", min(col("wage")).over(Window.partitionBy("region", "education", "jobclass")))
df = df.withColumn("sum_salary", sum(col("wage")).over(Window.partitionBy("region", "education", "jobclass").orderBy("wage")))
df = df.withColumn("count_salary_units", count(col("wage")).over(Window.partitionBy("region", "education", "jobclass")))

#df.display()
#df.distinct().display()
df.select("region", "education", "jobclass","wage","avg_salary","max_salary","min_salary","sum_salary","count_salary_units").distinct().filter(df.education=="1\. < HS Grad").display()
#df.select("region", "education", "jobclass", "avg_salary").display()
```

2.排名—(行编号，排名，密集排名，百分比排名，整体)

在 SQL 中—

```
 -- 2\. Ranking

 -- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - 
 -- Functionalities:

select region, education, jobclass, wage, row_number() over(partition by region, education, jobclass order by wage) from wage_data_csv
 -- row_number() adds an integer to the records w.r.t order by column based on partitions.

select region, education, jobclass, wage, rank() over(partition by region, education, jobclass order by wage) from wage_data_csv
 -- rank() adds an integers w.r.t order by column based on partitions, but if there is tie same number is assigned and for subsequent records, numbers are skipped.

select region, education, jobclass, wage, dense_rank() over(partition by region, education, jobclass order by wage) from wage_data_csv
 -- dense_rank() adds an integers w.r.t order by column based on partitions,if there is tie same number is assigned but for subsequent records, numbers are not skipped.

select region, education, jobclass, wage, percent_rank() over(partition by region, education, jobclass order by wage) from wage_data_csv
 -- percent_rank() adds an integers w.r.t order by column based on partitions, Here rank is scaled between 0 and 1 as percentages

select region, education, jobclass, wage, ntile(10) over(partition by region, education, jobclass order by wage) from wage_data_csv
 --ntile(10) adds an integers w.r.t order by column based on partitions, Here data is divided into chunks.

 -- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - 

-- usage

 -- to select records with wages more than 50%
 select * from (select region, education, jobclass, wage, percent_rank() over(partition by region, education, jobclass order by wage) as pr from wage_data_csv) where pr>0.5

-- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
```

在 Pyspark —

```
# Ranking Functions

from pyspark.sql.functions import row_number, rank, dense_rank, ntile, percent_rank
from pyspark.sql import Window

df = df.withColumn("row_number", row_number().over(Window.partitionBy("region", "education", "jobclass").orderBy("wage")))
df = df.withColumn("rank", rank().over(Window.partitionBy("region", "education", "jobclass").orderBy("wage")))
df = df.withColumn("dense_rank", dense_rank().over(Window.partitionBy("region", "education", "jobclass").orderBy("wage")))
df = df.withColumn("percent_rank", percent_rank().over(Window.partitionBy("region", "education", "jobclass").orderBy("wage")))
df = df.withColumn("ntile", ntile(10).over(Window.partitionBy("region", "education", "jobclass").orderBy("wage")))

#df.display()
#df.distinct().display()
df.select("region", "education", "jobclass","wage","row_number","rank","dense_rank","percent_rank","ntile").distinct().filter(df.education=="1\. < HS Grad").display()
#df.select("region", "education", "jobclass", "avg_salary").display()
```

3.值—(提前期、滞后期、第一个值、最后一个值、第 n 个值)

在 SQL 中—

```
-- 3\. Value Functions

 - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - 
 -- Functionalities

select region, education, jobclass, wage, lag(wage) over(partition by region, education, jobclass order by wage) from wage_data_csv where education = "1\. < HS Grad"
 -- Shifts entire wage column down by a value based on partition, first value is none

select region, education, jobclass, wage, lead(wage) over(partition by region, education, jobclass order by wage) from wage_data_csv where education = "1\. < HS Grad"
 -- Shifts entire wage column up by a value based on partition, last value is none based on partition

select region, education, jobclass, wage, FIRST_VALUE(wage) over(partition by region, education, jobclass order by wage) from wage_data_csv where education = "1\. < HS Grad"
 -- is used to retrieve first value from the column passed based on partition

select region, education, jobclass, wage, LAST_VALUE(wage) over(partition by region, education, jobclass) from wage_data_csv where education = "1\. < HS Grad"
 -- is used to retrieve last value from the column passed based on partition

select region, education, jobclass, wage, nth_value(wage,2) over(partition by region, education, jobclass order by wage) from wage_data_csv where education = "1\. < HS Grad"
 -- is used to retrieve nth value from the column passed based on partition, above nth value will be none

- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
```

在 Pyspark —

```
# Analytical Window Functions
from pyspark.sql.functions import cume_dist, lag, lead
from pyspark.sql import Window

df = df.withColumn("cume_dist", cume_dist().over(Window.partitionBy("region", "education", "jobclass").orderBy("wage")))
df = df.withColumn("lag", lag("wage").over(Window.partitionBy("region", "education", "jobclass").orderBy("wage")))
df = df.withColumn("lead", lead("wage").over(Window.partitionBy("region", "education", "jobclass").orderBy("wage")))

#df.display()
#df.distinct().display()
df.select("region", "education", "jobclass","wage","cume_dist","lag","lead").distinct().filter(df.education=="1\. < HS Grad").display()
```

我写这只是作为一个参考给我…..

我觉得我的大脑是一本图书馆手册，里面保存了所有概念的参考资料，在某一天，如果它想检索某个概念的更多细节，它可以从手册参考资料中选择这本书，并通过查看它来检索数据。

所以这就是为什么我写…

快乐学习..