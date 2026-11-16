# Monochrome / High Contrast

- **id:** `monochrome-high-contrast`
- **别名:** 单色高对比, 黑白极简, 零色彩, 高反差黑白, 奢侈品黑白站
- **一句话:** 零色彩。最大工艺。无处可藏。
- **适用:**
  - 克制即高端信号的奢侈与时尚品牌
  - 展示作品集的创意工作室与设计机构
  - 设计师或摄影师个人站点
  - 有强字体识别的编辑出版物
  - 权威与自信是主要品牌信号的产品
  - 别人都在动、自己靠站住来竞争的任何品牌
- **避免:**
  - 需要状态色（错误/成功/警告）作为核心 UI 模式的产品
  - 用色彩驱动情绪参与或留存的消费应用
  - 用颜色编码分类含义的数据可视化
  - 面向把硬朗黑白联想成冷峻的受众
  - 需要温暖、亲和或玩趣感的品牌
- **来源:** https://uidesignprompts.com/prompts/monochrome-high-contrast

## Prompt

## 单色 / 高对比设计系统 — 深度规格

### 理念
零色彩不是限制。它是信念。每个视觉决定 — 层级、节奏、强调、情绪 — 只通过字体、对比、空间与动效传达。结果是不能把色彩当拐杖的设计，因此其他一切都必须执行完美。

这相当于音乐家只弹一个音，却弹得完美。成功时非凡。失败时只是灰。差别是工艺。

参考审美：瑞士编辑设计、日本时装屋识别系统与奢侈品牌数字端的交汇。想 Bottega Veneta 的网站、Bureau Borsche 的自我推广、AnOther Magazine 的数字版。

---

### 色彩系统 — 绝对规则

```
纯黑：        #000000  — 主导标题、粗边框、实心按钮、全出血区块
偏黑：        #111111  — 白色区块上的卡片背景、反转表面
深灰：        #222222  — 次级深色表面
中灰：        #888888  — 正文、弱化标签、非激活链接
浅灰：        #CCCCCC  — 白色区块之间的边框、发丝线
近白：        #F2F2F2  — 交替区块背景（少用）
纯白：        #FFFFFF  — 主页面背景、黑色区块上的文字
```

**零色彩法则：**
- 不要蓝。不要红。不要绿。哪怕 5% 带色调的灰也不要。
- 不要渐变，不要带色阴影，不要彩色边框。
- 唯一允许的例外：若必须有单一交互强调（链接色、激活态），必须是 `#000000` 或 `#FFFFFF` — 反转，不是上色。
- 连错误态也通过图案与位置传达，而不是红色。

**反转法则：**
每个悬停态、每个激活态、每次交互反馈都用反转作信号。黑变白。白变黑。没有中间态，没有透明度淡化，没有色彩。这形成令人满意、毫不含糊的零色彩交互语言。

---

### 字体 — 核心工具

字体就是设计。没有色彩，字体必须承担一切 — 层级、个性、节奏、强调与情绪。每一层都用最大字体对比。

```
字体配对（仅两个角色）：
  展示 / 标题：    字重范围极广的 grotesque 或可变无衬线
                       选项：Inter（字重 100–900）、Helvetica Now、Aktiv Grotesk
                       或：编辑项目用高对比衬线
                       选项：Playfair Display、Libre Baskerville、EB Garamond
  正文 / UI：      同一 grotesque 的较轻端，或
                       中性无衬线：Inter 300–400、system-ui

字号阶（全部使用 — 尺寸之间的对比就是设计）：
  英雄展示：      clamp(64px, 12vw, 160px)  / 字重 900 / 行高 0.88 / 字距 -0.04em
  英雄强调：      同尺寸                  / 字重 100–300 / 斜体 / 与重字同一行
  区块标题：      clamp(32px, 5vw, 72px)    / 字重 900 / 行高 0.92 / 字距 -0.03em
  卡片标题：      clamp(18px, 2vw, 28px)    / 字重 700 / 行高 1.1
  正文：          15–16px                   / 字重 300–400 / 行高 1.72 / 颜色 #888
  标签 / 眉题：   10–11px                  / 字重 600–700 / 大写 / 字距 0.15–0.2em
  微字 / 说明：   10px                     / 字重 400 / 颜色 #888

关键手法 — 同一行内的字重对比：
  <h1>
    <span style="font-weight:900;">DESIGN</span>
    <em style="font-weight:200; font-style:italic;"> systems</em>
  </h1>
这是本风格的签名手法。同一标题里，超重的黑紧挨羽毛般轻的白。

关键手法 — 超大字作肌理：
  大号（200–300px+）单字母或词作为背景装饰，颜色：白底用 rgba(0,0,0,0.04)，黑底用 rgba(255,255,255,0.04)。不可读，只可感。

关键手法 — 旋转标签：
  区块标签逆时针旋转 90°，放在内容区左缘。
  CSS: writing-mode: vertical-rl; transform: rotate(180deg); font-size: 10px; letter-spacing: 0.2em;
```

