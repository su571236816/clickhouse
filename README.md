# clickhouse
Springboot clickhouse

![avatar](https://raw.githubusercontent.com/saimen90/clickhouse/master/sql-dbserver.png)

[Dubbo接口文档，查询地址：https://blog.csdn.net/qq_15371293/article/details/117090780]
##  
注意的是只有MergeTree系列的表引擎才支持主键索引，数据分区，数据副本，数据采样这样的特性，只有此系列的表引擎才支持ALTER操作。

MergeTree表引擎在写入一批数据的时候，数据总会以数据片段的形式写入磁盘，并且数据片段不可修改。为了避免片段过多，clickhouse会通过后台的的线程，定期合并这些数据片段，属于不同分区的数据片段会被合并成一个新的片段，这就是MergeTree的基本特点。

MergeTree家族中还有其他表引擎是在它的基础上进行扩展，例如ReplacingMergeTree表引擎具有删除重复数据的特性；SummingMergeTree表引擎则会按照排序键自动聚合数据。加上Replicated前缀，又会得到一组支持数据副本的表引擎，例如ReplicatedMergeTree、ReplicatedReplacingMergeTRee、ReplicatedSummingMergeTree等。可以看出MergeTree是根基，只有吃透了MergeTree表引擎的原理，就能掌握该系列引擎的精髓

## SpringBoot + Mybatis-puls + ClickHouse （分页查询、添加、修改、删除）
