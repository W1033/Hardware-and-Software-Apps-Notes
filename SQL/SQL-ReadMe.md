# SQL learning

- [Sql Or NoSql, 看完这一篇你就懂了](https://www.cnblogs.com/xrq730/p/11039384.html)


## Table Of Contents



## New Words



## Content

### 数据库字段命名规范
1. 采用 26 个英文字母(区分大小写)和 0-9 的自然数(经常不需要)加上下划线 `_` 组成，命名简洁明确，多个单词用下划线 `_` 分隔
2. 全部小写命名，禁止出现大写
3. 字段必须填写描述信息
4. 禁止使用数据库关键字，如：name, time, datetime, password 等
5. 字段名称一般采用名词或动宾短语
	+ 名词  示例：user_id    user_name    sex
	+ 动宾短语  示例：is_friend   is_good
6. 采用字段的名称必须是易于理解，一般不超过三个英文单词
7. 在命名表的列时，不要重复表的名称。例如，在名 employe 的表中避免使用名为 employee_lastname 的字段
8. 不要在列的名称中包含数据类型
9. 字段命名使用完整名称，禁止缩写
10. 表中字段是另外一张表的主键，则为表名 + id ，体现关联关系. 示例：user_id
