# VSCode 使用设置


## Table Of Contents
1. Mac 和 Win 下的通用设置
    + 1.1 快捷键:
    + 1.2 更改英文为中文
    + 1.3 调出 `settings.json` 编辑文件
    + 1.4 VSCode 打开多个项目
    + 1.5 VSCode 设置每行代码的长度: 
    + 1.6 关闭 VSCode 右侧缩略图 (预览面板):
    + 1.7 关闭 VSCode 自动换行
    + 1.8 如何打开终端?
    + 1.9 修改终端中的字体
    + 1.10 Visual Studio Code 修改文件树缩进
    + 1.11 隐藏/显示 左侧的 activity bar (活动栏)
    + 1.12 隐藏/显示 左侧的 side bar (侧标栏)
    + 1.13 快速生成文件模块
    + 1.14 查找某个函数在哪些地方被调用了
    + 1.15 鼠标操作
    + 1.16 创建多层子文件夹:
    + 1.17 `.vscode` 文件夹的作用
    + 1.18 通用插件
2. Mac 下设置
    + 2.1 关于 VSCode 版本字体的问题
    + 2.2 Mac 下 `settings.json` 基本设置
3. Windows 下设置
    + 3.1 Win 下 `settings.json` 的基本设置
    + 3.2 Windows VSCode 常用快捷键
4. 解决 mbp 使用 VSCode 导致风扇狂转的问题


## New Words


## Content
### 1. Mac 和 Win 下的通用设置
#### 1.1 快捷键
- Windows: `Ctrl + Shift + p` / Mac: `Command + Shift + p`:
  `show all commands` (显示所有命令面板)
- 更该默认设置: `File` -> `Preferences` --> `Settings`

#### 1.2 更改英文为中文
- 使用 Ctrl + Shift + P 调出所有命令行面板，输入 configure display language 安装中文包

#### 1.3 调出 `settings.json` 编辑文件
- File -> Preference -> Settings -> 点击左上角的 `{}` 图标。

#### 1.4 VSCode 打开多个项目
- Windows 下 `control + Shift + N`
- Mac 下 `command + Shift + N` 

#### 1.5 VSCode 设置每行代码的长度: 
- 在 setting.json 的规则内添加:  `editor.rulers:[80]` ，添加完毕之后右侧就会自动出来
  达到 80 个字符的时的竖线

#### 1.6 关闭 VSCode 右侧缩略图 (预览面板):
- 在 settings.json 中添加: `"editor.minimap.enabled": false,`

#### 1.7 关闭 VSCode 自动换行
- settings.json 中添加 `"editor.wordWrap": "off"`

