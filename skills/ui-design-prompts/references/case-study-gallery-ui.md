# Case Study Gallery UI

- **id:** `case-study-gallery-ui`
- **别名:** 案例库画廊 UI, 客户故事中心, 灵感筛选画廊, Swipe File 界面
- **一句话:** 快速浏览。任意筛选。打开完整故事。
- **适用:**
  - 案例库与客户故事中心
  - 素材库与示例画廊（营销、文案、UI、邮件、广告）
  - 带筛选和分类的精选灵感站
  - 通讯归档与拆解合集
  - 每条作品背后都有短故事的作品集站点
  - 任何有 50 条以上条目、人们先浏览再阅读的内容站
- **避免:**
  - 阅读顺序比浏览更重要的长文博客
  - 文档站点（改用带左侧导航树的文档布局）
  - 带价格和购物车的商店或目录
  - 少于 12 条条目的站点；简单列表或编辑式布局更好
- **来源:** https://uidesignprompts.com/prompts/case-study-gallery-ui

## Prompt

## 案例画廊 UI — 设计系统

### 你在构建什么
一个内容站点，访客按此顺序做三件事：
1. 浏览 — 扫视密集的以图为主的卡片网格，停在有力的钩子上。
2. 筛选 — 用固定在屏幕右缘的精致侧栏收窄网格。
3. 打开 — 点击卡片，在全页模态中阅读完整案例，用右上角叉号关闭，
   且不丢失在网格中的位置。

网格用于扫视。模态用于阅读。绝不要把两份工作混在一起：卡片只承载
钩子、缩略图、阅读时长和一个分类标签。其余一切都在模态里。

用户自行提供内容、分类法和图像。网格、侧栏和模态的布局由本提示固定；主题可以是任何东西（营销示例、邮件拆解、SaaS 入职流程、广告创意、UI 模式、创始人故事）。

### 视觉识别 — 编辑式素材库
把它想成设计师的钉板变成井然有序的图书馆：干净白画布、
统一处理的深色图像卡片，以及安静给分类上色的小粉彩标签。页面本身平静。能量在卡片上。

- 页面背景和全页模态画布是纯白（#FFFFFF）。让白在卡片网格和阅读栏周围可见；暖灰白只用于安静控件内部。
- 每张案例卡片直角、圆角为零，包括网格、上一篇/下一篇链接和「更多类似」卡片。通讯卡和要点卡也是直角。
- 卡片以图为主，深色遮罩，图上是白色粗标题。
- 每个分类一个粉彩标签色，处处相同（卡片、侧栏、模态）。
- 黑墨是操作色：选中筛选、主按钮、模态关闭按钮。
- 一种荧光笔黄留给模态内强调（「偷走这个」要点）。
- 焦点环是蓝色，键盘用户总能看见自己在哪。

设计令牌（CSS 变量或 Tailwind v4 `@theme` 令牌）：
```
--canvas:       #FFFFFF   /* 页面与全页模态背景 */
--white:        #FFFFFF   /* 侧栏与文章面板 */
--soft:         #F6F3EE   /* 搜索、排序、分段、通讯卡 */
--ink:          #121110   /* 主文字、选中态、主按钮 */
--ink-soft:     #3B3732   /* 正文 */
--muted:        #77716A   /* 说明、元数据、占位符 */
--line:         #E4DED4   /* 边框与分隔（暖，绝不用冷灰） */
--highlighter:  #FFE45C   /* 强调标记、要点 */
--focus:        #2B50FF   /* 焦点环 */
--scrim:        rgba(12,10,9,0.55)  /* 卡片图像叠层 */

/* 粉彩标签对：背景 / 文字 */
--tag-pink:      #FFD9E0 / #8A1C3C
--tag-green:     #D5F2D8 / #1E5A2B
--tag-blue:      #D6E6FF / #1D3F8A
--tag-yellow:    #FFF1B8 / #6B5300
--tag-lavender:  #E5DAFF / #4B2A9A
--tag-peach:     #FFE0CC / #8A3F10
--tag-teal:      #CDEFE9 / #0E5A52
--tag-gray:      #E9E5DE / #4A453F

--radius-card:  0px
--radius-tag:   10px
--radius-panel: 28px
--radius-btn:   14px
--sidebar-w:    304px
--gutter:       24px
```
标签颜色规则：每个分类恰好分配列表中的一对，并把映射存在分类法文件中。绝不要每次渲染随机上色，也绝不要在同一组里把一对给两个分类。上面所有粉彩文字色在其背景上都通过 4.5:1。

