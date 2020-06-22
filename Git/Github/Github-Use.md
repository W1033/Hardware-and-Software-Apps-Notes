# Github 

## 目录(Catalog)
1. `git` 中的 `origin master`、`master` 以及 `push` 命令
2. 提交代码到 `Github`
3. 把下载的仓库代码添加到 `git version`
4. 使用 `Git` 回退到 `Github` 的某个历史版本：

5. 在 WebStorm 中 解决 git 冲突的方法:
6. 在命令行中解决 git 冲突的方法, 见 《Pro-Git》 等看完了再做笔记。  

7. 解决 Mac 下使用 V2ray 提交代码报 `Failed to connect to github.com port 443: Operation timed out` 的问题.
8. 查看 `追风岛 vpn Mac 客户端` 设置文件中的 `代理 ip` 和 `端口(port)`:
9. 把蓝灯的代理添加到 `/Users/WANG/.gitconfig` 中:
10. 把 `V2RayU` 客户端的代理 IP 添加到 `/Users/WANG/.gitconfig` 中

11.  Mac 下在 Chrome/ Firefox 中自定义 github 网站样式.
12. 通过命令行在本地仓库中删除远程 github 仓库中的文件/夹

00. 修改 `Win`/`Mac` 中 Github 下载速度缓慢的问题 (Note: 现在好像已经无效)