---

### 签名元素 1 — 跑马灯 / 滚动条

横向滚动跑马灯是高端单色设计最可识别的单一元素。用作区块分隔或英雄强调。项目用 `·` 或 `×` 或 `—` 分隔。

```css
.marquee-track {
  display: flex; overflow: hidden;
  border-top: 1px solid #000; border-bottom: 1px solid #000;
  background: #000; padding: 14px 0;
}
.marquee-inner {
  display: flex; gap: 0; white-space: nowrap;
  animation: marquee 28s linear infinite;
  flex-shrink: 0;
}
.marquee-inner:nth-child(2) { animation-delay: -14s; }
@keyframes marquee { from { transform: translateX(0); } to { transform: translateX(-50%); } }

.marquee-item {
  font-size: 13px; font-weight: 700; text-transform: uppercase;
  letter-spacing: 0.14em; color: #fff; padding: 0 28px;
  display: flex; align-items: center; gap: 28px;
}
.marquee-item::after { content: '×'; color: #444; }

/* 白变体（白底上） */
.marquee-track.light { background: #fff; border-color: #000; }
.marquee-track.light .marquee-item { color: #000; }
.marquee-track.light .marquee-item::after { color: #ccc; }
```

悬停暂停：`&:hover .marquee-inner { animation-play-state: paused; }`

---

### 签名元素 2 — 全出血区块反转

在全白与全黑区块间交替，不用色彩也能制造页面节奏。过渡必须戏剧 — 不要渐变，不要淡化。之间一像素边框。

布局节奏（推荐顺序）：
```
1. 导航                  — 白底，4px 黑底边
2. 英雄                  — 黑色全出血
3. 跑马灯                — 黑（延续）
4. 服务 / 功能           — 白
5. 跑马灯                — 白变体
6. 作品 / 作品集         — 黑
7. 流程                  — 白
8. 定价                  — 黑
9. 页脚                  — 白，4px 黑顶边
```

每个区块过渡用粗（4px）黑边作为视觉卡点。

---

### 签名元素 3 — 滚动触发显现

文字元素进入视口时从下方滑上。由 IntersectionObserver 触发。这是系统中唯一的动画 — 其余即时或仅悬停。

```javascript
const reveals = document.querySelectorAll('.reveal');
const observer = new IntersectionObserver((entries) => {
  entries.forEach(entry => {
    if (entry.isIntersecting) {
      entry.target.classList.add('revealed');
      observer.unobserve(entry.target);
    }
  });
}, { threshold: 0.15 });
reveals.forEach(el => observer.observe(el));
```

```css
.reveal {
  opacity: 0;
  transform: translateY(28px);
  transition: opacity 0.55s ease, transform 0.55s ease;
}
.reveal.revealed {
  opacity: 1;
  transform: translateY(0);
}
/* 交错子项 */
.reveal-group .reveal:nth-child(2) { transition-delay: 0.1s; }
.reveal-group .reveal:nth-child(3) { transition-delay: 0.2s; }
.reveal-group .reveal:nth-child(4) { transition-delay: 0.3s; }
```

---

### 导航

4px 底边。Logo 左（9+ 字母，字重 900，字距 0.25em，大写）。中间链接（10–11px，大写，字距 0.15em，灰，悬停 → 黑）。右：两个 CTA 按钮，之间零间隙，一个白填充 + 一个黑填充。

```css
nav {
  position: sticky; top: 0; z-index: 100;
  background: #fff; border-bottom: 4px solid #000;
  padding: 0 40px; height: 60px;
  display: flex; align-items: center; justify-content: space-between;
}
.nav-logo { font-size: 16px; font-weight: 900; letter-spacing: 0.25em; text-transform: uppercase; color: #000; text-decoration: none; }
.nav-links { display: flex; gap: 32px; list-style: none; }
.nav-links a { font-size: 11px; font-weight: 600; text-transform: uppercase; letter-spacing: 0.14em; color: #888; text-decoration: none; transition: color 120ms; }
.nav-links a:hover { color: #000; }
.nav-right { display: flex; }
.btn { padding: 0 20px; height: 38px; font-size: 11px; font-weight: 700; letter-spacing: 0.12em; text-transform: uppercase; cursor: pointer; transition: background 120ms, color 120ms; border: 2px solid #000; white-space: nowrap; }
.btn-outline { background: #fff; color: #000; border-right: none; }
.btn-outline:hover { background: #000; color: #fff; }
.btn-fill { background: #000; color: #fff; }
.btn-fill:hover { background: #fff; color: #000; }
```

