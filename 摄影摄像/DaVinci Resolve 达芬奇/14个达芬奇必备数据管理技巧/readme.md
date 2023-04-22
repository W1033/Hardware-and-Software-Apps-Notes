# 新手扫盲：14个达芬奇必备数据管理技巧

> 原文：https://zhuanlan.zhihu.com/p/516186706


> Top Tip: 由于笔者是 Mac 电脑，所以快捷键以 Mac 为准。

## ▲ 1. 如何查看达芬奇项目文件存储位置？

比如双击 DaVinci Resolve 打开后，在 `项目管理器面板` 双击 "Untitled Project" 创建一个项目(Project)，进入到项目后首先点击 `Command + s`保存项目，并命名为 "Start learning DaVinCi"，那么这个项目保存在哪里？查找的步骤如下，在当前项目界面右下角点击**项目管理器图标**，如下图：

![image-20230207201941734](readme.assets/image-20230207201941734.png)

在弹出的项目管理器面板中，在数据库上右键，点击在 "访达" 中显示，操作如下图：

<img src="readme.assets/image-20230207202241851.png" alt="image-20230207202241851" style="zoom: 50%;" />

打开访达后，路径如下图：

- 笔者自己电脑的路径如下：`/Users/WANG/Library/Application Support/Blackmagic Design/DaVinci Resolve/Resolve Disk Database/Resolve Projects/Users/guest/Projects/Start learning DaVinCi` 

<img src="readme.assets/image-20230207210555982.png" alt="image-20230207210555982" style="zoom: 56%;" />

 双击 "Resolve Disk Database"，然后继续前进，直到在 Projects 文件夹中，找到以你项目命名的对应文件夹。

默认的顺序为： `../Resolve Projects/Users/guest/Projects`.

在达芬奇中，当你点击"另存项目"时，你的项目文件也会直接被保存在这个位置: `....../BlackMagic Design/ DaVinci Resolve/Support/Resolve Disk Database/Resolve Projects/Users/guest/Projects`.

当你双击任何项目文件夹时，你会发现一个名为"Project.db " 的文件，这就是你项目实际的数据库文件。

所以，只要搞清楚项目文件的路径，你就可以自由复制、移动它们了。

Note: *达芬奇和 PR/AE 这些软件不同，他是根据数据库来保存项目的。后缀是.db的文件是数据库文件，db是datebase(数据库)的缩写。*

## ▲ 2. 在达芬奇中创建一个新的数据库

创建如下图：

- 数据库名称：遵循标准数据库的创建，建议全小写字母和 `_` 组成，不要有空格。
- 位置：选择一个你想要建立数据库的位置，一定要是空文件夹，或者也可以直接创建一个新的文件夹，否则会弹出错误提示。
- 点击"创建"，新的数据库就显示在数据库列表里了

![image-20230207212339615](readme.assets/image-20230207212339615.png)



## ▲ 3. 如何将项目从一个数据库移到另一个数据库？

如果你有许多数据库，每个数据库里又有许多项目。那么如何在数据库之间进行项目转移呢？

1.首先进入"项目管理器"（对，还是那个小房子）。

2.点击"显示/隐藏数据库"图标，选中数据库中的某一个项目。

3.然后右键复制你的项目，再点击切换到另一个数据库，粘贴它就可以了。



~~<p style="color:red;">注：下面一些技巧在影视飓风的达芬奇视频教程里都有，不再重复罗列。</p>~~



## ▲ 4. 如何导出达芬奇项目文件？

## ▲ 5. 如何导入达芬奇项目？

## ▲ 6. 如何在电脑之间移动你的达芬奇项目？

## ▲ 7. 如何在达芬奇中恢复已存档的项目？

## ▲ 8. 如何将达芬奇数据库转移到另一台电脑上？
## ▲ 9. 如何重新连接达芬奇数据库？
## ▲ 10. 如何将时间线从一个项目移到另一个项目？
## ▲ 11. 如何从达芬奇导出时间线？
## ▲ 12. 如何导入达芬奇的时间线？
## ▲ 13. 达芬奇将优化媒体与缓存文件储存在何处？
## ▲ 14. 达芬奇在哪里保存代理文件？