### 字体排印
两个字体家族。一个管个性，一个管实用。
- 展示衬线（页面标题、模态标题、引文）：Fraunces、Instrument Serif 或
  Playfair Display。字重 500 到 600，letter-spacing -0.01em。
- UI 无衬线（卡片、筛选、正文、按钮）：DM Sans、Inter 或 Geist。字重 400、500、600、700。

```
页面 H1：         clamp(32px, 4vw, 52px)  衬线 500   lh 1.05
模态标题：        clamp(34px, 5vw, 64px)  衬线 500   lh 1.04   ls -0.015em
模态导语：        clamp(18px, 1.8vw, 22px) 无衬线 400  lh 1.55   颜色 --ink-soft
模态 H2：         28px                    衬线 500   lh 1.15
模态正文：        17–18px                 无衬线 400   lh 1.75   max-width 680px
卡片标题：        20px                    无衬线 700   lh 1.22   白色，在图上
芯片 / 标签：     14px                    无衬线 500   lh 1
分组标签：        11px                    无衬线 700   大写  ls 0.1em
元数据（阅读时长）：13px                   无衬线 500   等宽数字
按钮：            15px                    无衬线 600
```
卡片标题是钩子，不是标签（见内容规则）。20px 时保持 2 行。

### 页面外壳
外壳有三个区域：页头、内容栏、固定右侧栏。
```
┌──────────────────────────────────────────────────────┬──────────────┐
│ 页头：品牌在左 · 链接 + 社交在右                      │  固定        │
├──────────────────────────────────────────────────────┤  侧栏        │
│ 引言 + 已选筛选 + 结果计数                            │  （右，      │
├──────────────────────────────────────────────────────┤  304px，     │
│ 卡片网格（1440px 时 3 列）                            │  粘滞        │
│                                                      │  全高）      │
│ 加载更多                                              │              │
└──────────────────────────────────────────────────────┴──────────────┘
```
- 侧栏是 `position: fixed` 贴右缘，网格在页头下滚动时始终可见。它从不随页面滚走。
- 内容栏为它预留空间：
  `padding-right: calc(var(--sidebar-w) + var(--gutter) * 2);` 以及 `padding-left: 32px`。
- 内容最大宽度：无；网格填满可用栏，变宽时加列。
- 网格列：低于 640px 为 1 列，640–1099px 为 2 列（侧栏变成抽屉），
  1100–1799px 为 3 列，1800px 及以上 4 列。间距 20px。
- 垂直节奏：页头高 80px，其下 40px 是引言块，再下 28px 是网格，
  加载更多按钮下方 96px 是页脚。

### 页头
- 左：品牌标记（32px）加大写字标，letter-spacing 0.2em，13px，字重 700。
- 右：2 到 3 个文字链接（14px，字重 500，`--ink-soft`）和 2 到 3 个社交图标
  （28px，墨色，悬停下划线偏移）。链接和图标在侧栏左侧，绝不压在侧栏上。
- 不粘滞。网格视图上唯一粘滞/固定元素是侧栏，以及小屏上的「筛选」按钮。

### 引言与已选筛选条
网格上方：
- 展示衬线 H1：关于合集的陈述，例如
  「最好的[主题]，拆开看。」后跟一句 `--muted` 副标题。
- 结果行：左侧 `248 篇案例`（14px，`--muted`，计数用 `--ink` 字重 600），
  右侧仅小屏显示排序控件（桌面排序在侧栏）。
- 已选筛选作为可移除墨色芯片出现在 H1 下：标签加 x 按钮。
  其后显示「清除全部」文字按钮。未筛选时不渲染此行（不留空）。

### 卡片网格与卡片解剖
每张卡片是真正的链接（`<a href="/case/slug">`），因此无需 JavaScript 也能工作、
可新标签打开、可被抓取。JavaScript 把点击升级成模态。

```
┌─────────────────────────────────────┐
│  [缩略图，深色遮罩]                 │
│                                     │
│  白色钩子标题，                     │
│  最多两行                           │
│                                     │
│  ◐ 30 秒                 [ 分类 ]   │
└─────────────────────────────────────┘
```
- 宽高比 11 / 6，圆角为零（直角），`overflow: hidden`，
  `isolation: isolate`。
