# Pure Minimalist

- **id:** `pure-minimalist`
- **别名:** 纯极简, 编辑极简, 文字驱动极简, 墨色极简, Stripe Press风
- **一句话:** 每个词都挣得位置。每个像素都有工作。
- **适用:**
  - 写作工作室、内容机构与编辑服务
  - 咨询与专业服务公司
  - 附带刊物或 newsletter 的 SaaS 产品
  - 有强编辑声音的创始人与运营者
  - 写作质量本身就是产品演示的任何服务
  - 需要权威但不冰冷的法律、金融与专业品牌
- **避免:**
  - 需要亮色来传递能量、趣味或年轻感的产品
  - 靠视觉多样性驱动发现的电商或市场
  - 用技术密度传递可信度的开发者工具
  - 个性来自插画或动画的消费应用
  - 所在行业里极简会被读成简陋而非高端的品牌
- **来源:** https://uidesignprompts.com/prompts/pure-minimalist

## Prompt

## 纯极简设计系统 — 深度规格

### 理念
纯极简设计挣得留白 — 它不把空虚当装饰。每个间距决定、每个字体选择、每条边框，都是去掉不必要之物的结果，而不是加上看起来干净的东西。结果是通过精确传达权威的布局：精确的字号阶、墨色调加一种品牌色的克制色板，以及用细线而非色带做区块分隔。

这是以文字领先的品牌的设计语言。写作工作室、编辑平台、咨询公司、律所。内容就是产品。设计的工作是让开道路，同时发出认真之人做成的信号。

参考审美：Stripe Press、Every.to、Lenny's Newsletter，以及更好一类的机构作品集站点。它们共通：慷慨行高、克制使用的衬线展示体、墨色调而非真黑，以及读起来经过考虑却不自我炫耀的布局。

---

### 色彩系统

```
页面背景：    #FAFAF7  — 暖灰白，永远不要纯白（太刺、太通用）
暖表面：      #F2EDE4  — 交替区块，略更带色
沙表面：      #E8DCC8  — 最深暖表面，少用于强调面板
主墨：        #1A1917  — 标题，最重文字；暖近黑，永远不要 #000
次墨：        #4A4740  — 正文、描述；可读但明显次级
弱化：        #9A9590  — 标签、说明、时间戳、元文字
边框：        #E2DDD5  — 全部分隔、卡片边缘、区块分隔

品牌绿：      #1F4035  — 主交互色；按钮、眉题标签、激活态、关键强调
浅绿：        #2E5E4E  — 绿色元素的悬停态
绿淡彩：      rgba(31,64,53,0.08)  — 标签背景、芯片填充、浅徽章表面
强调陶土：    #C8622A — 少用：引语、POV 区块、高光时刻
```

**色彩规则：**
- 页面背景是 `#FAFAF7`，不是 `#FFFFFF`，也不是 AI 默认暖奶油 `#F4F1EA`。细微差别很重要 — 读作经过考虑，而不是模板。
- 墨绿（`#1F4035`）是唯一交互色。出现在主按钮、眉题标签、激活链接与行内标签。同一视觉块里永远不要出现在超过一种元素类型上。
- 陶土（`#C8622A`）只出现在 POV/品牌陈述区块 — 它是一次性颜色。用到别处会稀释信号。
- 整套色板是暖调。不要冷灰（带蓝调的 `#888`），不要冷近黑。每种弱化色都必须有暖（黄棕）偏向。
- 永远不要用投影。深度只通过边框色传达（`#E2DDD5`）。

---

### 字体 — 定义性决定

字体选择是防止本风格读成通用的关键。`Fraunces`（展示）+ `DM Sans`（正文）的组合形成编辑向、温暖、明确有意的配对。

**为什么是 Fraunces：**
Fraunces 是可变视觉尺寸衬线，大号时有古怪、墨绘个性。斜体有真正的书法性格。编辑品牌用它，正因为它不像默认衬线选择 — 它有观点而不装饰。

**为什么是 DM Sans：**
DM Sans 在 300–500 字重下正文尺寸异常干净。其几何构造与 Fraunces 更有机的字形搭配而不竞争。正文字重 300 时，创造让内容密集页面仍感轻盈的开放阅读体验。

