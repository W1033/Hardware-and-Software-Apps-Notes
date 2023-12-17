# VSCode 使用设置

## ▲ VSCode 常用快捷键

> 此段笔记大部分来自：https://zhuanlan.zhihu.com/p/564341329

*Edited: 2023.12.16*

<p style="background-color:#fdeed6; border-radius:6px; padding:20px;"><span style="color:#f79c21;">提示：</span>Command + K, Command + S 打开快捷键一览表（按下 Command 不放, 再按 K + S)</p>

### △ 光标移动

| 功能                      | 快捷键 |
| ------------------------- | -------------- |
| 把光标移动到连续文字/字符的前面？<br />（以空格来分割） | `option` + `←` |
|  | 说明：字符拿汉语和英文 2 种语言来解释：<br />（1）汉语：一段连续的没有空格的汉字（包含中文标点符号），直到一段文字前有空格才会停下来。<br />（2）英文：一般情况下会移动到当前单词的前面，因为一般每个单词之间都是拿空格分隔的。 |
| 移动到连续文字/字符的后面 | `option` + `←`     |
| 移动当前行(上/下) | `option` + `↑`/`↓` |
| 光标移动到行首 | `Command` + `←` |
| 光标移动到行尾 | `Command` + `→` |
| 花括号之间跳转 | `Command` + `shift` +`+` |
| 移动到文档第一行或最后一行 | `Command` + `↑` / `Command` + `↓` |

### △ 选中文本
| 快捷键                              | 功能                                                         |
| ----------------------------------- | ------------------------------------------------------------ |
| `Command` + `Shift` + `←`/`→` | 基于（上面光标移动）单词、行、文档的光标操作加上个 shift 键，<br />就可以移动光标的同时选择文本。e.g.: 下**示例(1)** |
| `Command` + `Shift` + `L` | 选中所有与当前选中内容相同部分 |
| `Command` + `Shift` + `Option` + `←`/`→` | 选中多行文本之后，把光标移动到多行文本的开头或结尾。e.g.: **示例(2)** |

##### 示例(1)：选中多行相同字符后，将光标从选中的位置扩展到当前行的末尾

首先选中第一行的 ``/` 后，使用快捷键 `Command` + `D` 选中接下来的几行，然后按下 **`Shift` + `Command` + `→`** 即可从选中的位置到一行的末尾。

<img src="./ReadMe.assets/image-20231216162220290.png" alt="image-20231216162220290" style="zoom:50%;" />

##### 示例(2): 选中多行文本之后，把光标移动到多行文本的开头

<img src="./ReadMe.assets/image-20231216162033335.png" alt="image-20231216162033335" style="zoom:50%;" />



### △ 添加注释

| 功能             | 快捷键                                         |
| ---------------- | ---------------------------------------------- |
| 单行注释     | `Command` + `/` 或 `Command` + `K, Command` + `C`                 |
| 取消单行注释  | `Command` + `K`, `Command` + `U` (按下 Command 不放, 再按 K + U) |
| 多行注释     | `Option` + `Shift` + `A`                              |

### △ 格式化代码
| 功能           | 快捷键                                                       |
| -------------- | ------------------------------------------------------------ |
| 代码格式化     | `Shift` + `Option` + `F` （formatter)                            |
| 折叠所有代码/字符 | 先按下 `Command` + `K` 再按下 `Command` + `0`(数字0) <br> (Hint: 无需全选文本/字符) |
| 展开所有代码/字符 | 先按下 `Command` + `K`, 再按下 `Command` + `J`                           |
| 格式化选定代码 | 先按下`Command` + `K` 再按下 `Command` + `F`                          |
| 增加/减少缩进     | `Command` + `[` / `]` |

### △ 文件、符号、代码之间的快速跳转

| 快捷键                                                       | 功能                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| `Command` + `P`                                              | **打开最近打开文件列表**，同时列表顶部出现搜索框；直接输入文件名按回车(enter)，在档期窗口打开对应文件；使用 `Command` + `Enter` 在新的编辑器窗口打开此文件。 |
|                                                              | `?`：列出当前可执行的动作<br /><img src="./ReadMe.assets/image-20231217110645478.png" alt="image-20231217110645478" style="zoom: 25%;" /> |
|                                                              | `:`跳转到行数，也可以 `Ctrl+G` 直接进入                      |
|                                                              | `@ `：跳转到 symbol（搜索变量或者函数），也可以 `Ctrl` + `Shift` + `O` 直接进入 |
|                                                              | `@`： 根据分类跳转 symbol，查找属性或函数，也可以 `Ctrl` + `Shift` + `O` 后输入:进入 |
|                                                              | `#`： 根据名字查找 symbol，也可以 `Ctrl` + `T`               |
| `Command` + `G`                                              | 行跳转，输入对应数字回车，可以跳转到当前文件的当前行         |
| `Command` + `P`<br />(输入文件名 + “:” + 行数)               | 跳转到指定文件的指定行数                                     |
| `Command` + `shift` + `O`<br />(字母 o)                      | 调出当前文件的符号（函数名等），使用方向键或者搜索，回车，就能跳转到你想要的符号；如果输入“:”可以对当前文件的所有符号进行分类 |
| `Command` + `T`                                              | 打开多个文件，搜索多个文件中的符号                           |
| `F12` (或加 `Fn`)                                            | 跳转到函数的定义处                                           |
| `Command` + `F12`                                            | 跳转到函数的实现位置。注: js 中没有接口的概念，定义和实现是相同的，所以 JS 中的 `F12` 和 `Command` + `F12` 效果是一样的 |
| `Shift` + `F12`                                              | 打开函数引用的预览（把光标放在函数或者类上，按 Shift + F12 可以打开一个引用列表和内嵌编辑器） |
| 当有多个错误时可以按 `F8` 逐个跳转                           | 跳转到下一个 Error 或 Warning                                |
| ~~`Command + Tab`(同时按住)，继续按着 `Command`键，松开 `Tab`键~~ | 打开当前打开文件的列表，选择要打开文件，松开 Command 就能打开对应文件 |

