# Bauhaus / Swiss Modern

- **id:** `bauhaus-swiss-modern`
- **别名:** 包豪斯, 瑞士现代主义, 国际主义平面, 网格至上, 构成主义UI
- **一句话:** 形式追随功能。网格即法律。色彩即结构。
- **适用:**
  - 设计工作室、建筑事务所与文化机构
  - 需要投射权威与系统纪律的创意机构
  - 学术与机构平台
  - 设计、艺术、字体、印刷与手工艺品牌
  - 界面本身应体现其所倡导学科的品牌
  - 自信与严谨是主要品牌信号的产品
- **避免:**
  - 需要温度与亲和力的消费科技产品
  - 需要友好或玩趣感的创业公司
  - 用颜色编码功能状态（错误/成功/警告）的产品
  - 需要全彩生活方式摄影的任何东西
  - 面向非设计素养买家的 SaaS 产品
- **来源:** https://uidesignprompts.com/prompts/bauhaus-swiss-modern

## Prompt

## 包豪斯 / 瑞士现代设计系统 — 深度规格

### 理念
这不是极简。极简是删。包豪斯是替 — 用几何、色彩与网格。在别的风格里可能是装饰的每个元素，在这里都变成结构：大红矩形定义区块边界，黄圆标记功能，黑色竖线划分栏。色彩是建筑。字体是建筑。网格是宪法。

参考：Josef Müller-Brockmann 的海报、Herbert Bayer 的字体实验、El Lissitzky 的构成主义构图。数字端：Knoll、Swiss Typefaces、Are.na。

---

### 色彩系统 — 作为建筑的原色

```
包豪斯红：     #E63329  — 激活色；行动号召、区块标题、结构强调
包豪斯蓝：     #1A3A6B  — 锚定色；英雄背景、大色场、权威
包豪斯黄：     #F5C800  — 高亮色；精选方案、悬停填充、强调
结构黑：       #111111  — 边框、字体、结构线、主导表面
灰白：         #F7F5F0  — 暖页面背景（正文区块永远不要纯白）
纯白：         #FFFFFF  — 深色场上的反白文字；蓝/黑上的白色内容
中灰：         #888888  — 次级标签、弱化文字、辅助文案
```

**包豪斯色彩五律：**
1. 色彩只用大块平涂 — 不要渐变、不要淡彩、不要透明度
2. 每个区块最多一种原色 — 同一色块里永远不要红 + 蓝 + 黄
3. 色彩传达结构与层级，不是装饰或情绪
4. 黑与白也是颜色 — 与原色同等分量对待
5. 不确定时：多黑，不多色。色彩要挣得位置。

**色彩 DNA 条：** 紧贴导航下方放一条 5 段水平条（高 8–12px）。五等分列：红 · 蓝 · 黄 · 黑 · 白。这是包豪斯签名标记 — 每页出现，作为识别系统的指纹。

```css
.color-dna {
  display: grid; grid-template-columns: repeat(5, 1fr); height: 10px;
}
.color-dna .c1 { background: #E63329; }
.color-dna .c2 { background: #1A3A6B; }
.color-dna .c3 { background: #F5C800; }
.color-dna .c4 { background: #111111; }
.color-dna .c5 { background: #FFFFFF; border-top: 1px solid #ddd; }
```

---

### 字体 — 作为视觉建筑的文字

```
主字体（包豪斯/瑞士）：
  'Jost', 'Helvetica Neue', 'Inter', sans-serif
  Jost 是数字版 Futura — 几何、贴近包豪斯，Google Fonts 免费。

字号阶（用激进对比 — 永远不要中间档）：
  海报 / 英雄：      clamp(72px, 13vw, 180px)  / 字重 900 / 行高 0.85 / 字距 -0.04em
  展示：              clamp(40px, 6vw, 80px)     / 字重 900 / 行高 0.9  / 字距 -0.03em
  区块标题：          clamp(24px, 3vw, 40px)     / 字重 700 / 行高 1.05 / 字距 -0.02em
  卡片标题：          18–22px                    / 字重 700 / 行高 1.1
  正文：              14–15px                    / 字重 300–400 / 行高 1.65 / 颜色 #888
  标签 / 眉题：       10–11px                    / 字重 700 / 大写 / 字距 0.16em
  微字：              10px                       / 字重 500 / 颜色 #888
```