---

### 英雄区块 — 黑色全出血，最大字体

英雄落在全出血黑底上。标题在单一字体块内使用极端字重对比。无图，无插画 — 只有字。

结构：
```
[眉题标签 — 11px 大写灰]

ENORMOUS                           ← 字重 900，白，100–160px
everything                         ← 字重 100，斜体，白，同尺寸
IS POSSIBLE.                       ← 字重 900，白

[正文行 — 16px，灰，300 字重，最大宽 440px]

[按钮：白填充，黑字]  [按钮：幽灵深灰边，灰字]

[3 项统计 — 数字大，标签极小大写，竖 1px 线分隔]
```

```css
.hero { background: #000; color: #fff; padding: 96px 40px 80px; position: relative; overflow: hidden; border-bottom: 4px solid #000; }
.hero-eyebrow { font-size: 11px; font-weight: 600; letter-spacing: 0.2em; text-transform: uppercase; color: #888; margin-bottom: 24px; }
.hero-heading {
  font-size: clamp(64px, 11vw, 148px);
  font-weight: 900; line-height: 0.88;
  letter-spacing: -0.04em; text-transform: uppercase;
  margin-bottom: 32px;
}
.hero-heading .thin { font-weight: 100; font-style: italic; display: block; }
.hero-heading .heavy { font-weight: 900; display: block; }

/* 超大装饰字母 — 肌理 */
.hero-deco {
  position: absolute; right: -20px; top: -40px;
  font-size: clamp(200px, 30vw, 400px); font-weight: 900;
  color: rgba(255,255,255,0.035); line-height: 1;
  pointer-events: none; user-select: none; letter-spacing: -0.05em;
}

.hero-desc { font-size: 16px; color: #888; max-width: 400px; line-height: 1.7; margin-bottom: 36px; font-weight: 300; }

.hero-actions { display: flex; gap: 0; flex-wrap: wrap; margin-bottom: 56px; }

/* 数据行 */
.hero-stats { display: flex; border-top: 1px solid #222; padding-top: 32px; }
.hero-stat { flex: 1; padding-right: 24px; margin-right: 24px; border-right: 1px solid #222; }
.hero-stat:last-child { border-right: none; }
.hero-stat-val { font-size: clamp(28px, 4vw, 48px); font-weight: 900; letter-spacing: -0.03em; color: #fff; line-height: 1; }
.hero-stat-label { font-size: 10px; font-weight: 600; text-transform: uppercase; letter-spacing: 0.15em; color: #888; margin-top: 5px; }
```

---

### 跑马灯（分隔）

用两次：一次黑（英雄与服务之间），一次白（服务与作品之间）。内容：品牌价值、服务列表或客户名，用 `×` 分隔。

---

### 服务 / 功能 — 白色区块，非对称网格

白底。区块标题巨大 — 不是与页面标题同尺寸，但大到感觉像结构。项目用两列网格（非对称：40%/60% 或 1fr/2fr）。

每张服务卡：粗顶边（4px 黑）、分类标签（10px 大写）、标题（字重 900）、描述（14px，#888，字重 300），以及链接箭头 `→`。

```css
.services { background: #fff; padding: 80px 40px; border-bottom: 4px solid #000; }
.services-heading { font-size: clamp(32px, 5vw, 72px); font-weight: 900; letter-spacing: -0.03em; color: #000; margin-bottom: 56px; text-transform: uppercase; line-height: 0.95; }
.services-heading em { font-weight: 100; font-style: italic; display: block; }
.services-grid { display: grid; grid-template-columns: 1fr 2fr; gap: 0; }
.services-left { padding-right: 40px; border-right: 1px solid #ccc; }
.services-right { padding-left: 40px; }
.service-item { border-top: 4px solid #000; padding: 24px 0; cursor: pointer; transition: background 120ms; }
.service-item:hover .service-arrow { transform: translate(4px, -4px); }
.service-cat { font-size: 10px; font-weight: 700; text-transform: uppercase; letter-spacing: 0.15em; color: #888; margin-bottom: 8px; }
.service-title { font-size: clamp(18px, 2vw, 26px); font-weight: 700; letter-spacing: -0.02em; color: #000; margin-bottom: 8px; line-height: 1.15; }
.service-desc { font-size: 13px; color: #888; line-height: 1.65; font-weight: 300; margin-bottom: 12px; }
.service-link { font-size: 11px; font-weight: 700; text-transform: uppercase; letter-spacing: 0.12em; color: #000; display: flex; align-items: center; gap: 8px; text-decoration: none; }
.service-arrow { display: inline-block; transition: transform 200ms ease; }
```

