# Clash 分流规则，重点分流 AI 服务、字节海外 AI 服务 、 WEB3 应用、教育类 APP、开发者常用下载节点等分流服务

> 本项目基于 ACL4SSL 项目进行修改，用于个人使用

# 重点个性化分流规则介绍

| 分流规则名称 | 说明                                                                                  |
| ------------ | ------------------------------------------------------------------------------------- |
| 🌈 OpenAI    | 需美国节点的 AI 服务，OpenAI、Claude、Grok、Perplexity、Google 服务与 Gemini 合并在此 |
| 🌈 CiciAI    | 建议使用新加坡节点，确保字节海外版的 APP 和 AI 服务可正常使用                         |
| 👨‍💻 Developer | 建议使用流量大或免费节点，各种 docker 镜像、模型文件下载专用                          |
| 🔒 Web3      | 建议使用自建的安全节点，避免出现安全风险                                              |
| 🫙 自定义     | 放自建节点，搭配上方分流规则使用                                                      |

# 使用方式

在订阅的 URL 上增加 config=[替换成下面 ini,或自定义]

[https://raw.githubusercontent.com/szkane/ClashRuleSet/main/Clash/kclash.ini](https://raw.githubusercontent.com/szkane/ClashRuleSet/main/Clash/kclash.ini)