### △ 全局

| 快捷键 | 功能 |
| ---- | ------ |
| `Command` + `C`           | 复制（未选中文本的情况下，复制光标所在行）|
| `Command` + `X`           | 剪切（未选中文本的情况下，剪切光标所在行）|
| `Command` + `Shift` + `P` 或 `F1` | **显示命令面板** |
| `Command` + `Shift` + `N` | 打开新窗口 |
| `Command` + `W`           | 关闭窗口 |
| `Command` + `K` + `W`     |  关闭所有窗口 |

### △ 查找替换

| 快捷键                    | 功能 |
| ------------------------- | ---- |
| `Command` + `F`                   | 查找 |
| `Command` + `Option` + `F`        | 替换 |
| `Command` + `G`                   | 查找下一个 |
| `Command` + `Shift` + `G`         | 查找上一个 |
| `Option` + `Enter`                | 选中所有匹配项 |
| `Command` + `D`                   | 向下选中相同内容 |
| `Command` + `K`  `Command` + `D`  | 移除前一个向下选中相同内容 |

### △ 显示相关

| 快捷键                            | 功能                                       |
| --------------------------------- | ------------------------------------------ |
| `Command` + `B`                   | 侧边栏(/目录栏)显示/隐藏                   |
| `Command` + `+/-`                 | 字体放大(zoomIn)/缩小(zoomOut)             |
| `Command` + `1/2/3`               | 拆分编辑器（注：把一个编辑器窗口变成 2+ ） |
| `Command` + `Shift` + `←`/`→`     | 切换窗口                                   |
| `F11`                             | 全屏                                       |
| `Command` + `Shift` + `G`         | 显示 Git                                   |
| `Command` + `Shift` + `F`         | 全局查找文件                               |
| `Command` + `K` / `Command` + `T` | 快速切换主题                               |
| `Command` + `Shift` + `D`         | 显示 Debug                                 |
| `Command` + `Shift` + `U`         | 显示 Output                                |



### △ 进阶


| 快捷键 | 功能 |
| ------ | ---- |
| `Command` + `Shift` + `K` | 删除当前行 |
| `Command` + `Shift` + `x` | 裁剪尾随空格(去掉一行的末尾那些没用的空格)  |
|  |  |
|  |  |
|  |  |










## ▲ VSCode 中使用正则表达式给 MD 文档内添加空格

### (1) 给中文和英文中间添加空格



### (2) 在数字前添加空格

<img src="ReadMe.assets/image-20220828163140573.png" alt="image-20220828163140573" style="zoom: 40%;" />

正则表达式的讲解见：`Github-clone/DataStructure-Algorithm-Learning/正则表达式/正则表达式-特殊字符.md`

### (3) 给一些特定格式的文字添加统一后缀

<img src="ReadMe.assets/image-20221108093239148.png" alt="image-20221108093239148" style="zoom:67%;" />



### (4) 把中文后面的空格替换为逗号

正则匹配中文字符：

- `([\u4e00-\u9fa5])\u0020`

> ##### 三种空格 unicode (\u00A0, \u0020, \u3000)表示的区别
> 1. 不间断空格 `\u00A0`，主要用在office中，让一个单词在结尾处不会换行显示，快捷键 ctrl + shift + space ;
> 2. 半角空格(英文符号) `\u0020`，代码中常用的;
> 3. 全角空格(中文符号) `\u3000`，中文文章中使用;