```
展示 / 标题：  'Fraunces', Georgia, serif
  H1:   clamp(34px, 5.5vw, 58px) / 字重 600 / 行高 1.1 / 字距 -0.03em
  H2:   clamp(24px, 3.5vw, 38px) / 字重 600 / 行高 1.2 / 字距 -0.02em
  H3:   18–20px / 字重 600 / 行高 1.3 / 字距 -0.01em
  斜体变体（字重 300，font-style: italic）用于标题内的强调短语。

正文：  'DM Sans', system-ui, sans-serif
  正文：      16px / 字重 300–400 / 行高 1.75 / 颜色：#4A4740
  标签：      11–12px / 字重 600 / 大写 / 字距 0.08–0.1em / 颜色：#1F4035
  说明：      12–13px / 字重 400 / 颜色：#9A9590
  导航链接：  14px / 字重 400 / 颜色：#9A9590 → 悬停 #1A1917
  按钮：      14px / 字重 500
  价格：      28px / 衬线 / 字重 600 / 字距 -0.03em
  步骤标签：  13px / 衬线 / 斜体 / 字重 300 / 颜色：#9A9590
```

**关键手法 — 标题内的斜体衬线：**
```html
<h1>Content that ranks when <em>everything else</em> gets ignored.</h1>
```
Fraunces 标题内的 `<em>` 渲染为真正斜体，与正体有真实光学差异。用于标题中最重要的短语 — 读者需要去感受、而不只是读到的那个。每个标题限一个 `<em>`。

**关键规则：** 永远不要用加粗正文来建立层级。用颜色（`#1A1917` vs `#4A4740` vs `#9A9590`）和尺寸建立层级。粗体只应出现在标题、导航与标签中。

---

### 布局架构

所有内容约束在居中的 `max-width: 720px` 列。这是本风格的本质布局决定 — 创造为阅读优化的宽度，迫使设计通过字体与区块节奏工作，而不是复杂多列网格。

```css
:root { --max: 720px; }
.section-inner, .hero, .faq-inner, etc. {
  max-width: var(--max);
  margin: 0 auto;
  padding: 0 40px; /* 移动端减到 20px */
}
```

满宽例外（导航、客户条、POV 区块）通过打破约束制造节奏 — 因为其他一切都尊重约束，它们感觉有意。

**区块解剖：**
```
┌──────────────────────────────────────────────────────┐
│ border-bottom: 1px solid #E2DDD5                     │
│ padding: 72px 40px                                   │
│                                                      │
│   [眉题 — 11px 大写绿]                               │
│   [标题 — Fraunces，38px，第 1 行]                   │
│   [标题 — Fraunces，38px，斜体第 2 行]               │
│   [副文 — DM Sans 15px 字重 300]                     │
│                                                      │
│   [区块内容]                                         │
│                                                      │
└──────────────────────────────────────────────────────┘
```

区块内边距始终是 `72px 40px`（桌面）和 `56px 20px`（移动端）。永远不要用 `80px`、`96px` 或 `100px` — 这些会制造松散的「模板留白」感。`72px` 是具体且经过考虑的。

---

### 签名元素 — POV 区块

满宽面板，深墨绿（`#1F4035`），承载品牌的编辑立场。这是页面上唯一的色彩戏剧时刻 — 其余都是暖中性。它出现在样文与定价之间，访客读过内容证据后冲击最大。

```css
.pov { background: #1F4035; padding: 72px 40px; }
.pov-label { font-size: 11px; font-weight: 600; letter-spacing: 0.1em; text-transform: uppercase; color: rgba(255,255,255,0.45); margin-bottom: 20px; }
.pov-quote {
  font-family: 'Fraunces', serif;
  font-size: clamp(22px, 4vw, 38px);
  font-weight: 300; font-style: italic;
  color: #fff; line-height: 1.35; letter-spacing: -0.02em; margin-bottom: 28px;
}
.pov-body { font-size: 15px; color: rgba(255,255,255,0.7); line-height: 1.75; max-width: 540px; font-weight: 300; }
.pov-body strong { color: #fff; font-weight: 600; }
```

引语应是直接、有观点的主张 — 不是标语。对 Content Bakerz：*「AI 写内容。我们写能排在它前面的内容。」* 支撑段落给出理由，不软化主张。

---

### 导航

高 60px。左：衬线 logo（Fraunces，19px，字重 600），品牌名强调词用绿。中：4–5 个链接，14px，字重 400，弱化色。右：幽灵按钮 + 绿色主按钮。底边 `1px solid #E2DDD5`。

```css
nav { border-bottom: 1px solid #E2DDD5; padding: 0 40px; height: 60px; display: flex; align-items: center; justify-content: space-between; background: #FAFAF7; position: sticky; top: 0; z-index: 100; }
.nav-logo { font-family: 'Fraunces', serif; font-size: 19px; font-weight: 600; color: #1A1917; letter-spacing: -0.01em; }
.nav-logo span { color: #1F4035; }
.nav-links a { font-size: 14px; color: #9A9590; transition: color 140ms; }
.nav-links a:hover { color: #1A1917; }
```

