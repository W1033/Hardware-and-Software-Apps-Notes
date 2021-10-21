# Github


## 使用 SSH 拉取和提交代码到 Github

SSH(Secure Shell Protocol)

> 中文文档链接: https://docs.github.com/cn/authentication/connecting-to-github-with-ssh

### 检查现有 SSH 密钥
> https://docs.github.com/cn/authentication/connecting-to-github-with-ssh/checking-for-existing-ssh-keys

### 生成新的 SSH key
> https://docs.github.com/cn/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent

```
Your identification has been saved in /Users/WANG/.ssh/id_ed25519.
Your public key has been saved in /Users/WANG/.ssh/id_ed25519.pub.
The key fingerprint is:
SHA256:Xu3J4TH97X4toM0+9M8WMAzOpHDkm31qV8s1tzaQc8I forownwang@gmail.com
The key's randomart image is:
+--[ED25519 256]--+
|        ..       |
|       ... o     |
|        o.= o    |
|         .++.=.  |
|        So..=E++o|
|       . . +==BoB|
|        .  B=+ *=|
|          o = +o=|
|           ... =*|
+----[SHA256]-----+
```
生成的 3 个文件内容见 随笔记 备份

### 将 SSH 密钥添加到 ssh-agent
1. 在后台启动 ssh 代理。
```shell
    eval "$(ssh-agent -s)"
    > Agent pid 16559
```
根据您的环境，您可能需要使用不同的命令。 例如，您可能需要在启动 ssh 代理之前运行 sudo-s-H 来使用根访问，或者您可能需要使用 `exec ssh-agent bash` 或 `exec ssh-agent zsh` 来运行 ssh-agent。
2. 见在线文档
3. 见在线文档
4. 见在线文档

### 新增 SSH 密钥到 Github 账户
> https://docs.github.com/cn/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account



众所周知在 clone GitHub 仓库时可以使用 HTTPS 或者 SSH 进行 clone，而 SSH 却没有 HTTPS 的网络连接问题，所以可以将 push/pull 的连接方式由 HTTPS 改为 SSH。

> 要求：你需要提前生成 SSH 公私钥对，并将公钥添加到你的 GitHub 账户中。关于这一部分的详细信息，请参阅 [Connecting to GitHub with SSH](https://docs.github.com/en/github/authenticating-to-github/connecting-to-github-with-ssh)。

进入仓库对应目录，执行如下命令：

```
$ git remote set-url origin git@github.com:xxx/xxx.git
```

更改完成后，可以使用如下命令查看当前的 origin 地址：

```
$ git remote -v
```

