# Typora



## ▲ Typora 1.8 添加的功能：Github Style Alert (Github 风格警告)

*Added: 2024.01.25*

> [!NOTE]  
> Highlights information that users should take into account, even when skimming.

[! 注意]
突出显示用户即使在浏览时也应考虑的信息。

> [!TIP]
> Optional information to help a user be more successful.

[!提示]
帮助用户取得更大成功的可选信息。

> [!IMPORTANT]  
> Crucial information necessary for users to succeed.

[!重要]
用户成功所需的关键信息。

> [!WARNING]  
> Critical content demanding immediate user attention due to potential risks.

[!警告]
由于潜在风险，需要用户立即关注的关键内容。

> [!CAUTION]
> Negative potential consequences of an action.

[!警告]
行动的潜在负面后果。



## ▲ 更改 Typora 侧边栏 sidebar 的字体大小

*Added: 2024.01.23*

找到当前主题（e.g.: vue-dark) vscode 打开后搜索 sidebar

<img src="./readme.assets/image-20240123113522800.png" alt="image-20240123113522800" style="zoom:50%;" />



## ▲ Typora 的 Vue 主题设置宋体的 CSS 代码

```css
:root {
    --side-bar-bg-color: #fff;
    --control-text-color: #777;
    --font-sans-serif: 'Source Sans Pro', '宋体', 'Source Code Pro', sans-serif !important;
    --font-monospace: 'Source Sans Pro', '宋体', 'Source Code Pro' !important;
}

html {
    font-size: 16px;
}

body {
    font-family: var(--font-sans-serif);
    color: #000;
    -webkit-font-smoothing: antialiased;
    line-height: 1.6rem;
    letter-spacing: 0;
    margin: 0;
    overflow-x: hidden;
}

```