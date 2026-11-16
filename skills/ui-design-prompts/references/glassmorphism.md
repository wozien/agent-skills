# Glassmorphism

- **id:** `glassmorphism`
- **别名:** 玻璃拟态, 毛玻璃, 磨砂玻璃, 玻璃拟物, Apple风玻璃
- **一句话:** 磨砂玻璃。晨光。有深度而无重量。
- **适用:**
  - 消费金融 — 个人理财、银行、投资
  - 健康、冥想与心理健康产品
  - 面向年轻受众的音乐与娱乐平台
  - 高端感驱动转化的生活方式应用
  - 拥有强摄影或插画资产的移动优先产品
  - 需要现代、贴近 Apple 审美的落地页
- **避免:**
  - 开发者工具或技术产品 — 柔软感指向消费而非工艺
  - 更看重高对比与信息密度的数据密集型仪表盘
  - 无障碍关键产品 — 磨砂叠层会降低对比度
  - 机构信任重于打磨的企业或 B2B 工具
  - 深色或黑色品牌色板的产品 — 玻璃需要浅色渐变来反射
- **来源:** https://uidesignprompts.com/prompts/glassmorphism

## Prompt

## 玻璃拟态设计系统 — 深度规格

### 理念
玻璃拟态把磨砂玻璃当作设计材料来模拟 — 而不是装饰。每块玻璃表面都应物理可信：足够通透以看见背后，足够不透明以可读，带捕捉光线的边缘，让人感觉有厚度。体验应是安静的奢华。不是夜店。不是技术演示。晨光透过干净的窗。

三层深度模型是整套系统的基础：
- **第 1 层（氛围）：** 背景渐变 — 温暖、通透，没有锐利的颜色过渡。
- **第 2 层（漫射）：** 玻璃表面后柔和的色场模糊 — 玻璃在反射什么。
- **第 3 层（表面）：** 玻璃面板本身 — 用户与之交互的东西。

每个设计决策都应强化这三层。会压扁深度的元素 — 在模糊上再叠重模糊、玻璃卡片过多、或使用深色/扁平背景 — 都会破坏系统。

---

### 背景系统 — 氛围层

背景不是一种颜色。它是一片柔光场。做法：

1. 基底渐变（暖奶油 → 柔鼠尾草绿，或薰衣草 → 腮红粉）作为页面背景
2. 在关键位置放置径向渐变（右上为主光源，左下为填充）以形成定向光感
3. 可选：`::before` 伪元素加大面积柔径向渐变模糊，增加深度

```css
/* 暖香槟到鼠尾草的色场 — 平静、高端，不是糖果 */
body {
  background:
    radial-gradient(ellipse 70% 60% at 80% 10%, rgba(180,210,185,0.55) 0%, transparent 60%),
    radial-gradient(ellipse 50% 70% at 15% 85%, rgba(210,195,170,0.4) 0%, transparent 55%),
    linear-gradient(160deg, #F5F0E8 0%, #E8EDE3 45%, #DCE8DC 100%);
}

/* 备选：冷薰衣草到腮红 */
body.variant-purple {
  background:
    radial-gradient(circle at 10% 20%, rgba(167,139,250,0.45) 0%, transparent 35%),
    radial-gradient(circle at 85% 75%, rgba(249,168,212,0.38) 0%, transparent 35%),
    linear-gradient(135deg, #C7D2FE 0%, #E9D5FF 35%, #FDE8FF 100%);
}
```

**规则：**
- 最多用 2–3 种低饱和色调。鲜艳色不超过一种。
- 渐变应通透发光，不要饱和或糖果感。
- 暖色背景（奶油、桃、鼠尾草）配暖色文字（#1A2E1F）。冷色背景（薰衣草、蓝）配冷色文字（#1E1B4B）。
- 永远不要用扁平白或扁平深色背景 — 玻璃没有东西可反射。
- 生产中避免动画背景球 — 那是 AI 生成玻璃拟态的识别特征，增加视觉噪声而无深度。

---

### 玻璃卡片公式 — 表层

每张玻璃卡片需要四个组件协同。缺任何一个就不像玻璃。

