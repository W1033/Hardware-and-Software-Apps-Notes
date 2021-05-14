# Sony Xperia XZ2 Premium



## TOC




## New Words




## Content

**Useful key combinations**
- Flash key: Volume down
- Fastboot key: Volume up*
- Recovery mode key: Volume down + Power key



### 如何在Windows 10上安裝Flashtool Driver?

> 来源： https://reat0ng.pixnet.net/blog/post/1396180
- flashtool 只适合 2017 年前的 Sony 手机。 所以 2017 后的无需安装。





###  如何确定 Sony 手机申请解锁 Bootloader 后是否解锁？

Dial *#*#7378423#*#* . Then go to -> "Service Info" -> "Configuration". If there is:
- Bootloader unlock allowed - Yes << this means that your Bootloader is Locked
- Bootloader Unlocked - Yes << this means that your bootloader is unlocked



### 记录错误：

#### 1. How to fix FAILED (status read failed (Too many links))

- https://www.droidwin.com/fix-status-read-failed-too-many-links/


#### 2. Writing 'recovery' FAILED (remote: 'No such partition.')

**Tip: 这个问题的最好解决方法，就是在刷机前拔掉内存和和 SIM.**

We actually do not have a recovery partition. You want to flash it to your current boot slot.

Do this: `fastboot getvar current-slot` this will return your  `<letter>`
> 使用 Android 的 fastboot 指令查詢 android 裝置目前使用那個槽(a/b)，知道是哪個槽後，比較能確定之後要燒錄哪個槽。
> 查詢目前使用那個槽(a/b)， 看目前的slot是 a 還是 b，一般都是 a。(tip：但是我的 sony xz2p 却是 b， 但是拔掉内存卡后就变成了 a)
> `$ sudo fastboot getvar current-slot`

then do: `fastboot flash boot_<letter> <filename>.img` (tip：twrp.img 是提前已经拷贝到机身可存储内存中了。)

You can continue forward.

#### 3. Twrp Stuck At "swipe To Unlock" （TWRP 卡在主界面）

这个应该是刷入的 Recovery 方式不对或者是版本不对，需要清除：

```shell
fastboot erase boo_a cache
fastboot reboot-bootloader
```

you are in recovery, you need to go to bootloader, so either:

**adb reboot bootloader**

or if that doesn't work

*Force reboot*: press and hold POWER + VOLDOWN (under a bright light, not kidding!!), after about 5 seconds or so buttons should start blinking, and after 30 seconds or so, the phone will reboot, let go of POWER, but keep holding VOLDOWN to get back to bootloader.
(you may need to try 2 or 3 times to get it right)

|

|

通过上面的 `fastboot erase boo_a cache` 之后，手机彻底变成砖了`^_^`.





### 下载 XZ2P 的 Recovery TWRP
**Important Hint:** 经过几十次的反复验证， 只有下面这个网址中的 TWRP 可以使用：

+ http://www.mediafire.com/file/sudsbi0ut6d3jry/331_xz2_Premium.gz/file

这个压缩包， 已经放到百度云盘 `#手机` 文件夹中了

> 链接：https://pan.baidu.com/s/1MHjxEjfiNlcWJzEuzT00ng 
> 提取码：j4ys 

下载完解压后， 把 `twrp-xz2p.img` 和 `vbmeta.img` 复制到 `platform-tools` 文件夹内，执行下面的 adb 命令

```shell
fastboot flash boot twrp-xz2p.img
fastboot --disable-verity --disable-verification flash vbmeta vbmeta.img
```







## 索尼手机如何刷机

完整文章讲解： https://zhuanlan.zhihu.com/p/187551676

### 1. 准备所需要的的安装包

1. 驱动工具 flashtool -- 已经安装。
2. 强刷工具 newflasher -- 已经安装。
3. 强刷固件 -- 已经通过百度云下载。
4. 手机解锁工具 -- 已经通过百度云下载。
5. adb 工具 -- Android Developers 已经安装
    + tip: 相关配置见统计目录的另外一个文件。