**关键手法 — 竖排文字标签：**
区块标签沿网格列左缘逆时针旋转 90°。用于定价列头、关于区块、宣言轨。
```css
.vertical-label {
  writing-mode: vertical-rl;
  transform: rotate(180deg);
  font-size: 11px; font-weight: 700;
  letter-spacing: 0.18em; text-transform: uppercase;
  color: #888;
}
/* 用在彩色单元格（蓝/黑）上时： */
.vertical-label.on-dark { color: rgba(255,255,255,0.4); }
```

**关键手法 — 海报级展示文字作为区块建筑：**
一个 100–180px 的词或数字主宰整个网格单元格，同时充当标题与装饰体量。文字本身就是视觉元素。

**关键手法 — 沿左边界 90° 跑的文字：**
对更高的彩色侧栏列（如定价标签、宣言词），文字竖排并填满全列高。字号 48–80px，字重 900，大写。

---

### 签名元素 1 — 几何形状构图

包豪斯设计用基本形 — 圆、方、三角 — 作为结构元素，不是装饰。在 UI 中表现为：

**1. 背景构图**（在英雄内容之后）：
大几何形 — 高约为区块 60% 的圆、穿越边界的矩形、重叠形 — 放在彩色区块边缘。颜色：对面原色的 rgba（蓝底上 15% 不透明度的黄圆等）

```css
/* 带几何构图的蓝色英雄 */
.hero-geo { position: relative; overflow: hidden; }
.hero-geo::before {
  content: ''; position: absolute;
  width: 420px; height: 420px; border-radius: 50%;
  background: rgba(245,200,0,0.12);
  bottom: -120px; right: -80px;
  pointer-events: none;
}
.hero-geo::after {
  content: ''; position: absolute;
  width: 200px; height: 200px;
  background: rgba(255,255,255,0.06);
  top: 40px; right: 140px;
  pointer-events: none;
}
```

**2. 作为功能标记的色圆：**
圆（48–64px）填一种原色，用于编号或标记精选内容。内部无文字 — 圆本身就是标记。

```css
.geo-circle {
  width: 52px; height: 52px; border-radius: 50%;
  background: var(--red); /* 或蓝、黄 */
  flex-shrink: 0;
}
.geo-circle.blue   { background: #1A3A6B; }
.geo-circle.yellow { background: #F5C800; }
```

**3. 直角转角线：**
大 L 形边框（粗：4–6px）用原色锚定在区块或卡片转角。形成构成主义「转角括号」母题。

```css
.corner-rule {
  position: absolute; top: 0; left: 0;
  width: 40px; height: 40px;
  border-top: 5px solid #E63329;
  border-left: 5px solid #E63329;
}
```

---

### 签名元素 2 — 非对称网格

每个区块使用非对称网格。永远不要等栏。有效比例：
```
英雄：          40% / 60%  （蓝色场 / 白色内容）
功能：          2fr / 1fr / 1fr  （主 / 两个强调）
宣言：          200px / 1fr  （竖标签列 / 内容）
定价：          180px / 1fr  （竖标签 / 三档方案）
作品网格：      3fr / 2fr  或  1fr / 1fr / 1fr / 1fr  （肖像 vs 风景）
关于：          1fr / 2fr  （图 / 文）
```

网格单元格用粗边框（4px 黑）分隔，而不是沟槽。单元格之间无间距 — 边框完成工作。

```css
/* 网格法则：边框，不是间隙 */
.section-grid { display: grid; gap: 0; }
.grid-cell { border-right: 4px solid #111; border-bottom: 4px solid #111; padding: 40px 36px; }
.grid-cell:last-child { border-right: none; }
.grid-row:last-child .grid-cell { border-bottom: none; }
```

---