```css
/* 三档玻璃不透明度 — 有意使用 */

/* 强玻璃：英雄卡片、主面板 */
.glass-strong {
  background: rgba(255,255,255,0.52);
  backdrop-filter: blur(20px);
  -webkit-backdrop-filter: blur(20px);
  border: 1px solid rgba(255,255,255,0.68);
  box-shadow:
    inset 0 1px 0 rgba(255,255,255,0.9),   /* 顶边高光 */
    inset 0 -1px 0 rgba(255,255,255,0.15),  /* 细微底边 */
    0 8px 32px rgba(0,0,0,0.06),
    0 2px 8px rgba(0,0,0,0.04);
}

/* 中玻璃：功能卡片、数据面板 */
.glass-mid {
  background: rgba(255,255,255,0.38);
  backdrop-filter: blur(16px);
  -webkit-backdrop-filter: blur(16px);
  border: 1px solid rgba(255,255,255,0.55);
  box-shadow:
    inset 0 1px 0 rgba(255,255,255,0.8),
    0 8px 24px rgba(0,0,0,0.05);
}

/* 轻玻璃：嵌套元素、次级卡片 */
.glass-light {
  background: rgba(255,255,255,0.26);
  backdrop-filter: blur(10px);
  -webkit-backdrop-filter: blur(10px);
  border: 1px solid rgba(255,255,255,0.42);
  box-shadow:
    inset 0 1px 0 rgba(255,255,255,0.6),
    0 4px 12px rgba(0,0,0,0.04);
}
```

**顶边高光是最关键的细节。** `inset 0 1px 0 rgba(255,255,255,0.9)` 模拟光线打在玻璃面板顶缘。没有它，玻璃卡片像半透明盒子。有了它，它们像物理物体。

**通过模糊变化做深度：**
- 英雄/前景卡片：`blur(20px)` — 更强模糊，更浅填充
- 功能卡片：`blur(16px)` — 中等
- 嵌套/次级元素：`blur(10px)` — 更轻，填充更少
- 永远不要超过 `blur(24px)` — 会发浑
- 永远不要在重模糊上再叠重模糊 — 两张嵌套的 `blur(20px)` 卡片会塌成雾

**圆角：** 大面板 20–28px，中卡片 14–18px，小元素 10–12px。永远不要 0 — 锐边破坏玻璃隐喻。

---

### 签名元素 — 动画数据环

执行出色的玻璃拟态金融或健康 UI 最鲜明的元素：圆形 SVG 弧在页面加载时自行描出，显示预算百分比、健康分数或目标完成度。

```html
<svg class="ring-svg" width="160" height="160" viewBox="0 0 160 160">
  <!-- 轨道环 -->
  <circle cx="80" cy="80" r="65" fill="none"
    stroke="rgba(26,46,31,0.08)" stroke-width="8"/>
  <!-- 动画填充环 -->
  <circle cx="80" cy="80" r="65" fill="none"
    stroke="#6B4EFF" stroke-width="8"
    stroke-linecap="round"
    stroke-dasharray="408"
    stroke-dashoffset="408"
    class="ring-fill"/>
</svg>
```

```css
.ring-svg { transform: rotate(-90deg); } /* 从顶部开始 */
.ring-fill {
  animation: drawRing 1.4s cubic-bezier(0.4, 0, 0.2, 1) 0.4s forwards;
}
/* 76%：dashoffset 从 408 到 408 * (1 - 0.76) = 约 98 */
@keyframes drawRing {
  to { stroke-dashoffset: 98; } /* 408 * (1 - percentage) */
}
```

环放在英雄玻璃卡片内。中心用衬线展示字体显示百分比。其下：带小分类行的支出拆分（圆点指示、标签、迷你条、金额）。

**Dashoffset 公式：** `stroke-dashoffset_end = circumference * (1 - percentage)`
周长 = `2 * π * r` = `2 * 3.14159 * 65` ≈ `408`

---

### 色彩系统

两个角色：**背景色板**（暖中性）与**强调**（一种鲜艳色）。

