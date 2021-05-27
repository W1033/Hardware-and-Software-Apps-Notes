# 闲聊Windows系统日志


> 文章来源：https://cloud.tencent.com/developer/article/1170984  （有改动）


## Windows系统日志简介

Windows 系统日志为 evtx 格式。

Windows操作系统在其运行的生命周期中会记录其大量的日志信息，这些日志信息包括：

- Windows 事件日志（Event Log），
- Windows 服务器系统的 IIS日志，
- FTP 日志，
- Exchange Server 邮件服务，
- MS [SQL Server](https://cloud.tencent.com/product/sqlserver?from=10680)数据库日志等。

Windows事件日志文件实际上是以特定的数据结构的方式存储内容，其中包括有关系统，安全，应用程序的记录。每个记录事件的数据结构中包含了9个元素（可以理解成数据库中的字段）：
- 日期/时间、
- 事件类型、
- 用户、
- 计算机、
- 事件ID、
- 来源、
- 类别、
- 描述、
- 数据等信息。

应急响应工程师可以根据日志取证，了解计算机上发生的具体行为。

查看系统日志方法，Windows系统中自带了一个叫做事件查看器的工具，它可以用来查看分析所有的 Windows 系统日志。打开事件查看器方法：

win7 系统点击左下角的 windows 图标， 点击 "所有程序" --> "附件" --> "运行"  > 输入：eventvwr 回车，（tip: 不管 win7 还是 win10 快速打开 “运行”窗口的快捷键都是 "win + r"）。使用该工具可以看到系统日志被分为了两大类：

- Windows 日志 
- 应用程序和服务日志

早期版本中 Windows 日志只有:

- 应用程序（Application），
- 安全（Security），
- 系统（System）,
- Setup，

新的版本中增加了 设置 及 转发事件日志（默认禁用）。

系统内置的三个核心日志文件（System，Security 和 Application）默认大小均为20480KB（20MB），记录事件数据超过20MB时，默认系统将优先覆盖过期的日志记录。其它应用程序及服务日志默认最大为1024KB，超过最大限制也优先覆盖过期的日志记录。

![img](https://ask.qcloudimg.com/http-save/yehe-1268449/djve0llm4g.jpeg?imageView2/2/w/1620)

Windows事件日志中共有五种事件类型，所有的事件必须拥有五种事件类型中的一种，且只可以有一种。五种事件类型分为：

1. 信息（Information）

信息事件指应用程序、驱动程序或服务的成功操作的事件。

1. 警告（Warning）

警告事件指不是直接的、主要的，但是会导致将来问题发生的问题。例如，当磁盘空间不足或未找到打印机时，都会记录一个“警告”事件。

1. 错误（Error）

错误事件指用户应该知道的重要的问题。错误事件通常指功能和数据的丢失。例如,如果一个服务不能作为系统引导被加载，那么它会产生一个错误事件。

1. 成功审核（Success audit）

成功的审核安全访问尝试，主要是指安全性日志，这里记录着用户登录/注销、对象访问、特权使用、账户管理、策略更改、详细跟踪、目录服务访问、账户登录等事件，例如所有的成功登录系统都会被记录为“ 成功审核”事件。

1. 失败审核（Failure audit）

失败的审核安全登录尝试，例如用户试图访问网络驱动器失败，则该尝试会被作为失败审核事件记录下来。

事件日志[文件存储](https://cloud.tencent.com/product/cfs?from=10680)位置（Vista/Win7/Win8/Win10/Server2008/Server 2012及之后的版本）

| 类型                    | 事件类型                                                     | 描述                                                         | 文件名                   |
| :---------------------- | :----------------------------------------------------------- | :----------------------------------------------------------- | :----------------------- |
| Windows日志             | 系统                                                         | 包含系统进程，设备磁盘活动等。事件记录了设备驱动无法正常启动或停止，硬件失败，重复IP地址，系统进程的启动，停止及暂停等行为。 | System.evtx              |
| 安全                    | 包含安全性相关的事件，如用户权限变更，登录及注销，文件及文件夹访问，打印等信息。 | Security.evtx                                                |                          |
| 应用程序                | 包含操作系统安装的应用程序软件相关的事件。事件包括了错误、警告及任何应用程序需要报告的信息，应用程序开发人员可以决定记录哪些信息。 | Application.evtx                                             |                          |
| 应用程序及服务日志      | Microsoft                                                    | Microsoft文件夹下包含了200多个微软内置的事件日志分类，只有部分类型默认启用记录功能，如远程桌面客户端连接、无线网络、有线网路、设备安装等相关日志。 | 详见日志存储目录对应文件 |
| Microsoft Office Alerts | 微软Office应用程序（包括Word/Excel/PowerPoint等）的各种警告信息，其中包含用户对文档操作过程中出现的各种行为，记录有文件名、路径等信息。 | OAerts.evtx                                                  |                          |
| Windows PowerShell      | Windows自带的PowerShell应用的日志信息。                      | Windows PowerShell.evtx                                      |                          |
| Internet Explorer       | IE浏览器应用程序的日志信息，默认未启用，需要通过组策略进行配置。 | Internet Explorer.evtx                                       |                          |

表1 事件日志存储位置

提示：%SystemRoot%为系统环境变量，默认值为C:\WINDOWS。

![img](https://ask.qcloudimg.com/http-save/yehe-1268449/vwrwqxsib5.jpeg?imageView2/2/w/1620)

图 EVTX事件日志文件

使用事件查看器工具可以将这些EVTX事件日志文件导出为evtx，xml，txt和csv格式的文件。

## **常见的Windows事件的分析方法**

Windows事件日志中记录的信息中，关键的要素包含事件级别、记录时间、事件来源、事件ID、事件描述、涉及的用户、计算机、操作代码及任务类别等。其中事件的ID与操作系统的版本有关，以下列举出的事件ID的操纵系统为Vista/Win7/Win8/Win10/Server2008/Server 2012及之后的版本：

| 事件ID | 说明                           |
| :----- | :----------------------------- |
| 1102   | 清理审计日志                   |
| 4624   | 账号成功登录                   |
| 4625   | 账号登录失败                   |
| 4768   | Kerberos身份验证（TGT请求）    |
| 4769   | Kerberos服务票证请求           |
| 4776   | NTLM身份验证                   |
| 4672   | 授予特殊权限                   |
| 4720   | 创建用户                       |
| 4726   | 删除用户                       |
| 4728   | 将成员添加到启用安全的全局组中 |
| 4729   | 将成员从安全的全局组中移除     |
| 4732   | 将成员添加到启用安全的本地组中 |
| 4733   | 将成员从启用安全的本地组中移除 |
| 4756   | 将成员添加到启用安全的通用组中 |
| 4757   | 将成员从启用安全的通用组中移除 |
| 4719   | 系统审计策略修改               |

表 常见Windows账户及相关shijain 对照表

五种事件类型中，最为重要的是成功审核（Success Audit），所有系统登录成功都会被标记成为成功审核。每个成功登录的事件都会标记一个登录类型：

| 登录类型 | 描述                                             |
| :------- | :----------------------------------------------- |
| 2        | 交互式登录（用户从控制台登录）                   |
| 3        | 网络（例如：通过net use,访问共享网络）           |
| 4        | 批处理（为批处理程序保留）                       |
| 5        | 服务启动（服务登录）                             |
| 6        | 不支持                                           |
| 7        | 解锁（带密码保护的屏幕保护程序的无人值班工作站） |
| 8        | 网络明文（IIS服务器登录验证）                    |
| 10       | 远程交互（终端服务，远程桌面，远程辅助）         |
| 11       | 缓存域证书登录                                   |

表 登录类型

## **Windows XML 事件日志格式**

系统事件日志主要保存的类型为：*.evtx，*.xml，*.txt，*.csv。对于后三种文件格式已经比较了解，现在分析下evtx后缀额格式。事件日志（evtx）文件是一种二进制格式的文件。

![img](https://ask.qcloudimg.com/http-save/yehe-1268449/q1p5nfygy6.jpeg?imageView2/2/w/1620)

图 evtx文件类型

文件头部签名为十六进制45 6C 66 46 69 6C 65 00（ElfFile\x00）。Evtx文件结构包含三部分：文件头，数据块，结尾空值。文件头由4096字节大小组成，具体的结构如下表：

| 偏移 | 长度 | 值               | 描述         |
| :--- | :--- | :--------------- | :----------- |
| 0    | 8    | “ElFile\x00”     | 签名         |
| 8    | 8    | 第一个数据块     |              |
| 16   | 8    | 最后一个数据块   |              |
| 24   | 8    | 下一个记录标识符 |              |
| 32   | 4    | 128              | 头的大小     |
| 36   | 2    | 1                | 次版本号     |
| 38   | 2    | 3                | 主版本号     |
| 40   | 2    | 4096             | 数据块偏移量 |
| 42   | 2    | 数据块的数量     |              |
| 44   | 76   | 空值             |              |
| 120  | 4    | 文件标志         |              |
| 124  | 4    | 校验和           |              |
| 128  | 3968 | 空值             |              |

表 File Header内容

Windows XML 事件日志大小

事件日志文件大小 = (数据块的数量*65536)+4096。

文件头偏移量为120的数据值为文件标志，该部分的组成如下表：

| 值     | 标识符 | 描述 |
| :----- | :----- | :--- |
| 0x0001 | 已更新 |      |
| 0x0002 | 已填充 |      |

![img](https://ask.qcloudimg.com/http-save/yehe-1268449/lubkp9xkz2.jpeg?imageView2/2/w/1620)

图 File Header文件格式

每个数据块大小为65536字节，数据块的头部标签名为45 6C 66 43 68 6E 6B 00(ElfChnk\x00)，数据块由数据块头部，事件记录，闲置空间，数据块文件头由512字节大小组成，具体结构如下表：

| 偏移 | 长度 | 值                         | 描述           |
| :--- | :--- | :------------------------- | :------------- |
| 0    | 8    | “ElfChnk\x00”              | 签名           |
| 8    | 8    | 第一个事件记录编号         |                |
| 16   | 8    | 最后一个事件记录编号       |                |
| 24   | 8    | 第一个事件记录标识符       |                |
| 32   | 8    | 最后一个事件记录标识符     |                |
| 40   | 4    | 128                        | 指针数据偏移量 |
| 44   | 4    | 最后一个事件记录数据偏移量 |                |
| 48   | 4    | 自由空间偏移               |                |
| 52   | 4    | 事件记录校验和             |                |
| 56   | 64   | 空值                       |                |
| 120  | 4    | 未知                       |                |
| 124  | 4    | 校验和                     |                |

表 Chunk header

![img](https://ask.qcloudimg.com/http-save/yehe-1268449/orw57q210x.jpeg?imageView2/2/w/1620)

图 Chunk Header文件格式

数据块包含多个事件记录，一个事件记录对应一条日志信息。事件记录的的大小及组成如下表：

| 偏移量 | 长度 | 值               | 描述 |
| :----- | :--- | :--------------- | :--- |
| 0      | 4    | “**\x00\x00”     | 签名 |
| 4      | 4    | 事件记录块的大小 |      |
| 8      | 8    | 事件记录标识符   |      |
| 16     | 8    | 事件记录写入时间 |      |
| 24     | …    | 事件记录内容     |      |
| …      | 4    | 尺寸拷贝         |      |

表 Event Record

## **Windows事件日志取证分析注意要点**

Windwos操作系统默认没有提供删除特定日志记录的功能，仅提供了删除所有日志的操作功能。也就意味着日志记录ID（Event Record ID）应该是连续的，默认的排序方式应该是从大到小往下排列。

通过对Windows事件日志的取证分析，取证人员可以对操纵系统、应用程序、服务、设备等操作行为记录，通过关键的时间点进行回溯。

## **事件查看器单条日志记录删除思路**

分析事件记录格式后，了解到Windows系统在解析事件记录日志时，按照Event Record的大小逐条读取日志的内容。假设修改某条日志的长度，使长度覆盖下一条日志，理论上Windows系统解析日志时，就会跳过下一条日志，相当于下一条日志被”删除”。 DanderSpritz中的eventlogedit 就是这个思路，仅仅时修改了程度，实际上并没有删除日志内容。实现思路如下图：

![img](https://ask.qcloudimg.com/http-save/yehe-1268449/koow2m8e4q.jpeg?imageView2/2/w/1620)

图 删除事件记录思路

为了确保修改后的日志文件能够被正确识别，还需要修改多个标志位和重新计算校验和。

![img](https://ask.qcloudimg.com/http-save/yehe-1268449/k748p7x9yi.jpeg?imageView2/2/w/1620)

图 不正确修改事件日志

为了确保不出现如上图所示的错误，总结一下删除单条日志内容的方法：

> 

1. File Header中的Next recordidentifier的值减一（偏移量为24字节）
2. 重新计算File Header中CheckSum（偏移量为124字节）
3. 修改Event Record，找到需删除的记录和需删除前一条记录并计算日志的长度，更新Event Record的Event record identifier
4. 更新ElfChnk，需要修改的内容为：Last event record number，Last event recordidentifier，Last event record data offset，Event recordschecksum，Checksum

根据以上的方式进行删除单条日志是NAS方程式组织的DanderSpritz中的eventlogedit实现方式。实际上只是将信息进行了隐藏，在此基础上，将指定日志的内容清空，就能够实现真正的日志删除。

## **单条日志删除**

准备：测试文件（test.evtx—系统中的Setup.evtx），Winhex，python

下载地址：https://github.com/ByPupil/delete-windows-log

该文件中包含了8条日志，下面演示删除第8条记录的实践过程。使用事件查看器打开确认最后一条事件的EventRecordID，该实验中的值为8。

![img](https://ask.qcloudimg.com/http-save/yehe-1268449/0p42db972p.jpeg?imageView2/2/w/1620)

图 test.evtx文件

1. File Header中的Next recordidentifier的值减一

File Header是整个文件最开始的部分，Nextrecord identifier的偏移量为24(0x18)，其长度为8字节。实验文件test.evtx内容如下：

![img](https://ask.qcloudimg.com/http-save/yehe-1268449/5ov5uxg1iw.jpeg?imageView2/2/w/1620)

图 test.evtx文件内容

Next record identifier的值为0x09。将该值减一0x08 写入。这儿需要提一下的是，该文件的字节序为小端，因此低位会在前面。

1. 重新计算File Header中CheckSum

计算方法：前120字节做CRC32运算，偏移量为124(0x7c)，长度为4。修改后的文件内容如下图：

![img](https://ask.qcloudimg.com/http-save/yehe-1268449/m0w7423mhn.jpeg?imageView2/2/w/1620)

图 修改后的test.evtx

现在提取前120字节的内容：

```javascript
456C6646696C650000000000000000000000000000000000080000000000000080000000010003000010010000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
```

使用python中binascii模块计算CRC32。代码如下：

![img](https://ask.qcloudimg.com/http-save/yehe-1268449/z3uzq96072.jpeg?imageView2/2/w/1620)

图 计算CRC32代码

输出的结果为：0xfb027480，修改文件内容，修改后如下图：

![img](https://ask.qcloudimg.com/http-save/yehe-1268449/imkt4i8ia9.jpeg?imageView2/2/w/1620)

图 修改checksum

1. 修改Event Record

通过find hex values查找2A2A0000，定位到第8条Event Record。该条Event Record的长度为 0x180。如下图：

![img](https://ask.qcloudimg.com/http-save/yehe-1268449/wzo57lnqrw.jpeg?imageView2/2/w/1620)

图 第8条EventRecord

第7条Event Record的长度为0x170。如下图：

![img](https://ask.qcloudimg.com/http-save/yehe-1268449/harhndm5i5.jpeg?imageView2/2/w/1620)

图 第7条EventRecord

计算需要修改的内容长度。新长度为0x170+0x180=0x2f0。由于是删除最后一条记录，所以不需要更新Event record identifier。修改长度的位置有两个，分别为第7条日志的长度和第 8条日志的最尾部。

![img](https://ask.qcloudimg.com/http-save/yehe-1268449/gt1d8uoowi.jpeg?imageView2/2/w/1620)

图 第7条日志

![img](https://ask.qcloudimg.com/http-save/yehe-1268449/5sqgs8yqws.jpeg?imageView2/2/w/1620)

图 第8条日志

1. 更新ElfChnk

搜索ElfChuk关键字，找到对应ElfChuk位置。如下图：

![img](https://ask.qcloudimg.com/http-save/yehe-1268449/4kmtxt70sk.jpeg?imageView2/2/w/1620)

图 Elfchnk

修改如下内容：

Last event record number减1，为0x07

Last event record identifier减1，为0x07

Last event record data offset，为0x13c8

Event records checksum，为0xf403d736

Checksum，为0x7563439c

Event records checksum的数据计算范围：chunk中的事件记录的偏移量是固定的，是从文件头偏移0x1200个字节，意思就是checksum的数据起始位置为0x1200。事件记录的结束位置的计算方式：chunk的起始块地址+ Free space offset= events records data。

Checksum的数据计算范围：是固定地址0x1000-0x1078，0x1080-0x1200 。

修改后的ElfChnk如下图：

![img](https://ask.qcloudimg.com/http-save/yehe-1268449/83wcwye04c.jpeg?imageView2/2/w/1620)

图 修改后的ElfChnk

经过修改后，使用系统自带的事件查看器打开，此时日志文件中最后一条记录被成功删除。

![img](https://ask.qcloudimg.com/http-save/yehe-1268449/mt676uz8m1.jpeg?imageView2/2/w/1620)

图 成功删除单条日志记录

此处讲的是删除最后一条记录的详细过曾，删除第一条和中间的记录在实际操作中会有一些不一样的部分，只要对了解evtx文件的格式，删除evtx格式内容中的记录方法并不唯一。只需要删除对应的数据块，并最终使该文件的校验通过即可。

## **恢复被删除的记录**

使用以上的方式删除单挑记录，其实被删除的数据并没有真正的被删掉，严格意义上讲就是将部分数据进行了隐藏。恢复原本的数据可以使用fox-it的danderspritz-evtx工具，原因就是用删除数据的思路反向恢复就行。使用该工具，确实可以将被删除的数据提取出来，不过恢复的evtx格式的文件并不能被打开。暂时没有研究该代码的实现过程，所以不能下分析具体原因。

工具使用如下图：

![img](https://ask.qcloudimg.com/http-save/yehe-1268449/696v69f8y5.jpeg?imageView2/2/w/1620)

图 danderspritz-evtx使用

恢复数据被导出为xml格式文件，如下图：

![img](https://ask.qcloudimg.com/http-save/yehe-1268449/ykcmr2f0eq.jpeg?imageView2/2/w/1620)

图 该条为被删除的第8条记录

恢复的evtx格式文件打开出错，如下图：

![img](https://ask.qcloudimg.com/http-save/yehe-1268449/mugebcfstr.jpeg?imageView2/2/w/1620)

如果需要将日志真正的删除，可以使用\x00填充被隐藏的数据部分填充。并重新计算相应的checksum。

## **参考链接**

> https://blog.fox-it.com/2017/12/08/detection-and-recovery-of-nsas-covered-up-tracks/ https://github.com/libyal/libevtx/blob/master/documentation/Windows%20XML%20Event%20Log%20(EVTX).asciidoc#2-file-header.asciidoc#2-file-header)

*** 本文作者：TomKing，本文属FreeBuf原创奖励计划，未经许可禁止转载**

本文分享自微信公众号 - FreeBuf（freebuf）

原文出处及转载信息见文内详细说明，如有侵权，请联系 yunjia_community@tencent.com 删除。

原始发表时间：2018-07-03

本文参与[腾讯云自媒体分享计划](https://cloud.tencent.com/developer/support-plan)，欢迎正在阅读的你也加入，一起分享。