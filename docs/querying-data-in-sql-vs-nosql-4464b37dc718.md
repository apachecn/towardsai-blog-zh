# 在 SQL 和 NoSQL 中查询数据

> 原文：<https://pub.towardsai.net/querying-data-in-sql-vs-nosql-4464b37dc718?source=collection_archive---------0----------------------->

## [工程](https://towardsai.net/p/category/engineering)

这两种语言在处理数据库方面有很多相似之处，但是有一些关键的不同之处没有在任何地方记录下来。请注意，这不是一篇关于 SQL DBMS 与 NoSQL 服务器的比较文章，因为该领域已经有许多文章，而是两种语言之间的复杂差异。

# **背景**

PostgreSQL 是一个开源的数据库关系管理系统，而 Couchbase NoSQL 是面向文档的数据库软件包。

Couchbase 是一个面向文档的数据库。面向文档的数据库以文档的形式存储数据，面向文档的数据库系统有很多种，但它们之间的共同点是对文档中的数据进行封装和编码。

面向文档的数据库中通常使用的编码有:

*   XML(E *可扩展标记语言，定义文档编码的一组规则，许多以 XML 形式开发的文档已经被开发为 SOAP、RSS 和 ATOM，它们通常用于表示 web 服务中的任意数据结构*
*   JSON(J *avaScript 对象符号*通常用于带有服务器的 web 应用程序)
*   [YAML](https://yaml.org) ( *又一种标记语言，*一种通常用于配置文件的数据序列化语言)

关系数据库和面向文档的数据库之间的区别在于，关系数据库是基于将数据存储在通常由程序员定义的关系表中的范例，并且单个对象可能跨越几个表。文档数据库在数据库的单个实例中存储给定对象的所有信息，并且每个存储的对象可以彼此不同。这消除了在将数据加载到数据库时对 ORM(对象关系映射)的需要或定义

# 查询中的差异

*   访问一个*列 vs document.node.element*

```
/*SQL*/
**SELECT column** 
/*NoSQL*/
**SELECT document.node.element**
```

*   使用 WHERE 运算符

```
/*SQL*/
**WHERE column IN ()**
/*NoSQL*/
**WHERE document.node.element IN []**
```

*   从时间戳中提取数据

```
/*SQL*/
**SELECT DATE(table.created_at), CAST(va.created_at AS DATE) as date**
/*NoSQL*/
**SUBSTR(document.createdAt,0,10) as date**
```

*   提取当前日期

```
/*SQL*/
**SELECT current_date as current_date**
/*NoSQL*/
**SUBSTR SUBSTR(clock_local(),0,10) as current_date**
```

![](img/d6d17d2f9891553f96567b50ccbda211.png)

**卡米尼托·德尔雷伊**