```
背景色板（暖）：
  奶油底：      #F5F0E8  — 页面背景起点
  浅鼠尾草：    #E8EDE3  — 页面背景中段
  鼠尾草：      #DCE8DC  — 页面背景终点 / 次级区块
  这三者应感觉像一片连续场，而不是三种颜色。

文字系统：
  深绿：        #1A2E1F  — 主标题与正文
  中绿：        #3D4F3F  — 次级文字、卡片标题
  弱鼠尾草：    #7A8C7C  — 说明、标签、占位文字
  这些是暖调近黑 — 永远不要用 #000000 或 #333333。

强调（仅一种）：
  紫：          #6B4EFF  — 所有交互元素
  深紫：        #5038E0  — 悬停态
  紫淡彩：      rgba(107,78,255,0.10)  — 标签背景、幽灵按钮

辅助数据色（仅用于图表与分类标签）：
  绿：     #3AB07A  — 储蓄、正向
  琥珀：   #F59E0B  — 警告、次分类
  粉：     #E879F9  — 第三分类
```

**规则：**
- 强调色（`#6B4EFF`）是页面上唯一鲜艳色。用在主 CTA、激活态、图表填充与关键数字。
- 永远不要用暖红（`#EF4444`）或锐蓝（`#2563EB`）作主强调 — 它们会与暖背景打架。
- Logo 渐变文字（AI 玻璃拟态常见）是陈词滥调 — 改用纯色或斜体衬线。
- 数据分类色只出现在图表与标签内，绝不进入结构 UI。

---

### 字体

把暖编辑衬线用于标题，干净几何无衬线用于正文与 UI。

```
展示 / 标题：        'DM Serif Display' — 温暖、编辑向、略出人意料
                     备选：'Playfair Display'、'Cormorant Garamond'
正文 / UI：          'DM Sans' — 干净、几何，与 DM Serif 搭配好
                     备选：'Inter'、'Plus Jakarta Sans'

字号阶：
  H1（英雄）：        clamp(38px, 5.5vw, 64px) / 衬线 / 默认字重（400） / 行高 1.05 / 字距 -0.02em
  H2（区块）：        clamp(28px, 4vw, 44px)   / 衬线 / 行高 1.15 / 字距 -0.02em
  卡片标题：          18–22px                   / 衬线 / 行高 1.25
  正文：              15–16px                   / 无衬线 / 字重 400 / 行高 1.72 / 弱化色
  标签 / 眉题：       11px                      / 无衬线 / 字重 600 / 大写 / 字距 0.1em / 紫色
  说明：              12px                      / 无衬线 / 字重 400 / 弱化色
  价格展示：          44–52px                   / 衬线 / 默认字重 / 字距 -0.04em
  卡片中的数字：      22–34px                   / 衬线 / 字距 -0.02em

关键手法 — 标题中的斜体：
  <h1>Your money, <em>in full view.</em></h1>
  斜体带来温度与区分，无需第二种字体。
  非斜体应是主导字重（900 或粗体），斜体是强调。
```

**规则：**
- 玻璃拟态标题永远不要用 Inter — 会读成通用 SaaS，而不是高端消费。
- 玻璃上的文字必须用深调近黑，不要纯 `#000` 或浅灰。暖背景上，暖近黑（`#1A2E1F`）看起来有意；冷黑看起来像事故。
- 正文段落避免超重字重（900）— 密集文字会破坏审美的轻盈。

---

### 导航

胶囊形浮动导航，最大宽 860px，居中。比正文卡片略更不透明 — 清楚浮在内容之上。

```css
.nav-wrap { position: sticky; top: 18px; z-index: 100; display: flex; justify-content: center; }

nav {
  width: 100%; max-width: 860px;
  padding: 11px 16px; border-radius: 999px;
  display: flex; align-items: center; justify-content: space-between; gap: 16px;
  background: rgba(255,255,255,0.52);
  backdrop-filter: blur(20px); -webkit-backdrop-filter: blur(20px);
  border: 1px solid rgba(255,255,255,0.7);
  box-shadow: inset 0 1px 0 rgba(255,255,255,0.9), 0 8px 24px rgba(26,46,31,0.06);
}

.nav-logo { font-family: 'DM Serif Display', serif; font-size: 19px; color: #1A2E1F; }
.nav-logo em { font-style: italic; color: #6B4EFF; }

.nav-links a {
  font-size: 13.5px; font-weight: 500; color: #7A8C7C;
  text-decoration: none; padding: 6px 13px; border-radius: 999px;
  transition: color 150ms, background 150ms;
}
.nav-links a:hover { color: #1A2E1F; background: rgba(255,255,255,0.5); }
```

