# Mihomo-RuleSets

自建 Mihomo 分流规则集（Rule Set）合集：多家公开作者规则全量合并、逐条审计、零自建，供 Mihomo 内核以 rule-provider（classical）方式加载。

文件直链格式：`https://raw.githubusercontent.com/PuthsenTaylor/Mihomo-RuleSets/main/<文件名>`

## 分流理念

- **按公司归属分流**：谷歌走谷歌、苹果走苹果，有总公司归属的服务只进总公司集，不按地理名单混编。
- **国外全代理、国内全直连**：海外服务的第一命中落自家代理策略组，不落漏网、不落直连；国内服务一律直连，在服务商眼中始终是国内 IP，账号风控画像连贯。国内公司的明确海外服务不按国内算，按服务本体归代理侧、不入直连集。
- **宁可漏、不可误杀**：多租户共用平台的整段域名不入集，宁可让个别域名走兜底，也不劫持无关流量。
- **零自建**：每条规则均有公开作者出处，不凭空编写域名；拿不准归属的条目不入集。
- **字节跳动三分离**：海外字节（TikTok、CapCut、Lark 海外版、BytePlus 等）与全球共用基础设施归 TikTok 集走代理，国内字节（抖音、头条、飞书、火山引擎等）不进海外集、也不入名单制的国内直连集（字节不在点名名单内），在配套配置中经 GEOSITE 兜底走直连，两边彻底划开。

## 一键使用：覆写脚本（推荐）

不想自己写规则的，直接用配套覆写脚本 **MihomoOverride.js**：在支持 JavaScript 覆写的 Mihomo 客户端中，把脚本地址填入覆写（脚本）一栏即可。脚本会保留你订阅自带的节点与传输参数，只重建 DNS、嗅探、全套策略组、本仓库全套规则集的引用与全部分流规则；脚本本身不包含任何节点信息，节点全部来自你自己的订阅。

脚本地址（raw 直链，可直接粘贴到客户端）：

```
https://gist.github.com/PuthsenTaylor/6d3a119274d974d6dbadf6c05e669ccd/raw/MihomoOverride.js
```

脚本版本与本仓库配套维护、同步更新。用脚本接入后，无需再按下面的手动方式逐个添加 rule-provider。

## 文件清单

全仓 23 份文件，共 12,998 条；每份集按域名与 IP 拆分为 `_Domain` / `_IP` 双文件（个别集只有域名文件）。