- 图像是案例的真实截图或关键视觉，`object-fit: cover`，
  页面和邮件截图用 `object-position: top center`。
- 遮罩：`linear-gradient(to bottom, rgba(12,10,9,0.62) 0%, rgba(12,10,9,0.50) 55%, rgba(12,10,9,0.72) 100%)`。
  每张卡片遮罩相同，网格读起来像一家人。
- 标题：左上，padding 20px 22px，白色，20px，字重 700，两行截断，轻微
  text-shadow `0 1px 12px rgba(0,0,0,0.35)`。
- 底行：绝对定位，左/右/底 14px，flex space-between，垂直居中。
  - 左：小图标（灯泡或时钟，18px，白）加阅读时长
    （「30 秒」「1 分钟」「3 分钟」），白 13px 字重 500。
  - 右：用其粉彩对的分类标签，14px，padding 7px 14px，圆角 10px。
- 每张卡片恰好一个分类标签。额外标签只出现在模态中。
- 悬停与焦点：卡片抬起 4px，图像在 400ms 内缩放到 1.04，遮罩约变亮
  12 percent，右上淡入一个小「打开」箭头芯片。
  键盘焦点画 3px `--focus` 环，偏移 3px。
- 激活（按下）：translateY(-1px)，遮罩回到正常。
- 变体：
  - 视频：居中 56px 白圆配墨色播放三角；标题移到底部元数据行上方。视频卡打开模态时播放器在顶部。
  - 精选（可选，最多每 12 张 1 张）：桌面跨 2 列，标题 28px。
  - 无图（少见）：纯深色 `#1C1A18` 加大衬线标题；绝不用库存图。
- 加载：同样宽高比的骨架卡，`#E9E4DA` 配缓慢横向微光。
- 空结果：居中块，衬线一行「没有匹配这些筛选的内容。」，一句弱化句子，以及「清除全部筛选」墨色按钮。
- 分页：网格下方居中「加载更多」次要按钮，带计数
  （「显示 248 中的 24」）。仅当按钮仍作为回退存在时才允许无限滚动。

### 右侧栏（精致、固定）
一块浮动面板，行为像控制台，而不是链接列表。

容器：
```css
.sidebar {
  position: fixed; top: 24px; right: 24px; bottom: 24px;
  width: var(--sidebar-w);
  background: #fff; border: 1px solid var(--line); border-radius: 28px;
  display: flex; flex-direction: column; overflow: hidden;
}
.sidebar-scroll { flex: 1; overflow-y: auto; padding: 20px 20px 8px;
  scrollbar-width: thin; scrollbar-color: #D8D1C4 transparent;
  -webkit-mask-image: linear-gradient(to bottom, #000 calc(100% - 24px), transparent);
          mask-image: linear-gradient(to bottom, #000 calc(100% - 24px), transparent); }
```
内容，从上到下：
1. 搜索：46px 输入，圆角 14px，`--soft` 填充，1px `--line` 边框，左侧搜索图标，
   右侧小「/」键帽提示。在任何地方按「/」聚焦它。输入时筛选
   （防抖 150ms）。占位符：「搜索 248 篇案例」。
2. 筛选标题：左侧「筛选」15px 字重 700；右侧「清除全部」文字按钮，
   仅在有选中时显示。其下 1px `--line` 线。
3. 分组（分类法，2 到 4 组）：每组是可折叠区块。
   - 分组标签：11px 大写，字距拉开，`--muted`，后跟填满剩余宽度的发丝线，再加小 chevron。这取代厚重的黑色标签块。
   - 标签下芯片换行，间距 8px，上边距 14px，组间距 24px。
   - 芯片：高 36px，padding 0 14px，圆角 10px，其分类的粉彩背景和文字，
     14px 字重 500，标签后 12px、55% 不透明度的计数（「SEO 18」）。
   - 选中芯片：背景 `--ink`，白字，左侧 14px 对勾，
     计数变白 70%。选中芯片保持尺寸，避免跳动。
   - 悬停：粉彩加深 6 percent 并抬起 1px。焦点：`--focus` 环。
   - 芯片是 `<fieldset>` 内的 `<button aria-pressed>`，`<legend>` 承载分组标签。
   - 逻辑：组内多选是 OR；跨组选择是 AND。
