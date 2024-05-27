# WebStorm 操作记录

## 目录(Catalog)
0. WebStorm 中的 `皮肤` 和 `主题`
1. WebStorm 中去掉灰色的参数提示: `parameter name hints`
2. 解决 Webstorm 提交代码 `Github` 的相关问题.
3. 解决 WebStorm 快捷键和 Mac 系统冲突
4. WebStorm 如何使用正则给文档每段之间添加空格?
5. 更改配色字体提示颜色
6. WebStorm 中更改文档的默认字体:
7. 更改字符编码:
8. 有用的快捷键:
9. 解决 JavaScript 无法运行, 和 JS 文件被当做 txt文件的问题 ?
10. 
11. 
12. 
13. 只修改编辑区的背景色，不改主题:
14. 更改 js/css/scss/less 文件的缩进:
15. webStorm 下将 vue 的代码锁紧由 2 个空格改为 4 个空格
16. WebStorm 自定义快捷键:
17. 导入主题包 (theme package)
18. 去掉文件窗口右边的竖线:
19. 调整字母长度分割线为80:
20. 更改默认的浏览器: 
21. 
22. 打开多个项目窗口:
23. WebStorm 左侧的折叠线展示/隐藏
24. WebStorm 中光标变成了白色小块：
25. WebStorm 中光标变成黑块：
26. 如何在 WebStorm 中使用正则快速删除空行？    
27. WebStorm 好用插件集锦:
28. 解决 MBP 下 WebStorm 启动扫描检查(inspections) 导致电脑风扇疯狂运行的问题



