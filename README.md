# 小红书数据接口（Xiaohongshu / RedNote API）：笔记、评论、博主、热点、蒲公英达人和关键词指数

**小红书数据 API · 小红书笔记搜索 · 小红书评论采集 · 博主主页和笔记 · 蒲公英达人报价 · 小红书关键词指数**

这个仓库是 [DataXAPI](https://dataxapi.com/zh/?ref=gh-xiaohongshu-api) 的小红书接口说明和能直接跑的脚本：33 个接口，一把 Key，按次付费，$0.02 起，**出错不收费**。不用登录平台账号，不用 Cookie，不开浏览器。

[免费拿 Key：试用最多 333 次，不用绑卡](https://dataxapi.com/zh/signin/?button=gh-xiaohongshu-api) · [全部接口文档](https://dataxapi.com/zh/apis/?ref=gh-xiaohongshu-api) · [接进 AI（MCP）](#接进-aimcp) · [English](#english)

最低充 $10，余额不过期；支持支付宝、微信支付和银行卡。

## 最常用的接口

DataXAPI 的客户近 30 天里调用最多的几个，从多到少：

| 接口 | 拿到什么 | 价格 |
|---|---|---|
| [小红书笔记搜索](https://dataxapi.com/zh/apis/xiaohongshu/notes/search/?ref=gh-xiaohongshu-api) | 按搜索词取一页小红书笔记：标题、正文、作者、互动数、图片，链接带访问令牌可直接打开；标明哪条是报备过的品牌合作笔记。可按综合、最新、最多点赞、最多评论、最多收藏排，可只要视频或图文笔记、只要一天、一周或半年内发布的。 | $0.02 一次 |
| [小红书笔记详情](https://dataxapi.com/zh/apis/xiaohongshu/notes/get/?ref=gh-xiaohongshu-api) | 按笔记编号或链接取一篇小红书笔记：标题、正文、作者、互动数、图片，以及是不是报备过的品牌合作笔记。 | $0.02 一次 |
| [小红书笔记评论](https://dataxapi.com/zh/apis/xiaohongshu/notes/comments/list/?ref=gh-xiaohongshu-api) | 按笔记编号或链接取一页小红书一级评论，按时间从新到旧，也可按最热：正文、评论者、点赞数、回复数、发布时间。 | $0.02 一次 |
| [小红书用户笔记](https://dataxapi.com/zh/apis/xiaohongshu/users/notes/list/?ref=gh-xiaohongshu-api) | 按用户编号或主页链接取一页该账号发布的小红书笔记：标题、正文、互动数、图片、是否置顶。 | $0.02 一次 |
| [小红书用户资料](https://dataxapi.com/zh/apis/xiaohongshu/users/get/?ref=gh-xiaohongshu-api) | 按用户编号或主页链接取小红书账号资料：昵称、小红书号、简介、粉丝数、关注数、笔记数、是否认证，以及主页显示的性别和自填地区。 | $0.02 一次 |
| [小红书蒲公英关键词逐日搜索指数](https://dataxapi.com/zh/apis/xiaohongshu/pgy/keywords/history/?ref=gh-xiaohongshu-api) | 按一个关键词取它在小红书上最近约三个月逐日的搜索指数（蒲公英），并带每天和这个词有关的笔记数、曝光数、阅读数和互动数。时间范围由平台定，不能选；搜索指数是平台算出的指数，不是搜索次数；日期是中国时间（UTC+8）的自然日。 | $0.04 一次 |
| [小红书用户搜索](https://dataxapi.com/zh/apis/xiaohongshu/users/search/?ref=gh-xiaohongshu-api) | 按搜索词取一页小红书账号：用户编号、小红书号、昵称、头像、是否认证。 | $0.02 一次 |
| [小红书热点](https://dataxapi.com/zh/apis/xiaohongshu/trends/list/?ref=gh-xiaohongshu-api) | 取小红书创作灵感里的热点话题：名称和平台给的热度值。 | $0.02 一次 |

## 全部 33 个接口

### 笔记

| 接口 | 拿到什么 | 价格 | 编号 |
|---|---|---|---|
| [小红书笔记搜索](https://dataxapi.com/zh/apis/xiaohongshu/notes/search/?ref=gh-xiaohongshu-api) | 按搜索词取一页小红书笔记：标题、正文、作者、互动数、图片，链接带访问令牌可直接打开；标明哪条是报备过的品牌合作笔记。可按综合、最新、最多点赞、最多评论、最多收藏排，可只要视频或图文笔记、只要一天、一周或半年内发布的。 | $0.02 一次 | `xiaohongshu.notes.search` |
| [小红书笔记详情](https://dataxapi.com/zh/apis/xiaohongshu/notes/get/?ref=gh-xiaohongshu-api) | 按笔记编号或链接取一篇小红书笔记：标题、正文、作者、互动数、图片，以及是不是报备过的品牌合作笔记。 | $0.02 一次 | `xiaohongshu.notes.get` |
| [小红书笔记评论](https://dataxapi.com/zh/apis/xiaohongshu/notes/comments/list/?ref=gh-xiaohongshu-api) | 按笔记编号或链接取一页小红书一级评论，按时间从新到旧，也可按最热：正文、评论者、点赞数、回复数、发布时间。 | $0.02 一次 | `xiaohongshu.notes.comments.list` |
| [小红书无水印原图和实况图下载地址](https://dataxapi.com/zh/apis/xiaohongshu/notes/media/get/?ref=gh-xiaohongshu-api) | 给一篇小红书图文笔记的编号、链接或分享文字，返回每张图片的无水印原图地址（平台保存的最大尺寸，带宽高和格式），实况图另给那段视频的地址；地址不用带请求头，过期了再调一次即可。只用于图文笔记，视频笔记用 xiaohongshu.videos.media.get。 | $0.02 一次 | `xiaohongshu.notes.media.get` |

### 账号

| 接口 | 拿到什么 | 价格 | 编号 |
|---|---|---|---|
| [小红书用户笔记](https://dataxapi.com/zh/apis/xiaohongshu/users/notes/list/?ref=gh-xiaohongshu-api) | 按用户编号或主页链接取一页该账号发布的小红书笔记：标题、正文、互动数、图片、是否置顶。 | $0.02 一次 | `xiaohongshu.users.notes.list` |
| [小红书用户资料](https://dataxapi.com/zh/apis/xiaohongshu/users/get/?ref=gh-xiaohongshu-api) | 按用户编号或主页链接取小红书账号资料：昵称、小红书号、简介、粉丝数、关注数、笔记数、是否认证，以及主页显示的性别和自填地区。 | $0.02 一次 | `xiaohongshu.users.get` |
| [小红书用户搜索](https://dataxapi.com/zh/apis/xiaohongshu/users/search/?ref=gh-xiaohongshu-api) | 按搜索词取一页小红书账号：用户编号、小红书号、昵称、头像、是否认证。 | $0.02 一次 | `xiaohongshu.users.search` |

### 蒲公英（达人和关键词指数）

| 接口 | 拿到什么 | 价格 | 编号 |
|---|---|---|---|
| [小红书蒲公英关键词逐日搜索指数](https://dataxapi.com/zh/apis/xiaohongshu/pgy/keywords/history/?ref=gh-xiaohongshu-api) | 按一个关键词取它在小红书上最近约三个月逐日的搜索指数（蒲公英），并带每天和这个词有关的笔记数、曝光数、阅读数和互动数。时间范围由平台定，不能选；搜索指数是平台算出的指数，不是搜索次数；日期是中国时间（UTC+8）的自然日。 | $0.04 一次 | `xiaohongshu.pgy.keywords.history` |
| [小红书蒲公英关联词](https://dataxapi.com/zh/apis/xiaohongshu/pgy/keywords/related/?ref=gh-xiaohongshu-api) | 按一个关键词取小红书用户搜它之前和之后还会搜的词（蒲公英），各带相关度名次、搜索指数、相关笔记数和阅读数，用来拓词选题。搜索指数是平台算出的指数，不是搜索次数；平台不给数的词，这几项为 null。 | $0.04 一次 | `xiaohongshu.pgy.keywords.related` |
| [小红书蒲公英博主搜索](https://dataxapi.com/zh/apis/xiaohongshu/pgy/creators/search/?ref=gh-xiaohongshu-api) | 按搜索词找蒲公英上的小红书博主（按博主写的内容匹配）：博主编号、昵称、小红书号、所在地、内容类目、粉丝数，完整档另有图文和视频报价、阅读和互动中位数。也可以按蒲公英找博主的筛选条件找，或和搜索词一起用：粉丝数、报价、预估 CPM、日常和合作笔记的阅读与互动中位数、主做图文或视频、博主类目、擅长内容、人设、所在地、性别、粉丝性别和年龄、近期合作行业，可剔除低活跃和掉粉的；按粉丝数、报价、阅读、互动、外溢进店、阅读单价、回复率、涨粉、完播率等排序。一次搜索最多翻到前 5000 位。其他蒲公英接口要的博主编号从这里取。 | $0.04 一次 | `xiaohongshu.pgy.creators.search` |
| [小红书蒲公英博主详情](https://dataxapi.com/zh/apis/xiaohongshu/pgy/creators/get/?ref=gh-xiaohongshu-api) | 按蒲公英博主编号取这位小红书博主在蒲公英上的资料：昵称、小红书号、所在地、内容类目、粉丝数，完整档另有图文和视频报价、最低报价、接不接图文和视频合作、商业笔记数和近 30 天合作笔记数、阅读和互动中位数、性别、内容特征和人设标签、合作过的行业、签约机构（MCN）、获赞与收藏。 | $0.04 一次 | `xiaohongshu.pgy.creators.get` |
| [小红书蒲公英博主粉丝画像](https://dataxapi.com/zh/apis/xiaohongshu/pgy/creators/audience/get/?ref=gh-xiaohongshu-api) | 按蒲公英博主编号取这位小红书博主的粉丝画像：性别、年龄、省份、城市、兴趣、设备各段的占比，和数据是哪一天的。 | $0.04 一次 | `xiaohongshu.pgy.creators.audience.get` |
| [小红书蒲公英博主数据表现](https://dataxapi.com/zh/apis/xiaohongshu/pgy/creators/metrics/?ref=gh-xiaohongshu-api) | 按蒲公英博主编号取这位小红书博主近 30 天或 90 天日常笔记或合作笔记的数据表现：笔记数和视频笔记数，曝光、阅读、互动、涨粉的中位数，互动率，完播率，点赞过百和过千的笔记占比，和超过了多少同类博主；曝光和阅读来自发现页、搜索、关注页等入口的占比。完整档另有逐篇笔记的曝光、阅读、互动和比中位数高出多少，以及长效笔记（约半年前发布的笔记）近期和长效阅读的数和来源。 | $0.04 一次 | `xiaohongshu.pgy.creators.metrics` |
| [小红书蒲公英博主笔记](https://dataxapi.com/zh/apis/xiaohongshu/pgy/creators/notes/list/?ref=gh-xiaohongshu-api) | 按蒲公英博主编号取一页这位小红书博主的笔记（蒲公英的“笔记案例”），带蒲公英给的数据：阅读数、点赞数、收藏数、外溢进店人数、是否商业合作和合作品牌、是否带过付费推广流量。可只看合作笔记、跨域合作笔记、图文或视频，按最新、阅读最多或互动最多排，按内容特征或类目筛，阅读数可只算自然流量。 | $0.04 一次 | `xiaohongshu.pgy.creators.notes.list` |
| [小红书蒲公英博主粉丝趋势](https://dataxapi.com/zh/apis/xiaohongshu/pgy/creators/followers/history/?ref=gh-xiaohongshu-api) | 按蒲公英博主编号取这位小红书博主最近 30 天或 60 天每天的粉丝数，以及这段时间净增多少、涨了百分之几。看博主有没有在涨粉、有没有突然掉粉或刷粉。 | $0.04 一次 | `xiaohongshu.pgy.creators.followers.history` |
| [小红书蒲公英相似博主](https://dataxapi.com/zh/apis/xiaohongshu/pgy/creators/related/?ref=gh-xiaohongshu-api) | 给一个蒲公英博主编号，取蒲公英推荐的和他相似的小红书博主：博主编号、昵称、小红书号、所在地、内容类目、粉丝数，完整档另有报价和阅读、互动中位数。一次 4 位（蒲公英一页就 4 位），通常共几位到几十位，可以翻页。 | $0.04 一次 | `xiaohongshu.pgy.creators.related` |
| [小红书蒲公英内容广场热门笔记](https://dataxapi.com/zh/apis/xiaohongshu/pgy/notes/trending/?ref=gh-xiaohongshu-api) | 取蒲公英内容广场的热门笔记榜：小红书热门、产品种草、电商推广、蒲公英合作等 8 个榜，看整榜或只看和某个词有关的，近 3、7、14、30 天，可只要图文或视频。每条有标题、发布时间、阅读、点赞、收藏、评论、图片，和博主的编号、昵称、粉丝数。不用给编号，适合找爆款和选题。 | $0.04 一次 | `xiaohongshu.pgy.notes.trending` |
| [小红书蒲公英博主合作成本和数据概览](https://dataxapi.com/zh/apis/xiaohongshu/pgy/creators/costs/metrics/?ref=gh-xiaohongshu-api) | 按蒲公英博主编号取这位小红书博主的合作成本：图文和视频的预估 CPM、预估互动单价、预估阅读单价、预估外溢进店单价，每项都带优于多少同行；还有单篇笔记曝光、阅读、互动、外溢进店的中位数，近 30 天粉丝增长率和发布笔记数，邀约 48 小时回复率和“好联系”标记，近 7 天活跃天数和“活跃”标记，蒲公英标的优势，内容类型占比和合作过的行业。可看日常笔记或合作笔记两种口径。 | $0.04 一次 | `xiaohongshu.pgy.creators.costs.metrics` |
| [小红书蒲公英博主粉丝概览](https://dataxapi.com/zh/apis/xiaohongshu/pgy/creators/followers/metrics/?ref=gh-xiaohongshu-api) | 按蒲公英博主编号取这位小红书博主粉丝的质量：粉丝数和近 30 天净增，活跃粉丝、互动粉丝、阅读粉丝、购买粉丝各有多少、占全部粉丝的比例，和超过了多少同类博主。看粉丝是不是真的在看、在买。 | $0.04 一次 | `xiaohongshu.pgy.creators.followers.metrics` |
| [小红书蒲公英博主核心数据趋势](https://dataxapi.com/zh/apis/xiaohongshu/pgy/creators/costs/history/?ref=gh-xiaohongshu-api) | 按蒲公英博主编号取这位小红书博主最近 30 天或 90 天每天的核心数据：CPM、CPE（互动单价）、CPV（阅读单价）、外溢进店单价，和单篇笔记曝光、阅读、互动、外溢进店人数的中位数，以及整段的汇总。可看日常笔记或合作笔记两种口径，看博主的投放性价比是在变好还是变差。 | $0.04 一次 | `xiaohongshu.pgy.creators.costs.history` |
| [小红书蒲公英笔记数据](https://dataxapi.com/zh/apis/xiaohongshu/pgy/notes/get/?ref=gh-xiaohongshu-api) | 按笔记编号取蒲公英给品牌看的这篇小红书笔记的数据：曝光、阅读、点赞、收藏、评论、分享、带来的涨粉，报备的合作品牌，品牌组件（评论区、正文、底部）的点击率档位，以及标题、正文、图片、发布时间和博主编号。合作笔记结案、核对博主交付用。蒲公英只给自己博主的笔记数据，取不到数据的笔记（如品牌自己发的）返回 404。 | $0.04 一次 | `xiaohongshu.pgy.notes.get` |

### 热榜和趋势

| 接口 | 拿到什么 | 价格 | 编号 |
|---|---|---|---|
| [小红书热点](https://dataxapi.com/zh/apis/xiaohongshu/trends/list/?ref=gh-xiaohongshu-api) | 取小红书创作灵感里的热点话题：名称和平台给的热度值。 | $0.02 一次 | `xiaohongshu.trends.list` |

### 商城商品

| 接口 | 拿到什么 | 价格 | 编号 |
|---|---|---|---|
| [小红书商品搜索](https://dataxapi.com/zh/apis/xiaohongshu/shop/products/search/?ref=gh-xiaohongshu-api) | 按搜索词取一页小红书商城的商品：标题、现价和原价（人民币）、已售件数、图片、店铺。看到的是 App 海外地区版本的商城（地区每次可能不同），促销和能不能买可能和国内用户看到的不一样。 | $0.02 一次 | `xiaohongshu.shop.products.search` |
| [小红书商品详情](https://dataxapi.com/zh/apis/xiaohongshu/shop/products/get/?ref=gh-xiaohongshu-api) | 按商品编号取小红书商城的一件商品：标题、现价和原价（人民币）、图片、评分、评价数、店铺。看到的是 App 海外地区版本的商品页（地区每次可能不同），促销和能不能买可能和国内用户看到的不一样。 | $0.02 一次 | `xiaohongshu.shop.products.get` |
| [小红书商品评价](https://dataxapi.com/zh/apis/xiaohongshu/shop/products/reviews/list/?ref=gh-xiaohongshu-api) | 按商品编号取小红书商城这件商品排在最前的一页买家评价：正文、评分、买的规格、晒图、点赞数。 | $0.02 一次 | `xiaohongshu.shop.products.reviews.list` |

### 视频

| 接口 | 拿到什么 | 价格 | 编号 |
|---|---|---|---|
| [小红书视频笔记详情（视频地址和字幕）](https://dataxapi.com/zh/apis/xiaohongshu/videos/get/?ref=gh-xiaohongshu-api) | 按笔记编号或链接取一篇小红书视频笔记：标题、正文、作者、互动数，加上视频文件地址、时长、封面、平台生成的中文字幕（SRT，可当文字稿），以及是不是报备过的品牌合作笔记。只用于视频笔记；图文笔记用笔记详情。 | $0.02 一次 | `xiaohongshu.videos.get` |
| [小红书视频转文字（文案提取、逐字稿）](https://dataxapi.com/zh/apis/xiaohongshu/videos/transcript/get/?ref=gh-xiaohongshu-api) | 给一篇小红书视频笔记的链接、分享文案或编号，返回视频里说的话：全文、每一句的起止时间和现成的 SRT 字幕，连同标题、作者和时长；平台给视频生成了字幕的直接用字幕，没有的识别语音，可以区分说话人。每次收费，识别语音的另按视频分钟数收，用平台字幕的不另收，没人说话不收。5 分钟以内的视频直接返回文字；超过 5 分钟、2 小时以内的先回一个凭证（job），过一会儿带着它再调这个接口取文字，按实际分钟数收，只在取到文字时收。 | $0.02 一次 | `xiaohongshu.videos.transcript.get` |
| [小红书无水印视频下载地址（各档清晰度和字幕）](https://dataxapi.com/zh/apis/xiaohongshu/videos/media/get/?ref=gh-xiaohongshu-api) | 给一篇小红书视频笔记的编号、链接或分享文字，返回无水印视频的全部文件地址：每种编码（H.264、H.265 等）的每档清晰度，带宽高、码率和大小，另有备用地址，以及封面和平台生成的字幕文件（SRT，按语言给）；地址不用带请求头，取不到了再调一次即可。只用于视频笔记，图文笔记用 xiaohongshu.notes.media.get。 | $0.02 一次 | `xiaohongshu.videos.media.get` |

### 图片

| 接口 | 拿到什么 | 价格 | 编号 |
|---|---|---|---|
| [小红书图片搜索](https://dataxapi.com/zh/apis/xiaohongshu/images/search/?ref=gh-xiaohongshu-api) | 按搜索词取一页小红书图片，每条是一张图片和它所在的笔记：图片地址、笔记的标题、正文、作者、点赞、评论、收藏、分享数。分享数在这里给不了（总是 0，不交付），要看分享数请用笔记详情 xiaohongshu.notes.get。 | $0.02 一次 | `xiaohongshu.images.search` |

### 评论

| 接口 | 拿到什么 | 价格 | 编号 |
|---|---|---|---|
| [小红书评论回复](https://dataxapi.com/zh/apis/xiaohongshu/comments/replies/list/?ref=gh-xiaohongshu-api) | 按评论编号和它所在的笔记编号取一页回复：正文、回复者、点赞数、发布时间、回复的是哪一条。 | $0.02 一次 | `xiaohongshu.comments.replies.list` |

### 话题

| 接口 | 拿到什么 | 价格 | 编号 |
|---|---|---|---|
| [小红书话题笔记](https://dataxapi.com/zh/apis/xiaohongshu/topics/notes/list/?ref=gh-xiaohongshu-api) | 按话题页编号取该话题下的热门笔记：标题、正文、作者、互动数、图片、话题标签。 | $0.02 一次 | `xiaohongshu.topics.notes.list` |
| [小红书话题详情](https://dataxapi.com/zh/apis/xiaohongshu/topics/get/?ref=gh-xiaohongshu-api) | 按话题页编号取一个小红书话题：名称、简介、浏览数、讨论数、分享链接。 | $0.02 一次 | `xiaohongshu.topics.get` |

### 关键词

| 接口 | 拿到什么 | 价格 | 编号 |
|---|---|---|---|
| [小红书搜索框联想词](https://dataxapi.com/zh/apis/xiaohongshu/keywords/related/?ref=gh-xiaohongshu-api) | 按关键词取小红书搜索框里输入这个词时给的联想词（下拉补全），按小红书列出的顺序排，一次约 10 个。只有词和名次，没有指数。 | $0.02 一次 | `xiaohongshu.keywords.related` |

## 真实返回长什么样

**小红书笔记搜索**（`xiaohongshu.notes.search`，参数 `{"query":"咖啡"}`），录下的真实返回，个人信息换成了 …：

```json
{
  "data": {
    "items": [
      {
        "id": "…",
        "url": "https://example.com/…",
        "type": "image",
        "title": "…",
        "text": "…",
        "published_at": "2026-05-17T05:25:25.000Z",
        "author": {
          "id": "…",
          "username": "…",
          "name": "…",
          "avatar_url": "https://example.com/…"
        },
        "metrics": {
          "likes": 48,
          "comments": 21,
          "shares": 5,
          "favorites": 10
        },
        "images": [
          "https://example.com/…"
        ]
      }
    ]
  },
  "page": {
    "next_cursor": "example-cursor-1",
    "cursor_expires_at": "2026-10-12T19:43:26.000Z",
    "has_more": true,
    "returned": 15
  }
}
```

每个接口都是同一种结构：列表在 `data.items`，单个在 `data.item`，下一页用 `page.next_cursor`，这次扣了多少在 `meta.billing.amount`，平台不给的字段为 `null` 并在 `meta.unavailable` 里写明。

## 快速开始

1. [拿一把 Key](https://dataxapi.com/zh/signin/?button=gh-xiaohongshu-api)（`dx_` 开头），放进环境变量：`export DATAXAPI_API_KEY=dx_...`
2. 调一次接口：

```bash
curl -G "https://api.dataxapi.com/v1/xiaohongshu/notes/search" \
  -H "Authorization: Bearer $DATAXAPI_API_KEY" \
  --data-urlencode 'query=咖啡'
```

3. 或者跑 `examples/` 里的脚本。只用 Python 标准库（3.9 以上）；不加 `--yes` 只报价、不调用，加了才真跑，跑完告诉你实际花了多少：

| 脚本 | 做什么 | 先看要花多少 |
|---|---|---|
| [quickstart.py](examples/quickstart.py) | 取几页结果，存成 CSV | `cd examples && python3 quickstart.py 咖啡` |

## 接进 AI（MCP）

Claude Code：

```bash
claude mcp add --transport http --scope user dataxapi https://api.dataxapi.com/mcp --header "Authorization: Bearer $DATAXAPI_API_KEY"
```

Cursor、Cherry Studio、WorkBuddy 等支持远程 MCP 的客户端：

```json
{
  "mcpServers": {
    "dataxapi": {
      "url": "https://api.dataxapi.com/mcp",
      "headers": {
        "Authorization": "Bearer dx_..."
      }
    }
  }
}
```

接上以后直接用中文问，比如“帮我看看这个关键词最近一个月在抖音上的热度”。AI 花钱前可以先免费查接口和价格。也可以装成技能：`npx skills add data-x-api/skills`。

## 常见问题

**要不要平台账号、Cookie 或扫码？**

不要。只要一把 DataXAPI Key，不碰你的账号，也就不存在账号被风控的问题。

**调用出错扣钱吗？**

不扣。每次返回里的 `meta.billing.amount` 写明这次扣了多少（美元）。

**数据有多新？**

默认在你调用时从平台实时读取，返回里的 `meta.fetched_at` 写明读取时间。

**怎么翻页？**

列表接口一次返回一页，把返回里的 `page.next_cursor` 作为 `cursor` 传回去取下一页，每一页单独计费。

## English

Xiaohongshu (RedNote) API: notes, comments, creators, trends, PGY creator data and keyword index, through one key, paid per call.

No platform account, cookie or QR login. Paid per call from $0.02; errors are not charged. Free trial: up to 333 calls, no card. [Get a key](https://dataxapi.com/signin/?button=gh-xiaohongshu-api) · [All endpoints](https://dataxapi.com/apis/?ref=gh-xiaohongshu-api) · MCP: `https://api.dataxapi.com/mcp`.

## License

MIT

<sub>接口和价格取自 DataXAPI 的目录 0264e2d6dd4ff743、价格版本 23；以 [dataxapi.com/zh/apis](https://dataxapi.com/zh/apis/?ref=gh-xiaohongshu-api) 为准。</sub>
