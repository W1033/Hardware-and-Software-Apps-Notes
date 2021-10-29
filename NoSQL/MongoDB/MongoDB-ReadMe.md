# MongoDB


[MongoDB 官网文档](http://www.mongodb.org.cn/tutorial/)


## 目录(Catalog)
1. MongoDB 是什么？
2. SQL(关系型数据库) 与 MongoDB 对应术语
3. MongoDB 安装注意事项:



## 生词(New Words)
- **aggregation [ˌæɡrɪ'ɡeɪʃən] --n.聚合, 聚集**
    + aggregation pipeline 聚合管道
- **pipeline ['paɪplaɪn] --n.管道；输油管**
    + a pipeline across the desert. 穿越沙漠的管道
- **transaction [træn'zækʃ(ə)n] --n.(计)事务; 交易**
    + transaction cost 交易成本
    + transaction volume 交易量
    + market transaction 时长交易
- **atomicity [ˌætə'mɪsɪtɪ] --n.原子性, 原子数**
    + atomicity problem 原子性问题
    + The primary concerns in this kind of application are 
     concurrency and atomicity.
    在这种应用程序中, 主要的问题是并发性和原子性. 
- **consistency [kən'sɪst(ə)nsɪ] --n.[计]一致性,  一致**
    + This is done for consistency and clarity only.
      这样做只是为了一致性和清晰. 
- **isolation [aɪsə'leɪʃ(ə)n] --n.隔离, [计]独立性**
    + But neither will anything else in isolation.
      但也不会孤立其他任何东西. 
- **durability [ˌdjuərə'biləti] --n.持久性, 耐久性**
    + How about the durability of product? 产品的耐久性怎么样？
- **theorem ['θɪərəm] --n.定理, 法则, 命题**
    + I agree with the theorem that the best
     [defence (/dɪ'fens/ --n.防御, 防卫) is offence 
     (/ə'fens/ --n.攻击, 罪行, 犯罪).
- **partition [pɑː'tɪʃ(ə)n] --n.分开, 分割  vt.分开, 分割**
- **tolerance ['tɒl(ə)r(ə)ns] --n.公差, 气度, 容忍**
    + partition tolerance 分割容忍
- **schema ['skiːmə]  --n.概要, 议程, 图解, 模式**
    + database schema 数据库模式
    + schema theory. 图式理论
    + a schema of scientific reasoning. 科学推理的图示. 
    + Did you overwrite the data schema? 你重写了整个数据模式吗？
    + Yeah, your algorithm is solid. It's a really good schema.
      你的算法很不错, 架构相当完美. 



## 内容(Content)
### 1. MongoDB 是什么？
- MongoDB 是由 C++ 语言编写的, 是一个基于分布式文件存储的开源数据库系统. 
- Added: 来源为[此文章](https://www.cnblogs.com/xrq730/p/11039384.html) <br>
  MongoDB 是一种文档型 NoSQL 数据库, 什么是文档型 NoSQL 呢? : 文档型 NoSQL
  指的是将半结构化数据储存为文档的一种 NoSQL, 文档 NoSQL 通常以 JSON 或者 XML
  格式存储数据, 因此文档型 NoSQL 是没有 Schema 的, 由于没有 Schema 的特性,
  我们可以随意地存储与读取数据, 因此文档 NoSQL 的出现是
  **解决关系型数据库结构扩展不方便的问题的.**
  
  MongoDB 是文档型 NoSQL 的代表产品, 同时也是所有 NoSQL 产品中的明星产品之一.
  按我的理解, 作为文档型 NoSQL, MongoDB 是一款完全和关系型数据库对标的产品,
  就我们从存储上来看:

  | id | name | age | phone | address |
  | :---: | :---: | :---: | :---: | :---: |
  | 1 | 张三 | 20 | 123456 | 广东 |
  | 2 | 王五 | 26 | 78910J | 深圳 |

  ```json
    {"address": "广东", "phone": "123456", "name": "张三", "id": 1, "age": 20},
    {"address": "深圳", "phone": "78910J", "name": "王五", "id": 2, "age": 26},
  ```
  可以看到, 关系型数据库就是按部就班地每个字段一列存, 在 MongoDB 里面就是一个 JSON
  字符串存储. 关系型数据可以为 name, phone 建立索引, MongoDB 使用 createIndex
  命令一样可以为列建立索引, 建立索引后可以大大提升查询效率. 其他方面而言,
  就大的基本概念, 二者之间也是类似的:
  | 关系型数据库 | MongoDB |
  |:---------:|:---------:|
  | 行 | 文档 |
  | 列 | 字段 |
  | join | 嵌入文档或链接 |

  因此, 对于 MongoDB, 我们只需要理解成一个 Free-Schema 的关系型数据库就完事了,
  他的优缺点比较一目了然. 优点:
    + (1) 没有预定义的字段, 扩展字段容易.
    + (2) 相较于关系型数据库, 读写性能优越, 命中二级索引的查询不会比关系型数据库慢,
      对于非索引字段的查询则是全面胜出.
        - MySQL 使用 B+ 树, 数据都在叶节点上, 每次查询都需要访问到叶节点;
          MongoDB 索引使用 B- 树, 所有节点都有 Data 域,
          只要找到指定索引就可以进行访问.
  
  缺点在于:
    + (1) 不支持事务操作, 虽然 MongoDB 4.0 之后宣称支持事务, 但是效果待观测.
    + (2) 多表之间的关联查询不支持(虽然有嵌入文档的方式), join 查询还是需要多次操作.
    + (3) 空间占用较大, 这个是 MongoDB 的设计问题, 空间预分配机制 +
      删除数据后空间不释放, 只有用 `db.repairDatabase()` 去修复才能释放.
    + (4) 目前没有发现 MongoDB 有关系型数据库例如 MySQL 的 Navicat
      这种成熟的运维工具.
  
  总而言之, MongoDB 的使用场景很大程度上可以对标关系型数据库, 但是比较适合处理那些没有
  join, 没有一致性要求且表 Schema 会常变化的数据.



### 2. SQL(关系型数据库) 与 MongoDB 对应术语
| SQL 术语 |  MongoDB 术语|
|:------|:------|
| `database` | `database` (数据库) |
| `table` (数据库表) | `collection` (集合) |
| `row` (数据记录行) | `document` (文档) |
| `column` (数据字段) | `field` (字段/域) |
| `index` (索引) | `index` (和关系型数据库的索引不太一样) |
| `table joins` (表关联) | `$lookup` (非关系型数据库, 数据的关联查询是其弱项)|
| `primary key` (主键) | `primary key` (MongoDB 自动将 _id 字段设置为主键)|
| `aggregation` (聚合/聚合查询) | `aggregation pipeline` (聚合管道) |
| `transactions` (事务) | `multi-document transactions` (跨文档事务) |

### 3. MongoDB 安装注意事项:
- 1、[下载地址](https://www.mongodb.com/download-center/community)
    + tips: 默认安装包 Package 选择.msi 格式 (.msi 和 .exe 一样是可执行格式)
- 2、安装过程中:
    + 第二个界面选择 Complete(全部)
    + 第三个界面: Install MongoDB as a Service 取消勾选
    + 第四个界面: 左下角的 Install MongoDB Compass(安装 MongoDB 可视化客户端)
      取消勾选(Reason: 这里会链接 MongoDB 美国的服务器)
