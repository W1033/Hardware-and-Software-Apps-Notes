
# [详细使用教程](http://itmyhome.com/markdown/article/extension/strikethrougn.html)


### Markdown 引入本地文件
- (1) 使用绝对路径
  
    + [transition-transform-animation.md](/Users/WANG/Github-clone/CSS-grocery/CSS3-过渡-转换-动画/transition-transform-animation.md)
- (2) 使用相对路径
    + [transition-transform-animation.md](File:///Users/WANG/Github-clone/CSS-grocery/CSS3-过渡-转换-动画/transition-transform-animation.md)

      注意 File 协议首字母要大写, `File://` 中英文字符不限, 文件夹亦可.


## 目录 (TOC)
1. Markdown 是什么?
2. Markdown 与 Word 的对比
3. Markdown 常用语法集合
4. 高级进阶语法




## Content

### 1. Markdown 是什么?
Markdown 是一种`轻量级标记语言(1)`, 它使用**纯文本格式**编写文档，使用一些预设的符号来代替样式, 当在 markdown 编辑器或阅读器中显示时, 会转换成有效的 HTML 文档.
- `(1)` 轻量级标记语言(Lightweight Markup Language, 简称 XML)是一类用简单句法描述简单格式的文本语言。它作为一种标记语言，可使用文本编辑器输入。

例如我们想要实现标题样式, 可以这么写:

![markdown title](./images-markdown/markdown01.jpg)

<p style="color: red;">上图: 左侧为书写方式, 右侧为显示效果</p>

上图的图片插入写法如下:
`![markdown title](./images-markdown/markdown01.jpg)`



### 2. Markdown 与 Word 的对比

####  word
文字处理程序, 内置丰富的文字排版/段落排版/标题/表格等功能; 

这些强大的功能是 Word 的优点, 但同时也是缺点.

当功能多了, 我们的注意力就会分散, 比如设置字体时我们经常会遇到:

这个字体大小到底是 14px 还是 16px 好？我想强调这一句话, 是要加粗还是标红？

#### Markdown
**本质是让我们回归到内容本身，注重文章的结构，而不是样式。**

例如想要强调一句话，那么直接使用两个星号(`**`)加粗，而不需要考虑是加粗还是标红,

因为 Markdown 中默认只有黑色字体，没有其他颜色字体。



### 3. Markdown 常用语法集合

原生的 Markdown 语法只包含了最基础的一些特性，例如：标题、加粗、斜体、段落、引用、超链接、图片、列表、代码块、水平分割线等。而一些自定义实现的编辑器，则有一些自定义的实现，例如：数学公式、TODO 列表等。

Markdown 语法非常简单。下面简单介绍一些常用的 Markdown 语法。

> https://zhuanlan.zhihu.com/p/69210764

#### 3.1 段落

#### 3.2 加粗、斜体、加粗斜体

#### 3.3 无序列表

#### 3.4 有序列表

#### 3.5 引用

#### 3.6 超链接

#### 3.7 图片

#### 3.8 代码块

#### 3.9 水平分割

#### 3.10 表格
**示例 1:**
```
| Tables        | Are           | Cool  |
| ------------- |:-------------:| -----:|
| col 3 is      | right-aligned | $1600 |
| col 2 is      | centered      |   $12 |
| zebra stripes | are neat      |    $1 |
```

**显示效果:**

| Tables        | Are           | Cool  |
| ------------- |:-------------:| -----:|
| col 3 is      | right-aligned | $1600 |
| col 2 is      | centered      |   $12 |
| zebra stripes | are neat      |    $1 |

**示例 2:**

```
dog | bird | cat
----|------|----
foo | foo  | foo
bar | bar  | bar
baz | baz  | baz
```
**显示效果:**

dog | bird | cat
----|------|----
foo | foo | foo
bar | bar | bar
baz | baz | baz



### 4. 编辑工具
因为 Markdown 本质上是一个纯文本，所以任何能打开纯文本的东西都可以来编辑 Markdown。

但如果你想要有预览功能，那么一款顺手的编辑功能还是有必要的。

在 Windows 和 MacOS 上推荐的编辑器有: **Visual Studio Code (VS code)**, **Typora**.

当然 Markdown 的编辑器还有很多, 比如对 LaTex 数学公式支持更好的 **Smark**; 内置文件管理器, 以及可以使用 iCloud 云服务器同步的 **Ulysses**, 可以多加尝试, 看看哪一款更符合自己的使用习惯. 







### 4. 高级进阶语法
#### 4.1 自定义大小和带边框的图片插入写法:
实际上也就是使用网页中的 HTML + CSS 源代码模式
```html
<img src="./images-markdown/markdown01.jpg" style="border-radius: 4px; width: 66%; box-shadow: 1px 1px 3px 2px #e5e5e5">
```





------ ------ ------ ------ ------ ------



1. 标题 `#, ##, ###, ####, #####, ######`
 # 一级标题
    ## 二级标题
    ### 三级标题
    #### 四级标题
    ##### 五级标题
    ###### 六级标题
    注：# 和「一级标题」之间建议保留一个字符的空格，这是最标准的 Markdown 写法。

1. 列表格式 `-` 或 `+`
    > 在 Markdown 中，你只需要在文字前面加上 - 就可以了，例如：
        - 文本1
        - 文本2
        - 文本3
    > 在 Markdown 中，你只需要在文字前面加上 + 就可以了，例如：
        + 文本1
        + 文本2
        + 文本3
    
   如果你希望有序列表，
   也可以在文字前面加上 1. 2. 3. 就可以了，例如：
        1. 文本1
        2. 文本2
        3. 文本3
    **注：-、1.和文本之间要保留一个字符的空格。**

1. 链接和图片 `[显示文本](链接地址)`
    插入图片：![alt text](http://path/to/img.jpg "title")
    文字链接：[Title](你的链接地址)
    图片加链接：[![alt text](http://path/to/img.jpg "title")](你的链接地址)  

1. 引用 `>`
    + 在我们写作的时候经常需要引用他人的文字，这个时候引用这个格式就很有必要了，在 Markdown 
      中，你只需要在你希望引用的文字前面加上 > 就好了，例如：
    > 一盏灯， 一片昏黄； 一简书， 一杯淡茶。 守着那一份淡定， 品读属于自己的寂寞。
    注：> 和文本之间要保留一个字符的空格。


1. 粗体和斜体 `**粗体**`, `*斜体*`
    + Markdown 的粗体和斜体也非常简单，用两个 * 包含一段文本就是粗体的语法，用一个 * 包含
      一段文本就是斜体的语法。例如：
    + *一盏灯*， 一片昏黄；**一简书**，

1. 代码引用 `` (这个在md中写文字穿插带`<button>`这样的元素时很有用)
    + 需要引用代码时，如果引用的语句只有一段，不分行，可以用 ` 将语句包起来。
    + 如果引用的语句为多行，可以将```置于这段代码的首行和末行。

1. 删除线: `~~~~`
    + 这就是 ~~删除线~~

1. 下划线: 
    1. 方法(1) 用 MathJax: $\underline{内容}$
    2. 方法(2) 用 html 样式: 
       `<i style="border-bottom: 1p solid yellow"><i>`


1. 表格



### Markdown 里使用 mermaid 画流程图 (vscode 可以安装 draw.io 插件实现)
- 流程图的定义仅由 graph 开始，但是方向的定义不止一种。
    + TB（ top bottom）表示从上到下
    + BT（bottom top）表示从下到上
    + RL（right left）表示从右到左
    + LR（left right）表示从左到右
    + TD 与 TB 一样表示从上到下
```mermaid
    graph LR
    A --> B
```

### markdown 代码块支持的语言
1. ```applescript```
1. ````actionscript3 | as3```
1. ```bash | shell```
1. ```cpp, c```
1. ```c# | c-sharp | csharp```
1. ```css```
1. ```delphi | pascal | pas```
1. ```diff path```
1. ```erl | erlang```
1. ```groovy```
1. ```java```
1. ```jfx, javafx```
1. ```js | javascript```
1. ```json```
1. ```perl | pl | Perl```
1. ```php```
1. ```text | plain```
1. ```py | python```
1. ```ruby | rails | ror | rb```
1. ```sass | scss```
1. ```scala```
1. ```sql```
1. Visual Basic ```vb | vbnet```
1. ```xml | xhtml | xslt | html```
1. ```objc | obj-c```
1. ```f# | f-sharp | fsharp```
1. ```xpp | dynamics-xpp```
1. ```r | s | splus```
1. ```matlab```
1. ```swift```
1. ```go | golang```