#### 1.8 如何打开终端?
- 1、快捷键: `control + `(esc 下的那个按键)`
- 2、View --> Terminal

#### 1.9 修改终端中的字体
- `"terminal.integrated.fontSize":14,`
- `"terminal.integrated.letterSpacing":1,`

#### 1.10 Visual Studio Code 修改文件树缩进
- `"worKbench.tree.indent": 24,`

#### 1.11 隐藏/显示 左侧的 activity bar (活动栏)
- Explorer (Ctrl + Shift + E) 探测器 (项目 文件)
- Search (Ctrl + Shift + F) 搜索
- Source Control (Ctrl + Shift + G): 代码控制工具 (Git: 可以查看修改了多少个文件)
- Debug (Ctrl + Shift + D) 调试
- Extensions (Ctrl + Shift + X) 插件扩展
   (横向拖动变宽在 Extensions 栏可以搜索内容的图标)

#### 1.12 隐藏/显示 左侧的 side bar (侧标栏)
- 右上角 `view -> Appearance -> Show activity bar`
- 快捷键
    + Windows 下: Ctrl + b
    + Mac 下:  command + b

#### 1.13 快速生成文件模块
- 快速生成 HTML 模版:  在当前文件中输入`!` 然后按下 `Tab` 按键

#### 1.14 查找某个函数在哪些地方被调用了
- 比如我已经在 `a.js` 文件里调用了 `foo()` 函数. 那么, 如果我想知道 `foo()`
  函数在其他文件中是否也被调用了, 该怎么做呢？
  
  做法如下: 在 `a.js` 文件里, 选中 `foo()` 函数 (或者将光标放置在foo()函数上),
  然后按住快捷键 `Shift + F12`, 就能看到 `foo()` 函数在哪些地方被调用了, 比较实用. 

#### 1.15 鼠标操作
- 在当前行的位置，鼠标三击，可以选中当前行。
- 用鼠标单击文件的行号，可以选中当前行。
- 在某个行号的位置，上下移动鼠标，可以选中多行。

#### 1.16 创建多层子文件夹:
- 我们可以在新建文件夹的时候，如果直接输入, 比如 `aa/bb/cc` 的类似格式即可.

#### 1.17 `.vscode` 文件夹的作用
- 如果你发现项目的根目录下有一个.vscode文件夹，说明这个文件夹代表的是当前项目的配置。
- 这个文件夹里可能包含以下集中文件: 
    + `settings.json`: 工作空间设置。只针对当前项目有效。比如说，我可以在这里面要求
      当前项目的代码统一使用制表符，而不需要要求每一位码农去修改各自的配置文件。
    + `sftp.json`: ftp文件传输的配置。

#### 1.18 通用插件
1. `vscode-icons`: 更换图标主题(即给文件添加对应的文件图标):
    + 显示方式: `Ctrl/command + Shift + p` 弹出显示所有命令面板, 输入:
      `Icons`, 点击 Activate VSCode icon
1. `image preview`: 光标悬浮在图片路径上, 显示图片预览.
1. `Chinese(Simplified) Language PacK for Visual Studio Code`:
   安装汉化 VS Code 插件.
1. `beautify`: 自动格式化代码; 可以放大标记, 调整代码间距, 快速格式化代码,
   可以让杂乱的 HTML, CSS, JS 代码瞬间变得整齐.
1. `Code Runner`: 搭建各类语言开发环境
1. `Debugger for Chrome`: 与chrome联调.
1. `ESLint`: 自动检测代码规范.
1. `English word hint`: 英语翻译提示.
1. `Code Spell ChecKer`英语拼写检查.
1. Github 插件
    + `GitLens`: 在 git 管理上有很强大的功能. 比如:
        - 查看某个 commit 的代码改动记录
        - 查看不同的分支
        - 可以将两个 commit 进行代码对比，甚至可以将两个 branch 分支进行代码比对。
          这一点，简直是 GitLens 最强大的功能。
    + `RemoteHub`: RemoteHub 和 GitLens 是同一个作者开发出来的。
      RemoteHub插件的作用是: 可以在本地查看 GitHub 网站上的代码，而无需将代码下载到本地。
    + `Git history` : github 提交历史查看
    + `GitHub pull Requests`
1. `MarKdown + Math`: MathJax 支持插件.
1. `open in browser`: 浏览器打开.
1. `MarKdown pdf`
1. `Prettier`
1. `Rainbow BracKets`: 彩虹括号
1. `SVG`
1. `SVG Viewer`
1. `Terminal`
1. `Vetur`
1. `C/C++`
1. `Dart`
1. `Awesome Flutter Snippets`
1. `Python`
1. `CSS PeeK`
1. `Flutter`
1. `Path Intellisense`
1. `IntelliSense for CSS`
1. `Code Spell ChecKer`: 单词拼写检查
1. `Live Server`: 实现静态/动态页面的实时预览, 保存即可看见页面更新, 无需手动刷新.
1. `indent-rainbow`: 缩进彩虹, 不同的颜色来提示当前的缩进位置.(tip: 颜色太丑.)
1. `Local history`: 查看文件修改历史记录.


### 2. Mac 下设置
#### 2.1 关于 VSCode 版本字体的问题
- VSCode 在
  [August 2019, version 1.38](https://code.visualstudio.com/updates/v1_38)
  版本之前和之后的字体对比差距明显, 默认字体还是 `Menlo`,
  但是英文和汉语字体都加粗了, 汉字的粗细尚可通过 `"editor.fontWeight": 300` 来改变,
  但是这个设置对于英文字体却不管用; 暂时仍然使用 version 1.38 的版本.

#### 2.2 Mac 下 `settings.json` 基本设置
- ```json
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


