---
LINK:
  - ClickHouse
---
## [簡介](https://clickhouse.com/docs/en/home)：

分析型數據庫 不擅長更新刪除等

ClickHouse column-oriented database management system (DBMS)(面向列的數據庫管理系統) for online analytical processing of queries (OLAP) (用於查詢到的在線分析處理)

性能超高

DBMS：

·DDL（数据定义语言）：可以动态地创建、修改或删除数据库、 表和视图，而无须重启服务。 

·DML（数据操作语言）：可以动态查询、插入、修改或删除数 据。 

·权限控制：可以按照用户粒度设置数据库或者表的操作权限，保 障数据的安全性。 ·数据备份与恢复：提供了数据备份导出与导入恢复机制，满足生 产环境的要求。 

·分布式管理：提供集群模式，能够自动管理多个数据库节点。

---

The quickest and easiest way to get up and running with ClickHouse is to create a new service in [ClickHouse Cloud](https://clickhouse.cloud/).

在雲中創建服務

---

### TABLE ENGINES 

##### The table engine determines:

- How and where the data is stored
- Which queries are supported
- Whether or not the data is replicated

There are many engines to choose from, but for a simple table on a single-node ClickHouse server, [MergeTree](https://clickhouse.com/docs/en/engines/table-engines/mergetree-family/mergetree) is your likely choice.

### A Brief Intro to Primary Keys

Before you go any further, it is important to understand how primary keys work in ClickHouse (the implementation of primary keys might seem unexpected!):

- primary keys in ClickHouse are **_not unique_** for each row in a table主鍵對於表中的每一行都不是唯一的

The primary key of a ClickHouse table determines確定 how the data is sorted when written to disk. ⁠主鍵決定了數據在寫入磁盤時的排序方式 Every 8,192 rows or 10MB of data (referred to as the **index granularity****⁠****⁠** **⁠****⁠**索引粒度) creates an entry in the primary key index file. This granularity concept creates a **sparse index** that can easily fit in memory, 這種粒度概念創建了一個可以輕鬆放入內存的稀疏索引and the granules represent a stripe of the smallest amount of column data that gets processed during `SELECT` queries.

The primary key can be defined using the `PRIMARY KEY` parameter. If you define a table without a `PRIMARY KEY` specified, then the key becomes the tuple specified in the `ORDER BY` clause. ⁠如果你定義一個沒有primarykey指定的表，name鍵就變成了order by子句中指定的元組 If you specify both a `PRIMARY KEY` and an `ORDER BY`, the primary key must be a subset of the sort order主鍵必須是排序順序的子集.

The primary key is also the sorting key, which is a tuple of `(user_id, timestamp)`. Therefore, the data stored in each column file will be sorted by `user_id`, then `timestamp`.  主鍵具有排序的功能通常會依據id排序然後是時間順序

---

- [教程](https://clickhouse.com/docs/en/tutorial)让你在一个表中插入 200 万行并编写一些分析查询
- 我们有一个[示例数据集](https://clickhouse.com/docs/en/getting-started/example-datasets/)列表，其中包含有关如何插入它们的说明
- 查看我们关于[ClickHouse 入门的 25 分钟视频](https://clickhouse.com/company/events/getting-started-with-clickhouse/)
- 如果您的数据来自外部来源，请查看我们[的集成指南集合，](https://clickhouse.com/docs/en/integrations/)以连接到消息队列、数据库、管道等
- 如果您使用的是 UI/BI 可视化工具，请查看将[UI 连接到 ClickHouse 的用户指南](https://clickhouse.com/docs/en/integrations/data-visualization/)
- [主键](https://clickhouse.com/docs/en/guides/improving-query-performance/sparse-primary-indexes/sparse-primary-indexes-intro)用户指南是您需要了解的有关主键以及如何定义它们的所有信息

使用C++寫的 列式存儲數據庫使用的SQL操作