移动端（<640px）：隐藏中间导航链接，只保留 logo + CTA 按钮。此内容密度不需要汉堡菜单。

---

### 如何运作 — 流程步骤

步骤竖列，每项用细 `1px` 底边作分隔。每行两列：左步骤标签（衬线斜体，字重 300，弱化 — 「one」「two」「three」，不是「01」「02」「03」），右步骤内容。

词标签（「one」「two」）而不是数字（「01」「02」）是刻意选择 — 读起来更人性、更编辑向，匹配写作工作室的品牌声音。

```css
.steps { display: flex; flex-direction: column; }
.step { display: grid; grid-template-columns: 48px 1fr; gap: 0 20px; padding: 28px 0; border-bottom: 1px solid #E2DDD5; }
.step-num { font-family: 'Fraunces', serif; font-size: 13px; color: #9A9590; padding-top: 4px; font-style: italic; font-weight: 300; }
.step-title { font-size: 16px; font-weight: 600; color: #1A1917; margin-bottom: 5px; }
.step-desc { font-size: 14px; color: #4A4740; line-height: 1.7; font-weight: 300; }
.step-tag { display: inline-block; margin-top: 10px; font-size: 11px; font-weight: 600; letter-spacing: 0.06em; text-transform: uppercase; color: #1F4035; background: rgba(31,64,53,0.08); padding: 3px 9px; border-radius: 3px; }
```

---

### 交付物网格 — 包含什么

`2×3` 功能卡片网格，以 `1px` 边框分隔。网格本身用 `background: #E2DDD5` 与 `gap: 1px`，让边框成为网格的一部分 — 而不是卡片边框。每张卡片有小 emoji 图标（emoji 唯一合适之处 — 作为功能记号，不是装饰）、粗标题与 2 行描述。

```css
.del-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 1px; background: #E2DDD5; border: 1px solid #E2DDD5; margin-top: 40px; }
.del-card { background: #FAFAF7; padding: 24px; }
.del-icon { font-size: 20px; margin-bottom: 12px; }
.del-title { font-size: 15px; font-weight: 600; color: #1A1917; margin-bottom: 5px; }
.del-desc { font-size: 13px; color: #4A4740; line-height: 1.65; font-weight: 300; }
```

---

### 样文 — 编辑列表格式

三篇博文样例竖列。每项两列行：内容左（标签、标题、摘要），元数据右（阅读时长、箭头）。悬停时标题变为绿色，箭头移动 `translate(2px, -2px)`。这是页面上唯一的悬停动画。

```css
.sample-card { display: grid; grid-template-columns: 1fr auto; gap: 16px 24px; padding: 24px 0; border-bottom: 1px solid #E2DDD5; cursor: pointer; }
.sample-tag { font-size: 11px; font-weight: 600; letter-spacing: 0.07em; text-transform: uppercase; color: #1F4035; margin-bottom: 7px; display: inline-block; }
.sample-title { font-family: 'Fraunces', serif; font-size: clamp(16px, 2vw, 20px); font-weight: 600; color: #1A1917; line-height: 1.3; letter-spacing: -0.01em; transition: color 150ms; }
.sample-card:hover .sample-title { color: #1F4035; }
.sample-excerpt { font-size: 13px; color: #4A4740; font-weight: 300; line-height: 1.6; margin-top: 6px; }
.sample-arrow { font-size: 16px; color: #9A9590; transition: transform 150ms, color 150ms; }
.sample-card:hover .sample-arrow { transform: translate(2px,-2px); color: #1F4035; }
```

样文标题应具体且可信 — 不是「如何写出更好的内容」，而是「如何写出把试用转成付费的产品驱动博文」。具体性是品牌演示的一部分。

---

### 定价 — 水平卡片行

三档方案显示为满宽水平行（不是标准三列卡片网格）。每行：左方案详情（名称、描述、包含项作小芯片），右价格 + CTA。这格式读作价目表，而不是对比表 — 更编辑向，更适合服务品牌。

```css
.plan-cards { display: flex; flex-direction: column; }
.plan-card { display: grid; grid-template-columns: 1fr auto; gap: 12px 32px; align-items: center; padding: 24px 0; border-bottom: 1px solid #E2DDD5; }
.plan-name { font-size: 16px; font-weight: 600; color: #1A1917; margin-bottom: 4px; }
.plan-desc { font-size: 13px; color: #4A4740; font-weight: 300; line-height: 1.6; max-width: 400px; }
.plan-include { font-size: 12px; color: #4A4740; background: #F2EDE4; border: 1px solid #E2DDD5; padding: 2px 9px; border-radius: 3px; }
.plan-price { font-family: 'Fraunces', serif; font-size: 28px; font-weight: 600; letter-spacing: -0.03em; color: #1A1917; }
```

