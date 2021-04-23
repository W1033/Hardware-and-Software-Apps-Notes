# Chrome 

Mac Chrome 调出控制台的快捷键: `fn` + `F12`



## 目录 (Catalog)
1. Chrome 下 advanced(进阶) 字体设置
2. Chrome 中长截图
3. Chrome 中保存当前网页中的所有图片



## 生词 (New Words)



## 内容 (Content)
### 1. Chrome 下 advanced(进阶) 字体设置
<img src="./images/chrome-advanced-font-setting.png"
    style="border-radius: 4px; width: 76%;
        box-shadow: 1px 1px 3px 2px #e5e5e5">


### 2. Chrome 中长截图
按 `F12`(Win) / `command + option + i`(Mac) 打开控制台, 接着按下
`Ctrl+Shift+P`(Win) / `Command + Shift + P`(Mac), 这时会出现一个搜索框,
输入 "Capture full size screenshot", 回车就可以自动截取整个网页内容并自动下载到本地.


### 3. Chrome 中保存当前网页中的所有图片
按 `F12`(Win) / `command + option + i`(Mac) 打开控制台, 点击 `Console`
进入控制台, 在输入框中输入
```
[...$$("img")].map(a => a.src).join('\r\n')
```
按回车,
然后我们可以看到网页内所有的图片的地址都被提取出来了.

而为了实现批量下载到本地, 我们可以将这些地址全部复制下来, 放在一个 “url.txt” 的文件内,
然后利用 wget 一键下载, 就可以全部保留到本地了。

