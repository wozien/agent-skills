---
name: ui-design-prompts
description: >-
  Applies one of 33 curated website UI design-style prompts (Chinese). Use when
  designing or restyling a website, landing page, dashboard, marketing page,
  portfolio, auth flow, 网站风格, 设计风格, UI prompt, 视觉风格, 落地页, or when the user
  names a style such as NeoBrutalism, Glassmorphism, Fintech UI, Todo List UI.
---

# ui-design-prompts

33 套网站 UI 设计风格。做页面或改视觉时先用本索引选风格，再打开对应 `references/` 全文，把 **Prompt** **原文执行**。不要改写语气，也不要擅自加「更现代 / 更简洁」。

来源：[uidesignprompts.com](https://uidesignprompts.com/explorer)。色值、字体名、CSS、占位符保持文件原文。

## 何时用

- 网站 / 落地页 / 营销页 / 后台 / 作品集 / 认证页，需要明确视觉风格
- 用户点名风格（中英文名、`id`、别名都可以）
- 用户说「用我常用的 UI 风格 / prompt」但没指定哪一条

不要用：纯后端、纯逻辑、与视觉无关的改动。

## 怎么选

1. 已点名 → 用 `id`、英文标题、中文别名匹配，打开对应 `references/<id>.md`。
2. 未点名 → 对照下面的 **适用 / 避免** 列出 2–4 个候选（标题 + 一句话），让用户选；只有一条明显合适时直接用。
3. 产品类型落在某条 **避免** 上 → 不要选那条，改推索引里更合适的。
4. 匹配不到 → 停下来说明，禁止临时代写一套「差不多」的风格。

选中后把该文件 **Prompt** 当硬约束：布局、色彩、字体、组件、动效、文案语气都跟它走。当次的产品信息（行业、受众、页面类型）可以叠加上去，但不能覆盖视觉规定。

若同时用了 `ui-ux-pro-max` 等通用设计 skill：以本风格 Prompt 为视觉准绳，通用 skill 只补无障碍、间距、组件结构等未覆盖项。

## 风格索引

全文都在 `references/`。选风格看「适用 / 避免」，生成 UI 必须读全文 Prompt。

### Todo List UI (`todo-list-ui`)

柔和卡片。优先级一目了然。点一下就能往前推进。

- 适用：待办与任务管理；产品里的清单（入职、项目、CRM）；习惯打卡与个人计划；带优先级/状态的团队任务；行记录 + 快捷操作的后台；需要精致 CRUD 示例的作品集
- 避免：10 列以上稠密表；以看板拖拽为主；要中性严肃的企业工具；深色高对比开发者工具
- 全文：[references/todo-list-ui.md](references/todo-list-ui.md)

### Case Study Gallery UI (`case-study-gallery-ui`)

快速浏览。任意筛选。打开完整故事。

- 适用：案例库与客户故事；素材/拆解画廊；带筛选的灵感站；通讯归档；每条都有短故事的作品集；50+ 条目、先浏览再阅读的内容站
- 避免：阅读顺序更重要的长文博客；文档站（用左侧导航树）；带购物车的商店；少于 12 条时用简单列表更好
- 全文：[references/case-study-gallery-ui.md](references/case-study-gallery-ui.md)

### Edtech UI (`edtech-ui`)

一张脸、一套项目、一份证明。向你看得见的人学习。

- 适用：AI 学院与技能训练营；创作者/创始人课程；有讲师出镜的同期班；会员 + 免费资料社区；按职业或城市做 SEO 落地页
- 避免：传统大学（需更正式）；儿童教育（需更明亮好玩）；企业 LMS/合规门户；没有讲师或视频证明
- 全文：[references/edtech-ui.md](references/edtech-ui.md)

### Creator Education Funnel (`creator-education-funnel`)

用个性去教。建立信任。让下一步清晰可见。

- 适用：独立创作者卖一门旗舰课；有课纲和每周交付的直播同期班；约咨询的教练；围绕学员作品的技能漏斗；最多三条学习路径的小学院
- 避免：要复杂搜索筛选的大课程市场；LMS/课时播放器/学员门户；企业培训采购；闪购促销型活动
- 全文：[references/creator-education-funnel.md](references/creator-education-funnel.md)

### Blog Detail Page UI Design (`blog-detail-ui`)

清晰建议。温暖细节。为阅读而建。

- 适用：长文购买指南与技术建议；带对比表的价格指南；有摘要/清单/来源的研究文；内容驱动的产品发现；多章节教程
- 避免：全程满幅摄影的故事；几乎不需导航的短公告；大 CTA 才是主体的活动页
- 全文：[references/blog-detail-ui.md](references/blog-detail-ui.md)

### Fintech UI (`fintech-ui`)

大胆。精确。让钱变简单。

- 适用：消费金融落地页；数字银行与支付；个人理财与预算；储蓄目标；编辑风金融营销站
- 避免：加密交易终端；稠密财务仪表盘/会计软件；传统企业银行站；手机银行 App 界面
- 全文：[references/fintech-ui.md](references/fintech-ui.md)

### Healthcare Startup UI Design (`healthcare-ui`)

冷静。有人味。建立在信任上。

- 适用：数字健康品牌站；远程医疗；私立诊所与家庭护理；预防医疗与心理健康；面向消费者的医疗科技
- 避免：医院管理后台/病历系统；健身追踪；医疗设备目录；企业 B2B 医疗平台
- 全文：[references/healthcare-ui.md](references/healthcare-ui.md)

### DTC Brand UI (`dtc-brand-ui`)

一个主视觉。一件产品。全部信念。

- 适用：1–3 个主打实体产品；视觉识别强的消费品；想摆脱模板的 Shopify DTC；单一旗舰产品发布；靠设计与信念竞争的品牌
- 避免：SKU/品类很多的大目录；B2B/企业产品；服务或 SaaS；只拼价格的大宗商品；平台/聚合商
- 全文：[references/dtc-brand-ui.md](references/dtc-brand-ui.md)

### Cinematic UI (`cinematic-ui`)

一次只讲一个镜头的故事。

- 适用：有视觉故事的品牌/产品发布；餐饮、时尚、酒店、建筑等影像主导项目；展览与娱乐发行
- 避免：核心是快速扫读或高频重复操作；影像无法形成一致主体或场景
- 全文：[references/cinematic-ui.md](references/cinematic-ui.md)

### Kinetic UI (`kinetic-ui`)

有效的动效。有生命感的交互。

- 适用：用打磨感证明品质的 SaaS 落地页；开发者/设计工具；要强第一印象的发布；动效即作品证明的作品集；交互叙事
- 避免：动效会造成迷失的无障碍关键应用；动画干扰读数的仪表盘；低带宽；阅读型站点；无 `prefers-reduced-motion` 回退
- 全文：[references/kinetic-ui.md](references/kinetic-ui.md)

### Modern Elite (`modern-elite`)

工程化的光。打磨到极致。

- 适用：高端 SaaS；开发者与设计师受众；品牌观感等于信任；作品集与创意机构
- 避免：要快速上线；简单工具型产品；动效与打磨预算有限
- 全文：[references/modern-elite.md](references/modern-elite.md)

### Glassmorphism (`glassmorphism`)

磨砂玻璃。晨光。有深度而无重量。

- 适用：消费理财/银行/投资；健康与冥想；年轻向音乐娱乐；靠高级感转化的生活方式 App；有强摄影资产的移动优先产品；偏 Apple 审美的落地页
- 避免：开发者/技术产品；要高对比的数据仪表盘；无障碍关键产品（磨砂降对比）；机构信任优先的 B2B；深色品牌（玻璃需要浅色渐变来反射）
- 全文：[references/glassmorphism.md](references/glassmorphism.md)

### Bauhaus / Swiss Modern (`bauhaus-swiss-modern`)

形式追随功能。网格即法律。色彩即结构。

- 适用：设计工作室、建筑事务所、文化机构；要权威与纪律的代理商；学术机构；设计/字体/印刷品牌；界面本身应体现其所倡导专业的产品
- 避免：要温度亲和的消费科技；要好玩的创业产品；用颜色编码对错状态；需要全彩生活摄影；面向非设计买家的 SaaS
- 全文：[references/bauhaus-swiss-modern.md](references/bauhaus-swiss-modern.md)

### Monochrome / High Contrast (`monochrome-high-contrast`)

零色彩。最大工艺。无处可藏。

- 适用：克制即高端的奢侈与时尚；创意工作室作品集；设计师/摄影师个人站；强字体识别的刊物；权威是主信号的品牌
- 避免：状态色是核心模式；靠色彩驱动情绪的消费 App；用颜色编码分类的数据可视化；黑白会被读成冷峻的受众；要温暖好玩的品牌
- 全文：[references/monochrome-high-contrast.md](references/monochrome-high-contrast.md)

### Terminal Design (`terminal-design`)

命令行审美。零装饰。纯信号。

- 适用：CLI 与周边工具；基础设施/DevOps；安全与黑客工具；技术向开源落地页；开发者个性强的博客/文档
- 避免：非技术消费产品；需要食物/生活摄影或插画；要温度的电商转化页；无障碍与亲和优先；面向经理/非工程买家的 SaaS
- 全文：[references/terminal-design.md](references/terminal-design.md)

### Pure Minimalist (`pure-minimalist`)

每个词都挣得位置。每个像素都有工作。

- 适用：写作工作室与编辑服务；咨询与专业服务；带刊物的 SaaS；写作质量本身就是演示的服务；要权威但不冰冷的专业品牌
- 避免：要靠亮色传递年轻能量；靠视觉多样性发现的电商；用技术密度取信的开发者工具；个性来自插画动画的消费 App；极简会被读成简陋的行业
- 全文：[references/pure-minimalist.md](references/pure-minimalist.md)

### Restaurant UI (`restaurant-ui`)

新鲜。本地。为让你饿而设计。

- 适用：要靠网站带单的本地餐厅；食物摄影强的咖啡/早午餐；快休闲与外卖店；WhatsApp 点餐；农场直达餐桌；菜单即产品
- 避免：更适合深色编辑风的精致正餐；报价表单优先的团餐；外卖聚合 App（用电商布局）；没有实体空间的幽灵厨房
- 全文：[references/restaurant-ui.md](references/restaurant-ui.md)

### Chat App UI (`chat-app-ui`)

三栏。一个目的。始终在上下文中。

- 适用：SaaS 应用内消息/通知；工程运维内部工具；客服聊天门户；社区与创作者空间；频道/线程型开发者工具；Slack 替代/工作区
- 避免：消费级一对一气泡聊天；单线程 AI 对话（无侧栏更干净）；简单评论区；聊天只是次要功能
- 全文：[references/chat-app-ui.md](references/chat-app-ui.md)

### Developer Portfolio (`developer-portfolio`)

暗色。克制。为被录用而建。

- 适用：找工作的工程师；项目+经历并重的全栈；要暗色高级感的自由职业者；希望作品集「看起来更资深」的初级开发；申请产品公司/创业公司
- 避免：展示视觉品牌作品的设计师（用浅色画廊）；代码不是主线的创意人；要正式 CV 的企业顾问；雇主只要一页传统简历
- 全文：[references/developer-portfolio.md](references/developer-portfolio.md)

### Claymorphism / 3D Soft UI (`claymorphism`)

充气感。好玩。物理上令人满足。

- 适用：年轻向消费 App；教育学习；健康心理；要亲切的无代码工具；游戏化与习惯打卡；移动优先效率工具；儿童与家庭产品
- 避免：企业/专业 B2B；要严肃的金融；开发者工具；密集仪表盘；权威比亲和更重要
- 全文：[references/claymorphism.md](references/claymorphism.md)

### Indie SaaS (`indie-saas-retro-utility`)

诚实。直接。由一个当真的人做出来。

- 适用：独立 SaaS 与单人工具；要诚实直接的自举产品；广告网络/newsletter/垂直工具；创始人即品牌
- 避免：要正式信任信号的企业 B2B；非技术消费 App；价值靠影像堆出来的产品；需要强色彩品牌；SKU 很多的电商
- 全文：[references/indie-saas-retro-utility.md](references/indie-saas-retro-utility.md)

### Sketch Design (`sketch-design`)

看起来像手绘。感觉活着。

- 适用：创意艺术产品；设计师/插画师作品集；教育或儿童产品；温度和人性重要的工具；要从精致 SaaS 里跳出来
- 避免：企业或金融；信任信号压倒一切；要精确的数据仪表盘；要精致高端形象
- 全文：[references/sketch-design.md](references/sketch-design.md)

### Engineering Blueprint UI (`engineering-blueprint-ui`)

精确。技术。按规格绘制。

- 适用：UI kit/设计系统展示；开发者工具落地页；面向工程师的 SaaS；技术向内部工具；要传达精度的作品集；线框/原型工具
- 避免：非技术消费 App；要温度柔软；电商或生活方式；健康家庭向；可读性必须先于风格
- 全文：[references/engineering-blueprint-ui.md](references/engineering-blueprint-ui.md)

### Admin Dashboard UI (`admin-dashboard-ui`)

彩色数据。清晰层级。为天天待在里面而建。

- 适用：SaaS 分析报表；电商后台；项目管理；CRM 与运营；数据可视化是核心体验
- 避免：单页营销站；没有数据的消费 App；只有一个主操作；内容/编辑型产品
- 全文：[references/admin-dashboard-ui.md](references/admin-dashboard-ui.md)

### Documentation UI (`documentation-ui`)

深色、结构清晰，为快速找到答案而设计。

- 适用：开发者文档；API 参考；技术 Wiki；开源项目文档；SDK/库指南
- 避免：营销落地页或消费产品；适合明亮温暖视觉的内容；浅色才是品牌预期；不需要深层导航的短内容
- 全文：[references/documentation-ui.md](references/documentation-ui.md)

### Newsletter UI (`newsletter-ui`)

编辑气质、订阅者优先，把读者变成粉丝。

- 适用：Newsletter 落地页与刊物首页；独立媒体与创作者；博客与个人刊物；思想领导力长文；要编辑向展示的创作者工具
- 避免：阅读不是主行为的 SaaS；电商/交易型；要强转化压迫感；开发者工具
- 全文：[references/newsletter-ui.md](references/newsletter-ui.md)

### NeoBrutalism (`neobrutalism`)

大胆、响亮、成体系，而且能用。

- 适用：要立刻跳出来的 SaaS 落地页；开发者工具与独立黑客产品；设计系统营销站；有文化自觉的大胆受众；对抗通用企业风
- 避免：医疗/法律/金融等要保守信任；买家期待精致极简的企业 B2B；复杂可视化里边框只会添噪；要柔软奢华
- 全文：[references/neobrutalism.md](references/neobrutalism.md)

### Quiz App UI (`quiz-app-ui`)

计时、计分、漂亮的紫色。

- 适用：测验 trivia；教育评估；游戏化引导；限时挑战；知识测试 SaaS
- 避免：要中性企业色板；多用户仪表盘/分析；长文或文档；紫色与既有品牌冲突
- 全文：[references/quiz-app-ui.md](references/quiz-app-ui.md)

### Newspaper Design (`newspaper-design`)

权威、墨色、编辑分量。

- 适用：内容优先与出版；媒体品牌落地页；权威最重要的产品；研究/知识库/情报；想像「权威大报」的 SaaS 落地页
- 避免：要明亮玩味的消费 App；年轻潮流向；视觉优先（设计/照片/视频工具）；速度与行动优先于阅读
- 全文：[references/newspaper-design.md](references/newspaper-design.md)

### Launchpad / Directory UI (`launchpad-ui`)

社区驱动、可投票，把最好的推到前面。

- 适用：产品发布与目录；社区策展列表；应用商店与工具发现；点赞排名；Newsletter 目录与创作者社区
- 避免：单产品落地页；个人作品集/博客；电商店面；没有列表、信息流或投票机制
- 全文：[references/launchpad-ui.md](references/launchpad-ui.md)

### Whimsical SaaS (`whimsical-saas`)

手作能量、独立灵魂，却意外能转化。

- 适用：独立创始人 SaaS；面向开发者/创作者的消费 App；有个性的一次性付费产品；创始人即品牌；要从无菌 VC 风里跳出来
- 避免：信任信号必须压过个性的企业 B2B；必须严肃的医疗/法律/金融；Fortune 500 买家；要看起来「企业」
- 全文：[references/whimsical-saas.md](references/whimsical-saas.md)

### E-Commerce UI (`ecommerce-ui`)

温暖、转化导向、产品优先。

- 适用：实体或数字商品商店；科技电子零售；多品类市场；D2C 店面；需要购物车与结账的产品站
- 避免：无库存的 SaaS/服务；博客或编辑刊物；购买在站外完成的 B2B；要深色高对比
- 全文：[references/ecommerce-ui.md](references/ecommerce-ui.md)

### Auth Pages UI (`auth-pages-ui`)

建立信任、干净、为转化优化。

- 适用：SaaS 登录注册；Google/Apple/邮箱社交登录；注册时品牌信任很重要；要客户 logo/推荐的 B2B；注册/登录/找回密码多页流
- 避免：不需要整页的单字段表单；深色模式优先的系统；简短比信任更重要的消费 App；没有社会证明可展示
- 全文：[references/auth-pages-ui.md](references/auth-pages-ui.md)

## 怎么补条目

新风格放到 `references/<id>.md`，并在本索引追加一条（一句话 + 适用 + 避免 + 链接）。不要把全文写进 SKILL.md。
