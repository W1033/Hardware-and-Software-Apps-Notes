# 手机解锁 + Root 教程

笔记来源文章(部分更改)：
> 扒开 Android 刷机 Root 的衣服：https://liaoguoyin.com/2019/android-root
>
> Magisk 



## 目录
1. 为什么刷机
2. 刷机分类
    + 2.1 刷机方式
3. 刷机、Root 流程概述
4. 刷机、Root 细节
    + 4.1 解锁 BootLoader
    + 4.2 刷入第三方 Recovery
5. Root 原理
    + 5.1 获取 Root 权限并管理
        - (1) 获取
        - (2) 管理
        - (3) Magisk
6. 数据清理
7. Tail
8. Refer



## 生词
- **tail `[teɪl]` --n.尾巴；踪迹. v.尾随, 跟踪**
    + Tail call 尾调用
    + tail gas 尾气
    + tail end 末端



## 文章正文

### 1. 为什么刷机


### 2. 刷机分类
#### 2.1 刷机方式


### 3. 刷机、Root 流程概述
1. 申请 Bootloader 解锁
    + 索尼手机官网查看和申请 bootloader 解锁, 官网网址：https://developer.sony.com/develop/open-devices/get-started/unlock-bootloader/
 

2. 下载 Android SDK
https://developer.android.com/studio/releases/platform-tools

3. 下载第三方 Recovery（恢复，复原）：TWRP
    + 下载地址：https://www.mediafire.com/file/sudsbi0ut6d3jry/331_xz2_Premium.gz/file

4. 用手机数据线连接手机按组合键进入 Fastboot 模式，使用 android sdk 内的 adb 命令行下刷入第三方 Recovery：TWRP

5. 下载用来获取 root 权限的软件 Magisk.zip 

6. 刷机方式：
    + (1) 卡刷：按组合键进入 Recovery 模式（TWRP），刷入 SuperSU.zip 或 Magisk.zip 获得 Root 权限，或者刷入 ROM 包.zip 重装手机系统。
    + (2) 线刷：数据线连接手机、电脑，按组合键进入 Recovery 模式（TWRP），在高级选项里开启 sideload 模式，在电脑上 cmd adb sideload *.zip 相比较优点是：不需要把包传到手机内存中）




### 4. 刷机、Root 细节
#### 4.1 解锁 BootLoader
#### 4.2 刷入第三方 Recovery


### 5. Root 原理
#### 5.1 获取 Root 权限并管理
##### (1) 获取
##### (2) 管理
##### (3) Magisk


### 6. 数据清理


### 7. Tail


### 8. Refer









### 1. 解锁 Bootloader 

#### 取得 bootloader 解锁码
Your unlock code for 354985090874813
The result is **05254F7851628DE6**


### 2. 下载上面笔记来源链接中的各个文件