![image-20230601205318185](./ReadMe.assets/image-20230601205318185.png)





## ▲ 1. Mac 和 Win 下的通用设置

### 1.1 快捷键

- 显示所有命令面板(show all commands): `Ctrl + Shift + p`(Windows) / `Command + Shift + p`(Mac) 
- 更该默认设置: `File` -> `Preferences` --> `Settings`

### 1.2 更改英文为中文
- 使用 Ctrl + Shift + P 调出所有命令行面板，输入 configure display language 安装中文包

### 1.3 调出 `settings.json` 编辑文件
- File -> Preference -> Settings -> 点击左上角的 `{}` 图标。

### 1.4 VSCode 打开多个项目
- Windows 下 `control + Shift + N`
- Mac 下 `command + Shift + N` 

### 1.5 VSCode 设置每行代码的长度: 
- 在 setting.json 的规则内添加:  `editor.rulers:[80]` ，添加完毕之后右侧就会自动出来达到 80 个字符的时的竖线

### 1.6 关闭 VSCode 右侧缩略图 (预览面板):

- 在 settings.json 中添加: `"editor.minimap.enabled": false,`

### 1.7 关闭 VSCode 自动换行

- settings.json 中添加 `"editor.wordWrap": "off"`

### 1.8 如何打开终端?
- 1、快捷键: `control + `(esc 下的那个按键)`
- 2、View --> Terminal

### 1.9 修改终端中的字体

- `"terminal.integrated.fontSize":14,`
- `"terminal.integrated.letterSpacing":1,`

### 1.10 Visual Studio Code 修改文件树缩进
- `"worKbench.tree.indent": 24,`

### 1.11 隐藏/显示 左侧的 activity bar (活动栏)

- Explorer (Ctrl + Shift + E) 探测器 (项目 文件)
- Search (Ctrl + Shift + F) 搜索
- Source Control (Ctrl + Shift + G): 代码控制工具 (Git: 可以查看修改了多少个文件)
- Debug (Ctrl + Shift + D) 调试
- Extensions (Ctrl + Shift + X) 插件扩展
   (横向拖动变宽在 Extensions 栏可以搜索内容的图标)

### 1.12 隐藏/显示 左侧的 side bar (侧边栏)
右上角 `view -> Appearance -> Show activity bar`

快捷键
+ Windows 下: `Ctrl + b`
+ Mac 下: `command + b`

### 1.13 快速生成文件模块
快速生成 HTML 模版:  在当前文件中输入`!` 然后按下 `Tab` 按键

### 1.14 查找某个函数在哪些地方被调用了
比如我已经在 `a.js` 文件里调用了 `foo()` 函数. 那么, 如果我想知道 `foo()` 函数在其他文件中是否也被调用了, 该怎么做呢？

做法如下: 在 `a.js` 文件里, 选中 `foo()` 函数 (或者将光标放置在foo()函数上), 然后按住快捷键 `Shift + F12`, 就能看到 `foo()` 函数在哪些地方被调用了, 比较实用. 

### 1.15 鼠标操作
- 在当前行的位置，鼠标三击，可以选中当前行。
- 用鼠标单击文件的行号，可以选中当前行。
- 在某个行号的位置，上下移动鼠标，可以选中多行。

### 1.16 创建多层子文件夹:
我们可以在新建文件夹的时候，如果直接输入, 比如 `aa/bb/cc` 的类似格式即可.

### 1.17 `.vscode` 文件夹的作用
如果你发现项目的根目录下有一个.vscode文件夹，说明这个文件夹代表的是当前项目的配置。

这个文件夹里可能包含以下集中文件: 
+ `settings.json`: 工作空间设置。只针对当前项目有效。比如说，我可以在这里面要求当前项目的代码统一使用制表符，而不需要要求每一位码农去修改各自的配置文件。
+ `sftp.json`: ftp文件传输的配置。



## ▲ Mac 下设置

### 2.2 Mac 下 `settings.json` 基本设置

```json
    {
        // - 粘贴到 vscode 的 settings.json 中时记得删除这些注释,
        // - ☆☆☆ 不用删除, vscode 中可以存在, 不报错
        "worKbench.iconTheme": "vscode-icons",
        "editor.rulers":[80],
        "editor.cursorStyle": "line",
        "editor.fontSize": 13,
        "editor.fontWeight": "400",
        "window.zoomLevel":0,
        "editor.wordWrapColumn": 80,
        // - 改完代码后立即自动保存. `onFocusChange` 是当光标离开该文件后,
        //   这个文件自动保存. 
        "files.autoSave": "afterDelay",
        // - 保存代码后, 默认不会立即进行代码的格式化.
        "editor.formatOnSave": false,
        "editor.lineHeight": 24,
        // - 自动检测(默认开启): VS Code 会根据你所打开的文件来决定该使用空格还是制表。
        //   也就是说，如果你的项目中使用的都是制表符，那么，当你在写新的代码时，
        //   按下tab 键后，编辑器就会识别成制表符。
        "editor.detectIndentation":false,
        // - 一个制表符默认等于 4 个空格.
        "editor.tabSize": 4,
        "terminal.integrated.fontSize":13,
        "diffEditor.renderSideBySide": false,
        // - 关闭左侧的缩略地图
        "editor.minimap.enabled": false,
        "marKdown.preview.fontSize": 13,
    
        // - 关闭代码片段提示
        "editor.quicKSuggestions": {
            "other": false,
        },
        // - 关闭参数提示
        "editor.parameterHints.enabled": false,
        "editor.wordBasedSuggestions": false,
        "editor.snippetSuggestions": "none",
    
        // - 设置 flow 
        "flow.useNPMPacKagedFlow": true,
        "javascript.validate.enable": false,
    
        // - 设置 Emmet
         "emmet.triggerExpansionOnTab": true,
    
         // - 配置插件: Sass/Less/Typescript/Jade/Pug Compile Hero
        "compile-hero": {
            "disable-compile-files-on-did-save-code": false,
            "javascript-output-directory": "./out",
            "javascript-output-toggle": false,
            "sass-output-directory": "./out",
            "sass-output-toggle": true
        }
    }