4. 阅读时长：4 段控件（任意、30 秒、1 分钟、3+ 分钟），高 40px，圆角 12px，
   `--soft` 轨道配白色滑动拇指，激活段 1px 边框。
5. 排序：原生 select，样式匹配搜索输入（最新、最旧、最短阅读、打开最多）。
6. 页脚卡（钉在侧栏底部，滚动区外）：
   `--soft` 填充，1px `--line` 边框，圆角为零，padding 16px，margin 12px。
   40px 圆形策展人头像，一行 14px 字重 600（「每周收到一篇新案例」），以及行内邮箱字段配墨色「加入」按钮（44px）。无虚线边框、无星星、无杂物。
- 状态镜像到 URL（`?cat=seo,sales&time=30s&q=email&sort=new`），以便分享筛选视图，浏览器后退可用。
- 计数实时更新，反映其他组的当前选择。
- 低于 1100px 侧栏变成右侧抽屉：从右缘滑入
  （宽 min(92vw, 380px)），覆盖 `rgba(12,10,9,0.5)` 背景，由右下固定
  「筛选」药丸按钮打开（墨色填充，白字，高 52px，有筛选时显示计数徽章）。抽屉右上有关闭图标，底部钉「显示 36 条结果」墨色按钮。

### 全页模态（案例阅读器）
点击卡片在占据整个视口的模态中打开完整案例。

行为：
- 覆盖全视口（`position: fixed; inset: 0; width: 100dvw; height: 100dvh`），
  背景 `--canvas`，内部滚动（`overflow-y: auto`）。背后页面停止
  滚动（锁定 body 滚动，保留网格滚动位置，关闭时恢复）。
- 以 220ms 淡入加 24px 上滑打开。关闭用反向 160ms。
- 关闭：叉号按钮固定在模态右上，滚动时始终可见。
  ```css
  .modal-close {
    position: fixed; top: 20px; right: 20px; z-index: 5;
    width: 48px; height: 48px; border-radius: 50%;
    background: var(--ink); color: #fff; display: grid; place-items: center;
    transition: transform .2s, background .2s;
  }
  .modal-close:hover { transform: scale(1.08) rotate(90deg); background: #000; }
  .modal-close svg { width: 20px; height: 20px; stroke: currentColor; stroke-width: 2.2; }
  ```
  图标是两根交叉线组成的干净 X。`aria-label="关闭案例"`。
  也在 Escape、浏览器后退、以及宽屏点击阅读栏外空白边距时关闭。
- 键盘：左右箭头在当前筛选列表内切到上一篇/下一篇。
  Tab 焦点困在模态内；关闭时焦点回到来源卡片。
- URL：打开把 `/case/<slug>` 推入历史；关闭回到带筛选的上一网格 URL。
  直接访问 `/case/<slug>` 以独立页渲染同样布局（完整 SEO 元数据），关闭图标作为回画廊的链接。
- ARIA：`role="dialog"`，`aria-modal="true"`，`aria-labelledby` 指向标题。

模态布局（从上到下，内容栏最大宽 1080px，居中，padding 0 32px）：
1. 顶栏（不粘滞，高 88px）：左侧弱化「24 条结果中的第 3 条」计数，配
   小的上一篇/下一篇箭头按钮（40px，1px 边框，圆角 12px）。关闭图标在屏幕右上（固定，见上）。
2. 主视觉媒体：主图或视频，圆角 28px，16:9，1px `--line` 边框。视频案例
   在此显示播放器，中性播放叠层（白圆、墨色三角）。
3. 标题块：分类标签（粉彩）加阅读时长和日期作为一行弱化元数据，
   然后展示衬线标题，然后导语段（一句话要点）。
4. 两列正文（桌面）：左主栏 680px，右「一览」侧栏 300px，
   间距 64px。侧栏是 `position: sticky; top: 96px`，包含：品牌或来源、
   渠道、目标、结果（标题指标用 36px 衬线）、使用的工具或战术（小标签）、
   以及「访问原文」描边按钮。移动端侧栏变成导语下的 2 列事实网格。
