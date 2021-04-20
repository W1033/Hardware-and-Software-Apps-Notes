# Markdown 使用文档


全局提示：当前文档参考如下几篇文章：
> [Learning-Markdown (Markdown 入门参考)](http://itmyhome.com/markdown/index.html)
> 
> [反思 Markdown](https://sspai.com/post/37340)





## 目录 (TOC)
1. Markdown 是什么?
2. Markdown 与 Word 的对比
3. Markdown 常用语法集合
4. 高级进阶语法



## 生词 (New Words)
- bit `/bɪt/` --
- LaTex `/'leɪteks/`





## Content

### 1. Markdown 是什么?
Markdown 是一种`轻量级标记语言(1)`, 它使用**纯文本格式**编写文档，使用一些预设的符号来代替样式, 当在 markdown 阅读器中查看时, 会被转换成有效的 HTML 文档.
- `(1)` 轻量级标记语言(Lightweight Markup Language, 简称 XML)是一类用简单句法描述简单格式的文本语言。

例如我们想要实现标题样式, 可以这么写 (下图左侧为书写方式, 右侧为显示效果.):

![markdown title](./images-markdown/markdown01.jpg)



### 2. Markdown vs 一般富文本编辑器







### 3. Markdown 常用语法集合
Markdown 语法只包含基础的特性，例如：标题、加粗、斜体、段落、引用、超链接、图片。。。  
而书写 markdown 的编辑器，则有一些自定义的样式，例如：数学公式、TODO 列表等。  
下面介绍一些常用的 markdown 语法。  

#### 3.1 段落与换行
##### 3.1.1 段落的前后必须有空行。否则相邻两段会显示成一行。
例如下面的一段引用:
```md
计算机中数据单位是 `bit(位/比特)`. 在计算机内部, 数据都是以二进制的形式存储和运行的.

二进制数据中的一个位(bit$^*$)简写为 b, 音译为比特, 是计算机存储数据的最小单位. 一个二进制位只能表示 0 或 1 两种状态, 要表示更多的信息, 就要把多个位组合成一个整体, 一般以 8 位二进制组成一个基本单位. 
```
如果上下段间没有空行，显示效果如下：
<p style="color: red; background-color: #fafafa">
计算机中数据单位是 `bit(位/比特)`. 在计算机内部, 数据都是以二进制的形式存储和运行的.
二进制数据中的一个位(bit)简写为 b, 音译为比特, 是计算机存储数据的最小单位. 一个二进制位只能表示 0 或 1 两种状态, 要表示更多的信息, 就要把多个位组合成一个整体, 一般以 8 位二进制组成一个基本单位. 
</p>
段落间添加一行空行即可正常显示了。
<div style="background-color: #fafafa">
<p style="color: red">计算机中数据单位是 `bit(位/比特)`. 在计算机内部, 数据都是以二进制的形式存储和运行的.</p>
<p style="color: red">二进制数据中的一个位(bit)简写为 b, 音译为比特, 是计算机存储数据的最小单位. 一个二进制位只能表示 0 或 1 两种状态, 要表示更多的信息, 就要把多个位组合成一个整体, 一般以 8 位二进制组成一个基本单位. </p>
</div>
空行指的是行内什么都没有，或者只有空白符（空格或制表符(一般特指 tab 键)）

##### 3.1.2 如果需要在段落内换行有 2 种方法：
1. 在准备换行的字符后面添加 `<br>` 代码。
2. 在需要换行的字符后添加 2 个及以上的空格，然后换行写其他文字。 我们拿上面的例子来改写：
<p style="color: red; background-color: #fafafa">二进制数据中的一个位(bit)简写为 b, 音译为比特, 是计算机存储数据的最小单位. <br> 一个二进制位只能表示 0 或 1 两种状态, 要表示更多的信息, 就要把多个位组合成一个整体, 一般以8位二进制组成一个基本单位. </p>


#### 3.2 标题
用 Markdown 书写时，只需要在文本前面加上 『#』 即可创建一级标题。同理，创建二级标题、三级标题等只需要增加 『#』 个数即可，Markdown 共支持六级标题。如下所示：

<img src="./images-markdown/markdown01.jpg" style="border-radius: 4px; width: 79%; box-shadow: 1px 1px 5px 2px #e5e5e5">

**Hint:** `#` 号 和「标题」之间保留一个字符的空格，markdown 语法默认都依照此规范。


#### 3.3 引用
引用只需要在整个段落的第一行前面加上 `>`（右箭头符号），写法如下：
```
> 桃花坞里桃花庵，桃花庵里桃花仙。桃花仙人种桃树，又摘桃花换酒钱。
```
展示效果如下：
> 桃花坞里桃花庵，桃花庵里桃花仙。桃花仙人种桃树，又摘桃花换酒钱。

区块引用可以嵌套，只要根据层次加上不同数量的 `>` 即可。例如：
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


#### 3.4 列表
##### 3.4.1 无序列表
使用中横线(`-`)或星号(`*`)来表示无序列表，注意后面需要加个空格。

<img src="./images-markdown/8.jpg" style="border-radius: 4px; width: 79%; box-shadow: 1px 1px 5px 2px #e5e5e5">

#### 3.4.2 有序列表
<img src="./images-markdown/9.jpg" style="border-radius: 4px; width: 79%; box-shadow: 1px 1px 5px 2px #e5e5e5">


#### 3.5 代码
<img src="./images-markdown/3.jpg" style="border-radius: 4px; width: 79%; box-shadow: 1px 1px 5px 2px #e5e5e5">


#### 3.6 分割线
<img src="./images-markdown/7.jpg" style="border-radius: 4px; width: 79%; box-shadow: 1px 1px 5px 2px #e5e5e5">

#### 3.7 超链接


#### 3.8 图片
<img src="./images-markdown/5.jpg" style="border-radius: 4px; width: 79%; box-shadow: 1px 1px 5px 2px #e5e5e5">


#### 3.9 强调


#### 3.10 字符转义


#### 3.11 表格
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








### 4. Markdown 扩展语法
#### 4.1 删除线
#### 4.2 代码块和语法高亮
#### 4.3 表格
#### 4.4 Task List（任务列)
#### 4.5 markdown 引入本地文件
- (1) 使用绝对路径
  
    + [transition-transform-animation.md](/Users/WANG/Github-clone/CSS-grocery/CSS3-过渡-转换-动画/transition-transform-animation.md)
- (2) 使用相对路径
    + [transition-transform-animation.md](File:///Users/WANG/Github-clone/CSS-grocery/CSS3-过渡-转换-动画/transition-transform-animation.md)

      注意 File 协议首字母要大写, `File://` 中英文字符不限, 文件夹亦可.
#### 4.6 自定义图片插入写法:
实际上也就是使用网页中的 HTML + CSS 源代码模式
```html
<img src="./images-markdown/markdown01.jpg" style="border-radius: 4px; width: 79%; box-shadow: 1px 1px 5px 2px #e5e5e5">
```

### 5. 编辑工具
因为 Markdown 本质上是一个纯文本，所以任何能打开纯文本的东西都可以来编辑 Markdown。

但如果你想要有预览功能，那么一款顺手的编辑功能还是有必要的。

在 Windows 和 MacOS 上推荐的编辑器有: **Visual Studio Code (VS code)**, **Typora**.

当然 Markdown 的编辑器还有很多, 比如对 LaTex 数学公式支持更好的 **Smark**; 内置文件管理器, 以及可以使用 iCloud 云服务器同步的 **Ulysses**, 可以多加尝试, 适合自己的才是最好的. 


### 6. 格式转换
#### 6.1 HTML
#### 6.2 PDF
#### 6.1 Word






#### 3.1 标题


#### 3.2 样式文本

您可以使用粗体、斜体或删除线文本来表示强调。

| 样式  | 语法 | 示例  | 输出  |
| :-----: | :-----: |:-----: | :-----: |
| 粗体(加粗)| `** **` | `**这是粗体文本**` | **粗体文本** |
| 斜体 | `* *` |  `*这是斜体文本*`  | *斜体文本* |
| 加粗斜体 | `*** ***`|`***所有这些文本都很重要***` | ***加粗斜体文本***|
| 删除线  | `~~ ~~` | `~~这是错误文本~~`  | ~~删除错误文本~~ |

<img src="./images-markdown/1.jpg" style="border-radius: 4px; width: 70%; box-shadow: 1px 1px 5px 2px #e5e5e5">




#### 3.5 引用



#### 3.6 超链接





#### 3.8 代码块