**不要** 用满宽实心底导航 — 它会毁掉页面的分层深度。胶囊导航在视觉上浮动，强化玻璃审美。

---

### 按钮

三种按钮，按视觉重量排序：

```css
/* 主按钮：实心强调 — 页面上最重的元素 */
.btn-primary {
  background: #6B4EFF; color: #fff;
  padding: 12px 22px; border-radius: 12px; font-size: 14px; font-weight: 500;
  box-shadow: 0 6px 20px rgba(107,78,255,0.32), inset 0 1px 0 rgba(255,255,255,0.2);
  transition: transform 180ms ease, box-shadow 180ms ease, background 180ms ease;
}
.btn-primary:hover { transform: translateY(-2px); background: #5038E0; box-shadow: 0 12px 32px rgba(107,78,255,0.38); }

/* 幽灵：玻璃处理，次级操作 */
.btn-ghost {
  background: rgba(255,255,255,0.42); color: #1A2E1F;
  padding: 11px 20px; border-radius: 12px; font-size: 14px; font-weight: 500;
  border: 1px solid rgba(255,255,255,0.65);
  backdrop-filter: blur(12px); -webkit-backdrop-filter: blur(12px);
  transition: transform 180ms ease, background 180ms ease;
}
.btn-ghost:hover { transform: translateY(-2px); background: rgba(255,255,255,0.58); }

/* 强调幽灵：淡紫，第三级或按方案操作 */
.btn-accent-ghost {
  background: rgba(107,78,255,0.10); color: #6B4EFF;
  padding: 11px 20px; border-radius: 12px; font-size: 14px; font-weight: 500;
  border: 1px solid rgba(107,78,255,0.25);
  transition: transform 180ms ease, background 180ms ease;
}
.btn-accent-ghost:hover { transform: translateY(-2px); background: rgba(107,78,255,0.16); }
```

实心主按钮是页面上**唯一的非玻璃元素**。相对周围一切应感觉落地而重 — 这种对比让它成为最清晰的 CTA。

---

### 功能 Bento 网格

玻璃拟态中，非对称 bento 布局优于均匀功能网格。尺寸变化制造构图兴趣，并让卡片展示迷你可视化，而不只是文字。

```css
.bento {
  display: grid;
  grid-template-columns: 1.4fr 1fr 1fr;
  grid-template-rows: auto auto;
  gap: 16px;
}
.bento-card.tall { grid-row: span 2; }     /* 左侧高卡片 */
.bento-card.wide { grid-column: span 2; }  /* 底部宽卡片 */
```

卡片内容层级：
1. 眉题标签（10px，大写，紫，字距 0.1em）
2. 标题（衬线，18–22px）
3. 描述（最多 2–3 句，13px，弱化）
4. **迷你可视化** — 这让 bento 感觉像产品演示，而不是功能列表

每张卡片的迷你可视化类型：
- **支出卡片（高）：** 7 条迷你柱状图 + 分类胶囊云
- **目标卡片：** 3 条带标签与百分比的目标进度条
- **提醒卡片：** 2 条展示真实提醒示例的通知行
- **洞察卡片（宽）：** 左侧文字洞察 + 右侧 SVG 趋势线

---

### 定价区块

精选方案打破玻璃模式 — 用深色文字色（`#1A2E1F`）作实心背景，在视觉上锚定定价网格。浅背景上的深色卡片是玻璃系统中可能的最高对比处理。

```css
/* 非精选方案：玻璃处理 */
.plan { background: var(--glass-mid); backdrop-filter: blur(16px); border: 1px solid var(--glass-border-mid); }

/* 精选方案：实心深色 — 从所有玻璃元素中独立出来 */
.plan-featured { background: #1A2E1F; border: none; }
.plan-featured .plan-name  { color: rgba(255,255,255,0.5); }
.plan-featured .plan-price { color: #fff; }
.plan-featured .plan-features li { color: rgba(255,255,255,0.75); }
```

月付/年付切换用 `<div>` 开关（不是原生复选框），做成带滑动拇指的胶囊。年付是默认（激活）态 — 显示更低价格，鼓励年付注册。