「最受欢迎」徽章用绿淡彩（`rgba(31,64,53,0.08)`）背景与绿字 — 与眉题标签相同。一致性重要。

---

### FAQ 手风琴

单列列表。每项：问题在满宽按钮中（文字左对齐，右侧 `+` 图标），答案在带 `max-height` 过渡的折叠 `div` 中。一次只开一项 — 点新项会关上前一项。

```css
.faq-q { width: 100%; background: none; border: none; padding: 20px 0; display: flex; align-items: center; justify-content: space-between; font-size: 15px; font-weight: 600; color: #1A1917; cursor: pointer; }
.faq-q:hover { color: #1F4035; }
.faq-icon { font-size: 18px; color: #9A9590; transition: transform 200ms; font-weight: 300; }
.faq-item.open .faq-icon { transform: rotate(45deg); color: #1F4035; }
.faq-a { font-size: 14px; color: #4A4740; line-height: 1.75; font-weight: 300; max-height: 0; overflow: hidden; transition: max-height 280ms ease, padding 280ms ease; }
.faq-item.open .faq-a { max-height: 200px; padding: 0 0 20px; }
```

FAQ 问题应是真实异议，不是软球问题。对 Content Bakerz：「你们真的用 AI 吗？」「多久能看到结果？」「如果不喜欢草稿怎么办？」这些是成交或丢单的问题。

---

### 滚动显现

所有区块元素用 IntersectionObserver 随滚动显现。`opacity: 0 → 1` + `translateY(16px → 0)`，`threshold: 0.1`。用 nth-child 的 `transition-delay` 交错。已经可见的元素在加载时立即触发。

```css
.reveal { opacity: 0; transform: translateY(16px); transition: opacity 0.5s ease, transform 0.5s ease; }
.reveal.in { opacity: 1; transform: translateY(0); }
.reveal:nth-child(2) { transition-delay: 0.08s; }
.reveal:nth-child(3) { transition-delay: 0.16s; }
```

```javascript
const obs = new IntersectionObserver(entries => {
  entries.forEach(e => { if (e.isIntersecting) { e.target.classList.add('in'); obs.unobserve(e.target); } });
}, { threshold: 0.1 });
document.querySelectorAll('.reveal').forEach(el => obs.observe(el));
```

---

### 不要做什么
- ✗ 永远不要用纯白（`#FFFFFF`）或通用奶油（`#F4F1EA`）页面背景 — 色板是 `#FAFAF7`
- ✗ 永远不要给标题用 Inter — Fraunces 才是区分选择
- ✗ 永远不要用加粗正文做层级 — 改用颜色过渡
- ✗ 永远不要用三列定价卡片网格 — 水平行适合服务品牌
- ✗ 永远不要用编号 `01 / 02 / 03` 惯例做流程步骤 — 词标签（「one」「two」）更编辑向
- ✗ 永远不要把陶土强调（`#C8622A`）当按钮或交互色 — 它只出现在 POV 区块
- ✗ 永远不要居中对齐正文段落 — 只左对齐
- ✗ 永远不要给任何元素加投影 — 边框完成全部深度工作
- ✗ 永远不要用超过一个满宽色面板 — 绿色 POV 区块是唯一戏剧时刻
- ✗ 永远不要用「Lorem ipsum」或「我们帮助企业增长」这类占位文案 — 每个词都必须针对实际服务

### 待替换数据（占位映射）
- `[BRAND_NAME]` — 导航 logo、页脚、CTA 区块、所有引用
- `[TAGLINE]` — 英雄 H1，拆行并带一个斜体 `<em>` 短语
- `[HERO_SUB]` — 2 句：问题，然后是具体解决方案
- `[TRUST_ITEMS]` — 3 个短证明点：「无长期合同」「5 天出第一篇」等
- `[CLIENT_NAMES]` — 4–5 个公司名或服务过的行业
- `[PROCESS_STEPS]` — 4 步：词标签、标题、2 句描述、时间线标签
- `[DELIVERABLES]` — 6 张卡片：emoji 图标、标题、2 行描述
- `[SAMPLE_POSTS]` — 3 篇：行业标签、标题（要具体！）、2 句摘要、阅读时长
- `[POV_QUOTE]` — 一句大胆直接主张，不软化
- `[POV_BODY]` — 2–3 句解释主张背后的理由
- `[PRICING]` — 3 档：名称、描述、3–4 项包含内容、价格、CTA 标签
- `[FAQ]` — 4–5 个真实异议与具体回答
- `[CTA_HEADING]` — 收束标题，带一个斜体强调短语
- `[CONTACT_EMAIL]` — 用于「先和我们谈谈」mailto 链接