## 生词(New Words)
- **stylish ['staɪlɪʃ] --adj.时尚的; 优雅的; 潇洒的.**
    + She always faced stylish and elegant. 他总是时尚和优雅相伴.
    + Most of the clothes aren't that stylish. 大部分衣服都不太时髦.


## 内容(Content)
### 1. `git` 中的 `origin master`、`master` 以及 `push` 命令
- `git branch -a` 展示所有 git 分支
    + `* master` : 本地分支
    + `remotes/origin/HEAD -> origin/master` 远程分支
    + `remotes/origin/master` 远程分支
- `git branch -r` 展示远程分支
    + `origin/HEAD -> origin/master`
    + `origin/master`
- `git diff origin/origin master` 可以看到两者的不同
- `git push origin master` 省略了 <dst> 等价于 `git push origin master:master`
  其中 origin 指定了你要 push 到哪个 remote。一般写的形式为 
  `git push origin <src>:<dst>`，冒号前面表示 local branch 的名字，冒号后表示 
  remote repository 下 branch 的名字。注意，如果省略了 <dst>, git 会认为你想 push 到
  remote repository 下和 local branch 相同名字的 branch.
- `git push origin: mybranch` 在 origin repository 里面查找 mybranch 删除它。
  用一个空的去更新它，就相当于删除了。
- `git remote update origin --prune` 刷新远程分支列表

### 2. 提交代码到 `Github`
1. 创建 git 仓库
    + 上传代码之前一定要把本地的git升级到最新版本，不要问我为什么
    +  cd 到你的本地项目根目录下，执行git命令：
    +  `git init`   // 把这个目录变成Git可以管理的仓库 
2. 将项目的所有文件添加到仓库中
    + `git add .` 
    + (.代表全部)(如果只想添加某个特定的文件，只需要把.换成特定的文件名即可)       
3. 将 add 的文件 commit (委托，提交)到仓库
    + `git commit -m "注释语句"` 
4. 去 github 上创建自己的 Repository，(也可以使用现有的仓库)
5. 将本地的仓库关联到github上
    + `git remote add origin https://xxx//xxxx//xxx/xxxxx.git` 
      (仓库名尽量不要用驼峰写法，因为会报错)
    + (链接地址就是打开创建的仓库之后那个写着"Clone or download"的长条绿色按钮)
6. 上传 github 之前，需要先pull(拉下)一下，执行命令如下:
    + `git pull origin master`              
    + 下拉(pull)时提示错误 Fatal:refusing to merge unrelated histories
      (拒绝合并最近的历史记录) 的解决方法，把上面的代码改为:
    + `git  pull origin master --allow-unrelated-histories`  
      allow前面有两个破折号(dash)       
7. 最后一步上传代码到 github 远程仓库
    + `git push -u origin master` 
    + (执行完后如果没有异常就说明上传成功了，中间可能会让输入 Username 和 Password，
      输入 github 的账号和密码即可)

### 3. 把下载的仓库代码添加到 `git version`
- `file` --> `Settings` --> `Version Control`

### 4. 使用 `Git` 回退到 `Github` 的某个历史版本：
- 1、进入到项目文件夹，
    + 命令行中输入 `git log` 查看所有历史版本，获取 git 的某个历史版本的 commit id,
      (id 为 40 位的 16 进制数字，通过 SHA1 计算得到). 如果命令行窗口过小，不会一次
      显示完所有的历史版本，根据提示按下 return 便可以一直回退到最原始的版本。
    + Tip: 可以从 github 的 commits 提交记录对比找到想要的历史版本。
- 1-1、如果只想显示提交的历史版本的 commit id 号和对应的注释。可以在命令行中输入:
    + `git log --pretty=oneline`     
- 2、把本地项目中的文件恢复到历史版本
    + `git reset --hard id` (id 即为上面的 40 位随机字符)
    + 执行完 `git reset --hard id` 之后当前本地项目中的内容既是历史版本中的内容了。
- 3、把当前本地得到的历史版本推到远程服务器：
    + `git push -f -u origin master` (Tip: `-u` 可以省略)
    + 如果执行完上面的输入后，命令行提示 `Everything up-to-data` 文件并没有提交，
      原因可能是当前文件夹并没有执行过用 git 提交代码到 github 的操作，可以重新执行下面
      命令:
        - `git add .`
        - `git commit -m "message"`
        - `git push -f origin master`

### 5. 在 WebStorm 中 解决 git 冲突的方法:
- 先将本地仓库的修改的文件 commit, 由于此时本地文件和远程仓库有冲突，提交并不会成功，但
  WebStorm会提示 merge 代码，这样就会把把远程和本地做的修改同时保留，这样操作过来后，再次
  修改本地文件，便可以正常提交了。

### 6. 在命令行中解决 git 冲突的方法, 见 《Pro-Git》 等看完了再做笔记。  

### 7. 解决 Mac 下使用 V2ray 提交代码报 `Failed to connect to github.com port 443: Operation timed out` 的问题.
- `V2ray`客户端的代理导致的, webstorm 无法提交代码到 github, 从 `iTerm` 中也可以测试, 测试代码如下:
  ```shell
    git clone https://chromium.googlesource.com/v8/v8.git
  ```
  提示错误为: 
  ```base
    fatal: unable to access 'https://chromium.googlesource.com/v8/v8.git/':
    Failed to connect to chromium.googlesource.com port 443: Operation timed out
  ```
- 同时也不知道到底是下面哪一行代码起的作用: 
  (参考文章为: https://www.zhihu.com/question/26954892)
  ```shell
    # 查看有没有设置代理的代码(本机上没效果, 但是评论里说这 2 行代码是有效果的.)
    git config --global http.proxy
    # 取消代理
    git config --global --unset http.proxy
    git config --global --unset https.proxy

    # 文章里另外一种说:使用以下命令确认系统是否使用了代理
    env | grep -i proxy (这个为粘贴文章中的: env | grep -i proxy)
    / - 如果有设置 https 代理, 可以使用命令去除
    unset https_proxy
  ```
- 可能需要重启电脑.  

### 8. 查看 `追风岛 vpn Mac 客户端` 设置文件中的 `代理 ip` 和 `端口(port)`:
- (1) 在顶部追风岛客户端上右键查看 `复制用户主目录` 路径, 然后在 finder 中按下
  `Shift + Command + G` 弹出 `前往文件夹` 弹框, 粘贴复制的路径
  `/Users/WANG/Library/Application Support/com.nina.netfly/netfly` 点击 `前往`,
  在打开的文件夹中, 打开 `tempPath` 文件(Tip: 看不出文件后缀), 可看到 ip 
  `127.0.0.1`, port 为 `1080`.
- (2) 打开 `iTerm`, 通过如下代码设置 proxy:
  ```shell
    git config --global http.proxy 127.0.0.1:1080
    git config --global https.proxy 127.0.0.1:1080
  ```
- (3) 通过第 (2) 步设置的代码可以在 `.gitConfig` 文件中查看, 路径为
  `/Users/WANG/.gitconfig` 
- (4) 然后通过上面第(2) 步仍然不能提交代码, 个人认为可能是 `v2ray` 客户端的通病, 
  所以还是要打开 `.gitconfig` 文件删除通过上面 2 行代码添加的 `proxy`.
  然后通过下面 2 行代码删除系统内被设置的代理:
  ```shell
    # 查看有没有设置代理的代码(本机上没效果, 但是评论里说这 2 行代码是有效果的.)
    git config --global http.proxy
    # 取消代理
    git config --global --unset http.proxy
    git config --global --unset https.proxy
  ```
- (4) 重启电脑.

### 9. 把蓝灯的代理添加到 `/Users/WANG/.gitconfig` 中:
- (1) 每次启动蓝灯，它会自动修改操作系统的网络代理指向它自己。不需要我们手动配置，很是方便。
  需要网络代理的地方其实不止是浏览器，很多命令行工具也会访问网络。比如，我们通过
  homebrew 安装 dart 的时候，brew 命令会从 Google 的服务器上下载安装文件。
  然后你就会看到网络连接错误的提示信息。

  要解决这类问题，只需要为 Shell 设置两个环境变量 HTTP_PROXY 和 HTTPS_PROXY 即可。
  我们直接利用蓝灯在本地启动好的代理端口。

  我们首先找到蓝灯在本地启动的具体端口号。打开蓝灯，依次选择 
  `Settings -> ADVANCED SETTINGS` 即可看到蓝灯在本地选择的端口号。
- (2) 打开 `iTerm`, 通过如下代码设置 proxy:
  ```base
    git config --global http.proxy 127.0.0.1:49374
    git config --global https.proxy 127.0.0.1:49374
  ```
- (3) 通过第 (2) 步设置的代码可以在 `.gitConfig` 文件中查看, 路径为
  `/Users/WANG/.gitconfig` (tip: 可以修改本地仓库代码, 提交代码到 github 便可测试.)

### 10. 把 `V2RayU` 客户端的代理 IP 添加到 `/Users/WANG/.gitconfig` 中
- 查看电脑顶部的 `V2RayU` 客户端, 右键点击 `查看 config.json`, 在浏览器中打开后会看到
  ```js
    inbounds": [
    {
      "listen": "127.0.0.1",
      "protocol": "socks",
      "settings": {
        "udp": false,
        "auth": "noauth"
      },
      "port": "1080"
    },
    {
      "listen": "127.0.0.1",
      "protocol": "http",
      "settings": {
        "timeout": 360
      },
      "port": "1087"
    }
  ],
  ```
- (2) 其中 `"protocol": "http"` 即为要设置的 http 代理, 打开 `iTerm` 输入以下命令:
  ```base
    git config --global http.proxy 127.0.0.1:1087
    git config --global https.proxy 127.0.0.1:1087
  ```
- Tip: 关于 `V2Ray` 使用的更多教程, 去 google 搜索即可.

### 11. Mac 下在 Chrome/ Firefox 中自定义 github 网站样式. (下面以 Chrome 为例)
1. 在 Chrome 应用商店中安装 `Stylish` 插件.
    + `Stylish`--为任意网站自定义主题: 利用用户样式管理器 Stylish
      来重新编辑网站的样式. 您可利用 Stylish 为许多网站安装主题和皮肤,
      也可创建自己的注意和皮肤.
2. 打开 `github.com` 网站, 然后点击右上角的 `Stylish` 插件图标,
   在下拉图标中点击 `为此网站查找更多样式`, 进入到 Stylish 的主页后, 
   搜索 `Github-font-size`, 打开主题后, 点击 `Install Style`,
   然后回到 `github.com` 网站, 再次点击右上角的 `Stylish` 插件图标,
   在 `已安装样式` 中显示的就是你已安装的样式,  看到 `Github-font-size`
   样式后(Tip: 服务器应该在国外, 如果没有显示请稍作等待. 如果一直没有展示, 点击
   `Stylish on` 后面竖排的 `三个小圆点`, 点击 `管理样式`,
   在打开的窗口中找到安装的样式, 点击下面的 `修改`.), 点击 `编辑`
   按钮(像铅笔一样的图标), 在打开的页面中, 把下面第 3 步自定义的 `CSS`
   代码站粘贴到右侧的框内. <br/>
   **Note**: 如果英文好, 可以不用搜索 `Github-font-size` 插件来做更改,
   你可以直接在 `Stylish` 中自己 `Create One Style` 即可.
3. 自定义的 `CSS` 样式, 这些样式会覆盖 `github` 网站中的样式.
   ```css
    body {
        color: #333333;
    }
    .line-data, #gist-form .file .input textarea, .blob-code-inner {
        font-size: 14px !important;
    }
    code, pre {
        font-size: 14px !important;
    }
    .markdown-body {
        font-family: -apple-system, BlinkMacSystemFont, Segoe UI, Roboto, Oxygen, Ubuntu, Cantarell, Fira Sans, Droid Sans, Helvetica Neue, sans-serif;
        font-size: 15px;
        line-height: 1.6;
        word-wrap: break-word;
    }
    .markdown-body .highlight pre, .markdown-body pre {
        background-color: #f6f6f6;
        border-radius: 3px;
    }
    .markdown-body code, .markdown-body tt {
        background-color: #f6f6f6;
        border-radius: 4px;
        color: #e96900;
    }
    .pl-c {
        color: #aa6633;
    }
   ```
### 12. 通过命令行在本地仓库中删除远程 github 仓库中的文件/夹
- 前几天在 webstorm 中修改了仓库中几个文件夹, 最后提交到 github 后, 有一个
  名为 `《SQL基础教程》` 的文件夹一直存在(注意: 此文件夹内部为空),
  因为 github 网站不提供在线删除的功能,
  所以只能通过命令行来解决, 下面贴出执行命令:
  ```shell
    # 打开 iTerm 进入到相对应的本地仓库
    # (1) 删除本地 git 缓存
    git rm -r --cached <filename>

    # (2) 重新 track(跟组) 文件
    git add -A
    git commit -m '《SQL基础教程》'

    # (3) 推送到远程仓库 (确保当前代码是最新的)
    git push origin master
  ```









### 00. 修改 `Win`/`Mac` 中 Github 下载速度缓慢的问题 (Note: 现在好像已经无效)
- 通过查看下载链接，能够发现最终被指向到Amazon的服务器（http://github-cloud.s3.amazonaws.com）
 了。由于国内访问亚马逊网站非常慢，我们需要修改Hosts文件来实现流畅访问。
- 什么是 Hosts 文件？
   + 在互联网协议中，host表示能够同其他机器互相访问的本地计算机。一台本地机有
     唯一标志代码，同网络掩码一起组成IP地址，如果通过点到点协议通过ISP访问互联网，那么
     在连接期间将会拥有唯一的IP地址，这段时间内你的主机就是一个host。
   + 在这种情况下，host表示一个网络节点。host是根据 TCP/IP for Windows 的标准
     来工作的，它的作用是包含 IP地址 和 Host name(主机名) 的映射关系，是一个 映射 IP
     地址和 Host name(主机名)的规定，规定要求每段只能包括一个映射关系，IP 地址要放在
     每段的最前面，空格后再写上映射的 Host name 主机名。对于这段的映射说明
     用 “#” 分割后用文字说明。

1. 打开 Hosts 文件:
   + Windows 
       - Hosts 文件的路径：`C:\Windows\System32\drivers\etc`
   + Mac 中
       - 点击 "Finder (访达)" 图标打开, 然后点击屏幕上面的 "前往" --> "前往文件夹"
         输入 `/private/etc/` 点击前往按钮, 即可找到 hosts 文件夹.
         (或者: - 打开Finder，按快捷键组合 `Shift+Command+G` 查找文件,
         输入`/etc/hosts` 确认前往.)
       - 如需修改，可将hosts文件复制到其它位置（如桌面），之后再打开，编辑并保存后，
         将其拖拽回原来的文件夹，替换原文件即可。  
1. 追加域名的 IP 地址
   + 我们可以利用  `https://www.ipaddress.com`来获得一下 2 个 Github 域名的 IP 地址:
       - (1) github.com
       - (2) github.global.ssl.fastly.net
   + 打开网页后， 利用输入框分别查询两个域名, 然后记录查询的
       - github.com 查询为 IP Address: `192.30.253.113`
       - github.global.ssl.fastly.net 查询 IP Address 为: `199.232.5.194`
   + 将以上 2 个 IP 写入 Hosts 文件中. 然后保存. 
       - ```
            192.30.253.113 github.com
            199.232.5.194 github.global.ssl.fastly.net
         ```
1. 刷新 DNS 缓存
    + Windows 下: 在终端或 cmd 中, 执行以下命令: `ipconfig/flushdns` 即可.
    + Mac 下: 
        - (1st) 在 "iTerm/终端" 中输入: 
          ```base
            sudo Killall -HUP mDNSResponder 
            echo macOS DNS Cache Reset
          ```
        - (2nd) 第二种方法是如果不想使用命令行可以安装 PowerMyMac 
            + 打开软件后点击 "TookKit (工具套装)" --> "Maintenance (维修, 保养)"
              点击 "View" --> 单击左侧的 "Flush DNS" 然后点击右侧的 "Clean" 完成.
