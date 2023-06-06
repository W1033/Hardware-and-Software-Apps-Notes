# 用 Markdown 做 PPT



<p style="background-color:#f9e2d2; border-radius:6px; padding:20px;"><strong style="color:#dd5a2b;">Hint：</strong>作为简单的展示用 PPT 可以用，复杂的效果目前我个人看不行。</p>



> 文章来源：https://juejin.cn/post/7062979350651469831



相信绝大多数朋友做 PPT（幻灯片 / Slides / Deck 等各种称呼了）都是用的 PowerPoint 或者 KeyNote 吧？功能是比较强大，但你有没有遇到过这样的痛点：

- 各种标题、段落的格式不统一，比如字体大小、行间距等等各个页面不太一样，然后得用格式刷来挨个刷一下。
- 想给 PPT 做版本控制，然后就保存了各种复制版本，比如“一版”、“二版”、“终版”、“最终版”、“最终不改版”、“最终稳定不改版”等等，想必大家都见过类似这样的场景吧。
- 想插入代码，但是插入之后发现格式全乱了或者高亮全没了，然后不得不截图插入进去。
- 想插入个公式，然后发现 PPT、Keynote 对 Latex 兼容不太好或者配置稍微麻烦，就只能自己重新敲一遍或者贴截图。
- 想插入一个酷炫的交互组件，比如嵌入一个微博的网页页面实时访问、插入一个可以交互的组件、插入一个音乐播放器组件，原生的 PPT 功能几乎都不支持，这全得依赖于 PowerPoint 或者 KeyNote 来支持才行。

如果你遇到这些痛点，那请你一定要看下去。如果你没有遇到，那也请你看下去吧（拜托。

好，说回正题，我列举了那么多痛点，那这些痛点咋解决呢？

能！甚至解决方案更加轻量级，那就是用 Markdown 来做 PPT！

你试过用 Markdown 写 PPT 吗？没有吧，试试吧，试过之后你就发现上面的功能简直易如反掌。

具体怎么实现呢？

接下来，就有请今天的主角登场了！它就是 Slidev。


## 什么是 Slidev？

简而言之，Slidev 就是可以让我们用 Markdown 写 PPT 的工具库，基于 Node.js、Vue.js 开发。

利用它我们可以简单地把 Markdown 转化成 PPT，而且它可以支持各种好看的主题、代码高亮、公式、流程图、自定义的网页交互组件，还可以方便地导出成 pdf 或者直接部署成一个网页使用。

