# Mihomo-RuleSets

## 项目简介

本仓库为自建 Mihomo Rule Set 合集，收录供个人 Mihomo 配置使用的规则集文件。每份文件均由多位常见作者公开发布的同类清单全量合并而成，构建遵循以下三项原则：

- **多作者全量合并**：拉取该分类下各作者的清单并求全集，不做取舍。
- **零自建**：每条规则均须出自某位作者的已发布数据，不手工编写规则条目。
- **集内排序与去冗余**：条目按匹配优先级排序（精确域名在前、后缀由细到宽、关键词其次、IP 段由窄到宽），并删除完全重复及被自家更宽条目覆盖的冗余条目。

## 文件索引

### Apple.yaml

- 用途：苹果（Apple）规则集，覆盖苹果及其服务（iCloud、Apple Music、App Store、Apple TV 等）域名与苹果 IP 地址段。
- 条目数：1,613 条。
- 构建日期：2026-11-25。
- 数据来源：MetaCubeX、blackmatrix7、v2fly、ddranic、ACL4SSR、DustinWin、Loyalsoldier，共 7 家作者。

### Disney.yaml

- 用途：迪士尼（Disney）规则集，覆盖迪士尼家族（Disney+、Hulu、ESPN、ABC、Marvel、Star Wars、国家地理、Hotstar、Star+ 等子品牌）域名。
- 条目数：243 条。
- 构建日期：2026-11-25。
- 数据来源：MetaCubeX、blackmatrix7、v2fly、ddranic、ACL4SSR、DustinWin，共 6 家作者。

### Lan-Private.yaml

- 用途：局域网 / 私有地址规则集，覆盖局域网域名、私有地址段及本地服务发现域名。
- 条目数：170 条。
- 构建日期：2026-11-25。
- 数据来源：MetaCubeX、blackmatrix7、ACL4SSR、v2fly、DustinWin、Aethersailor、Loyalsoldier，共 7 家作者。

### Google.yaml

- 用途：谷歌（Google）规则集，覆盖谷歌及其子品牌（YouTube、Gmail、Google Play 等）域名与谷歌 IP 地址段。
- 条目数：7,976 条。
- 构建日期：2026-11-25。
- 数据来源：MetaCubeX、blackmatrix7、v2fly、ddranic、ACL4SSR、DustinWin、Loyalsoldier，共 7 家作者。

### Netflix.yaml

- 用途：奈飞（Netflix）规则集，覆盖奈飞及其服务（流媒体、Fast.com 测速、DNS 检测等）域名与奈飞 IP 地址段。
- 条目数：1,157 条。
- 构建日期：2026-11-25。
- 数据来源：MetaCubeX、blackmatrix7、v2fly、ddranic、ACL4SSR、DustinWin，共 6 家作者。

### NTP.yaml

- 用途：网络时间服务（NTP）规则集，覆盖全球网络时间服务域名，含国内、中立公共、品牌专属与其他海外条目。
- 条目数：169 条。
- 构建日期：2026-11-25。
- 数据来源：v2fly、MetaCubeX、ddranic、blackmatrix7，共 4 家作者。

### Spotify.yaml

- 用途：Spotify 规则集，覆盖 Spotify 音乐流媒体服务及其官方域名与 IP 地址段。
- 条目数：34 条。
- 构建日期：2026-11-25。
- 数据来源：MetaCubeX、blackmatrix7、v2fly、ddranic、ACL4SSR、DustinWin，共 6 家作者。

### TikTok.yaml

- 用途：海外字节（TikTok）规则集，覆盖 TikTok、Musical.ly、CapCut 海外版等海外字节系服务域名；只收海外分类，不含国内字节数据。
- 条目数：61 条。
- 构建日期：2026-11-25。
- 数据来源：MetaCubeX、blackmatrix7、v2fly、ddranic、ACL4SSR、DustinWin，共 6 家作者。

## 维护说明

- 本仓库按段逐个新增文件：每完成一段自建集，即在本仓库新增对应文件，并同步更新本索引中的条目数、构建日期与数据来源。
- 文件更新时，重新拉取各来源作者的最新清单，重复全量合并、排序与去冗余的完整流程后整体替换文件内容，不做零散的手工增补。
- Mihomo Custom 配置中的 rule-provider 逐段指向本仓库对应文件的 raw 地址；文件内容变更后，客户端按 rule-provider 的更新间隔自动拉取新版。
