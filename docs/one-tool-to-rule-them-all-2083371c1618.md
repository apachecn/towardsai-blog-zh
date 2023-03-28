# DBT——统治他们的唯一工具

> 原文：<https://pub.towardsai.net/one-tool-to-rule-them-all-2083371c1618?source=collection_archive---------1----------------------->

数据构建工具(DBT)为您提供更好的数据质量。

![](img/24638ccf3ff1d13f101bcd32c25da8d0.png)

潘卡杰·帕特尔在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上的照片

找出数据的问题是我的专长。我喜欢它。我不断调查为什么从一个来源到下一个来源的数字不匹配，并从根本上解决问题。不幸的是，或者对我来说幸运的是，有许多数据质量问题。

数据质量差的影响是巨大的。根据 Gartner 的数据质量市场调查，2017 年数据质量差的平均年财务成本约为**1500 万美元**。但这还不是最糟糕的。根据麻省理工学院斯隆管理学院的研究，知识工作者浪费了高达 50%的时间来处理数据质量问题，而对于数据科学家来说，这一数字高达 80%，这表明大多数员工因为数据质量问题而无法完成他们的工作。

本文将解释什么是糟糕的数据质量，什么是数据构建工具(dbt ),以及最后，dbt 如何提供帮助。

# 什么是数据质量？

数据质量是确保信息准确和完整的过程。它也被称为数据完整性，指的是如何存储和组织信息，即数据适合使用的程度。

当数据收集或输入不准确或处理、存储或访问不当时，可能会出现数据质量问题。例如，如果文件中的数据不完整，那就是数据质量的问题。如果您不保持记录最新，随着时间的推移，不正确的信息会添加到您的数据库中，并且您的报告的准确性也会受到影响。存储和访问信息时也会出错。

持续监控数据是任何质量保证过程的基石。目标应该是限制错误的数量，这样，数据质量会变得更好。

持续的监控过程应该能够减少错误的数量。这不仅能保持高质量的标准，还能很好地表明流程正在按预期运行。对于商业领袖来说，凭借自己的力量让一项产品或服务取得成功已经够难的了，但如果没有不可靠的数据，这就变得更具挑战性了。

# **什么是数据构建工具(DBT)？**

DBT 是数据转换工作的工具。用户可以在他们喜欢的文本编辑器中编写 dbt 代码，并运行 dbt 命令。代码被编译成原始 SQL，并根据配置的数据仓库执行。

1.  文档— dbt 帮助您编写、编辑和共享 dbt 模型的文档。您可以用纯文本给出每个模型和字段的描述。这些描述，包括像列名和数据类型这样的元数据，可以作为一个网站生成，并与团队的其他成员共享。
2.  测试—dbt 可以通过断言每个模型中的 SQL 应该产生什么结果来检查它们是否有意义。当您从数据集中导入一个现有的模式时，您会得到包括唯一值、对应于另一个模型的值以及特定列表中的值的断言。
3.  种子文件加载器—这些文件可以将原始值映射到更易读的值，或者赋予静态数据。
4.  快照— dbt 提供了一种对某个时间点的原始数据进行快照的机制。

关于这个库的更多信息在他们的 [*介绍页面。*](https://docs.getdbt.com/docs/introduction)

# **是否有其他与 dbt 集成的软件包可以最大限度地发挥优势？**

## 1.dbt-codegen⁴

如果您还没有开始设置您的 dbt 模型，这个库将帮助您完成这项工作！这个包包含三个宏来帮助建立模型。

*   *generate_source* 为源生成轻量级 YAML。
*   *generate_base_model* 生成基础模型的 SQL，粘贴到文件中。
*   *generate_model_yaml* 生成模型的 yaml，粘贴到 schema.yml 文件中。

## 2.dbt-期望值

在 python 中,“远大前程”是一个共享的、开放的数据质量标准。它帮助数据团队通过数据测试、记录和分析来消除管道债务。”⁵

现在，除了 dbt 之外，我们有了相同的库！这给当前的 dbt 库增加了额外的测试。如果你想看所有的列表，请点击查看！

## 3.dbt _ 度量

该宏基于指标生成查询。您可以通过几种不同的方式来完成，包括比较一个时期与另一个时期的指标、平均指标或累计指标，或者累计指标。

*这也将很快在 dbt 服务器上实现，更多信息请访问*[*dbt _ metrics*](https://github.com/dbt-labs/dbt_metrics)*。*

# 设置 DBT 项目

我的特定设置将包括三种模式“导入”、“基本”和“聚合”。这些模式中的每一个都有相同的表，dbt 将这些标签称为“模型”，将文件夹标记为“模型”文件夹，导入目录、基本目录和聚集目录都位于其中。

```
.
├── analysis
├── data
├── macros
├── models
│   ├── import
|   ├── base
│   └── aggregated
├── snapshots
└── tests
```

我将使用由 [*dbt-codegen*](https://github.com/dbt-labs/dbt-codegen) 包提供的命令。您可以使用以下命令轻松设置源文件:

```
dbt run-operation generate_source --args 'schema_name: base' > models/import/customers.yml
```

您可以添加额外的参数，如 database_name、generate_columns(这是我绝对推荐的！)、include_descriptions、table_pattern 或 exclude。

然后，我们可以获得模型 SQL 文件。

```
dbt run-operation generate_base_model --args '{"source_name": "base", "table_name": "customers"}' > models/base/customers.sql
```

最后，是实际的 YML 模型文件。

```
dbt run-operation generate_model_yaml --args '{"model_name": "customers"}' > models/base/customers.yml
```

由此产生的客户。YML 看起来会像这样:

```
version: 2

models:
  - name: customers
    columns:
      - name: customer_id
        description: "The Id for customers"
      - name: customer_name
        description: "The actual name of the customer"
```

现在我们可以添加测试。

```
version: 2

models:
  - name: customers
    columns:
      - name: customer_id
        tests:
          - unique
          - dbt_expectations.expect_column_values_to_be_between:
               min_value: 0
               max_value: 10
      - name: customer_name
        description: "The actual name of the customer
```

第一个测试是已经作为库的一部分的唯一性测试，而第二个测试是 dbt_expectations 测试的一部分。

可以实现更多的宏来检查您的数据是否与预期相符。如果这些宏都不能满足您的需要，您可以编写自己的宏。

通过实现 dbt 和这些额外的宏，您可以提高洞察力和数据质量。

```
**References**
1\. [https://www.gartner.com/smarterwithgartner/how-to-stop-data-quality-undermining-your-business](https://www.gartner.com/smarterwithgartner/how-to-stop-data-quality-undermining-your-business)
2\. [https://sloanreview.mit.edu/article/seizing-opportunity-in-data-quality/#:%7E:text=One%20consequence%20is%20that%20knowledge,go%20as%20high%20as%2080%25.&text=In%20fact%2C%20only%2016%25%20of,use%20to%20make%20important%20decisions](https://sloanreview.mit.edu/article/seizing-opportunity-in-data-quality/#:%7E:text=One%20consequence%20is%20that%20knowledge,go%20as%20high%20as%2080%25.&text=In%20fact%2C%20only%2016%25%20of,use%20to%20make%20important%20decisions).
3\. [https://docs.getdbt.com/docs/introduction](https://docs.getdbt.com/docs/introduction)
4\. [https://github.com/dbt-labs/dbt-codegen](https://github.com/dbt-labs/dbt-codegen)
5\. [https://greatexpectations.io/](https://greatexpectations.io/)
6\. [https://docs.getre.io/latest/docs/introduction/whatis](https://docs.getre.io/latest/docs/introduction/whatis)
```