| 文件 | 版本 | 条数 | 内容 |
| --- | --- | --- | --- |
| [LAN_Domain.yaml](LAN_Domain.yaml) | v2.5.0 | 142 | 局域网本地域名、路由器管理域名、本地服务发现域名、反向解析域名等 |
| [LAN_IP.yaml](LAN_IP.yaml) | v2.5.0 | 28 | 私有、保留、环回、链路本地、组播、共享地址空间与文档示例等 IP 地址段 |
| [Google_Domain.yaml](Google_Domain.yaml) | v2.5.1 | 885 | YouTube、Gmail、Gemini、Google Play、Google Search、Google Maps、Google Drive、Google Photos 等谷歌全线服务 |
| [Google_IP.yaml](Google_IP.yaml) | v2.5.0 | 7090 | 谷歌全球 IP 地址段 |
| [Apple_Domain.yaml](Apple_Domain.yaml) | v2.5.4 | 1439 | iCloud、App Store、Apple Music、Apple TV、Beats 等苹果全线服务 |
| [Apple_IP.yaml](Apple_IP.yaml) | v2.5.0 | 13 | 苹果全球 IP 地址段 |
| [Netflix_Domain.yaml](Netflix_Domain.yaml) | v2.5.0 | 23 | Netflix、Fast.com 等奈飞服务域名 |
| [Netflix_IP.yaml](Netflix_IP.yaml) | v2.5.0 | 1121 | 奈飞全球 IP 地址段 |
| [Disney_Domain.yaml](Disney_Domain.yaml) | v2.5.1 | 242 | Disney+、Hulu、ESPN、ABC、Marvel、Star Wars、国家地理、Hotstar 等迪士尼家族服务 |
| [Emby_Domain.yaml](Emby_Domain.yaml) | v2.5.1 | 18 | Emby、Infuse、VidHub、Forward、Fileball、AfuseKt、FinFlow 等服务与进程名 |
| [TikTok_Domain.yaml](TikTok_Domain.yaml) | v2.5.1 | 256 | TikTok、CapCut、Coze、Lark 海外版、BytePlus、Pico 等字节跳动海外服务及全球共用基础设施 |
| [Spotify_Domain.yaml](Spotify_Domain.yaml) | v2.5.0 | 32 | Spotify、Anchor 等服务域名 |
| [Spotify_IP.yaml](Spotify_IP.yaml) | v2.5.0 | 2 | Spotify 全球 IP 地址段 |
| [Telegram_Domain.yaml](Telegram_Domain.yaml) | v2.5.0 | 35 | Telegram、Telegra.ph、Fragment、TON 等服务域名 |
| [Telegram_IP.yaml](Telegram_IP.yaml) | v2.5.2 | 13 | Telegram 全球 IP 地址段 |
| [Meta_Domain.yaml](Meta_Domain.yaml) | v2.5.1 | 559 | Facebook、Instagram、WhatsApp、Messenger、Threads、Meta Quest、Meta AI 等服务域名 |
| [Meta_IP.yaml](Meta_IP.yaml) | v2.5.3 | 141 | Meta 全球 IP 地址段 |
| [Twitter_Domain.yaml](Twitter_Domain.yaml) | v2.5.0 | 27 | X / Twitter、t.co、xAI / Grok 等服务域名 |
| [Twitter_IP.yaml](Twitter_IP.yaml) | v2.5.0 | 21 | X / Twitter 全球 IP 地址段 |
| [AI_Domain.yaml](AI_Domain.yaml) | v2.5.3 | 193 | ChatGPT、Claude、Perplexity、Midjourney、Runway、Suno、Cursor、Copilot 等海外 AI 服务域名 |
| [AI_IP.yaml](AI_IP.yaml) | v2.5.1 | 2 | 海外 AI 服务 IP 地址段 |
| [Domestic-Direct_Domain.yaml](Domestic-Direct_Domain.yaml) | v2.5.12 | 641 | OPPO 系、微信、QQ、搜狗输入法、百度输入法、支付宝、淘宝、盒马、京东、拼多多、美团、得物、航旅纵横、中国联通、币安等交易所与国内银行服务域名（用户点名名单制重构） |
| [Domestic-Direct_IP.yaml](Domestic-Direct_IP.yaml) | v2.5.3 | 75 | 腾讯、阿里巴巴、中国联通等名单内公司作者源 IP 地址段 |

## 手动接入：rule-provider

也可以在 Mihomo 配置中以 rule-provider 逐个引入，按需选用：

```yaml
rule-providers:
  Google_Domain:
    type: http
    behavior: classical
    format: yaml
    url: "https://raw.githubusercontent.com/PuthsenTaylor/Mihomo-RuleSets/main/Google_Domain.yaml"
    path: ./ruleset/Google_Domain.yaml
    interval: 86400

rules:
  - RULE-SET,Google_Domain,Google,no-resolve
  - RULE-SET,Google_IP,Google
#使用代理软件自身数据库兜底
  - GEOSITE,google,Google
  - GEOIP,google,Google,no-resolve
```

域名集（`_Domain`）的规则行建议带 `no-resolve`，IP 集（`_IP`）不带，靠解析后比对地址段。

## 维护方式

每日自动同步多家作者（blackmatrix7、MetaCubeX、v2fly、ACL4SSR 等）的公开规则更新：新增条目通过归属、误杀、无用三道审计后自动并入并升补丁版；作者删除的条目与归属存疑的新增不自动处理，留待人工裁定；其中国内直连集只同步用户点名名单内的公司，名单外的新增一律只登记待裁、不并入。

## 说明

本仓库规则整理自上述作者的公开清单，版权归原作者所有，仅供学习与个人网络分流配置参考。