官方主页：[sli.dev/](https://link.juejin.cn?target=https%3A%2F%2Fsli.dev%2F)

中文：https://cn.sli.dev/guide/why.html#slidev

Github: 从官网内可以跳转

## 安装和启动

下面我们就来了解下它的基本使用啦。

首先我们需要先安装好 Node.js，推荐 14.x 及以上版本，安装方法见 [setup.scrape.center/nodejs](https://link.juejin.cn?target=https%3A%2F%2Fsetup.scrape.center%2Fnodejs)。

接着，我们就可以使用 npm 这个命令了。

然后我们可以初始化一个仓库，运行命令如下：

```sh
npm init slidev@latest
```

这个命令就是初始化一个 Slidev 的仓库，运行之后它会让我们输入和选择一些选项，如图所示：

![img](readme.assets/550de98d10404a408d1231ee4e5540bdtplv-k3u1fbpfcp-zoom-in-crop-mark4536000.webp)

比如上图就是先输入项目文件夹的名称，比如这里我取名叫做 slidevtest。

总之一些选项完成之后，Slidev 会在本地 3000 端口上启动，如图所示：

![img](readme.assets/7a55a312d4494a77996a9814ea5a6662tplv-k3u1fbpfcp-zoom-in-crop-mark4536000.webp)

接着，我们就可以打开浏览器 [http://localhost:3000](https://link.juejin.cn?target=http%3A%2F%2Flocalhost%3A3000) 来查看一个 HelloWorld 版本的 PPT 了，如图所示：

![img](readme.assets/928a740e3a934f77865e18c23a75818dtplv-k3u1fbpfcp-zoom-in-crop-mark4536000.webp)

我们可以点击空格进行翻页，第二页展示了一张常规的 PPT 的样式，包括标题、正文、列表等，如图所示：

![img](readme.assets/7ec88a5a32ff4557904deaf8c56adf7etplv-k3u1fbpfcp-zoom-in-crop-mark4536000.webp)

那这一页的 Markdown 是什么样的呢？其实就是非常常规的 Markdown 文章的写法，内容如下：

```Markdown
# What is Slidev?

Slidev is a slides maker and presenter designed for developers, consist of the following features

- 📝 **Text-based** - focus on the content with Markdown, and then style them later
- 🎨 **Themable** - theme can be shared and used with npm packages
- 🧑‍💻 **Developer Friendly** - code highlighting, live coding with autocompletion
- 🤹 **Interactive** - embedding Vue components to enhance your expressions
- 🎥 **Recording** - built-in recording and camera view
- 📤 **Portable** - export into PDF, PNGs, or even a hostable SPA
- 🛠 **Hackable** - anything possible on a webpage

<br>
<br>

Read more about [Why Slidev?](https://sli.dev/guide/why)
```

是不是？我们只需要用同样格式的 Markdown 语法就可以轻松将其转化为 PPT 了。

## 快捷键操作

再下一页介绍了各种快捷键的操作，这个就很常规了，比如点击空格、上下左右键来进行页面切换，如图所示：

![img](readme.assets/d41aef96cdba45c7b88e2252b1940f6ftplv-k3u1fbpfcp-zoom-in-crop-mark4536000.webp)

更多快捷键的操作可以看这里的说明：https://sli.dev/guide/navigation.html，一些简单的快捷键列举如下：

- f：切换全屏
- right / space：下一动画或幻灯片
- left：上一动画或幻灯片
- up：上一张幻灯片
- down：下一张幻灯片
- o：切换[幻灯片总览](https://link.juejin.cn?target=https%3A%2F%2Fcn.sli.dev%2Fguide%2Fnavigation.html%23slides-overview)
- d：切换暗黑模式
- g：显示“前往...”

## 代码高亮

接下来就是代码环节了，因为 Markdown 对代码编写非常友好，所以展示自然也不是问题了，比如代码高亮、代码对齐等都是常规操作，如图所示：

![img](readme.assets/1b2870c42ece4b7187d2be4116e253b1tplv-k3u1fbpfcp-zoom-in-crop-mark4536000.webp)

那左边的代码定义就直接这么写就行了：

~~~Markdown
# Code

Use code snippets and get the highlighting directly![^1]

```ts {all|2|1-6|9|all}
interface User {
  id: number
  firstName: string
  lastName: string
  role: string
}

function updateUser(id: number, update: User) {
  const user = getUser(id)
  const newUser = {...user, ...update}  
  saveUser(id, newUser)
}
```
~~~

由于是 Markdown，所以我们可以指定是什么语言，比如 TypeScript、Python 等等。

## 网页组件

接下来就是非常酷炫的环节了，我们还可以自定义一些网页组件，然后展示出来。

比如我们看下面的一张图。左边就呈现了一个数字计数器，点击左侧数字就会减 1，点击右侧数字就会加 1；另外图的右侧还嵌入了一个组件，这里显示了一个推特的消息，通过一个卡片的形式呈现了出来，不仅仅可以看内容，甚至我们还可以点击下方的喜欢、回复、复制等按钮来进行一些交互。

这些功能在网页里面并不稀奇，但是如果能做到 PPT 里面，那感觉就挺酷的。

![img](readme.assets/6735866bfc574673ad4ddb1c18812a65tplv-k3u1fbpfcp-zoom-in-crop-mark4536000.webp)

那这一页怎么做到的呢？这个其实是引入了一些基于 Vue.js 的组件，本节对应的 Markdown 代码如下：

~~~Markdown
# Components

<div grid="~ cols-2 gap-4">
<div>

You can use Vue components directly inside your slides.

We have provided a few built-in components like `<Tweet/>` and `<Youtube/>` that you can use directly. And adding your custom components is also super easy.

```html
<Counter :count="10" />
```

<!-- ./components/Counter.vue -->
<Counter :count="10" m="t-4" />

Check out [the guides](https://sli.dev/builtin/components.html) for more.

</div>
<div>

```html
<Tweet id="1390115482657726468" />
```

<Tweet id="1390115482657726468" scale="0.65" />

</div>
</div>
~~~

这里我们可以看到，这里引入了 Counter、Tweet 组件，而这个 Counter 就是 Vue.js 的组件，代码如下：

```Markdown
<script setup lang="ts">

import { ref } from 'vue'

const props = defineProps({
  count: {
    default: 0,
  },
})

const counter = ref(props.count)
</script>

<template>
  <div flex="~" w="min" border="~ gray-400 opacity-50 rounded-md">
    <button
      border="r gray-400 opacity-50"
      p="2"
      font="mono"
      outline="!none"
      hover:bg="gray-400 opacity-20"
      @click="counter -= 1"
    >
      -
    </button>
    <span m="auto" p="2">{{ counter }}</span>
    <button
      border="l gray-400 opacity-50"
      p="2"
      font="mono"
      outline="!none"
      hover:bg="gray-400 opacity-20"
      @click="counter += 1"
    >
      +
    </button>
  </div>
</template>
```

这就是一个标准的基于 Vue.js 3.x 的组件，都是标准的 Vue.js 语法，所以如果我们要添加想要的组件，直接自己写就行了，什么都能实现，只要网页能支持的，统统都能写！

## 主题定义

当然，一些主题定制也是非常方便的，我们可以在 Markdown 文件直接更改一些配置就好了，比如就把 theme 换个名字，整个主题样式就变了，看如下的对比图：

![img](readme.assets/ca8f7043c53c4c64ab55d91452fdfcectplv-k3u1fbpfcp-zoom-in-crop-mark4536000.webp)

上面就是一些内置主题，当然我们也可以去官方文档查看一些别人已经写好的主题，见：https://sli.dev/themes/gallery.html。

另外我们自己写主题也是可以的，所有的主题样式都可以通过 CSS 等配置好，想要什么就可以有什么，见：https://sli.dev/themes/write-a-theme.html

## 公式和图表

接下来就是一个非常强大实用的功能，公式和图表，支持 Latex、流程图，如图所示：

![img](readme.assets/c9e78904f9af4036bd9f4c92e242e71ctplv-k3u1fbpfcp-zoom-in-crop-mark4536000.webp)

![img](readme.assets/ef04bb30f4734719b291843099a40faftplv-k3u1fbpfcp-zoom-in-crop-mark4536000.webp)

比如上面的 Latex 的源代码就是这样的：

```LaTeX
LaTeX复制代码Inline $\sqrt{3x-1}+(1+x)^2$

Block
$$
\begin{array}{c}

\nabla \times \vec{\mathbf{B}} -\, \frac1c\, \frac{\partial\vec{\mathbf{E}}}{\partial t} &
= \frac{4\pi}{c}\vec{\mathbf{j}}    \nabla \cdot \vec{\mathbf{E}} & = 4 \pi \rho \\

\nabla \times \vec{\mathbf{E}}\, +\, \frac1c\, \frac{\partial\vec{\mathbf{B}}}{\partial t} & = \vec{\mathbf{0}} \\

\nabla \cdot \vec{\mathbf{B}} & = 0

\end{array}
$$
```

其语法也是和 Latex 一样的。

其背后是怎么实现的呢？其实是因为 Slidev 默认集成了 Katex 这个库，见：[katex.org/](https://link.juejin.cn?target=https%3A%2F%2Fkatex.org%2F)，有了 Katex 的加持，所有公式的显示都不是事。

## 页面分隔

有的朋友就好奇了，既然是用 Markdown 写 PPT，那么每一页之间是怎么分割的呢？

其实很简单，最常规的，用三条横线分割就好了，比如：

```markdown
---
layout: cover
---

# 第 1 页

This is the cover page.

---

# 第 2 页

The second page
```

当然，除了使用三横线，我们还可以使用更丰富的定义模式，可以给每一页制定一些具体信息，就是使用两层三横线。

比如这样：

```markdown
---
theme: seriph
layout: cover
background: 'https://source.unsplash.com/1600x900/?nature,water'
---
```

上面这样的配置可以替代三横线，是另一种可以用作页面分隔的写法，借助这种写法我们可以定义更多页面的具体信息。

## 备注

当然我们肯定也想给 PPT 添加备注，这个也非常简单，通过注释的形式写到 Markdown 源文件就好了：

```LaTeX
---
layout: cover
---

# 第 1 页

This is the cover page.

<!-- 这是一条备注 -->
```

这里可以看到其实就是用了注释的特定语法。

## 演讲者头像

当然还有很多酷炫的功能，比如说，我们在讲 PPT 的时候，可能想同时自己也出镜，Slidev 也可以支持。

因为开的是网页，而网页又有捕捉摄像头的功能，所以最终效果可以是这样子：

![img](readme.assets/7fa977d2f5714b549a50f70b888589e0tplv-k3u1fbpfcp-zoom-in-crop-mark4536000.webp)

是的没错！右下角就是演讲者的个人头像，它被嵌入到了 PPT 中！是不是非常酷！

## 演讲录制

当然，Slidev 还支持演讲录制功能，因为它背后集成了 WebRTC 和 RecordRTC 的 API，一些录制配置如下所示：

![img](readme.assets/e8616bfda18841f09bcfdb393dd9ee37tplv-k3u1fbpfcp-zoom-in-crop-mark4536000.webp)

所以，演讲过程的录制完全不是问题。

具体的操作可以查看：https://sli.dev/guide/recording.html

## 部署

当然用 Slidev 写的 PPT 还可以支持部署，因为这毕竟就是一个网页。

而且部署非常简单和轻量级，因为这就是一些纯静态的 HTML、JavaScript 文件，我们可以轻松把它部署到 GitHub Pages、Netlify 等站点上。

**试想这么一个场景：别人在演讲之前还在各种拷贝 PPT，而你打开了一个浏览器直接输入了一个网址，PPT 就出来了，众人惊叹，就问你装不装逼？**

具体的部署操作可以查看：https://sli.dev/guide/hosting.html

让我们看几个别人已经部署好的 PPT，直接网页打开就行了：

- https://demo.sli.dev/composable-vue/1

就是这么简单方便。

## 版本控制

什么？你想实现版本控制，那再简单不过了。

Markdown 嘛，配合下专业版本管理工具 Git，版本控制再也不是难题。

## 总结

以上就是对 Slidev 的简单介绍，确实不得不说有些功能真的非常实用，而且我本身特别喜欢 Markdown 和网页开发，所以这个简直对我来说太方便了。