### 签名元素 3 — 带色彩叠层的构成主义作品网格

作品集/作品网格使用黑白图像（或彩色背景单元格），悬停时出现原色叠层。这是页面上最交互、视觉上最戏剧的元素。

```css
.work-grid { display: grid; grid-template-columns: repeat(2, 1fr); gap: 4px; background: #111; }
.work-card {
  position: relative; overflow: hidden;
  background: #111; min-height: 260px;
  display: flex; flex-direction: column; justify-content: flex-end;
  padding: 28px; cursor: pointer;
}
/* 色场作背景 — 在原色间交替 */
.work-card.red  { background: #E63329; }
.work-card.blue { background: #1A3A6B; }
.work-card.yellow { background: #F5C800; }

/* 悬停：色彩填满黑底 */
.work-card:not(.red):not(.blue):not(.yellow):hover { background: #E63329; }

.work-card-overlay {
  position: absolute; inset: 0;
  background: var(--red); /* 每张卡片变化 */
  opacity: 0; transition: opacity 200ms;
}
.work-card:hover .work-card-overlay { opacity: 0.9; }

.work-num { font-size: 10px; font-weight: 700; letter-spacing: 0.15em; text-transform: uppercase; color: rgba(255,255,255,0.35); margin-bottom: auto; }
.work-title { font-size: clamp(20px, 3vw, 32px); font-weight: 900; color: #fff; text-transform: uppercase; letter-spacing: -0.02em; line-height: 1.05; position: relative; z-index: 1; }
.work-cat { font-size: 10px; font-weight: 700; letter-spacing: 0.12em; text-transform: uppercase; color: rgba(255,255,255,0.5); position: relative; z-index: 1; margin-top: 6px; }
```

---

### 导航

高 60px。底边 4px 黑。Logo：几何红方点 + 品牌名，字重 900，大写。中间链接：10px 大写，字距 0.12em，灰 → 悬停变黑。当前链接：3px 红底边。右侧：相邻按钮（零间隙），描边 + 填充成对。

```css
nav { position: sticky; top: 0; z-index: 100; background: #fff; border-bottom: 4px solid #111; padding: 0 32px; height: 60px; display: flex; align-items: stretch; }
.nav-logo { font-size: 18px; font-weight: 900; letter-spacing: 0.1em; text-transform: uppercase; display: flex; align-items: center; gap: 10px; padding-right: 24px; border-right: 4px solid #111; margin-right: 24px; flex-shrink: 0; }
.nav-dot { width: 14px; height: 14px; background: #E63329; flex-shrink: 0; }
.nav-links { display: flex; align-items: stretch; list-style: none; gap: 0; }
.nav-links a { font-size: 11px; font-weight: 500; letter-spacing: 0.12em; text-transform: uppercase; color: #888; text-decoration: none; padding: 0 18px; display: flex; align-items: center; border-bottom: 3px solid transparent; transition: color 120ms, border-color 120ms; }
.nav-links a:hover { color: #111; }
.nav-links a.active { color: #111; border-bottom-color: #E63329; }
.nav-right { margin-left: auto; display: flex; align-items: center; gap: 0; }
.btn { border: 2px solid #111; padding: 0 20px; height: 38px; font-size: 11px; font-family: inherit; font-weight: 700; letter-spacing: 0.1em; text-transform: uppercase; cursor: pointer; transition: background 120ms, color 120ms; white-space: nowrap; }
.btn-ghost { background: #fff; color: #111; border-right: none; }
.btn-ghost:hover { background: #111; color: #fff; }
.btn-red { background: #E63329; color: #fff; border-color: #E63329; }
.btn-red:hover { background: #C22921; border-color: #C22921; }
```

---

### 英雄区块 — 蓝色场 / 白色网格分割

两列非对称网格（40% 蓝 / 60% 白），以 4px 黑边分隔。

**左列（蓝）：**
- 几何构图背景（黄圆 + 白方，低不透明度）
- 眉题标签：极小大写，rgba(white, 0.4)
- 海报级标题：2–3 个词，字重 900，白，紧行高
- 一个词用黄（包豪斯用色彩作强调的手法）
- 标语：11px 大写，rgba(white, 0.4)

