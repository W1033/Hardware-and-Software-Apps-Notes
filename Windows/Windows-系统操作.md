##  Windows 10 系统操作

- 壁纸切换软件: https://johnsad.ventures/software/backgroundswitcher/

- 解决黑域激活后弹出电脑失效的问题:
    + 激活后, 执行 adb tcpip 3035 后再拔线.



1. 如何打开注册表编辑器: Win + R 调出 “运行” 对话框， 输入 “regedit”

1. Windows 系统提示说这些字符不允许用在文件名或者目录中:
    + Tilde (`~`)
    + Number sign (`#`)
    + Percent (`%`)
    + Ampersand (`&`)
    + Asterisk (`*`)
    + Braces (`{ }`)
    + Backslash (`\`)
    + Colon (`:`)
    + Angle brackets (`< >`)
    + Question mark (`?`)
    + Slash (`/`)
    + Plus sign (`+`)
    + Pipe (`|`)
    + Quotation mark (`"`)

1. Win10 调出任务管理器的快捷键: Ctrl + shift + Esc

1. 如何更改 win10 的 powershell 为 cmd ？  <br/>
    (https://www.ithome.com/html/win10/282909.htm)
    答: 打开注册表编辑器，定位至： \HKEY_CLASSES_ROOT\Directory\Background\shell\Powershell\command

1. Win10 禁止軟件開機啟動？
    答: 屏幕左下角 windows 圖標右擊 --> 任務管理器 --> 啟動 --> 找到對應的軟件右擊 "禁止"

1. 在 Windows 10 中显示桌面图标
    答: 依次选择“开始”菜单  >“设置” >“个性化”>“主题”>“桌面图标设置”。

1. 如何删除Windows.old文件夹?
   答: windows10升级后产生的Windows.old文件夹，先按C盘属性-磁盘清理-清理系统文件流程清理一遍，
   剩下Windows.old文件夹残留，手动删除提示“权限不够”不允许删除，再进入该Windows.old文件夹属性授权，但是依然说授权不够。
   了解到您遇到了关于Windows.old文件夹 。该文件夹会在10天后自动删除。您无需手动删除该文件夹。

1. Win10系统 Win+E 快捷键改回打开我的电脑方法
    答: 1、打开“这台电脑”  --> 点击左上方菜单 "查看" --> 在下拉菜单右边打开 "选项" --> 常规 --
    下的 "打开文件资源管理器时打开"点击下拉改为 "此电脑/本机" -- 应用 -- 确定。

1. win10 更改密钥
    答: 桌面"我的電腦"--> 右鍵“屬性” --> 右下角更改密鑰。

1. WIN10系统如何完全获管理员权限
    答:

1. Win10 外接双显示屏遇到的问题？
    答: GTX1060 支持 DVI 和 HDMI 的接口分别外接一个显示器，但是音频线必须要连接在 DIV 接口的显示屏上，
    如果连接在 HDMI 的接口上, 另外一个显示屏提示"电缆没有连接"

1. 设置环境变量:
    答: 此电脑 --> 属性 --> 高级系统设置 --> 高级 --> 环境变量 -->

1. Win10版本号在哪里查看 ？
    答: WIN+R 调出运行工具 --> 输入" dxdiag" 然后回车.

1. Win10 待机不休眠方法:
    答: 桌面右键 --> 个性化 --> (左侧)锁屏界面 --> (右侧)屏幕保护程序设置 --> 更改电源设置 -->
        更改计算机睡眠时间 --> 使计算机进入睡眠状态: 从不。 保存。

1. 打开/关闭 Windows Defender
    答: 选择“开始” 按钮，然后依次选择 “设置”  > “更新和安全” >“Windows 安全中心” > “防火墙和网络保护”。
       选择网络配置文件，然后在“Windows Defender 防火墙”下，将设置切换为“开”或“关”。

1. Win10 字体文件夹路径：
    A: `C:\Windows\Fonts`

1. win10 分屏
    + **一分为二**: 只要在当前的窗口下按 [Widnows 键 + `← / →`]. 窗口就会自动向左或向右
      缩小为原来的一般. 然后你可以选择其他的正在运行的软件或者文档工具, 以填充剩下的空白屏幕.
    + **一分为四**: 在「两分屏」下，你还能通过按下 「Windows 键 + ↑/↓」。开启 第3个窗格
      甚至4个窗格。 每个窗格占 1/4 分屏。换言之，任意一个普通窗口，你想把它放到屏幕左上角，
      作为 1/4 分屏窗口话。只要连续按下 「Windows 键 + ← + ↑」即可   

1. Windows 文本操作快捷键
    - 1、基本操作快捷键
        + `Ctrl + Z`：撤销
        + `Ctrl + Y`：重做
        + `Ctrl + S`：保存
        + `Ctrl + F`：查找
        + `Ctrl + F3`：查找上一个
        + `F3`：查找下一个
        + `Ctrl + R`：替换
    - 2、光标选中快捷键
        + `Shift + ← / → (方向键)`：光标向左/向右选中一个字符
        + `Ctrl + Shift + ← / →` (方向键)：光标向左/向右选中一个单词
        + `Shift + Home`：光标从当前位置一直选中到行首
        + `Shift + End`：光标从当前位置一直选中到行尾
    - 3、光标跳转快捷键
        + `Home`：光标跳转至行首
        + `End`： 光标跳转至行尾
        + `PgUp`：光标跳转至首行
        + `PgDn`：光标跳转至末行
        + `Ctrl + ← / →` (方向键)：光标向左/向右跳转一个单词
        + `Ctrl + Home`：光标跳转至首行首个字符前面(文件开头)
        + `Ctrl + End`：光标跳转至末行最后一个字符后面(文件结尾)

### win 10 常用軟件：
  - 監控軟件 -- wise system monitor
  - 調節色溫 -- f.lux / win10 夜灯功能
  - 清理垃圾:
        + Glary Utilities (http://www.dayanzai.me/glary-utilities.html)
        + TuneUp Utilities
        + Advanced SystemCare
  - 搜索軟件 -- everything / Listary
  - 卸載工具 -- Geek uninstaller
  - 數學公式編輯器 -- Mathtype (一般都是用網頁的，這個實際上並用不到)
  - GIF录屏 -- ScreenToGif
  - 压缩软件 -- Bandizip, 7ZIP
  - 视频播放 -- Potplayer / VLC
  - 下载工具 -- uTorrent, PanDownload, 冰点文库
  - 文件恢复 -- 易我数据恢复向导
  - 剪切板加强工具 -- Ditto
  - pdf 转 word -- ABBYYFineReader / smallPDF
  - 英语词典 -- Google translate + 欧路词典
  - 强制关闭卡死程序 -- superF4
  - nTrun: Win + R 快捷启动工具 (https://zhuanlan.zhihu.com/p/35722313)
  - 跨平台 todolist -- 小黄条
  - Markdown 编辑器 -- Typora


### win10 系统清理
- 用 CCleaner 清理. 下载: http://www.carrotchou.blog/55.html
