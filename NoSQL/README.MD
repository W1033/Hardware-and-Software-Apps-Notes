# NoSQL


## 目录(Catalog)
### 1. 关系型数据库遵循ACID规则
### 2. 什么是 NoSQL?
### 3. CAP定理 (CAP theorem) 
### 4. NoSQL的优点/缺点
### 5. BASE
### 6. ACID vs BASE
### 7. NoSQL 数据库分类



## 生词(New Words)
- **transaction [træn'zækʃ(ə)n] n.(计)事务; 交易**
    + transaction cost 交易成本
    + transaction volume 交易量
    + market transaction 时长交易
- **consistency [kən'sɪst(ə)nsɪ] --n.[计]一致性, 一致**
    + This is done for consistency and clarity only. 这样做只是为了一致性和清晰. 
- **isolation [aɪsə'leɪʃ(ə)n] --n.隔离, [计]独立性**
    + But neither will anything else in isolation. 但也不会孤立其他任何东西. 
- **durability [ˌdjuərə'biləti] --n.持久性, 耐久性**
    + How about the durability of product? 产品的耐久性怎么样？
- **availability [ə,velə'bɪləti] (availa-bility) --n.可用; 有效; 可用性**
    + general availability. 一般利用率
    + water availability. 水资源可利用量.
- **partition [pɑː'tɪʃ(ə)n] n.分开, 分割  vt.分开, 分割**
- **tolerance ['tɒl(ə)r(ə)ns] n.公差, 气度, 容忍**
    + partition tolerance 分割容忍
- **schema ['skiːmə]  --n.概要, 议程, 图解, 模式**
    + database schema 数据库模式
    + schema theory. 图式理论
    + a schema of scientific reasoning. 科学推理的图示. 
    + Did you overwrite the data schema? 你重写了整个数据模式吗？
    + Yeah, your algorithm is solid. It's a really good schema.
      你的算法很不错, 架构相当完美. 



## 内容(Content)
### 1. 关系型数据库遵循 `ACID` 规则
> 事务在英文中是 transaction, 和现实世界中的交易很类似, 它有如下四个特性: 
- 1、A (Atomicity) 原子性
- 2、C (Consistency) 一致性
- 3、I (Isolation) 独立性
- 4、D (Durability) 持久性



### 2. 什么是 NoSQL?
- NoSQL 指的是非关系型的数据库.  NoSQL 有时候也称作 `Not Only SQL` 的缩写,
  是对不同与传统的关系型数据库的数据库管理系统的统称. 
  (Tip: `RDBMS 关系数据库管理系统`(`Relational Database Management System`))
- **NoSQL 用于超大规模数据的存储.**
  (e.g. Google 或 Facebook 每天为它们的用户收集万亿比特的数据). 
  这些类型的数据存储不需要固定的模式, 无需多余操作就可以横向扩展. 

### 3. CAP定理 (CAP theorem) 
 - 在计算机科学中, CAP定理(CAP theorem), 又被称作布鲁尔定理 (Brewer's theorem),
    它指出对于一个分布式计算系统来说, 不可能同时满足以下三点:
    + 一致性(Consistency) (所有节点在同一时间具有相同的数据)
    + 可用性(Availability) (保证每个请求不管成功或者失败都有响应)
    + 分隔容忍(Partition tolerance)
      (系统中任意信息的丢失或失败不会影响系统的继续运作)
- CAP理论的核心是: 一个分布式系统不可能同时很好的满足一致性,
  可用性和分区容错性这三个需求, 最多只能同时较好的满足两个. 因此, 根据 CAP
  原理将 NoSQL 数据库分成了满足 CA 原则、满足 CP 原则和满足 AP 原则三 大类: 
    + `CA` - 单点集群, 满足一致性, 可用性的系统, 通常在可扩展性上不太强大. 
    + `CP` - 满足一致性, 分区容忍必的系统, 通常性能不是特别高. 
    + `AP` - 满足可用性, 分区容忍性的系统, 通常可能对一致性要求低一些. 
  
  <img src="./MongoDB/mongoDB-images/cap-theoram-image.png"
    style="margin-left: 0;">

### 4. NoSQL的优点/缺点
- 优点:
    + (1) 高可扩展性
    + (2) 分布式计算
    + (3) 低成本
    + (4) 架构的灵活性, 半结构化数据
    + (5) 没有复杂的关系
- 缺点:
    + (1) 没有标准化
    + (2) 有限的查询功能 (到目前为止)
    + (3) 最终一致是不直观的程序
- 下表来自这篇[文章](https://www.cnblogs.com/xrq730/p/11039384.html)
  | NoSQL | 代表产品 | 解决关系型数据库的什么问题 | 优点 | 缺点 |
  | :---: | :---: | :---: | :---: | :---: |
  | KV(key-value) 型 | `Redis` | (1) 热点 KV 型数据读写 QPS 高, 读性能受高 OPS 写数据的直接影响. | (1) KV 方式读写性能非常强劲. <br>(2) 原子命令的特点可用于实现分布式锁. | (1) 数据无法持久化. <br>(2) 不支持条件查询. <br>(3) 基于内存, 存储空间有限. |
  | 搜索型 | `ElasticSearch` | (1) 条件查询性能高度依赖索引, 不支持全文搜索. <br>(2) 分库分表后无法对表做全量查询与聚合. | (1) 支持丰富的条件查询, 支持全文搜索. <br>(2) 支持 Group By, 有强大的数据分析能力. <br>(3) 支持海量数据存储 |(1) 硬件成本昂贵. <br>(2) 读取相对于写入有一定延时. <br>(3) 修改字段需要重建表  |
  | 列式 | `HBase`| (1) 海量数据存储后的读写性能低 | (1) 支持海量护具存储, 特别适合数据增长不可预估的场景. <br>(2) KV 方式读写, 性能强劲. <br>(3) 水平扩容方便. (4) 可部署于廉价服务器, 成本低. | (1) 基本没有条件查询能力 <br>(2) 不支持分页查询. <br>(3) 运维复杂. (4) 比较依赖开发者水平, RowKey 设计能力.  |
  | 文档型 | `MongoDB` | (1) 表 Scheme 扩展不方便 | (1) 没有预定义的 Scheme, 可随意变更字段. <br>(2) 命中二级索引的情况下性能不比关系型数据库差, 非索引字段查询对比关系型数据库则是全面胜出. | (1) 没有链表能力. (2) 运维工具还不成熟(目前应该已经成熟了). (3) 占用空间大. |

  Notice: 上面的表中所有的 NoSQL 的缺点都不会体现事务(transaction)这个点,
  因为这是所有 NoSQL 相比关系型数据库共有的一个问题.


### 5. BASE
- `BASE`: Basically Available, Soft-state, Eventually Consistent.
  由 Eric Brewer 定义. 
  
  `BASE` 是 NoSQL 数据库通常对可用性及一致性的弱要求原则:
    + Basically Available --基本可用
    + Soft-state --软状态/柔性事务.  "Soft state" 可以理解为"无连接"的,
      而 "Hard state" 是"面向连接"的
    + Eventual Consistency --最终一致性 最终一致性,  也是是 ACID 的最终目的. 

### 6. ACID vs BASE
|ACID|BASE|
|:---:|:---:|
|原子性(Atomicity)	|基本可用(Basically Available)|
|一致性(Consistency)	|软状态/柔性事务(Soft state)|
|隔离性(Isolation)|	最终一致性 (Eventual consistency)|
|持久性 (Durable)|	|


### 7. NoSQL 数据库分类
|类型|部分代表|特点|
|:---|:---|:---|
|列存储| `HBase` <br>`Cassandra` <br>`HyperTable` | 顾名思义, 是按列存储数据的. 最大的特点是方便存储结构化和半结构化数据, 方便做数据压缩, 对针对某一列或者某几列的查询有非常大的IO优势. |
|文档存储|`MongoDB` <br>`CourchDB`| 文档存储一般用类似json的格式存储, 存储的内容是文档型的. 这样也就有有机会对某些字段建立索引, 实现关系数据库的某些功能.  |
|key-value 存储| `Redis` <br>`Berkeley DB` <br>`MemcacheDB` | 可以通过key快速查询到其value. 一般来说, 存储不管value的格式, 照单全收. (Redis包含了其他功能) |
|图存储| `Neo4J` <br>`FlockDB` | 图形关系的最佳存储. 使用传统关系数据库来解决的话性能低下, 而且设计使用不方便. |
|对象存储| `db4o` <br>`ersant`| 通过类似面向对象语言的语法操作数据库, 通过对象的方式存取数据. |
|xml 数据库| `Berkeley DB XML` <br>`BaseX`| 高效的存储XML数据, 并支持XML的内部查询语法, 比如XQuery,Xpath. |