**右列（白）：**
- 正文描述：15px，字重 300，#555
- 两个相邻 CTA 按钮（红 + 幽灵）
- 数据行：3 项统计，细线分隔，数字 36px 字重 900

```css
.hero { display: grid; grid-template-columns: 40% 60%; border-bottom: 4px solid #111; min-height: 360px; }
.hero-left { background: #1A3A6B; padding: 52px 36px; position: relative; overflow: hidden; display: flex; flex-direction: column; justify-content: space-between; gap: 28px; }
.hero-right { padding: 52px 36px; border-left: 4px solid #111; display: flex; flex-direction: column; justify-content: space-between; gap: 28px; }
.hero-eyebrow { font-size: 11px; font-weight: 500; letter-spacing: 0.15em; text-transform: uppercase; color: rgba(255,255,255,0.35); }
.hero-h1 { font-size: clamp(40px, 6vw, 80px); font-weight: 900; line-height: 0.9; letter-spacing: -0.03em; text-transform: uppercase; color: #fff; }
.hero-h1 .accent { color: #F5C800; }
.hero-tagline { font-size: 10px; font-weight: 700; letter-spacing: 0.16em; text-transform: uppercase; color: rgba(255,255,255,0.35); }
.hero-desc { font-size: 15px; line-height: 1.65; color: #444; font-weight: 300; }
.hero-actions { display: flex; gap: 0; }
.hero-stats { display: flex; gap: 0; border-top: 2px solid #111; padding-top: 20px; }
.hero-stat { flex: 1; padding-right: 20px; margin-right: 20px; border-right: 1px solid #ddd; }
.hero-stat:last-child { border-right: none; }
.stat-num { font-size: 36px; font-weight: 900; letter-spacing: -0.04em; line-height: 1; color: #111; }
.stat-label { font-size: 10px; font-weight: 700; letter-spacing: 0.12em; text-transform: uppercase; color: #888; margin-top: 4px; }
```

---

### 功能网格 — 彩色单元格，非对称

三列（2fr / 1fr / 1fr）。每个单元格有粗边框分隔。一格红底，一格黄底，一格白。彩色单元格把原色当大背景场 — 不是带色强调的卡片。

```
┌──────────────────────────┬──────────────┬──────────────┐
│  白 — 主文案格           │  红 — 数据   │ 黄 — 行动号召│
│  (2fr)                   │  (1fr)       │  (1fr)       │
└──────────────────────────┴──────────────┴──────────────┘
```

---

### 宣言 / 方法轨

左：竖标签列（宽 200px，黑或蓝底，白字旋转 90°，字重 900，56px）。
右：原则三列网格。每条原则：红数字标签（10px）、粗标题、轻描述。

```css
.manifesto { display: grid; grid-template-columns: 200px 1fr; border-bottom: 4px solid #111; }
.manifesto-label { background: #111; border-right: 4px solid #111; display: flex; align-items: center; justify-content: center; padding: 32px 0; }
.manifesto-word { font-size: 56px; font-weight: 900; text-transform: uppercase; color: #fff; letter-spacing: -0.03em; writing-mode: vertical-rl; transform: rotate(180deg); }
.manifesto-cols { display: grid; grid-template-columns: repeat(3, 1fr); }
.manifesto-col { padding: 36px 32px; border-right: 2px solid #eee; }
.manifesto-col:last-child { border-right: none; }
.manifesto-num { font-size: 10px; font-weight: 700; letter-spacing: 0.12em; color: #E63329; margin-bottom: 12px; text-transform: uppercase; }
.manifesto-title { font-size: 18px; font-weight: 700; letter-spacing: -0.01em; color: #111; margin-bottom: 8px; line-height: 1.2; }
.manifesto-desc { font-size: 13px; color: #888; line-height: 1.65; font-weight: 300; }
```

---

### 作品网格 — 带悬停叠层的彩色单元格