---

### 作品网格 — 黑色区块，图/文卡片

全出血黑。2×N 作品/作品集卡片网格。每张卡片：白色编号（极小，左上）、项目名（大，字重 900，白）、分类（小大写，灰），以及悬停反转的「查看 →」链接。

```css
.work { background: #000; padding: 80px 40px; border-bottom: 4px solid #000; }
.work-heading { font-size: clamp(28px, 4vw, 56px); font-weight: 900; color: #fff; text-transform: uppercase; letter-spacing: -0.03em; margin-bottom: 48px; }
.work-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 2px; background: #222; }
.work-card {
  background: #000; padding: 32px;
  border: none; cursor: pointer;
  transition: background 180ms;
  display: flex; flex-direction: column; justify-content: space-between; min-height: 220px;
}
.work-card:hover { background: #fff; }
.work-card:hover .work-title, .work-card:hover .work-num { color: #000; }
.work-card:hover .work-cat { color: #888; }
.work-card:hover .work-link { color: #000; }
.work-num { font-size: 10px; font-weight: 600; letter-spacing: 0.15em; color: #444; text-transform: uppercase; margin-bottom: auto; padding-bottom: 32px; }
.work-title { font-size: clamp(22px, 3vw, 36px); font-weight: 900; color: #fff; letter-spacing: -0.02em; line-height: 1.05; margin-bottom: 8px; text-transform: uppercase; transition: color 180ms; }
.work-cat { font-size: 10px; font-weight: 600; text-transform: uppercase; letter-spacing: 0.14em; color: #444; transition: color 180ms; }
.work-link { font-size: 11px; font-weight: 700; text-transform: uppercase; letter-spacing: 0.1em; color: #444; margin-top: 24px; transition: color 180ms; }
```

---

### 流程 / 关于 — 白，带旋转标签的编号项

白色区块。左：旋转竖标签。右：编号流程项，各以发丝线（1px #ccc）分隔。数字大（64px，字重 900，颜色 #f2f2f2 — 几乎看不见）。标题在旁，描述在下。

```css
.process { background: #fff; padding: 80px 40px; border-bottom: 4px solid #000; display: grid; grid-template-columns: 64px 1fr; gap: 0 40px; }
.process-label-col { position: relative; }
.process-rotated-label { writing-mode: vertical-rl; transform: rotate(180deg); font-size: 10px; font-weight: 700; letter-spacing: 0.2em; text-transform: uppercase; color: #ccc; position: sticky; top: 80px; }
.process-items { }
.process-item { border-top: 1px solid #ccc; padding: 28px 0; display: grid; grid-template-columns: 80px 1fr; gap: 0 24px; align-items: start; }
.process-num { font-size: 56px; font-weight: 900; color: #f2f2f2; line-height: 1; letter-spacing: -0.04em; }
.process-title { font-size: 22px; font-weight: 700; color: #000; letter-spacing: -0.02em; margin-bottom: 8px; }
.process-desc { font-size: 13px; color: #888; line-height: 1.7; font-weight: 300; }
```

---

### 定价 — 黑色区块，带边框的网格表

黑底。标题白。三档方案并排在带边框卡片中。「推荐」方案反转为白（黑底上白卡片黑字）— 可能的最高对比。

每张卡片：方案档（极小大写）、价格（64px 字重 900）、周期、带 `—` 项目符号的功能列表、全宽 CTA 按钮。

```css
.pricing { background: #000; padding: 80px 40px; }
.pricing-heading { font-size: clamp(32px, 5vw, 64px); font-weight: 900; color: #fff; text-transform: uppercase; letter-spacing: -0.03em; line-height: 0.92; margin-bottom: 48px; }
.pricing-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 0; border: 2px solid #222; }
.plan { border-right: 2px solid #222; padding: 32px; background: #111; }
.plan:last-child { border-right: none; }
.plan.featured { background: #fff; }
.plan-name { font-size: 10px; font-weight: 700; letter-spacing: 0.15em; text-transform: uppercase; color: #888; margin-bottom: 16px; padding-bottom: 16px; border-bottom: 1px solid #222; }
.plan.featured .plan-name { border-bottom-color: #ccc; }
.plan-price { font-size: clamp(44px, 5vw, 64px); font-weight: 900; letter-spacing: -0.04em; color: #fff; line-height: 1; }
.plan.featured .plan-price { color: #000; }
.plan-period { font-size: 10px; font-weight: 600; text-transform: uppercase; letter-spacing: 0.1em; color: #888; margin: 6px 0 20px; }
.plan-features { list-style: none; margin-bottom: 24px; display: flex; flex-direction: column; gap: 9px; }
.plan-features li { font-size: 12px; color: #888; display: flex; gap: 10px; font-weight: 400; line-height: 1.4; }
.plan.featured .plan-features li { color: #444; }
.plan-features li::before { content: '—'; flex-shrink: 0; color: #333; }
.plan.featured .plan-features li::before { color: #000; }
```

