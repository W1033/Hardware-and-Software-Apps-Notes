# [Clash 配置 rule-providers 实现自由搭配及自动更新规则功能

> 原文地址：https://www.920.im/clash-rule-providers-configuration/

本文最后更新于 2022 年 4 月 20 日，已超过 468 天没有更新，如文章内容或资源失效，请留言反馈。订阅 [TG 频道](https://www.920.im/go.html/?url=https://t.me/xjzim) 获取更多福利

## 前言

目前各大订阅转换服务在选择 clash 订阅类型时，会将所选的远程配置中所有 rules 规则全部拉取并填充在相应的 yaml 配置文件中。这样的配置文件有以下几点弊端：

1. 文件内容及行数较多
2. 自行添加及修改部分规则内容较为麻烦
3. 对于自己搭建节点的用户，无法自动更新
4. 受限于远程配置，无法自由组合自己想要的规则

在了解到 [Clash](https://www.920.im/tag/clash/) Premium Core 支持 [rule-providers](https://www.920.im/tag/rule-providers/) 功能后，我们便可以完美的解决上述问题。

## 文件配置

首先我们来看下官方 wiki 中对于 [rule-providers](https://www.920.im/tag/rule-providers/) 字段及对应 rules 字段的配置示例说明：

```yaml
rule-providers:
  apple:
    behavior: "domain" # domain, ipcidr or classical (premium core only)
    type: http
    url: "url"
    interval: 3600
    path: ./apple.yaml
    microsoft:
    behavior: "domain"
    type: file
    path: /microsoft.yaml
```

我们可以看到在 [rule-providers](https://www.920.im/tag/rule-providers/) 字段中，需要有以下内容：

- `behavior`：可填写 `domain` `ipcidr` `classical`

- `type`：可填写 http 及 file「在线文件填写 http，本地文件填写 file」

- `interval`：更新间隔

- `path`：文件储存路径

    

`behavior` 的三种类型对应的文件内容格式分别如下：

### domain

```yaml
payload:  
	- '.blogger.com'  
	- '*.*.microsoft.com'  
	- 'books.itunes.apple.com'
```

### ipcidr

```yaml
payload:  
	- '192.168.1.0/24'  
	- '10.0.0.0.1/32'
```

### classical

```yaml
payload:  
	- DOMAIN-SUFFIX,google.com 
	- DOMAIN-KEYWORD,google  
    - DOMAIN,ad.com  
    - SRC-IP-CIDR,192.168.1.201/32  
    - IP-CIDR,127.0.0.0/8  
    - GEOIP,CN  
    - DST-PORT,80  
    - SRC-PORT,7777  
    # MATCH is not necessary here
```

接着我们来看对应的 rules 字段配置示例：

```yaml
rules:  
    - RULE-SET,apple,REJECT  
    - RULE-SET,microsoft,policy
```

我们可以看到在 rules 字段中，需要有以下内容：

- RULE-SET 「默认，无需修改」
- [rule-providers](https://www.920.im/tag/rule-providers/) 对应的名称「如上述例子中的 apple、microsoft 等」
- 处理方式「如直连、代理、拒绝等」

------

在知道以上配置规则样式后，我们以使用比较知名的 ACL4SSR Online 在线规则为例，进行相应配置编写如下：

```yaml
rule-providers:
# 内容：可以自行添加其它自己想要在线规则列表
  LocalAreaNetwork:
    behavior: classical # domain, ipcidr or classical (premium core only)
    type: http
    url: "https://raw.githubusercontent.com/ACL4SSR/ACL4SSR/master/Clash/Providers/LocalAreaNetwork.yaml"
    interval: 86400
    path: ./ACL4SSR/LocalAreaNetwork.yaml
  UnBan:
    behavior: classical 
    type: http
    url: "https://raw.githubusercontent.com/ACL4SSR/ACL4SSR/master/Clash/Providers/UnBan.yaml"
    interval: 86400
    path: ./ACL4SSR/UnBan.yaml
  BanAD:
    behavior: classical 
    type: http
    url: "https://raw.githubusercontent.com/ACL4SSR/ACL4SSR/master/Clash/Providers/BanAD.yaml"
    interval: 86400
    path: ./ACL4SSR/BanAD.yaml
  BanProgramAD:
    behavior: classical 
    type: http
    url: "https://raw.githubusercontent.com/ACL4SSR/ACL4SSR/master/Clash/Providers/BanProgramAD.yaml"
    interval: 86400
    path: ./ACL4SSR/BanProgramAD.yaml
  GoogleFCM:
    behavior: classical 
    type: http
    url: "https://raw.githubusercontent.com/ACL4SSR/ACL4SSR/master/Clash/Providers/Ruleset/GoogleFCM.yaml"
    interval: 86400
    path: ./ACL4SSR/GoogleFCM.yaml
  GoogleCN:
    behavior: classical 
    type: http
    url: "https://raw.githubusercontent.com/ACL4SSR/ACL4SSR/master/Clash/Providers/Ruleset/GoogleCN.yaml"
    interval: 86400
    path: ./ACL4SSR/GoogleCN.yaml
  SteamCN:
    behavior: classical 
    type: http
    url: "https://raw.githubusercontent.com/ACL4SSR/ACL4SSR/master/Clash/Providers/Ruleset/SteamCN.yaml"
    interval: 86400
    path: ./ACL4SSR/SteamCN.yaml
  Microsoft:
    behavior: classical 
    type: http
    url: "https://raw.githubusercontent.com/ACL4SSR/ACL4SSR/master/Clash/Providers/Ruleset/Microsoft.yaml"
    interval: 86400
    path: ./ACL4SSR/Microsoft.yaml
  Apple:
    behavior: classical 
    type: http
    url: "https://raw.githubusercontent.com/ACL4SSR/ACL4SSR/master/Clash/Providers/Ruleset/Apple.yaml"
    interval: 86400
    path: ./ACL4SSR/Apple.yaml
  Telegram:
    behavior: classical 
    type: http
    url: "https://raw.githubusercontent.com/ACL4SSR/ACL4SSR/master/Clash/Providers/Ruleset/Telegram.yaml"
    interval: 86400
    path: ./ACL4SSR/Telegram.yaml
  ProxyLite:
    behavior: classical 
    type: http
    url: "https://raw.githubusercontent.com/ACL4SSR/ACL4SSR/master/Clash/Providers/ProxyLite.yaml"
    interval: 86400
    path: ./ACL4SSR/ProxyLite.yaml
  ProxyMedia:
    behavior: classical 
    type: http
    url: "https://raw.githubusercontent.com/ACL4SSR/ACL4SSR/master/Clash/Providers/ProxyMedia.yaml"
    interval: 86400
    path: ./ACL4SSR/ProxyMedia.yaml
  ChinaDomain:
    behavior: classical 
    type: http
    url: "https://raw.githubusercontent.com/ACL4SSR/ACL4SSR/master/Clash/Providers/ChinaDomain.yaml"
    interval: 86400
    path: ./ACL4SSR/ChinaDomain.yaml
  ChinaCompanyIp:
    behavior: ipcidr 
    type: http
    url: "https://raw.githubusercontent.com/ACL4SSR/ACL4SSR/master/Clash/Providers/ChinaCompanyIp.yaml"
    interval: 86400
    path: ./ACL4SSR/ChinaCompanyIp.yaml
rules:
# 内容：可以自行添加其它自己想要的规则
# ACL4SSR Online
 - RULE-SET,LocalAreaNetwork,🎯 全球直连
 - RULE-SET,UnBan,🎯 全球直连
 - RULE-SET,BanAD,🛑 全球拦截
 - RULE-SET,BanProgramAD,🍃 应用净化
 - RULE-SET,GoogleFCM,📢 谷歌FCM
 - RULE-SET,GoogleCN,🎯 全球直连
 - RULE-SET,SteamCN,🎯 全球直连
 - RULE-SET,Microsoft,Ⓜ️ 微软服务
 - RULE-SET,Apple,🍎 苹果服务
 - RULE-SET,Telegram,📲 电报信息
 - RULE-SET,ProxyLite,🚀 节点选择 
 - RULE-SET,ProxyMedia,🌍 国外媒体
 - RULE-SET,ChinaDomain,🎯 全球直连
 - RULE-SET,ChinaCompanyIp,🎯 全球直连
 - GEOIP,CN,🎯 全球直连
 - MATCH,🐟 漏网之鱼
```

我们完全可以在上述内容列表的基础上，自行添加自己想要的 rule-providers 列表或者相应的 rules 规则，并且可以实现自动更新的功能。

rule-providers 字段及功能只支持 premium core 使用，非 premium core 可能不支持相关字段，请大家自行尝试。个人测试 CFW，Openclash 等均支持

## 题外话

我们在 clash 的 wiki 中同样可以看到其还支持类似的 proxy-providers 功能，我们拓展一下，应该可以实现任意机场同自己节点的组合并且同样支持动态更新相应节点。

## 参考链接

- [https://github.com/Dreamacro/clash/wiki/premium-core-features](https://www.920.im/go.html/?url=https://github.com/Dreamacro/clash/wiki/premium-core-features)
- [https://github.com/ACL4SSR/ACL4SSR/issues/729](https://www.920.im/go.html/?url=https://github.com/ACL4SSR/ACL4SSR/issues/729)