见上方签名元素 3。4 张卡片网格（2×2，移动端 4×1）。交替色背景。每张卡片：项目编号（极小大写）、项目名（海报字重）、分类（下方极小大写）。悬停显现红叠层，项目链接可见。

---

### 定价区块 — 竖标签轨 + 3 档方案

左列（180px）：黄底竖排文字「RATES」，字重 900，48px，旋转 90°。
右：三列方案，粗边框分隔。精选方案用蓝底、黄价、白字。

---

### 页脚

两列网格。左：红底，品牌名白，字重 900。右：链接 + 版权。
红色左列与白色右列以 4px 黑边分隔。

```css
footer { display: grid; grid-template-columns: 200px 1fr; border-top: 4px solid #111; }
.footer-left { background: #E63329; padding: 28px 32px; border-right: 4px solid #111; display: flex; align-items: center; }
.footer-brand { font-size: 28px; font-weight: 900; letter-spacing: 0.1em; text-transform: uppercase; color: #fff; }
.footer-right { padding: 28px 32px; display: flex; justify-content: space-between; align-items: center; flex-wrap: wrap; gap: 12px; }
.footer-links { display: flex; gap: 24px; list-style: none; flex-wrap: wrap; }
.footer-links a { font-size: 11px; font-weight: 500; letter-spacing: 0.12em; text-transform: uppercase; color: #888; text-decoration: none; transition: color 120ms; }
.footer-links a:hover { color: #111; }
```

---

### 滚动显现动画（克制）

只有一种动画：元素上滑 20px 并淡入。无复杂序列。由 IntersectionObserver 在 `.reveal` 元素上触发。用 `transition-delay` 交错网格子项。

```css
.reveal { opacity: 0; transform: translateY(20px); transition: opacity 0.45s ease, transform 0.45s ease; }
.reveal.in { opacity: 1; transform: translateY(0); }
.reveal:nth-child(2) { transition-delay: 0.08s; }
.reveal:nth-child(3) { transition-delay: 0.16s; }
.reveal:nth-child(4) { transition-delay: 0.24s; }
```

---

### 不要做什么
- ✗ 永远不要用渐变 — 哪怕极淡的也不行。色彩要么平涂要么缺席。
- ✗ 永远不要用 box-shadow 或投影 — 深度来自色彩对比
- ✗ 永远不要用圆角 — 所有几何都是棱角，除明确的圆
- ✗ 永远不要用等栏网格（1fr 1fr 1fr 是电子表格，不是包豪斯）
- ✗ 永远不要每个区块用超过一种原色 — 色彩是结构，不是装饰
- ✗ 永远不要用中等字号 — 要么大（展示）要么小（标签）。中间没有。
- ✗ 永远不要用彩色摄影 — 只要高对比黑白
- ✗ 永远不要用图标库 — 用几何形（■ ● ▲）与字体符号
- ✗ 永远不要把留白当填充 — 每块空区都是结构决定
- ✗ 永远不要用长于 450ms 的动画 — 包豪斯是果断的，不是飘的

### 待替换数据（占位映射）
- `[BRAND_NAME]` — 导航 logo、页脚
- `[HERO_HEADLINE]` — 最多 2–3 个词，其中一个词用黄作强调
- `[HERO_SUBTEXT]` — 2–3 句，字重 300，#444
- `[HERO_STATS]` — 3 项统计：数字 + 标签
- `[FEATURE_CELLS]` — 3 格：主格（文案）、红数据格（数字 + 标签）、黄格（CTA）
- `[MANIFESTO_WORD]` — 竖标签词（例如 "Method"、"Craft"、"System"）
- `[PRINCIPLES]` — 3 项：编号、标题、描述
- `[WORK_ITEMS]` — 4 个项目：编号、标题、分类、卡片色（红/蓝/黄/黑）
- `[PRICING_TIERS]` — 3 档：名称、价格、周期、3–5 项功能
- `[FOOTER_LINKS]` — 4–6 个链接
- `[COLOR_DNA]` — 始终 红 · 蓝 · 黄 · 黑 · 白（永远不要改顺序）