5. 主栏中的正文分节，每节衬线 H2 和短编号标签
   （「01」）：背景设定、他们做了什么、为什么有效、偷走这个。
   - 正文 17–18px，行高 1.75，`--ink-soft`。
   - 行内图和截图拉满栏宽，圆角 20px，1px 边框，配
     13px 弱化说明。点击打开简单灯箱。
   - 引文：衬线斜体 26px，3px 墨色左线，左内边距 24px。
   - 「偷走这个」：白卡，圆角为零，1px 边框，padding 28px，3 到 5 条要点列表，每行关键短语包在荧光笔标记中：
     ```css
     mark.hl { background: linear-gradient(transparent 55%, var(--highlighter) 55%);
               color: inherit; padding: 0 2px; }
     ```
6. 操作行：复制链接（描边）、保存（描边）、分享（墨色）。高 48px 的按钮。
7. 上一篇 / 下一篇：两张并排直角链接卡（衬线 22px 标题，左小缩略图），
   遵循当前筛选顺序。
8. 更多类似：3 张卡片，使用网格中完全相同的卡片组件，按共享分类筛选。
9. 页脚条：直角 `--soft` 面板中的通讯订阅，然后站点页脚。

低于 900px 时模态单列；侧栏事实放在导语下；关闭按钮缩到 44px；上一篇/下一篇卡片堆叠。

### 路由模式（推荐 Next.js App Router）
使用拦截路由和并行路由，让同一 URL 既是模态也是页面：
```
app/
  layout.tsx                  渲染 {children} 和 {modal}
  page.tsx                    画廊（页头、侧栏、网格）
  @modal/
    default.tsx               返回 null
    (.)case/[slug]/page.tsx   拦截的模态版本
  case/[slug]/page.tsx        独立页（SEO、直链）
```
网格状态（筛选、搜索、排序）活在 URL search params 中。其他框架
在打开时用 `history.pushState`，用 `popstate` 监听器关闭。

### 内容模型
每篇案例是一条数据（带 frontmatter 的 MDX、JSON 或 CMS 记录）：
```
title:        string   // 钩子，最多 70 个字符
slug:         string
thumbnail:    image    // 最小 1100 x 600，真实截图或关键视觉
heroImage:    image    // 可选，模态用更大版本
video:        url      // 可选，使其成为视频案例
category:     string   // 恰好一个主分类（驱动标签色）
tags:         string[] // 0–6 个额外标签（显示在模态中）
readTime:     "30 secs" | "1 min" | "3 mins"
date:         ISO date
source:       { name, url }
summary:      string   // 模态和 meta description 用的一句话导语
facts:        { channel, goal, result, tools[] }
sections:     { setup, whatTheyDid, whyItWorks, stealThis[] }
gallery:      { image, caption }[]
```
分类法文件：带有序分类及其粉彩对的分组，例如
`{ group: "Acquisition", items: [{ label, color }] }`。用户定义分组和标签；
每组保持 3 到 6 项，让侧栏紧凑。

### 内容规则（这些让风格成立）
- 标题是钩子：具体主张、数字、对比或意外细节
  （「那封赚到 2M 点击的邮件」「为什么这则广告没有形容词」）。绝不要用平淡标签
  （「邮件示例 12」）。
- 缩略图是真的：事物本身的裁剪截图。裁切一致
  （页面和邮件顶部对齐）。绝不用通用库存图或 AI 渲染。
- 阅读时长诚实，只用三个值：30 秒、1 分钟、3 分钟。
- 每篇案例以「偷走这个」列表收尾。若没有可偷的，它就不该存在。
- 分类名保持一两个词。侧栏计数必须准确。
- 用直白句子写作。没有填充开场，没有「在当今快节奏的世界」。