## 生词(New Words)
- **revolution [revə'luːʃ(ə)n] --n.革命，旋转，运行，公转**
    + revolution per minute 每分钟的旋转率。(缩写: r/min)
    + computer revolution 计算机革命
    + revolution counter 转速计
    + the revolution of the seasons. 季节的循环
    + the revolution of the earth around the sun. 地球绕着太阳的公转。
- **diagnostic [daɪəg'nɒstɪk]/[ˌdaɪəɡ'nɑstɪk] --诊断的; 判断的.**


## 内容(Content)
### 0. WebStorm 中的 `皮肤` 和 `主题`
- `皮肤`(appearance): 是显示界面
- `主题`(Theme): 是代码主题
- ~~2019 年 WebStorm 支持全局的主题了, 可以装个 vscode 的主题:
  `Visual Studio Code Dark Plus Theme`~~

### 1. WebStorm 中去掉灰色的参数提示: `parameter name hints`

- `Settings` --> 输入: `parameter hints` --> `Editor` --> `General`
  --> `Appearance` --> `Show parameter name hints` 去掉勾选   

### 2. 解决 Webstorm 提交代码 `Github` 的相关问题.
- (1) 无法登录 `Gtihub` 账号:
    + 解决方法: 把 `Github` 网站的 `Personal access tokens` 中的已有 token 删除,
      重新生成 token 后再次添加 `github` 账号.
- (2) 无法从 `github` 上 `clone` 仓库, 提示被拒:
    + R: 在第一步添加账号时, 账户下面的那行 `Clone git repositories use ssh`
      不要勾上, 如果选中会通过 `SSH` 加密传输来 `clone` 仓库,
      但它的使用前提是我们必须在 `gighub` 配置 `SSH Key`, 并在本地生成 `id_rsa`私钥.
      (更多设置可见此文章: https://blog.csdn.net/dotphoenix/article/details/100130424)

### 3. 解决 WebStorm 快捷键和 Mac 系统冲突
- 在 Mac 下使用进行代码多行注释, 使用 `Command` + `shift` + `/`,
  结果每次成功注释之后, WebStrom 的菜单栏的 help 就会被打开,
  因为快捷键和 Mac系统自带的快捷键冲突, 因此在 `偏好` 设置 --> `键盘`中,
  将 `应用快捷键` 中的 `显示帮助菜单` 的快捷键关闭或使用其他即可解决上述问题。

### 4. WebStorm 如何使用正则给文档每段之间添加空格?

按下 `command + R` 打开全局替换, 勾选 `RegExp`, 

在第一行搜索框中输入 `。\n{1}` 然后点击后面的 `Search in selection only` 按钮(tip: 就是 `三`横线旁边有个竖线的按钮)

然后在第二行搜索框中输入 `。\n\r`


### 5. 更改配色字体提示颜色
- `Settings` --> `Editors` --> `colors&fonts` --> `HTML` -->
  在下面黑框里点击你想设置的代码然后看到上面对应的部分(foreground)就可以设置了，如果不能
  设置上面的 foreground,记得把下面的 use inherited attributed 前面的对号取消就可以了。

### 6. WebStorm 中更改文档的默认字体:

- `Settings` -> `Editor` -> `Color Scheme` -> `General`

### 7. 更改字符编码:

- 主界面的最下面即可看到当前文件的字符编码

## 快捷键：

| 操作描述                         | Windows 快捷键             | MacOS 快捷键                                                 |
| -------------------------------- | -------------------------- | :----------------------------------------------------------- |
| 选中下一个相同内容               | `Alt + J`                  | Command + G                                                  |
| 选中所有相同内容                 | `Ctrl + Shift + Alt + J`   | Command + Ctrl + G                                           |
| 在不选中的情况下复制一行         | `Ctrl + D`                 |                                                              |
| 复制选中内容，不选中时复制当前行 | `Ctrl + C`                 |                                                              |
| 后退/撤销                        | `Ctrl + Z`                 |                                                              |
| 取消后退/撤销                    | `Ctrl + Shift + Z`         |                                                              |
| 查找（当前文件）                 | `Ctrl + F`                 |                                                              |
| 替换（当前文件）                 | `Ctrl + R`                 |                                                              |
| 格式化代码                       | `Ctrl + Alt + L`           | `Command` + `Option`(⌥) + `L`                                |
| 自动缩进                         | `Ctrl + Alt + I`           |                                                              |
| 切换窗口                         | `Ctrl + Shift + Space`     |                                                              |
| 展开/折叠当前代码                | `Ctrl` + `+/-`             | `Command`(⌘)  + `+`<br />`Command`(⌘)  + `-`                 |
| 展开/折叠全部代码                | `Ctrl` + `Shift` + `+/-`   | `Command`(⌘) + `Shift`(⇧) + `+`<br />`Command`(⌘) + `Shift`(⇧) + `-` |
| 全局搜索                         | `Ctrl` + `Shift` + `F`     | `Command` + `Shift` + `F`                                    |
| 单行注释                         | `Ctrl` + `/`               | `Command` + `/`                                              |
| 多行注释                         | `Ctrl` + `Shift + `/`      | `Command` + `Shift` + `/` (注意: 和 MacOS 系统快捷键冲突)    |
| 快速在当前行上插入一行           | `Ctrl` + `Shift` + `Enter` | `Option` + `Command` + `Enter`                               |
| 快速在当前行下插入一行           | `Ctrl` + `Enter`           |                                                              |


### 9. 解决 JavaScript 无法运行, 和 JS 文件被当做 txt文件的问题 ?

- `Preferences` --> `Editor` --> `File types` --> 在右侧方框中找到
  `JavaScript` 然后在下面的 Registered Patterns 中更该为 `*.js` 

### 13. 只修改编辑区的背景色，不改主题:

-  `Settings -> Editor -> Color Scheme -> General -> Text -> Default text`

### 12.

### 14. 更改 js/css/scss/less 文件的缩进:

- `File -> Settings -> Editor -> Code Style --> 相应的文件格式然后更改`

### 15. webStorm 下将 vue 的代码锁紧由 2 个空格改为 4 个空格
- (1) `File -> Settings -> Editor -> Code Style -> Javascript`
  indent 都设置为 4.
- (2) 修改 Vue 项目下的 .editConfig 中的 `indent_size = 4`
- (3) 后重启 webstorm

### 16. WebStorm 自定义快捷键:
- 自定义 "创建文件" 快捷键为: `Alt` + `A`: 
  `Settings` --> `Keymap` --> `Main menu` --> `File`
-  MacOS 自定义 "文件重命名 (Rename)" 的快捷键为：`Shift` + `R`

### 17. 安装组件
- 用 npm 安装 nodejs 需要的模块组件: 
    + File -> Setting -> Plugins -> Browse repositories...
    + 然后在 Settings -- Languages & Frameworks -- Node.js and NPM中配置 
      Node interpreter（node解释程序） C:\Program Files\nodejs\node.exe
      (就是node在C盘的安装路径),如果此时没有安装 node 的核心模块，会提示让在线安装，
      确定就好了。下面的express(代理)应该就是显示的版本号。
    + tip: 下面的 `Coding assistance` (编码助手)记得打开.
     `enabled`: 激活的. `Disable`: 禁止。

### 18. 去掉文件窗口右边的竖线:
- `Setting` --> `Editor` --> `Appearance` --> `show hard wrap guide`
  (configured in code style options)

### 19. 调整字母长度分割线为80:
- 首先把上面的 `show hard wrap guide` 提示打开
- 然后 `Setting -- Editor -- Code Style --> Hard wrap at: 80`
  下面的 `Visual guides` 也设置为 80

### 20. 更改默认的浏览器: 
+ `Setting -- Tools -- Web Browsers`

### 21. 

### 22. 在新窗口打开项目:
- `Setting` --> `Appearance & Behavior` --> `System Settings` -->
  `Project Opening` -- `Open project in new window`

### 23. WebStorm 左侧的折叠线展示/隐藏
- `Setting --> Editor --> general --> code folding (代码折叠)`
   --> show code folding outline`

### 24. WebStorm 中光标变成了白色小块：
- `Setting -> Editor -> Appearance -> use block caret(使用块插入符号)`   

### 25. WebStorm 中光标变成黑块：
- windows 上是 `ins`/`Insert` 键。 Mac 是 `fn + Eenter` 键 

### 26. 如何在 WebStorm 中使用正则快速删除空行？
- 按下 `Command + R` 弹出替换框，勾选 `Matches` 和 `Regexp`(Regular Expression),
  然后在第一个输入框中输入正则 `\B\n`
  (Tip: `\B`:匹配一个单词的非边界位置。`\n`:匹配一个换行符)   

### 27. WebStorm 好用插件集锦:
- `Rainbow brackets` -- 彩虹括号
- `Visual Studio Code Dark Plus Theme`

### 28. 解决 MBP 下 WebStorm 启动扫描检查(inspections) 导致电脑风扇疯狂运行的问题
- 无法停止/杀死 开机扫描文件夹建立索引(indexing) 的 `Backgournd Tasks`; 在 JetBrains
  的论坛上, 这个问题 2010 年就已经提出来了, 但是 2020 年还没有给出解决方法...... LOL.
- ~~当一个文件夹下放置太多仓库, 启动 Macbook Pro 2015 后 WebStorm~~
  ~~会扫描所有的仓库来进行各种检查,这样非常耗内存和 CPU, CPU 急速运行后导致温度迅速升高,~~
  ~~为了加速散热风扇的转速也会跟着提高(tip: 我的 mbp 腾讯`lemon`~~
  ~~显示风扇转速可到 `6200 RPM` [转速单位: RPM: Revolutions Per Minute. 转每分,~~
  ~~表示设备每分钟的旋转次数.] ), 这样会导致笔记本发出强烈的噪音;~~
  ~~想要解决这个问题我们就要降级 WebStorm 的检查等级, 这样就会加速大文件的读写.~~
- ~~WebStorm 的检查等级分为 3 个等级:~~
    - ~~(1) `Inspections` 为最高等级检查,可以检查 "单词拼写", "语法错误",~~
          ~~"变量使用", "方法之间调用" 等.~~
    - (2) ~~`Syntax` 可以检查单词拼写错误, 简单语法错误.~~
    - (3) ~~`None` 不设置检查.~~
- ~~我们可以从 `Settings` --> `Preferences` --> `Editor` --> `Inspections`~~
  ~~在右侧的 `Project Default` 的下面把不需要的检查项目后的 ✓ 号去除即可.~~
  ~~当然你也可以直接选择把下面 `Disable new inspections by default` 前的 ✓ 勾上.~~

### 29. 更该 webstorm 更该内存大小
- `help`  --> `Change memory settings`