6.  TWRP -- 已经下载

### 2. 设置电脑安装驱动环境

1. Win7直接安装，win8/10请百度如何禁止系统强制签名 
2. 安装 flashtool 
3. 更多见下文



提示： TWRP 正确刷入之后， 手机连接电脑后就可以识别到手机了，此时手机里还没有系统，所以还需要下载 ftf 系统拷贝到手机内存中， 然后再使用 TWRP 安装 install









# 索尼手机（XZ1C ）简易解锁与刷机教程

[![孤独的旅行者](https://pic4.zhimg.com/v2-f3e6b394b5513df4ccc839c650f2c72d_xs.jpg?source=172ae18b)](https://www.zhihu.com/people/gu-shi-da-wang-titans)

[孤独的旅行者](https://www.zhihu.com/people/gu-shi-da-wang-titans)

怕是不对的

12 人赞同了该文章

*机锋论坛也要关了，有的刷机资料没地方放，就扔知乎了。关注我的不要生气哈哈。*

原文在这里[Sony Xperia XZ1/XZ1 Compact安卓论坛 机锋论坛](https://link.zhihu.com/?target=http%3A//bbs.gfan.com/forum.php%3Fmod%3Dviewthread%26tid%3D9655135%26extra%3Dpage%3D1%26filter%3Ddateline%26orderby%3Dlastpost%26dateline%3D7948800%26typeid%3D12927%26dateline%3D7948800%26typeid%3D12927%26orderby%3Dlastpost) 当然，已经看不见了。

本人小白一个，之前只接触过小米的刷机，没曾想索尼的刷机有些麻烦，在摸索了三天碰了很多次失败之后终于成功将老的XZ1C刷机，在这里我写一个简单的教程希望能减少后来的朋友们刷机碰到的问题。本人的刷机过程参考了很多机锋的帖子，感谢那些素未相识的坛友。

整个过程仅供参考,大家可以根据自己的需求选择。理论上除了新的X1,X1MK2都可以采用这个方式去刷机。另外像lineage os ，havoc-os都算不错的选择，而且更新到安卓11，速度很快，更多ROM还是要去xda自己多翻翻。

[Sonyforum.xda-developers.com![图标](https://pic4.zhimg.com/v2-07b15ca53466b3762c684b1e3987ceff_180x120.jpg)](https://link.zhihu.com/?target=https%3A//forum.xda-developers.com/c/sony.12026/)

全文一共20个步骤，第一次折腾一圈大概需要2-3小时，想要一边看一边刷机的请确保有时间。

另外日版索尼少问，问就是孤儿锁区，也不要问能不能刷包，你能解锁就能刷，不能解锁不要问，刷了出问题也不要问，总之日版没人管，实属管不了。



**1. 准备所需要的安装包**

**官方或者汉化二选一即可。**

**（1）驱动工具 flashtool**

英文通用新版：

[Windows - Downloads - Flashtool](https://link.zhihu.com/?target=http%3A//www.flashtool.net/downloads_windows.php)

汉化可用旧版：

[http://pan.baidu.com/s/1jI6RLXk](https://link.zhihu.com/?target=http%3A//pan.baidu.com/s/1jI6RLXk) 提取码：bldo



**（2）强刷工具newflasher （如果连接国外网络通畅可以不需要）**

英文通用新版：

[https://pan.baidu.com/s/19_AS3H-sQEhoUd8G339gEw](https://link.zhihu.com/?target=https%3A//pan.baidu.com/s/19_AS3H-sQEhoUd8G339gEw) 提取码：NEWF

汉化可用旧版：

[https://pan.baidu.com/s/1jIviL2Q](https://link.zhihu.com/?target=https%3A//pan.baidu.com/s/1jIviL2Q) 提取码：tbny



**（3）强刷固件**

可以通过flashtool自带的XPERIFIRM下载，这里提供近几代Xperia手机的各版本全套固件。

[https://pan.baidu.com/s/1diFpeNsQd80Sf-3HQaXRtQ](https://link.zhihu.com/?target=https%3A//pan.baidu.com/s/1diFpeNsQd80Sf-3HQaXRtQ) 提取码：yyni



**（4）手机解锁工具**

[https://pan.baidu.com/s/1Vs387_8xIsdUwwhRxm9xWQ](https://link.zhihu.com/?target=https%3A//pan.baidu.com/s/1Vs387_8xIsdUwwhRxm9xWQ)



**(5)Abd工具**

官方abd

[SDK Platform Tools 版本说明 | Android 开发者 | Android Developers](https://link.zhihu.com/?target=https%3A//developer.android.com/studio/releases/platform-tools.html)

个人修改一键abd

[https://pan.baidu.com/s/10n_sN0T0wV9ugmDDaW9Gmw](https://link.zhihu.com/?target=https%3A//pan.baidu.com/s/10n_sN0T0wV9ugmDDaW9Gmw) 提取码：NEWF



**(6)TWRP**

官方TWRP

[TWRP](https://link.zhihu.com/?target=https%3A//twrp.me/)

马少 XZ1C/XZ1/XZP 适用TWRP

[https://pan.baidu.com/s/1a_w1RgeB1pJjwzg5Q0lZfQ](https://link.zhihu.com/?target=https%3A//pan.baidu.com/s/1a_w1RgeB1pJjwzg5Q0lZfQ) 提取码：xrrp



**2.** **设置电脑安装驱动环境**

（1）Win7直接安装，win8/10请百度如何禁止系统强制签名

[Win10专业版如何禁用驱动程序强制签名？](https://link.zhihu.com/?target=https%3A//baijiahao.baidu.com/s%3Fid%3D1671282617582172457)

以WIN10为例 右键-个性化-主页-更新与安全-恢复-立刻重启-疑难解答-高级选项-启动设置-重启-点击数字键7

电脑重启后进入禁止系统强制签名模式，再次重启会取消该状态，因此我们需要在重启之前折腾完所有事情，否则在安装最后一步的时候提示谷歌驱动安装失败。

（2）安装FlashTool，安装完成后到X:\Flashtool\drivers 下找到Flashtool-drivers.exe，安装。（X为当前安装盘符，默认是C盘，用完就可以删除没有影响）

![img](https://pic3.zhimg.com/80/v2-24950c7d1dcb5e029a5a40b630b48892_720w.jpg)

我们只需要点击安装前两项，后面都是比XZ1更老的索尼手机驱动，没有安装必要性。

安装Flashtool-drivers时，提示Windows安全选项，选择使用安装此驱动软件。

安装完成后手机插入电脑才会被正确识别。



**3. 获取手机IMEI号**

（3）先把手机插入电脑，把需保存资料转出或云端备份，刷系统后旧资料全部消失

（4）手机登录google账户，如果没有就需要使用梯子一类的软件让自己注册一个

（5）打开系统设置-系统-关于手机-点击版本号7次，此时提醒你开发者模式已打开，进入开发者选项，往下拉一点点就能看到OEM解锁，把这项点开。（如果没登录账号OEM这项会找不到）

（6）从开发者模式退出来，点击设置-用户和账户-google账户-移除账户，点击google play商店，如果提示你登录账户就可以进行下一步。（注意，此步骤非常重要，除非四清）

（7）手机打电话界面，输入*#06#，把第一行较长的IMEI号记录下来，关机。



**4. 用电脑解锁设备**

（8）使用梯子，选择全局代理模式，打开浏览器，登录索尼官方解锁申请网页

[https://developer.sony.com/develop/open-devices/get-started/unlock-bootloader/](https://link.zhihu.com/?target=https%3A//developer.sony.com/develop/open-devices/get-started/unlock-bootloader/)

在最下面的Device处选择你的设备型号，输入刚才的IMEI 号，勾选前两项带蓝色的字，点击submit。

（9）如果此时显示的是数字加字母的验证码说明你的梯子有问题，此时完全无法输入，无法进行下一步。如果是图片验证码要求你点击看到的图片，说明一切正常，过了验证之后会给你一个长长的解锁码，复制粘贴到一边，一会会用。

![img](https://pic3.zhimg.com/80/v2-9da11a0fd4a5c78d632d4b2f53fe407a_720w.jpg)





**5.更新固件**

（10）方法1：Flashtool

首先确定下载的文件为ftf格式。第三方改过的可能是是zip/rar格式，可以解压后把boot文件夹中boot_delivery.xml剪切回上级菜单，然后重新打包成zip,后缀改为ftf格式。

很多刷机不推荐Flashtool按装强刷固件是因为需要连接github下载全部验证文件，如果国外网络链接不顺畅，很难下载完，如果顺畅使用flashtool就可以了。具体可以参见下面连接，很简单。

[索尼Xperia XZ刷机教程_Sony XZ强刷官方FTF系统包www.netded.com![图标](https://pic1.zhimg.com/v2-3dd18e1bfefc6ccac29060fdc9ebb8b8_180x120.jpg)](https://link.zhihu.com/?target=https%3A//www.netded.com/a/jingpinshouji/2016/0928/32177.html)

![img](https://pic2.zhimg.com/80/v2-5eb47d9b1f9ff0b1cbee690a7e7a7f39_720w.jpg)



（10）方法2：newflasher

首先将下好的强刷固件改后缀从ftf为zip。

解压后检查boot文件夹里面的文件后缀名，需要将.sinb改为sin以及把tab改为ta，并将根目录的boot_delivery.xml剪切到boot文件夹里面，并将newflasher到固件同目录。检查固件内是否带simlock，有就去掉，否则会锁SIM卡。

最终效果应该是这样

![img](https://pic2.zhimg.com/80/v2-4d40ae3d59f4549df5cffa5456b74739_720w.jpg)

双击newflasher.exe并按照提示刷强刷固件

![img](https://pic3.zhimg.com/80/v2-2d056b3bc51aed84abe8f27531f299fe_720w.jpg)

一般会要求点击音量下键2秒，再将手机插入电脑，进入Flash mode，手机指示灯是绿色，这时候松手，然后在电脑上运行newflasher

刷新之后手机会重启，此时手机已经被重置，我们需要把手机关机。



**6.手机解锁**

（11）按住手机音量键上两秒，然后插入电脑，进入Fastboot mode，此时手机信号灯会变蓝，这时候松手，解压刷机工具，点击解锁.bat，复制粘贴刚才记下的解锁码，完成解锁。

此时可以重新开机，开机的时候会多出来一个解锁提示，这说明解锁成功。


**7.安装第三方recovery（TWRP）**

（12）然后我们再关机，按住手机音量键上两秒，然后插入电脑，此时手机信号灯会变蓝，这时候松手。

（13）我们将之电脑前下载好的TWRP压缩包解压,里面会有个img文件，重新好记住的名，或者不管也行。



（14）

方法一：官方ABD

安装abd工具，记住安装的位置，将解压出来的img文件复制粘贴到安装的位置，默认是C:\Program Files x86\Minimal ADB and Fastboot，然后双击文件夹里面的cmd-here文件，

在里面复制粘贴fastboot flash recovery xxx.Img （xxx是解压出来的TWRP.img的名称）

点击回车，一般几秒钟就会成功，只要不显示failed就可以进行下一步。



方法二：个人ABD

我自己通过网上找到的Z3一键刷TWRP包自己重新整合了一下，下载文件后进行解压。

在手机蓝灯连接电脑的条件下运行fastboot.exe，然后将自己下好的rec改名为boot.img替换成文件夹中的同名文件，点击bat文件即可一键安装recovery。

个人文件件集成TWRP3.5.0 for G8441，如果同型号手机直接点击bat文件即可。

（注：为什么安装TWRP第三方recovery？ 答：图像化，简单好用，更新快，方便折腾）



**8.安装系统**

（17）刷完拔掉数据线，等待亮屏，出现索尼LOGO，按住电源和音量下键，进入TWRP模式，如果熟悉英语就继续，不熟悉在第一次滑动的时候有language的选项，可以选择chinese(tradition),然后就是繁体中文界面了。

（18）点击WIPE/清除（右上角的），点击格式化数据/ Format data，输入yes,点击回车，格式化系统后点击返回，点击Reboot/重启，选择power off/关机。

（19）关机后同时按住电源和音量下键，再进入TWRP模式，将手机插入电脑，电脑会识别手机存储，将下载好的系统拉近手机的存储当中，记住放进了哪个文件夹里。

（20）安装，重启

至此，整个刷机流程就结束了。



这里提供马少的安卓9.0XZ1C/XZ1修改版优化版，我个人曾经用过，很完善的国内ROM,增加了一些后续机型的功能。注意该ROM有推广软件，如果不喜欢推广软件可以把安装包解压，将里面推广软件文件夹删除重新打包或者是手机启动后手动删除。

**[https://pan.baidu.com/s/1k-sX__-1h1E7ir0J7Wf-Uw](https://link.zhihu.com/?target=https%3A//pan.baidu.com/s/1k-sX__-1h1E7ir0J7Wf-Uw) 验证码：achy**

如果是马少的系统安装完成后不要重启，需要返回，把Magisk和XperiaPatch两个ZIP文件拖入，先安装Magisk，安装完返回再安装XperiaPatch，安装完XperiaPatch后再重启手机，否则会卡重启。

编辑于 1 小时前

[刷机](https://www.zhihu.com/topic/19568555)

[手机 ROM](https://www.zhihu.com/topic/19567511)

[索尼手机](https://www.zhihu.com/topic/19859169)

赞同 12

12 条评论

分享

喜欢收藏申请转载



- 

## 12 条评论

切换为时间排序

写下你的评论...







发布

- [![黄怀远](https://pic1.zhimg.com/v2-7968034155742e8b16d0b54da2d4ccf2_s.jpg?source=06d4cd63)](https://www.zhihu.com/people/huang-jun-jie-29-85)[黄怀远](https://www.zhihu.com/people/huang-jun-jie-29-85)10 小时前

    你好，请问我是一路ota升级的，刷rom的时候还要强刷一下最新的底包ftf吗

    赞回复踩 举报

- [![孤独的旅行者](https://pic4.zhimg.com/v2-f3e6b394b5513df4ccc839c650f2c72d_s.jpg?source=06d4cd63)](https://www.zhihu.com/people/gu-shi-da-wang-titans)[孤独的旅行者](https://www.zhihu.com/people/gu-shi-da-wang-titans) (作者) 回复[黄怀远](https://www.zhihu.com/people/huang-jun-jie-29-85)1 小时前

    不同ROM针对不同固件版本，自己按照ROM要求对照固件版本。

    赞回复踩 举报

- [![黄怀远](https://pic1.zhimg.com/v2-7968034155742e8b16d0b54da2d4ccf2_s.jpg?source=06d4cd63)](https://www.zhihu.com/people/huang-jun-jie-29-85)[黄怀远](https://www.zhihu.com/people/huang-jun-jie-29-85)回复[孤独的旅行者](https://www.zhihu.com/people/gu-shi-da-wang-titans) (作者)36 分钟前

    解锁前ota升级到最新版，固件也会到最新版吗，马大的应该是固件按照最新版的吧，港版的，昨天用马大微博发的twrp不行，后来更新了官方最新版的twrp就刷上rom了，就是广告程序不知道怎么卸载

    赞回复踩 举报

- [![不吃芹菜](https://pic1.zhimg.com/v2-db6a529874eeba1040940a8f71250444_s.jpg?source=06d4cd63)](https://www.zhihu.com/people/bu-chi-qin-cai-70)[不吃芹菜](https://www.zhihu.com/people/bu-chi-qin-cai-70)05-09

    我忘记XZ1C的开机密码了，也可以使用这一套刷机吗？折腾死我了快。![[捂脸]](https://pic1.zhimg.com/v2-b62e608e405aeb33cd52830218f561ea.png)![[捂脸]](https://pic1.zhimg.com/v2-b62e608e405aeb33cd52830218f561ea.png)试着刷了好几次，都不行，在更新那里一直转圈，进不去主页。求指导。

    赞回复踩 举报

- [你丁丁小别讲话](https://www.zhihu.com/people/ni-ding-ding-xiao-bie-jiang-hua)04-09

    请问，马少这个刷机包日版是不是不能用啊，我刷了直接无信号

    赞回复踩 举报

- [![孤独的旅行者](https://pic1.zhimg.com/v2-f3e6b394b5513df4ccc839c650f2c72d_s.jpg?source=06d4cd63)](https://www.zhihu.com/people/gu-shi-da-wang-titans)[孤独的旅行者](https://www.zhihu.com/people/gu-shi-da-wang-titans) (作者) 回复[你丁丁小别讲话](https://www.zhihu.com/people/ni-ding-ding-xiao-bie-jiang-hua)04-16

    可能是，马少群里刷这个包的没人用日版的，另外这个包里有很多是用的大陆版系统提取的。如果是非日版可以解锁电信卡。

    赞回复踩 举报

- [![有好好喜欢吗](https://pic2.zhimg.com/v2-d34ee29fd7ccd6647ed5190c0ce2c7fb_s.jpg?source=06d4cd63)](https://www.zhihu.com/people/you-hao-hao-xi-huan-ma-83)[有好好喜欢吗](https://www.zhihu.com/people/you-hao-hao-xi-huan-ma-83)03-29

    日版能解锁刷吗？，不是都说do不能解bl。

    赞回复踩 举报

- [![孤独的旅行者](https://pic1.zhimg.com/v2-f3e6b394b5513df4ccc839c650f2c72d_s.jpg?source=06d4cd63)](https://www.zhihu.com/people/gu-shi-da-wang-titans)[孤独的旅行者](https://www.zhihu.com/people/gu-shi-da-wang-titans) (作者) 回复[有好好喜欢吗](https://www.zhihu.com/people/you-hao-hao-xi-huan-ma-83)03-30

    淘宝奸商有的可以付费解锁，具体怎么做的不知道。

    赞回复踩 举报

- [![我是节操呀](https://pic1.zhimg.com/v2-c27bf708f731ebc4e1031093aa81e52a_s.jpg?source=06d4cd63)](https://www.zhihu.com/people/zhen-jie-cao)[我是节操呀](https://www.zhihu.com/people/zhen-jie-cao)02-01

    有日版固件吗

    赞回复踩 举报

- [![孤独的旅行者](https://pic2.zhimg.com/v2-f3e6b394b5513df4ccc839c650f2c72d_s.jpg?source=06d4cd63)](https://www.zhihu.com/people/gu-shi-da-wang-titans)[孤独的旅行者](https://www.zhihu.com/people/gu-shi-da-wang-titans) (作者) 回复[我是节操呀](https://www.zhihu.com/people/zhen-jie-cao)03-03

    固件已经更新，现在有了。

    赞回复踩 举报

- 运气是我实力的全部

    Adb 和twrp的链接失效了

    赞回复踩 举报

- [![孤独的旅行者](https://pic4.zhimg.com/v2-f3e6b394b5513df4ccc839c650f2c72d_s.jpg?source=06d4cd63)](https://www.zhihu.com/people/gu-shi-da-wang-titans)[孤独的旅行者](https://www.zhihu.com/people/gu-shi-da-wang-titans) (作者) 回复[运气是我实力的全部](https://www.zhihu.com/people/yun-qi-shi-wo-shi-li-de-quan-bu)03-22

    ADB提供新的整合一件安装包，TWRP已经更新。

    赞回复踩 举报