```css
.toggle { width: 48px; height: 26px; background: rgba(26,46,31,0.1); border-radius: 999px; cursor: pointer; position: relative; transition: background 200ms; }
.toggle.on { background: #6B4EFF; }
.toggle-thumb { width: 20px; height: 20px; background: #fff; border-radius: 50%; position: absolute; top: 2px; left: 2px; box-shadow: 0 1px 4px rgba(0,0,0,0.15); transition: transform 200ms ease; }
.toggle.on .toggle-thumb { transform: translateX(22px); }
```

---

### 动效原则

本系统只有三类动画。其余全部即时。

**1. 加载时数据显现**（签名时刻）：
- SVG 环自行描出：`stroke-dashoffset` 从完整周长动画到目标值
- 柱状图从底部放大：`transform: scaleY(0) → scaleY(1)`，`transform-origin: bottom`
- 目标进度条从左延伸：`transform: scaleX(0) → scaleX(1)`，`transform-origin: left`
- 时长：0.9s–1.4s，`cubic-bezier(0.4, 0, 0.2, 1)`，页面加载后延迟 300–600ms

**2. 悬停交互**（微反馈）：
- 卡片与按钮：180–200ms ease 内 `translateY(-2px)` 到 `-4px`
- 悬停时阴影加深：`box-shadow` 过渡到更大偏移 + 略高不透明度
- 永远不要对卡片用 `scale()` — 会在复杂玻璃构图中造成布局偏移

**3. 计费切换**（状态变化）：
- 胶囊滑动：200ms ease 的 `transform: translateX(22px)`
- 价格数字立即更新（无需动画）
- 背景色过渡：200ms

```css
@media (prefers-reduced-motion: reduce) {
  .ring-fill, .mbar, .goal-fill, .spend-bar { animation: none !important; }
  .bento-card, .btn { transition: none !important; }
}
```

---

### 不要做什么
- ✗ 永远不要用漂移动画球 — 那是最容易识别的 AI 玻璃拟态陈词滥调
- ✗ 永远不要用扁平白或扁平深色背景 — 玻璃没有东西可反射
- ✗ 永远不要在重模糊里再嵌重模糊 — 模糊叠模糊产生雾，不是深度
- ✗ 永远不要给 Logo 用渐变文字 — 立刻读成模板
- ✗ 永远不要用 emoji 当功能卡片图标 — 用迷你 SVG 可视化或实心图标形
- ✗ 永远不要给标题用 Inter — 改用暖衬线搭配无衬线
- ✗ 永远不要用纯黑（`#000`）或纯白（`#fff`）作文色 — 用暖近黑
- ✗ 永远不要用满宽实心导航 — 浮在页面上的胶囊导航强化深度
- ✗ 永远不要让每个方案都是玻璃卡片 — 精选方案应实心以锚定网格
- ✗ 永远不要加超过一种鲜艳强调色 — 整套系统有效是因为一种紫把它钉住

### 待替换数据（占位映射）
- `[PRODUCT_NAME]` — 导航与页脚中的 logo，文案中引用
- `[TAGLINE]` — 英雄标题，拆成常规行与斜体行
- `[HERO_SUB]` — 2–3 句，16px，弱化色，最多 50 词
- `[RING_PERCENTAGE]` — 英雄卡片环中显示的主指标（0–100）
- `[SPEND_CATEGORIES]` — 4 行：名称、百分比、十六进制色、美元金额
- `[HERO_STATS]` — 2 张迷你数据卡：标签、数值、变化字符串
- `[PROOF_STATS]` — 4–5 个社会证明数字：数值、标签
- `[BENTO_CARDS]` — 数组：标签、标题、描述、可视化类型
- `[GOALS]` — 3 个目标进度项：标签、百分比
- `[ALERTS]` — 2 个通知示例：图标、标题、副标题
- `[INSIGHT_TEXT]` — 一句数据洞察 + 支撑句
- `[PRICING_TIERS]` — 3 档：名称、月价、年价、功能列表
- `[CTA_LABEL]` — 主按钮文字
- `[TRUST_TEXT]` — 例如「无需信用卡 · 随时取消」
