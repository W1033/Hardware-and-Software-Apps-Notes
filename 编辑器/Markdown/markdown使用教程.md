
# +[详细使用教程](http://itmyhome.com/markdown/article/extension/strikethrougn.html)


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

下面简单介绍一些常用的 Markdown 语法。

#### 3.1 标题
用 Markdown 书写时，只需要在文本前面加上 『#』 即可创建一级标题。同理，创建二级标题、三级标题等只需要增加 『#』 个数即可，Markdown 共支持六级标题。如下所示：

<img src="./images-markdown/markdown01.jpg" style="border-radius: 4px; width: 79%; box-shadow: 1px 1px 5px 2px #e5e5e5">

**Hint:** `#` 号 和「标题」之间保留一个字符的空格，markdown 语法默认都依照此规范。

#### 3.2 样式文本

您可以使用粗体、斜体或删除线文本来表示强调。

| 样式  | 语法 | 示例  | 输出  |
| :-----: | :-----: |:-----: | :-----: |
| 粗体(加粗)| `** **` | `**这是粗体文本**` | **粗体文本** |
| 斜体 | `* *` |  `*这是斜体文本*`  | *斜体文本* |
| 加粗斜体 | `*** ***`|`***所有这些文本都很重要***` | ***加粗斜体文本***|
| 删除线  | `~~ ~~` | `~~这是错误文本~~`  | ~~删除错误文本~~ |

<img src="./images-markdown/1.jpg" style="border-radius: 4px; width: 70%; box-shadow: 1px 1px 5px 2px #e5e5e5">


#### 3.3 无序列表
使用中横线(`-`)或星号(`*`)来表示无序列表，注意后面需要加个空格。

<img src="./images-markdown/8.jpg" style="border-radius: 4px; width: 79%; box-shadow: 1px 1px 5px 2px #e5e5e5">


#### 3.4 有序列表

<img src="./images-markdown/9.jpg" style="border-radius: 4px; width: 79%; box-shadow: 1px 1px 5px 2px #e5e5e5">

#### 3.5 引用
Markdown 标记区块引用只需要在整个段落的第一行前面加上 `>`（右箭头符号） ：
```
> 桃花坞里桃花庵，桃花庵里桃花仙。桃花仙人种桃树，又摘桃花换酒钱。
```
展示效果如下：
> 桃花坞里桃花庵，桃花庵里桃花仙。桃花仙人种桃树，又摘桃花换酒钱。

区块引用可以嵌套，只要根据层次加上不同数量的 `>` 即可(tip：和不同等级的标题类似。)； 例如：
```
> 这是第一级引用。
>
> > 这是第二级引用。
```

展示效果如下：

> 这是第一级引用。
>
> > 这是第二级引用。

<img src="./images-markdown/6.jpg" style="border-radius: 4px; width: 79%; box-shadow: 1px 1px 5px 2px #e5e5e5">


#### 3.6 超链接

<img src="./images-markdown/2.jpg" style="border-radius: 4px; width: 79%; box-shadow: 1px 1px 5px 2px #e5e5e5">


#### 3.7 图片

<img src="./images-markdown/5.jpg" style="border-radius: 4px; width: 79%; box-shadow: 1px 1px 5px 2px #e5e5e5">


#### 3.8 代码块

<img src="./images-markdown/3.jpg" style="border-radius: 4px; width: 79%; box-shadow: 1px 1px 5px 2px #e5e5e5">


#### 3.9 水平分割

<img src="./images-markdown/7.jpg" style="border-radius: 4px; width: 79%; box-shadow: 1px 1px 5px 2px #e5e5e5">


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

<img src="./images-markdown/7.jpg" style="border-radius: 4px; width: 79%; box-shadow: 1px 1px 5px 2px #e5e5e5">


### 4. 编辑工具
因为 Markdown 本质上是一个纯文本，所以任何能打开纯文本的东西都可以来编辑 Markdown。

但如果你想要有预览功能，那么一款顺手的编辑功能还是有必要的。

在 Windows 和 MacOS 上推荐的编辑器有: **Visual Studio Code (VS code)**, **Typora**.

当然 Markdown 的编辑器还有很多, 比如对 LaTex 数学公式支持更好的 **Smark**; 内置文件管理器, 以及可以使用 iCloud 云服务器同步的 **Ulysses**, 可以多加尝试, 适合自己的才是最好用的. 







### 4. 高级进阶语法
#### 4.1 自定义大小和带边框的图片插入写法:
实际上也就是使用网页中的 HTML + CSS 源代码模式
```html
<img src="./images-markdown/markdown01.jpg" style="border-radius: 4px; width: 79%; box-shadow: 1px 1px 5px 2px #e5e5e5">
```


