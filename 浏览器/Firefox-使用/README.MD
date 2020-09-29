## Firefox 使用集锦
- 如何更改火狐浏览器的界面，颜色、字体包括 web 控制台的字体等 ?
    + (1)、在火狐地址栏中输入: about:profiles
    + (2)、在打开的界面中, "正在使用此配置文件，因而不能删除" 下 --> 点击
        "根目录" 后的 "打开文件夹"
    + (3)、在打开的文件夹中查看是否有 chrome 文件夹，如果没有就新建一个， 然后进入
        到文件夹内，新建 `userChrome.css`
    + (4)、在 `userChrome.css` 内添加 css 样式
        ```css
            * {
                font-family: "Microsoft YaHei", Arial, Helvetica, sans-serif !important;
                letter-spacing: .5px !important;
                font-weight: 500 !important;
                line-height: 16px !important;
            }
        ```

## 如何查看一个网站都是用什么语言编写的?
- 为什么你们都不知道这个网站？直接把你要查看的网址复制粘贴就好了: `https://builtwith.com/`
- 补充一个可以看别人网站运用了哪些网络技术的网站：<a href="https://link.zhihu.com/?target=https%3A//w3techs.com/sites" class=" wrap external" target="_blank" rel="nofollow noreferrer" data-za-detail-view-id="1043">Web technologies used by a site</a>，打开后把网址最后加上你要查看的网站的网址即可。</p></span>


- 插件:
    + BuiltWith: BuiltWith is a web site profiler tool. Upon looking up a page,
      BuiltWith returns a list all the technologies in use on that page that 
      it can find.
        - built (build 的过去式 -- build [bɪld] -v.建造;开发;创建. n.体格;身材)
    + W3Techs: Opens shows which web technologies the current site is using.
    + 比价狗
    + 店查查
    + 翻译侠
    + 购物党实时比价工具
    + 京价保
    + 新同文堂
    + AdBlocker 广告栏
    + Disconnect
    + Easy YouTube Video Downloader Express
    + Enhancer for YouTube
    + FoxyTab
    + History Cleaner
    + HTTPS Everywhere
    + Octotree
    + PDF Mage
    + Refined Github
    + Video Download Pro
    + Video Downloader professional
    + Video DownloaderHelper
    + Video Speed Controller
    + YouTube 视频一键下载器 
    + YouTube Downloader 
    + YouTube Downloader Lite