# Mihomo-RuleSets

自建 Mihomo Rule Set 合集，供个人 Mihomo 配置以 rule-provider（classical）方式加载。

客户端拉取地址：`https://raw.githubusercontent.com/PuthsenTaylor/Mihomo-RuleSets/main/<文件名>`

## 文件索引

| 文件 | 版本 | 更新 | 条数 | 涵盖 |
| --- | --- | --- | --- | --- |
| [LAN.yaml](LAN.yaml) | v1.0.1 | 2026-11-25 | 170 | 局域网域名、私有 IP 地址段与本地服务发现域名 |
| [NTP.yaml](NTP.yaml) | v1.0.0 | 2026-11-25 | 169 | 全球 NTP 时间服务器域名（NTP Pool、品牌时间服务与国内外公共 NTP 服务器） |
| [Google.yaml](Google.yaml) | v1.0.2 | 2026-11-25 | 7975 | YouTube、Gmail、Gemini、Google Play 等谷歌全线服务与谷歌 IP 段 |
| [Apple.yaml](Apple.yaml) | v1.0.3 | 2026-11-25 | 1482 | iCloud、App Store、Apple Music、Apple TV、Beats 等苹果全线服务与苹果 IP 段 |
| [Netflix.yaml](Netflix.yaml) | v1.0.1 | 2026-11-25 | 1144 | Netflix 流媒体、Fast.com 测速等服务与奈飞 IP 段 |
| [Disney.yaml](Disney.yaml) | v1.0.2 | 2026-11-25 | 242 | Disney+、Hulu、ESPN、ABC、Marvel、Star Wars、国家地理、Hotstar 等迪士尼家族服务 |
| [Emby.yaml](Emby.yaml) | v1.0.2 | 2026-11-25 | 18 | Emby 官方服务（emby.media、mb3admin.com、emby.org、emby.tv）、UHD 服务域名；第三方 Emby 客户端官方域名（Infuse、VidHub、Forward、Fileball、AfuseKt）；进程名：FinFlow 与 Emby 官方应用（Android/Android TV/Windows 客户端与 Emby Server） |
| [TikTok.yaml](TikTok.yaml) | v1.0.6 | 2026-11-25 | 123 | TikTok、CapCut、Coze、Lark 海外版、BytePlus 等字节跳动海外服务；Pico 全球站 picoxr.com 为用户授权点名补入（无作者出处）；BytePlus 基础设施域名 ivolces.com / ivolces-test.com（自 DD 集改判移入）与 bytepluses.com、cr.volces.com 海外实证主机 6 条经官方文档实证补入 |
| [Spotify.yaml](Spotify.yaml) | v1.0.1 | 2026-11-25 | 34 | Spotify 音乐流媒体、Anchor 播客服务域名与 IP 段 |
| [Telegram.yaml](Telegram.yaml) | v1.0.1 | 2026-11-25 | 53 | Telegram 客户端、Telegra.ph、Fragment 与 TON 入口及 Telegram IP 段 |
| [Meta.yaml](Meta.yaml) | v1.0.1 | 2026-11-25 | 709 | Facebook、Instagram、WhatsApp、Messenger、Threads、Meta Quest、Meta AI 及 Meta IP 段 |
| [Twitter.yaml](Twitter.yaml) | v1.0.0 | 2026-11-25 | 48 | X / Twitter、t.co 短链、xAI / Grok 及 Twitter IP 段 |
| [AI.yaml](AI.yaml) | v1.0.3 | 2026-11-25 | 208 | ChatGPT、Claude、Perplexity、Poe、Groq、HuggingFace、Cursor、Manus、Runway、Suno、Character.AI 等海外 AI 服务（只收海外 AI；作者零收录的主流服务凭官网实证补入） |
| [Domestic-Direct.yaml](Domestic-Direct.yaml) | v1.0.9 | 2026-11-25 | 6151 | Binance（币安）、OKX（欧易）、Gate、Bitget、Bybit 五家交易所；腾讯全系（含海外面）；OPPO 系（含海外面）；阿里巴巴全系（含海外面）、京东全系（含海外面）、拼多多（不含 Temu）、美团、得物、航旅纵横、三网运营商（中国移动、中国电信、中国联通）、百度全系、搜狗全系（含两家输入法；百度组海外面已按国内全直连口径回补）、字节跳动国内全系（抖音、头条、西瓜、飞书国内、豆包、火山引擎等；海外面归 TikTok 集；ivolces.com / ivolces-test.com 已改判 BytePlus 国际面、移入 TikTok 集）（国内直连重构：第一步交易所、第二步腾讯、第三步 OPPO、第四步阿里/京东/拼多多/美团/得物/航旅纵横/运营商、第五步百度/搜狗、第六步字节国内；收官点名补入 simeji.me、hailuo.ai 两条，无作者出处、用户可否决） |
