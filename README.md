# Clash 分流规则，重点分流 AI 服务、字节海外 AI 服务 、 WEB3 应用、教育类 APP、开发者常用下载节点等分流服务

> 本项目基于 ACL4SSR 项目进行修改，用于个人使用

# 重点个性化分流规则介绍

| 分流规则名称 | 说明                                                                                  |
| ------------ | ------------------------------------------------------------------------------------- |
| 🌈 OpenAI    | 需美国节点的 AI 服务，OpenAI、Claude、Grok、Perplexity、Google 服务与 Gemini 合并在此 |
| 🌈 CiciAI    | 建议使用新加坡节点，确保字节海外版的 APP 和 AI 服务可正常使用                         |
| 👨‍💻 Developer | 建议使用流量大或免费节点，各种 docker 镜像、模型文件下载专用                          |
| 🔒 Web3      | 建议使用自建的安全节点，避免出现安全风险                                              |
| 🫙 自定义    | 放自建节点，搭配上方分流规则使用                                                      |

其他分流规则，包括 哔哩哔哩,Khan,海外媒体,Spotify,Netflix, YouTube, DisneyPlus, 游戏平台等常用规则。

## 重要提醒

部分AI网站和APP优先使用了 `HTTP/3 (QUIC)`协议，导致即使分流和TUN 模式下都可能无法使用服务，在确保IP干净也无法使用的情况下，请添加下面的自定义规则（可能会影响部分游戏服务）并启用。

```
AND,((NETWORK,UDP),(DST-PORT,443)),REJECT
```

特别说明：为什么要加第一行 REJECT？
hysteria2，这是一个基于 UDP 的暴力传输协议。

误区：很多人以为用了 UDP 协议的节点，就必须让所有 UDP 流量都通畅。

真相：

Hysteria2 协议本身确实是用 UDP 发包给服务器的（这是底层的车）。

但是，浏览器里的 HTTP/3 (QUIC) 也是 UDP。

当我们加了 - AND,((NETWORK,UDP),(DST-PORT,443)),REJECT 这一行时，我们并没有掐断 Hysteria2 的连接。我们只是在本地告诉浏览器：“别尝试用 QUIC 直连或者乱发 UDP 包了，老老实实把数据包封装成 TCP 给我”。

一旦浏览器转为 TCP，Clash 就会把它接管过来，完美地通过 Hysteria2 协议封装发出去。

# 使用方式

在订阅的 URL 上增加 config=[替换成下面 ini,或自定义]

[https://raw.githubusercontent.com/szkane/ClashRuleSet/main/Clash/kclash.ini](https://raw.githubusercontent.com/szkane/ClashRuleSet/main/Clash/kclash.ini)

订阅地址后面增加：`&config=https%3A%2F%2Fraw.githubusercontent.com%2Fszkane%2FClashRuleSet%2Frefs%2Fheads%2Fmain%2FClash%2Fkclash.ini`
