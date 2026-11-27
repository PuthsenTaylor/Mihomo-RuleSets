# Mihomo-RuleSets

[![Last Commit](https://img.shields.io/github/last-commit/PuthsenTaylor/Mihomo-RuleSets)](https://github.com/PuthsenTaylor/Mihomo-RuleSets/commits/main)
![Format](https://img.shields.io/badge/Mihomo-classical%20rule--provider-blue)

自建 Mihomo 分流规则集（Rule Set）合集：多家公开作者规则全量合并、逐条审计、零自建，供 Mihomo 内核以 rule-provider（classical）方式加载。

全仓已经过逐条普查细审：每条域名与每个 IP 段逐一核验归属，过误杀与无用两道过滤（多租户共用平台整段、别家宣告的地址段、已注销域名等一律剔除），并以负探针反向核查——未收录的服务应落兜底，不得被任何集误捞；全部集经 Mihomo 内核实载验证，运行时计数与文件条数逐份一致。

文件直链格式：`https://raw.githubusercontent.com/PuthsenTaylor/Mihomo-RuleSets/main/<文件名>`

## 特性

- **多源交叉比对**：同一服务取多家作者数据的并集，单家独有条目逐条复核后才收，不整包照收任何一家。
- **双闸过滤**：误杀闸拦多租户共用平台整段与泛关键词，无用闸拦被宽条目遮蔽的冗余、已关停服务的死条目。
- **公司归属优先**：有总公司归属的服务只进总公司集，不按地理名单混编。
- **持续同步**：自动跟进各来源作者的更新，过闸的新增自动并入，删除与存疑项人工裁定，不盲目跟删。

## 分流理念

- **按公司归属分流**：谷歌走谷歌、苹果走苹果，有总公司归属的服务只进总公司集，不按地理名单混编。
- **国外全代理、国内全直连**：海外服务的第一命中落自家代理策略组，不落漏网、不落直连；国内服务一律直连，在服务商眼中始终是国内 IP，账号风控画像连贯。国内公司的明确海外服务不按国内算，按服务本体归代理侧、不入直连集。
- **宁可漏、不可误杀**：多租户共用平台的整段域名不入集，宁可让个别域名走兜底，也不劫持无关流量。
- **零自建**：每条规则均有公开作者出处，不凭空编写域名；拿不准归属的条目不入集。极少数无作者出处、但经实证确认归属的条目，按点名破例单独登记保留，不在此限。
- **字节跳动三分离**：海外字节（TikTok、CapCut、Lark 海外版、BytePlus 等）与全球共用基础设施归 TikTok 集走代理，国内字节（抖音、头条、飞书、火山引擎等）不进海外集、也不入名单制的国内直连集（字节不在点名名单内），在配套配置中经 GEOSITE 兜底走直连，两边彻底划开。

## 数据来源与致谢

本仓库不生产原始规则。全部条目整理自以下八家公开作者项目的当前版本，逐家交叉比对后合并，在此一并致谢：

- [v2fly/domain-list-community](https://github.com/v2fly/domain-list-community)
- [MetaCubeX/meta-rules-dat](https://github.com/MetaCubeX/meta-rules-dat)
- [ddranic/ios-proxy-rules](https://github.com/ddranic/ios-proxy-rules)
- [ACL4SSR/ACL4SSR](https://github.com/ACL4SSR/ACL4SSR)
- [DustinWin/ruleset_geodata](https://github.com/DustinWin/ruleset_geodata)
- [Loyalsoldier/geoip](https://github.com/Loyalsoldier/geoip)
- [Aethersailor/Custom_OpenClash_Rules](https://github.com/Aethersailor/Custom_OpenClash_Rules)
- [MagicRule](https://github.com/magical404/MagicRule)

历史条目中另有少量出自 blackmatrix7/ios_rule_script 的存量条目：该项目已停止更新，其存量条目按既定口径保留在册、不再作为同步来源。各条目的具体归属以维护记录为准；如原作者对条目的整理方式有异议，请通过 Issues 联系，将及时处理。

## 一键使用：覆写脚本（推荐）

不想自己写规则的，直接用配套覆写脚本 **MihomoOverride.js**：在支持 JavaScript 覆写的 Mihomo 客户端中，把脚本地址填入覆写（脚本）一栏即可。脚本会保留你订阅自带的节点与传输参数，只重建 DNS、嗅探、全套策略组、本仓库全套规则集的引用与全部分流规则；脚本本身不包含任何节点信息，节点全部来自你自己的订阅。

脚本地址（raw 直链，可直接粘贴到客户端）：

```
https://gist.github.com/PuthsenTaylor/6d3a119274d974d6dbadf6c05e669ccd/raw/MihomoOverride.js
```

脚本版本与本仓库配套维护、同步更新。用脚本接入后，无需再按下面的手动方式逐个添加 rule-provider。

## 架构与口径

- **ASN 不入集、由配置直达行承载**：classical 规则集只要混入一条 IP-ASN 条目，整份集在内核运行时会加载为零，因此本仓库所有 IP 集均不收 IP-ASN。字节海外、Telegram、Meta 与腾讯的自治系统号（ASN）覆盖，改由配套配置中的 IP-ASN 直达行按号精确承载。使用覆写脚本接入时，脚本会一并写入这些直达行。这也是 TikTok 只有 `_Domain` 域名文件、没有 `_IP` 文件的原因：其 IP 侧覆盖由 ASN 直达行与 GEOIP 兜底承担。
- **国内直连名单制**：国内直连集（Domestic-Direct）按点名名单收录，共 23 家总公司 / 28 样：欧加（OPPO 系）、腾讯 5 产品（微信、QQ、王者荣耀、和平精英、搜狗输入法）、阿里 3 产品（支付宝、淘宝、盒马）、京东、拼多多、美团、得物、航旅纵横、中国联通、百度输入法、交易所 5 家与银行 8 家。名单外的国内服务不入直连集，由 GEOSITE,cn 兜底直连；名单内公司的明确海外服务仍按服务本体归代理侧，不入直连集。
- **AI 集范围**：AI 集只收没有总公司集的海外 AI 服务，全量收录（ChatGPT、Claude、Perplexity、Mistral、Midjourney、Runway、Suno、Cursor 等）；有总公司集的 AI 服务归各自公司集——Google 的 AI 入 Google 集、Grok 入 Twitter 集、Meta AI 入 Meta 集；微软 / GitHub 与 JetBrains 按既定例外留在 AI 集。

## 文件清单

全仓 23 份文件，共 12,717 条；每份集按域名与 IP 拆分为 `_Domain` / `_IP` 双文件，其中 Disney、Emby 只有域名文件，TikTok 的 IP 侧覆盖由 ASN 直达行承载、同样只有域名文件（见上文「架构与口径」）。

| 文件 | 版本 | 条数 | 内容 |
| --- | --- | --- | --- |
| [LAN_Domain.yaml](LAN_Domain.yaml) | v2.5.2 | 151 | 局域网本地域名、路由器管理域名、本地服务发现域名、反向解析域名等 |
| [LAN_IP.yaml](LAN_IP.yaml) | v2.5.0 | 28 | 私有、保留、环回、链路本地、组播、共享地址空间与文档示例等 IP 地址段 |
| [Google_Domain.yaml](Google_Domain.yaml) | v2.5.4 | 878 | YouTube、Gmail、Gemini、Google Play、Google Search、Google Maps、Google Drive、Google Photos 等谷歌全线服务 |
| [Google_IP.yaml](Google_IP.yaml) | v2.5.2 | 6809 | 谷歌全球 IP 地址段 |
| [Apple_Domain.yaml](Apple_Domain.yaml) | v2.5.5 | 1441 | iCloud、App Store、Apple Music、Apple TV、Beats 等苹果全线服务 |
| [Apple_IP.yaml](Apple_IP.yaml) | v2.5.1 | 11 | 苹果全球 IP 地址段 |
| [Netflix_Domain.yaml](Netflix_Domain.yaml) | v2.5.1 | 24 | Netflix、Fast.com 等奈飞服务域名 |
| [Netflix_IP.yaml](Netflix_IP.yaml) | v2.5.2 | 1079 | 奈飞全球 IP 地址段 |
| [Disney_Domain.yaml](Disney_Domain.yaml) | v2.5.1 | 242 | Disney+、Hulu、ESPN、ABC、Marvel、Star Wars、国家地理、Hotstar 等迪士尼家族服务 |
| [Emby_Domain.yaml](Emby_Domain.yaml) | v2.5.1 | 18 | Emby、Infuse、VidHub、Forward、Fileball、AfuseKt、FinFlow 等服务与进程名 |
| [TikTok_Domain.yaml](TikTok_Domain.yaml) | v2.5.1 | 256 | TikTok、CapCut、Coze、Lark 海外版、BytePlus、Pico 等字节跳动海外服务及全球共用基础设施 |
| [Spotify_Domain.yaml](Spotify_Domain.yaml) | v2.5.0 | 32 | Spotify、Anchor 等服务域名 |
| [Spotify_IP.yaml](Spotify_IP.yaml) | v2.5.0 | 2 | Spotify 全球 IP 地址段 |
| [Telegram_Domain.yaml](Telegram_Domain.yaml) | v2.5.0 | 35 | Telegram、Telegra.ph、Fragment、TON 等服务域名 |
| [Telegram_IP.yaml](Telegram_IP.yaml) | v2.5.5 | 15 | Telegram 全球 IP 地址段 |
| [Meta_Domain.yaml](Meta_Domain.yaml) | v2.5.2 | 560 | Facebook、Instagram、WhatsApp、Messenger、Threads、Meta Quest、Meta AI 等服务域名 |
| [Meta_IP.yaml](Meta_IP.yaml) | v2.5.5 | 139 | Meta 全球 IP 地址段 |
| [Twitter_Domain.yaml](Twitter_Domain.yaml) | v2.5.0 | 27 | X / Twitter、t.co、xAI / Grok 等服务域名 |
| [Twitter_IP.yaml](Twitter_IP.yaml) | v2.5.0 | 21 | X / Twitter 全球 IP 地址段 |
| [AI_Domain.yaml](AI_Domain.yaml) | v2.5.4 | 235 | ChatGPT、Claude、Perplexity、Mistral、Midjourney、Runway、Suno、Cursor 等无总公司集的海外 AI 服务域名（全量收录） |
| [AI_IP.yaml](AI_IP.yaml) | v2.5.1 | 2 | 海外 AI 服务 IP 地址段 |
| [Domestic-Direct_Domain.yaml](Domestic-Direct_Domain.yaml) | v2.5.14 | 642 | OPPO 系、微信、QQ、搜狗输入法、百度输入法、支付宝、淘宝、盒马、京东、拼多多、美团、得物、航旅纵横、中国联通、币安等交易所与国内银行服务域名（用户点名名单制重构） |
| [Domestic-Direct_IP.yaml](Domestic-Direct_IP.yaml) | v2.5.4 | 70 | 腾讯、阿里巴巴、中国联通等名单内公司作者源 IP 地址段 |

## 手动接入：rule-provider

也可以在 Mihomo 配置中以 rule-provider 逐个引入，按需选用，不必全套照搬：

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
  - RULE-SET,Google_Domain,Google
  - RULE-SET,Google_IP,Google,no-resolve
#使用代理软件自身数据库兜底
  - GEOSITE,google,Google
  - GEOIP,google,Google,no-resolve
```

域名集（`_Domain`）的规则行不带 `no-resolve`，靠域名本身比对，不涉及解析；IP 集（`_IP`）与 GEOIP 的规则行带 `no-resolve`，避免内核为了比对地址段而提前做一次 DNS 解析，目标已经是 IP 或已完成解析时照常命中。

## 更新与维护机制

- **同步节奏**：每 12 小时自动检查上述八家来源的公开更新，逐份比对。
- **自动并入**：作者新增且通过归属、误杀、无用三道审计的条目，自动并入对应集并升补丁版；过不了闸的新增只登记、不并入。
- **人工裁定**：作者删除的条目、归属存疑的新增、以及与本仓库既定裁定冲突的内容，不自动处理，攒齐后由维护者逐项裁定。已被裁定剔除的内容登记在案，作者再发也不会被自动带回。
- **名单制例外**：国内直连集只同步点名名单内的公司，名单外的新增一律只登记待裁。
- **点名破例与观察名单**：少量无作者出处但经实证确认的破例条目、以及状态待观察的条目，由人工维护，自动同步不增删。

## 使用须知

1. 本仓库只提供规则数据文件，不提供任何代理节点、订阅或网络接入服务；规则要生效，需配合你自己的 Mihomo 配置与节点使用。
2. 规则按「特性」与「分流理念」中的口径整理，与你的预期不一致时，请先核对配套配置中的策略组与兜底设置，再判断是规则问题还是配置问题。
3. 引用地址请用 raw 直链并保留自动更新间隔；把文件下载后静态使用，将无法跟上各来源的持续修订。
4. 各集可独立取舍：只用其中几份时，配套的 GEOSITE / GEOIP 兜底请按你自己的配置习惯补齐，避免未收录服务无处落点。

## 免责声明

1. 本仓库内容仅供网络流量管理、分流配置的学习与研究使用，不构成任何形式的使用建议或保证。
2. 规则数据整理自第三方公开清单，尽管经过交叉比对与逐条审计，仍不保证其完整性、准确性与时效性；各服务商的域名与 IP 段随时可能变更，规则滞后或个别条目有误在所难免。
3. 本仓库与条目所涉的任何公司、产品与服务均无隶属、合作或授权关系；文中提及的名称仅用于说明规则的归属对象，相关商标与权利归其各自权利人所有。
4. 使用者应自行确认其使用行为符合所在地法律法规与所用服务的服务条款；因使用本仓库内容产生的任何后果，由使用者自行承担，与本仓库维护者无关。
5. 本仓库维护者保留随时修订本声明与仓库内容的权利；继续使用本仓库内容，视为接受本声明的当前版本。

## 许可与版权

- 本仓库所收录规则数据的版权归各原始作者所有，其使用与再分发应遵守各来源项目各自的许可协议（见「数据来源与致谢」中的链接）。
- 本仓库的整理、审计与编排成果，如需整体转载或再分发，请注明出处为本仓库，并遵守上一条中各来源的许可要求。
- 本仓库的整理、审计与编排部分以 CC BY-SA 4.0 许可发布，全文见仓库根目录的 LICENSE 文件；署名时请注明本仓库出处，改编与再分发须以相同许可共享。

## 反馈方式

- 发现条目归属错误、遗漏或已失效，请到 [GitHub Issues](https://github.com/PuthsenTaylor/Mihomo-RuleSets/issues) 反馈，并注明涉及的文件名与具体条目，以便核查。
- 与规则无关的问题（如 Mihomo 内核或客户端本身的故障），请到对应项目的官方渠道反馈，本仓库无法处理。