---

### 页脚 — 白，4px 顶边

干净、字体向。Logo 左（巨大，字重 900，字距宽）。右：两列链接。底栏：版权左，一行宣言右。

```css
footer { background: #fff; border-top: 4px solid #000; padding: 64px 40px 32px; }
.footer-top { display: grid; grid-template-columns: 1fr 1fr 1fr; gap: 40px; margin-bottom: 56px; }
.footer-brand { font-size: clamp(40px, 6vw, 80px); font-weight: 900; letter-spacing: -0.03em; text-transform: uppercase; color: #000; line-height: 0.9; }
.footer-tagline { font-size: 13px; color: #888; font-weight: 300; margin-top: 12px; max-width: 200px; line-height: 1.6; }
.footer-col-label { font-size: 10px; font-weight: 700; text-transform: uppercase; letter-spacing: 0.15em; color: #ccc; margin-bottom: 16px; }
.footer-links { list-style: none; display: flex; flex-direction: column; gap: 10px; }
.footer-links a { font-size: 14px; font-weight: 700; color: #000; text-decoration: none; text-transform: uppercase; letter-spacing: 0.04em; transition: color 120ms; }
.footer-links a:hover { color: #888; }
.footer-bar { border-top: 1px solid #ccc; padding-top: 20px; display: flex; justify-content: space-between; align-items: center; font-size: 11px; color: #888; font-weight: 400; }
```

---

### 交互规则 — 仅反转
```
悬停态：  反转背景与文字色。过渡：150–180ms，linear。
激活态：  scale(0.97) — 干脆、即时反馈。
焦点态：  outline: 3px solid #000; outline-offset: 2px — 无色彩。
链接：    默认色 #000。悬停：色 #888 或出现下划线。
卡片：    悬停时背景 #000 → #fff（白色区块：#fff → #000）。
按钮：    始终反转 — 黑填充 → 白填充，白填充 → 黑填充。
```

---

### 不要做什么
- ✗ 永远不要在任何地方加一种颜色 — 哪怕「微妙」淡彩或带色相的偏灰
- ✗ 永远不要用任何渐变 — 哪怕黑到略浅的黑
- ✗ 永远不要用柔和 box-shadow — 它们增加温度；只用硬 4px 偏移阴影
- ✗ 永远不要用 1px 到 999px 之间的圆角 — 要么 0（锐）要么全胶囊（999px）
- ✗ 永远不要让两个层级用同一字号 — 对比就是一切
- ✗ 永远不要居中对齐长正文 — 只左对齐
- ✗ 永远不要用彩色摄影 — 只要高对比黑白摄影
- ✗ 永远不要用图标库图标 — 改用文字、箭头（→ ↑）和破折号（—）
- ✗ 永远不要加超过 200ms 的悬停动画 — 干脆，不飘
- ✗ 永远不要用超过两种字体 — 配对就是色板

### 待替换数据（占位映射）
- `[BRAND_NAME]` — 导航 logo、页脚展示、英雄装饰字母
- `[TAGLINE]` — 2–3 词英雄标题，拆成重/轻/重行
- `[HERO_SUBTEXT]` — 1–2 句，字重 300，#888，最多 50 词
- `[HERO_STATS]` — 3 项统计：数字、标签
- `[MARQUEE_ITEMS]` — 8–10 项：服务名、价值、客户行业
- `[SERVICES]` — 4–6 项：分类标签、标题、描述、链接文字
- `[WORK_ITEMS]` — 4–8 个项目：编号、名称、分类
- `[PROCESS_STEPS]` — 3–5 步：编号、标题、描述
- `[PRICING_TIERS]` — 3 档：名称、价格、周期、4–6 项功能
- `[FOOTER_LINKS]` — 两列各 4–5 个链接
- `[COPYRIGHT]` — 年份、公司名
- `[MANIFESTO_LINE]` — 短收束陈述，例如「零色彩。纯工艺。」