###  Windows 下设置:
#### Windows 下更改 VSCode 中的字体为 Source Code Pro
- 从 github 下载:
  [Source Code Pro](https://github.com/adobe-fonts/source-code-pro)
  点击 latest release, 选择 otf 文件下载，放到字体文件夹 (C:\Windows\Fonts)
    + tips: 字体有2个版本，可以都安装
- 在 `settings.json` 中设置
    + "editor.fontFamily": "Source Code Variable, 'Source Code Variable Italic'"
    + 具体的字体名参照自己下的字体，同样在 C:\Windows\Fonts 中可以找到

### 3. Win10 下 VSCode 的基本设置
#### 3.1 Win 下 `settings.json` 的基本设置
- ```json
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
- Tips: `editor.fontFamily: "Source Code Pro, Source Han Sans SC Light"`
  解决了中文和英文的显示问题, 一定不要更改, `Source Code Pro` 解决的是英文显示字体, 
  `Source Han Sans SC Light`解决的是汉语字体显示的问题. 

#### 3.2 Windows VSCode 常用快捷键:
1. 注释: 
　　+ (1) 单行注释: `[Ctrl + K, Ctrl + c]` 或 `Ctrl` + `/`
　　+ (2) 取消单行注释: `[Ctrl + K, Ctrl + U] (按下 Ctrl 不放, 再按 K + U)`
　　+ (3) 多行注释: `[Alt + Shift + A]`
　　+ (4) 多行注释: `/**`
1. 折叠代码快捷键: 先按下 `Ctrl + K` 再按下 `Ctrl + 0(数字0)` 
    + (Tip: 即使是折叠全部代码也不用全选文本) 
1. 代码展开: 先按下 `Ctrl + K`，再按下 `Ctrl + J` ;
1. 移动行: `Alt + Up/Down`
1. 显示/隐藏左侧目录栏: `Ctrl + B`
1. 复制当前行: `Shift + Alt + Up/Down`
1. 删除当前行: `Shift + Ctrl + K / Mac: Shift + command + K`
1. 控制台终端显示与隐藏: `Ctrl + ~`
1. 查找文件/安装vs code 插件地址: `Ctrl + p`
1. 代码格式化: `Shift + Alt +f`
1. 新建一个窗口 : `Ctrl + Shift + n`
1. 行增加缩进: `Ctrl + [`
1. 行减少缩进: `Ctrl + ]`
1. 裁剪尾随空格(去掉一行的末尾那些没用的空格) : `Ctrl + Shift + x`
1. 字体放大/缩小: `Ctrl + ( + 或 - )`
1. 拆分编辑器 : `Ctrl + 1/2/3`
1. 切换窗口 : `Ctrl + Shift + left/right`
1. 关闭编辑器窗口 : `Ctrl + w`
1. 关闭所有窗口 : `Ctrl + K + w`
1. 切换全屏 : `F11`
1. 自动换行 : `Alt + z`
1. 显示git : `Ctrl + Shift + g`
1. 全局查找文件: `Ctrl + Shift + f`
1. 显示相关插件的命令(如: git log): `Ctrl + Shift + p`
1. 选中文字: `Shift + left / right / up / down`
1. 删除行 :  `Ctrl + Shift + K`
1. 快速切换主题: `Ctrl + K / Ctrl + t`
1. 快速回到顶部 :  `Ctrl + home`
1. 快速回到底部 : `Ctrl + end`
1. 格式化选定代码 : `Ctrl + K / Ctrl + f`



### 4. 解决 mbp 使用 VSCode 导致风扇狂转的问题
- 一般情况下, vscode 的进程不会导致风扇一直狂转, 所以打开 "活动监视器" 查找是哪个占了极高的 cpu 即可.
