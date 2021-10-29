# PostgreSQL 安装教程

## 生词
- **privilege ['prɪvɪlɪdʒ] --n.特权; 荣幸**
    + It is truly a privilege to be here. 能来此处真是莫大的荣幸.
    + the privileged classes. 特权阶级.
- **schema ['skiːmə]  --n.概要，议程，图解，模式**
    + database schema 数据库模式
    + schema theory. 图式理论
    + a schema of scientific reasoning. 科学推理的图示。
    + Did you overwrite the data schema? 你重写了整个数据模式吗？
    + Yeah, your algorithm is solid. It's a really good schema.
      你的算法很不错，架构相当完美。
---

## (1) PostgreSQL win10 安装教程
- 下载 `https://www.enterprisedb.com/downloads/postgres-postgresql-downloads` 
  右键以管理员身份运行
- 更改 `C:\Program Files\PostgreSQL\10` 到 `C:\PostgreSQL\10`
- 设置密码: `111111`
- 设置地区 (Select the locale to be used by the new database cluster)
    + 选择 "C"
- 完成时取消勾选 "Launch Stack Builder at (退出时启动堆栈生成器)"
- 修改设置文件:
    + 打开 `C:\PostgreSQL\10\data\postgresql.conf`
    + 把 `listen_addresses = '*'` 前添加 # 注释掉, 再添加一行 
      `listen_addresses = 'localhost'`
    + 在左下角的 windows 图标上右键选择 --> `控制面板` --> `管理工具`
      (右上角的 "查看方式" 更改为 "大图标") --> `服务` 找到 "postgresql-x64-10" 用鼠标
      右键进行点击, 然后在弹出的菜单中选择 "启动" 或者 "重新启动". 这样上面修改的 
      listen_addresses 就生效了.
#### Windows 下安装 PostgreSQL 报错：The database cluster initialisation failed.
- 1、第一次安装PostgreSQL报错The database cluster initialisation failed.时，等待
  安装程序结束运行，然后到PostgreSQL的安装后的程序目录下，右击文件夹-属性-安全，给每个
  Window账户都授权修改、读取和运行等权限；
- 2、使用PostgreSQL程序文件夹目录下的uninstall-postgresql.exe卸载程序；
- 3、重新安装PostgreSQL，再选择语言locale 时，选择“C”（网上有很多人建议选择诸如Chinese 
  HongKong等）

####  PgAdmin 
- PgdAdmin 是和 postgreSQL 安装程序一起被安装的, 打开方式点击桌面左下角的 windows
    图标, 找到 PostgreSQL 软件目录, 点击展开后即可看到.
- 使用 pgAdmin 链接远程数据库服务需要注意一下这些问题:
	+ 关闭服务器端机器防火墙
	+ 修改服务器端链接监听 (postgresql.conf 配置文件)
	+  修改链接认证方式 (pg_hba.conf 配置文件)

---
## (2) PostgreSQL Mac 下安装和使用
- 安装: 
    + (1) 下载: Enterprise 下载链接: 
        - `https://www.enterprisedb.com/downloads/postgres-postgresql-downloads`
    + (2) 安装: 
        - 路径可以自定义, 本机在 `/Users/WANG/` 下新建了一个名为 "postgreSQL" 
          的文件夹, 所有要安装的文件都在此文件夹下. 
        - 设置密码和上面 windows 一样为 `111111` 
        - Local (设置地区): `zh_CN.UTF-8` (此处和 windows 不一样, windows 下如果
          选择 zh_CN 后运行就会报错, 哎......)
    + (3) 启动: 
        - 打开 `/Users/WANG/postgreSQL/bin` 文件夹后点击一下名为`psql` 的可执行
          文件 (Tip: 不要双击), 然后按下 `Option + Command + C` 复制当前文件的路径名
         `/Users/WANG/postgreSQL/bin/psql` 
        - 接着在 iTerm 中运行以下代码: 
          `/Users/WANG/postgreSQL/bin/psql -U postgres` (Tip: 这里的启动和
         《SQL基础教程》中 windows 下的启动是差不多的, 只是 windows 下是 `psql.exe`, 
          更详细的笔记见: `chapter00-01.md` 文件)
    - (4) 安装完成后, 如果 iTerm 中运行启动的代码报错, 可以尝试打开安装文件夹点击 
      `uninstall-postgresql.app` 删除重新安装, 此时还有一处需要删除的内容, 要不然再次
      安装会报错; 打开 Finder --> 应用程序 --> 点击上部的查看列表为 `List(三)` 形式 --> 
      找到名为 `PostgreSQL...` 的文件夹后, 点击删除. 方可重新安装.      
- 使用: 
    + (1) 上面安装的步骤 (3) 中在 iTerm 中输入 
      `/Users/WANG/postgreSQL/bin/psql -U postgres` 时, 会让输入安装时设置的密码, 
      输入密码后, 提示: 
      ```sql
        psql (10.10)
        Type "help" for help.

        postgres=#
      ```
      即代表可以正常创建和使用 postgreSQL 创建表了,
    + (2) 在 iTerm 的 `postgres=#` 后接着输入: `create database shop;` (`;` 勿遗漏)
        - 代表创建数据库 (Tip: 和 <SQL 基础教程> 中 windows 下创建数据库是一样的), 
          下面出现 "CREATE DATABASE" 代表创建成功.
        - 接着在 `postgres=#` 后输入 `\q` (quit) 退出 postgres 默认数据库.
        - 然后输入 `/Users/WANG/postgreSQL/bin/psql -U postgres -d shop` 代表
          切换到创建的 "shop" 数据库中. 
        - 接下来创建表 (table) 可以在 pgAdmin 可视化界面中创建. 打开路径 
          `/Users/WANG/postgreSQL` 点击 `pgAdmin4.app` 图标, 在浏览器中就会打开 
          pgAdmin 的可视界面, 此时可以看到在 Mac 的顶部图标栏, 也可以看到 pgAdmin 的
          大象图标, Configure/Restart 都是在图标上右键即可.
        - 回到浏览器中的 pgAdmin 可视界面中, `Databases (2)` 中就已经有我们创建的
          名为 `shop` 的数据库了, 在 shop 上右键点击 `CREATE Script` 在右侧打开的
          编辑界面中,即可编辑创建名为 Product 的表了, 创建语法在 `chapter00-01.md`
          中, 不同平台的 SQL 执行代码都是相同的. (Tip: 编辑窗口里的代码为默认提示代码,
          删除即可.)
        - 写完创建 Product 表的代码后, 点击 `类似于雷电的图标 (Execute/Refresh )`
          执行提示创建成功即可. 
        - 查看 Product 表在: 点击 `shop` --> `Schemas` --> `Tables(1)` --> 
          `product` --> `Columns(6)` 点击右侧的 Properties 即可看到 
        - 向表中插入数据, 在 pgAdmin 中的方式和创建 Product 表的方式一样. 代码见: 
          chapter00-01 --> 下的 `1-6.sql` (Tip: 看到当前窗口下部的 "Message" 下
          提示 COMMIT 就代表提交了.)
        - 然后在再次在 `shop` 上右键点击 `CREATE Script`, 打开的窗口中输入 
          ```sql
            select *
            from Product;
          ```
          执行雷电图标执行按钮, 就可以在下部的 `Data Output` 中看到查询结果.

