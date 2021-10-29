# Markdown



## Markdown 中插入空格的方式: 
```
    紧贴 $a\!b$
    没有空格 $ab$
    小空格 a\,b
    中等空格 a\;b
    大空格 a\ b
    quad空格 $a\quad b$
    两个quad空格 $a\qquad b$
```



#### 4.5 markdown 引入本地文件
- (1) 使用绝对路径
  
    + [transition-transform-animation.md](/Users/WANG/Github-clone/CSS-grocery/CSS3-过渡-转换-动画/transition-transform-animation.md)
- (2) 使用相对路径
    + [transition-transform-animation.md](File:///Users/WANG/Github-clone/CSS-grocery/CSS3-过渡-转换-动画/transition-transform-animation.md)

      注意 File 协议首字母要大写, `File://` 中英文字符不限, 文件夹亦可.





### 2. Markdown vs 一般富文本编辑器
当我们希望拿一个东西来跟 Markdown 对比的时候, 相信很多人很自然地想到了 Word, 而想到 Word 也就容易想到 Word 与 `LaTex`$\color{red}{^{(2)}}$ 之间那旷日弥久的神圣战争. Word 与 LaTex 都是排版系统, 都提供了文档从书写到展示的完整解决方案, 但是实现方式各有不同:
+ Word 是**内容与形式同时处理**; LaTex 是**内容与形式分离**.
+ Word 是**所见即所得**; LaTex 是**源码(纯文本)输入**.

`(2)` LaTex 是什么?
> LaTex 是由美国计算机科学家莱斯利·兰伯特在 20 世纪 80 年代初期开发的 一种基于 `TeX`$\color{red}{^{(3)}}$ 的排版系统，用户可以使用 TEX 所提供的强大功能，在几天甚至几小时内生成具有书籍质量的印刷品。对于生成**复杂表格**和**数学公式**，这一点表现得尤为突出。因此它非常适用于生成**高印刷质量的科技和数学类文档**。这个系统同样适用于生成从简单的信件到完整书籍的所有其他种类的文档。

`(3)` TeX 排版软件 

> TeX 是一个由美国计算机教授高德纳（Donald Ervin Knuth）编写的排版软件。TeX的~~MIME类型为application/x-tex，~~是一款自由软件。它在学术界特别是数学、物理学和计算机科学界十分流行。TeX被普遍认为是一个优秀的排版工具，尤其是对于复杂数学公式的处理。利用 LaTeX 等终端软件，TeX 就能够排版出精美的文本以帮助人们辨认和查找。

*提示：* 关于 LaTex 和 Word 的更多对比请见知乎的这篇文章: [LaTeX 相对于 Word 有什么优势？](https://www.zhihu.com/question/20542113)

其实从这个角度看, Markdown 其实跟 LaTex 有很多相似之处, 完全兼具这两个特点, 都是源码输入, 都是内容与形式分离.

所以 Markdown 与富文本编辑器的比较其实可以分解成以下两点的比较:
1. **内容与形式分离** vs **所见即所得**
2. **源码输入** vs **所见即所得.**
