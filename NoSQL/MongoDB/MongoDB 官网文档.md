# [MongoDB 官网文档](http://www.mongodb.org.cn/tutorial/)


## 目录(Catalog)
1. MongoDB 是什么？
2. SQL(关系型数据库) 与 MongoDB 对应术语
3. MongoDB 安装注意事项:



## 生词(New Words)
- **aggregation [ˌæɡrɪ'ɡeɪʃən] n.聚合, 聚集**
    + --> aggregation pipeline 聚合管道
- **pipeline ['paɪplaɪn] n.管道；输油管**
    + --> a pipeline across the desert. 穿越沙漠的管道
- **transaction [træn'zækʃ(ə)n] n.(计)事务; 交易**
    + --> transaction cost 交易成本
    + --> transaction volume 交易量
    + --> market transaction 时长交易
- **atomicity [ˌætə'mɪsɪtɪ] n.原子性, 原子数**
    + --> atomicity problem 原子性问题
    + --> The primary concerns in this kind of application are 
     concurrency and atomicity.
    在这种应用程序中, 主要的问题是并发性和原子性. 
- **consistency [kən'sɪst(ə)nsɪ] n.[计]一致性,  一致**
    + --> This is done for consistency and clarity only.
      这样做只是为了一致性和清晰. 
- **isolation [aɪsə'leɪʃ(ə)n] n.隔离, [计]独立性**
    + --> But neither will anything else in isolation.
      但也不会孤立其他任何东西. 
- **durability [ˌdjuərə'biləti] n.持久性, 耐久性**
    + --> How about the durability of product? 产品的耐久性怎么样？
- **theorem ['θɪərəm] n.定理, 法则, 命题**
    + --> I agree with the theorem that the best
     [defence (/dɪ'fens/ n.防御, 防卫) is offence 
     (/ə'fens/ n.攻击, 罪行, 犯罪).
- **partition [pɑː'tɪʃ(ə)n] n.分开, 分割  vt.分开, 分割**
- **tolerance ['tɒl(ə)r(ə)ns] n.公差, 气度, 容忍**
    + --> partition tolerance 分割容忍



## 内容(Content)
### 1. MongoDB 是什么？
- MongoDB 是由 C++ 语言编写的, 是一个基于分布式文件存储的开源数据库系统. 


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
