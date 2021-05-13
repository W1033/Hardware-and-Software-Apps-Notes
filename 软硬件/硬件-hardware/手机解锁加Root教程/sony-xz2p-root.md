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
- flashtool 只适合 2017 年前的 Sony 手机

### 如何确定 Sony 手机是否解锁？

Dial *#*#7378423#*#* . Then go to -> "Service Info" -> "Configuration". If there is:
- Bootloader unlock allowed - Yes << this means that your Bootloader is Locked
- Bootloader Unlocked - Yes << this means that your bootloader is unlocked



记录错误：

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


#### 3. Twrp Stuck At "swipe To Unlock"
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