```

## ▲ Windows 下设置:
### Windows 下更改 VSCode 中的字体为 Source Code Pro
从 github 下载: [Source Code Pro](https://github.com/adobe-fonts/source-code-pro) 点击 latest release, 选择 otf 文件下载，放到字体文件夹 (C:\Windows\Fonts)
  + tips: 字体有2个版本，可以都安装

- 在 `settings.json` 中设置
    + "editor.fontFamily": "Source Code Variable, 'Source Code Variable Italic'"
    + 具体的字体名参照自己下的字体，同样在 C:\Windows\Fonts 中可以找到

## ▲ Win10 下 VSCode 的基本设置

### Win 下 `settings.json` 的基本设置
```json
{
    "files.autoSave": "afterDelay",
    "editor.fontFamily": "Source Code Pro, Source Han Sans SC Light",
    "editor.lineHeight": 24,
    "editor.detectIndentation":false,
    "editor.tabSize": 4,
    "terminal.integrated.fontSize":14,
    "terminal.integrated.letterSpacing":1,
    "editor.rulers":[80],
    "editor.cursorStyle": "line",
    "terminal.integrated.fontFamily": "Source Code Pro, Source Han Sans SC Light",
    "debug.console.fontFamily": "Source Code Pro, Source Han Sans SC Light",
    "marKdown.preview.fontFamily": "Source Code Pro, Source Han Sans SC Light",
    "editor.fontSize": 14,
    "editor.letterSpacing": 1,
    "window.zoomLevel":0,
    "editor.wordWrap": "on",
    "editor.wordWrapColumn": 100,
    "debug.toolBarLocation": "docKed",
    "terminal.integrated.shell.windows": "C:\\Program Files\\Git\\bin\\bash.exe",
    "diffEditor.renderSideBySide": false,
    "worKbench.tree.indent": 24,
    "editor.minimap.enabled": false
}
```
Tips: `editor.fontFamily: "Source Code Pro, Source Han Sans SC Light"` 解决了中文和英文的显示问题, 一定不要更改, `Source Code Pro` 解决的是英文显示字体,  `Source Han Sans SC Light`解决的是汉语字体显示的问题. 


## ▲ 解决 mbp 使用 VSCode 导致风扇狂转的问题
一般情况下, vscode 的进程不会导致风扇一直狂转, 所以打开 "活动监视器" 查找是哪个占了极高的 cpu 即可.


## ▲ Gitlens 取消每行后面的代码变更记录
具体操作步骤如下:

按快捷键 `Ctrl/Command` + `,` 打开设置面板

搜索栏输入 `gitlens.toggleLineBLame`

取消 Specifies whether to provide a blame annotation for the current line, by default. Use the Toggle Line Blame Annotations command (gitlens. toggleLineBLame) to toggle the annotations on and off for the current window. (默认情况下，指定是否为当前行提供责备注释。 使用 Toggle Line Blame Annotations 命令 (gitlens.toggleLineBLame) 打开和关闭当前窗口的注释。) 前的勾选。



## ▲ 快速跳出成对的标点符号

比如：vscode 自动补充的 `""` ，在双引号写完字符串之后，直接再次按下双引号键即可。