### 组件参考
```css
.tag { display: inline-flex; align-items: center; padding: 7px 14px;
       border-radius: 10px; font-size: 14px; font-weight: 500; line-height: 1;
       background: var(--tag-bg); color: var(--tag-fg); }

.chip { height: 36px; padding: 0 14px; border-radius: 10px; font-size: 14px; font-weight: 500;
        background: var(--tag-bg); color: var(--tag-fg); display: inline-flex;
        align-items: center; gap: 8px; transition: background .15s, transform .15s; }
.chip[aria-pressed="true"] { background: var(--ink); color: #fff; }
.chip:hover { transform: translateY(-1px); }

.case-card { position: relative; display: block; aspect-ratio: 11 / 6;
  border-radius: 0; overflow: hidden; isolation: isolate; background: #1C1A18;
  transition: transform .25s ease; }
.case-card:hover { transform: translateY(-4px); }
.case-card img { position: absolute; inset: 0; width: 100%; height: 100%;
  object-fit: cover; object-position: top center; transition: transform .4s ease; z-index: -2; }
.case-card:hover img { transform: scale(1.04); }
.case-card::before { content: ""; position: absolute; inset: 0; z-index: -1;
  background: linear-gradient(to bottom, rgba(12,10,9,.62), rgba(12,10,9,.50) 55%, rgba(12,10,9,.72)); }
.case-card h3 { color: #fff; font-size: 20px; font-weight: 700; line-height: 1.22;
  padding: 20px 22px; display: -webkit-box; -webkit-line-clamp: 2;
  -webkit-box-orient: vertical; overflow: hidden; }

.btn-ink { height: 48px; padding: 0 22px; border-radius: 14px; background: var(--ink);
  color: #fff; font-weight: 600; }
.btn-outline { height: 48px; padding: 0 22px; border-radius: 14px; background: transparent;
  color: var(--ink); border: 1px solid var(--ink); font-weight: 600; }
:focus-visible { outline: 3px solid var(--focus); outline-offset: 3px; }
```

### 动效
- 卡片：250ms 抬起，400ms 图像缩放。网格项首次加载和每次筛选变更后上移 16px 淡入，40ms 错开（错开上限 12 项）。
- 筛选变更：结果 180ms 交叉淡入；绝不要用长过渡动画布局跳动。
- 侧栏芯片：仅 150ms 背景和变换过渡。
- 模态：进 220ms，出 160ms；关闭按钮悬停旋转 90 degrees。
- 尊重 `prefers-reduced-motion`：去掉变换，只保留不透明度淡入。

### 无障碍
- 卡片是带描述性名称的链接（「阅读案例：<title>」）。可见标题
  位于保证白字至少 4.5:1 对比的遮罩上。
- 筛选芯片是带 `aria-pressed` 的切换按钮；分组是带 legend 的 fieldset；
  结果计数通过 `aria-live="polite"` 区域宣告。
- 模态：焦点陷阱、Escape 关闭、焦点回到打开者、背景 `inert`。
- 200 percent 缩放和纯键盘都可用。
- 绝不要只靠颜色传达分类；标签文字始终存在。

### 性能与 SEO
- 缩略图：WebP 或 AVIF，宽 1100px，`loading="lazy"`（前 6 张 eager），显式宽高避免布局偏移，加载时用主色占位。
- 每篇案例在 `/case/<slug>` 有可索引页面，含 title、description、Open Graph 图，
  以及 `Article` 结构化数据。模态是该页的渐进增强。
- 超过 100 项时分页或虚拟化；首次渲染保持在 24 张卡以内。

### 内容槽位（由用户提供）
- `[SITE_NAME]`、logo、页头链接和社交链接
- 引言的 `[H1]` 和 `[SUBTITLE]`
- `[TAXONOMY]` 分组和标签，配已分配的粉彩色
- `[CASES]` 条目，遵循内容模型，配真实截图
- `[NEWSLETTER]` 表单端点和策展人头像
- `[SORT_OPTIONS]`（若与默认不同）

### 不要做
- 没有左侧栏。筛选面板始终固定在右侧。
- 没有灰白页面背景；把柔暖色留给控件和小面板。
- 没有圆角卡片。案例、要点、通讯和上一篇/下一篇卡片保持直角。
- 没有跨越侧栏的全宽页头条；右缘归侧栏。
- 分组名不用厚重黑色标签块；用发丝标签模式。
- 侧栏没有虚线边框、星星装饰或贴纸式小组件。
- 没有随机标签色；每个分类一对粉彩，处处使用。
- 卡片上不超过一个分类标签。
- 没有库存摄影或 AI 生成缩略图顶替真实示例。
- 卡片悬停移动不超过 4px，缩放不超过 1.04。
- 卡片或侧栏没有投影；用边框和遮罩。
- 没有带页码的分页；用加载更多或带回退的无限滚动。
- 模态不小于视口；始终全页。
- 除右上叉号（外加 Escape 和后退）外没有其他关闭控件。
- 模态内主内容不用轮播；用纵向阅读流。
- 没有泛标题或泛按钮，如「点击这里」或「阅读更多」。
- 没有第三种字体，没有第二种操作色；墨色就是操作色。
