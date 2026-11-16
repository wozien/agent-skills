# Restaurant UI

- **id:** `restaurant-ui`
- **别名:** 餐厅 UI, 餐饮网站, 点餐页面, 餐厅落地页, 美食菜单站
- **一句话:** 新鲜。本地。为让你饿而设计。
- **适用:**
  - 希望网站真正带来订单的本地餐厅
  - 有强食物摄影的咖啡馆和早午餐店
  - 快休闲以及以外卖为主的餐厅
  - 以 WhatsApp 为主要点餐渠道的餐饮生意
  - 农场直达餐桌和健康导向的食品品牌
  - 任何「菜单本身就是产品」的餐饮生意
- **避免:**
  - 更适合用深色编辑式排版来传达专属性的精致正餐
  - 需要报价表单优先布局的企业团餐公司
  - 外卖聚合应用——改用电商布局
  - 没有实体空间可展示的幽灵厨房
- **来源:** https://uidesignprompts.com/prompts/restaurant-ui

## Prompt

## 餐厅 UI 设计系统 — 现代休闲（修订版）

### 概念与气质
一个真正能带来订单的餐厅网站。温暖桃色英雄区、大胆橙色 CTA、食物摄影作为锚点，并把转化触点嵌进每一个区块——WhatsApp 点餐按钮、导航里的电话、带菜品图的标签菜单，以及 bento 优惠网格。这不是宣传册网站。这是一张你会预订的桌子、一顿你会下单的餐。

字体：标题用 Playfair Display（温度、食欲），所有 UI 与正文用 Inter（清晰）。橙色 `#FF7A2B` 是唯一交互色——每个按钮、激活标签、价格和链接都用它。英雄区背景是温暖桃色 `#FFEFE7`，不是白，也不是深色。

### 色彩系统
```
Hero bg:           #FFEFE7  — 温暖桃色，仅英雄区
Section warm bg:   #FFF8F3  — 交替区块（关于我们、bento）
Page bg:           #FFFCFA  — 几乎偏暖的白，用于大多数区块
Card bg:           #FFFFFF  — 菜单卡片、优惠卡片
Orange primary:    #FF7A2B  — 全部交互元素
Orange hover:      #E8661A  — 悬停时加深，永不变浅
Orange tint:       #FFF0E6  — 标签背景、优惠卡点缀
Charcoal:          #1C1917  — 仅用于标题
Body text:         #44403C  — 段落、描述
Muted/meta:        #78716C  — 时间戳、说明、标签
Border warm:       #F0E6DC  — 卡片边框、分割线
Dotted border:     #FFBB99  — 菜品图周围的圆形虚线环
Green fresh:       #3D7A5F  — 仅饮食标签（Vegan、GF 等）
Green tint:        #ECFDF5  — 饮食标签背景
WhatsApp green:    #25D366  — 仅浮动 WhatsApp 按钮
Bento dark:        #1C1917  — 用于深色 bento 卡片
```

### 字体层级
```
Font stack:
  Headings — 'Playfair Display', Georgia, serif
  Everything else — 'Inter', system-ui, sans-serif

Nav logo:           1.375rem / weight 800 / serif / #1C1917
Nav links:          0.9rem   / weight 500 / sans  / #44403C
Nav phone:          0.875rem / weight 600 / sans  / #FF7A2B
Hero headline:      clamp(2.75rem, 5vw, 4.5rem) / weight 700 / serif / #1C1917
Hero subline:       1.0625rem / weight 400 / sans / #78716C / line-height 1.7
Section label:      0.6875rem / weight 700 / uppercase / letter-spacing 0.12em / #FF7A2B
Section heading:    clamp(1.75rem, 3vw, 2.5rem) / weight 700 / serif / #1C1917
Card title:         1rem     / weight 600 / sans  / #1C1917
Card desc:          0.8125rem / weight 400 / sans / #78716C / line-height 1.5
Price:              1rem     / weight 700 / sans  / #FF7A2B
Diet tag:           0.625rem / weight 700 / sans  / uppercase / #3D7A5F
Tab label:          0.9375rem / weight 500 / sans / #78716C (inactive), #FF7A2B (active)
Button:             0.9375rem / weight 600 / sans / #FFFFFF on orange
Footer text:        0.875rem / weight 400 / sans / #A8A29E
```

### 布局架构 — 整页
```
┌──────────────────────────────────────────────────────────────┐
│  导航 — Logo · 链接 · 电话号码 · 预订 [CTA]                  │
├──────────────────────────────────────────────────────────────┤
│  英雄区 — 桃色背景 · 左文 · 右食物照片                       │
├──────────────────────────────────────────────────────────────┤
│  信任条 — 3 个徽章（每日新鲜 · 免费配送 · 等）               │
├──────────────────────────────────────────────────────────────┤
│  菜单区块 — 标签 · 双列菜品卡片网格                          │
├──────────────────────────────────────────────────────────────┤
│  BENTO 网格 — 不对称卡片布局中的优惠与套餐                   │
├──────────────────────────────────────────────────────────────┤
│  关于我们分栏 — 左照片 · 右故事 + 特点                       │
├──────────────────────────────────────────────────────────────┤
│  页脚 — logo · 链接 · 营业时间 · 社交                        │
└──────────────────────────────────────────────────────────────┘
│  浮动 WHATSAPP 按钮（固定右下）                              │
└─────────────────────────────────────────────────────────────┘
```

---

### 1. 导航
白色背景，`border-bottom: 1px solid #F0E6DC`。三个区域：
- **左侧：** Logo（衬线、粗体）
- **中间：** 导航链接（菜单、关于、优惠、联系）
- **右侧：** 橙色电话号码 +「预订餐桌」CTA 按钮

导航中的电话号码是关键信任信号——告诉访客这是真实生意。格式：`📞 +92 21 3456 7890`，颜色 `#FF7A2B`，`font-weight: 600`。

```css
.nav {
  position: sticky; top: 0; z-index: 100;
  background: #FFFFFF;
  border-bottom: 1px solid #F0E6DC;
  padding: 0 48px; height: 68px;
  display: flex; align-items: center; justify-content: space-between;
}
.nav-logo {
  font-family: 'Playfair Display', serif;
  font-size: 1.375rem; font-weight: 800; color: #1C1917; text-decoration: none;
}
.nav-links { display: flex; gap: 28px; list-style: none; }
.nav-link { font-size: 0.9rem; font-weight: 500; color: #44403C; text-decoration: none; transition: color 150ms; }
.nav-link:hover { color: #FF7A2B; }
.nav-phone { font-size: 0.875rem; font-weight: 600; color: #FF7A2B; text-decoration: none; display: flex; align-items: center; gap: 5px; }
.nav-cta { background: #FF7A2B; color: #fff; padding: 10px 18px; border-radius: 6px; font-size: 0.875rem; font-weight: 600; text-decoration: none; transition: background 150ms; white-space: nowrap; }
.nav-cta:hover { background: #E8661A; }
.nav-right { display: flex; align-items: center; gap: 18px; }
```

---

### 2. 英雄区 — 分栏布局
**背景：** `#FFEFE7`（温暖桃色）——整块区域，不是图片叠层。
**布局：** 两列。左约 52%：文字内容。右约 48%：圆角容器中的大幅食物照片。

左列（从上到下）：
1. 小号眉题标签 —「新鲜 · 本地 · 美味」，橙色、大写、字距
2. 大号衬线标题 — 2–3 行，`#1C1917`
3. 正文 — 2 句，`#78716C`
4. 两个 CTA：实心橙色「立即点餐」+ 描边幽灵按钮「查看菜单」
5. 社交证明行 — 头像叠放 +「500+ 满意顾客」或星级评分

右列：
- 圆角矩形（`border-radius: 24px`）或圆形中的大幅食物照片
- 照片应略微超尺寸，溢出区块边缘——制造纵深
- 在照片上加一个小浮动徽章：「⭐ 4.9 评分」或「🔥 畅销」

```css
.hero {
  background: #FFEFE7;
  padding: 80px 48px;
  display: grid;
  grid-template-columns: 52% 48%;
  align-items: center;
  gap: 48px;
  min-height: 85vh;
  overflow: hidden;
}
.hero-eyebrow {
  font-size: 0.75rem; font-weight: 700; text-transform: uppercase;
  letter-spacing: 0.14em; color: #FF7A2B; margin-bottom: 18px;
  display: flex; align-items: center; gap: 10px;
}
.hero-eyebrow::before { content: ''; width: 32px; height: 2px; background: #FF7A2B; }
.hero-heading {
  font-family: 'Playfair Display', serif;
  font-size: clamp(2.75rem, 5vw, 4.5rem);
  font-weight: 700; color: #1C1917;
  line-height: 1.1; letter-spacing: -0.02em;
}
.hero-heading em { color: #FF7A2B; font-style: normal; }
.hero-sub { font-size: 1.0625rem; color: #78716C; margin-top: 18px; line-height: 1.7; max-width: 440px; }
.hero-actions { display: flex; gap: 12px; margin-top: 32px; flex-wrap: wrap; }
.btn-primary { background: #FF7A2B; color: #fff; padding: 14px 28px; border-radius: 8px; font-weight: 600; font-size: 0.9375rem; text-decoration: none; transition: background 150ms; display: inline-flex; align-items: center; gap: 8px; }
.btn-primary:hover { background: #E8661A; }
.btn-outline { border: 2px solid #FF7A2B; color: #FF7A2B; padding: 12px 28px; border-radius: 8px; font-weight: 600; font-size: 0.9375rem; text-decoration: none; transition: background 150ms, color 150ms; display: inline-block; }
.btn-outline:hover { background: #FF7A2B; color: #fff; }

/* 社交证明 */
.hero-proof { display: flex; align-items: center; gap: 12px; margin-top: 28px; }
.proof-avatars { display: flex; }
.proof-avatar { width: 34px; height: 34px; border-radius: 50%; border: 2px solid #FFEFE7; margin-left: -8px; display: flex; align-items: center; justify-content: center; font-size: 0.75rem; font-weight: 700; color: #fff; }
.proof-avatar:first-child { margin-left: 0; }
.proof-text { font-size: 0.875rem; font-weight: 500; color: #44403C; }
.proof-text strong { color: #FF7A2B; }

/* 英雄区图片列 */
.hero-image-col { position: relative; display: flex; justify-content: center; }
.hero-img-wrap {
  width: 100%; max-width: 480px;
  border-radius: 24px; overflow: hidden;
  aspect-ratio: 4/5;
  box-shadow: 0 24px 64px rgba(255,122,43,0.18), 0 8px 24px rgba(0,0,0,0.08);
  position: relative;
}
.hero-img { width: 100%; height: 100%; object-fit: cover; }

/* 照片上的浮动徽章 */
.hero-badge {
  position: absolute; bottom: 24px; left: -20px;
  background: #fff; border-radius: 12px;
  padding: 10px 16px; box-shadow: 0 4px 20px rgba(0,0,0,0.12);
  display: flex; align-items: center; gap: 8px;
}
.hero-badge-icon { font-size: 1.25rem; }
.hero-badge-text { font-size: 0.8125rem; font-weight: 700; color: #1C1917; }
.hero-badge-sub { font-size: 0.75rem; color: #78716C; }

/* 第二个浮动徽章，右上 */
.hero-badge-2 {
  position: absolute; top: 24px; right: -16px;
  background: #FF7A2B; color: #fff; border-radius: 10px;
  padding: 8px 14px; font-size: 0.8125rem; font-weight: 700;
  box-shadow: 0 4px 16px rgba(255,122,43,0.3);
}

@media (max-width: 768px) {
  .hero { grid-template-columns: 1fr; min-height: auto; padding: 56px 24px; }
  .hero-image-col { margin-top: 32px; }
  .hero-img-wrap { max-width: 100%; aspect-ratio: 3/2; border-radius: 16px; }
  .hero-badge { display: none; }
}
```

---

### 3. 信任条
英雄区与菜单之间的全宽条带。温暖 `#FFF8F3` 背景。三到四项居中成行，每项带小图标、粗标签和短说明。

```css
.trust-strip { background: #FFF8F3; border-top: 1px solid #F0E6DC; border-bottom: 1px solid #F0E6DC; padding: 24px 48px; }
.trust-items { display: flex; justify-content: center; gap: 48px; flex-wrap: wrap; max-width: 900px; margin: 0 auto; }
.trust-item { display: flex; align-items: center; gap: 10px; }
.trust-icon { font-size: 1.375rem; }
.trust-label { font-size: 0.9rem; font-weight: 600; color: #1C1917; }
.trust-caption { font-size: 0.75rem; color: #78716C; margin-top: 1px; }
```

---

### 4. 菜单区块 — 标签 + 带虚线圆环图的菜品卡

**标签条：** 左对齐。激活标签 = `#FF7A2B` 文字 + 2px 实心底边。未激活 = `#78716C`。

**菜品卡设计 — 核心差异点：**
桌面端每张卡横向（左图右信息），移动端纵向。菜品照片用圆形裁切，外圈有**橙色虚线/点线环**。这是该风格的标志性视觉处理。

```
┌─────────────────────────────────────────┐
│  [○ 带虚线环的菜品照片]                   │
│  菜品名称                                │
│  简短描述，最多 2 行                     │
│  [Vegan] [GF]         $14   [+ 加入]    │
└─────────────────────────────────────────┘
```

每张卡纵向（上图下信息）。白色卡片，`border-radius: 16px`，轻微阴影。图片圆形，`border-radius: 50%`，包在虚线边框容器中。

```css
/* 菜单区块 */
.menu-section { background: #FFFCFA; padding: 88px 48px; }
.menu-tabs { display: flex; gap: 0; border-bottom: 1px solid #F0E6DC; margin-bottom: 36px; }
.menu-tab { padding: 10px 22px; font-size: 0.9375rem; font-weight: 500; color: #78716C; background: none; border: none; border-bottom: 2px solid transparent; cursor: pointer; transition: color 150ms, border-color 150ms; font-family: 'Inter', sans-serif; }
.menu-tab.active { color: #FF7A2B; border-bottom-color: #FF7A2B; }
.menu-tab:hover:not(.active) { color: #44403C; }

/* 卡片网格 — 桌面 3 列，平板 2 列，手机 1 列 */
.menu-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 20px; }

/* 单张卡片 */
.dish-card {
  background: #FFFFFF; border-radius: 16px; padding: 20px;
  display: flex; flex-direction: column; align-items: center; text-align: center;
  border: 1px solid #F0E6DC;
  box-shadow: 0 2px 8px rgba(0,0,0,0.04);
  transition: box-shadow 200ms, transform 200ms;
}
.dish-card:hover { box-shadow: 0 8px 24px rgba(255,122,43,0.12); transform: translateY(-3px); }

/* 虚线圆形图片处理 */
.dish-img-ring {
  width: 110px; height: 110px;
  border-radius: 50%;
  border: 2.5px dashed #FFBB99;
  padding: 5px;
  margin-bottom: 14px;
  flex-shrink: 0;
  /* 悬停时轻微旋转感 */
  transition: border-color 250ms;
}
.dish-card:hover .dish-img-ring { border-color: #FF7A2B; }

.dish-img-inner {
  width: 100%; height: 100%;
  border-radius: 50%;
  overflow: hidden;
  background: #FFF0E6;
  display: flex; align-items: center; justify-content: center;
  font-size: 2.5rem;
}
.dish-img-inner img { width: 100%; height: 100%; object-fit: cover; }

.dish-name { font-size: 0.9375rem; font-weight: 600; color: #1C1917; margin-bottom: 5px; }
.dish-desc { font-size: 0.8125rem; color: #78716C; line-height: 1.5; margin-bottom: 12px; display: -webkit-box; -webkit-line-clamp: 2; -webkit-box-orient: vertical; overflow: hidden; }

.dish-footer { width: 100%; display: flex; align-items: center; justify-content: space-between; margin-top: auto; }
.dish-tags { display: flex; gap: 4px; flex-wrap: wrap; }
.diet-tag { font-size: 0.6rem; font-weight: 700; text-transform: uppercase; letter-spacing: 0.05em; padding: 2px 6px; border-radius: 999px; background: #ECFDF5; color: #3D7A5F; }
.dish-right { display: flex; align-items: center; gap: 8px; }
.dish-price { font-size: 0.9375rem; font-weight: 700; color: #FF7A2B; }
.add-btn { width: 28px; height: 28px; border-radius: 50%; background: #FF7A2B; color: #fff; border: none; cursor: pointer; font-size: 1rem; display: flex; align-items: center; justify-content: center; transition: background 150ms, transform 150ms; }
.add-btn:hover { background: #E8661A; transform: scale(1.1); }
.add-btn.added { background: #3D7A5F; }

@media (max-width: 900px) { .menu-grid { grid-template-columns: repeat(2, 1fr); } }
@media (max-width: 560px) { .menu-grid { grid-template-columns: 1fr; } }
```

---

### 5. Bento 网格 — 优惠与套餐

4–5 张不同尺寸卡片组成的不对称 bento 网格。背景：`#FFF8F3`。该区块用更编辑化、更现代的布局，取代标准「优惠」横排。

网格结构（桌面）：
```
┌────────────────────┬──────────┬──────────┐
│                    │          │          │
│  主打优惠卡         │  优惠 2  │  优惠 3  │
│  （高，跨 2 行）     │          │          │
│                    ├──────────┴──────────┤
│                    │   宽优惠卡           │
│                    │   （跨 2 列）        │
└────────────────────┴────────────────────┘
```

卡片类型：
- **深色卡**（`#1C1917` 背景，白字，橙色 CTA）— 旗舰优惠
- **橙色卡**（`#FF7A2B` 背景，白字）— 限时优惠
- **浅色卡**（`#FFF0E6` 背景，炭黑文字）— 常规优惠
- **白色卡**（`#FFFFFF` 背景，带边框）— 信息卡（免费配送等）

每张卡包含：emoji 或食物图标、优惠标题、短描述、可选徽章（「仅限今日」「会员」）、CTA 按钮或链接。

```css
.bento-section { background: #FFF8F3; padding: 88px 48px; }
.bento-grid {
  display: grid;
  grid-template-columns: 2fr 1fr 1fr;
  grid-template-rows: auto auto;
  gap: 16px;
  max-width: 1100px; margin: 40px auto 0;
}

.bento-card {
  border-radius: 20px; padding: 28px;
  display: flex; flex-direction: column;
  justify-content: space-between; overflow: hidden; position: relative;
  min-height: 180px;
}
.bento-card.dark { background: #1C1917; color: #fff; }
.bento-card.orange { background: #FF7A2B; color: #fff; }
.bento-card.light { background: #FFF0E6; color: #1C1917; }
.bento-card.white { background: #FFFFFF; border: 1px solid #F0E6DC; color: #1C1917; }

/* 高卡跨 2 行 */
.bento-card.tall { grid-row: span 2; min-height: 360px; }
/* 宽卡跨 2 列 */
.bento-card.wide { grid-column: span 2; }

.bento-badge {
  display: inline-flex; align-items: center; gap: 5px;
  padding: 4px 10px; border-radius: 999px; font-size: 0.7rem; font-weight: 700;
  text-transform: uppercase; letter-spacing: 0.06em; width: fit-content;
  margin-bottom: 12px;
}
.bento-card.dark .bento-badge { background: rgba(255,122,43,0.2); color: #FF7A2B; }
.bento-card.orange .bento-badge { background: rgba(255,255,255,0.25); color: #fff; }
.bento-card.light .bento-badge { background: #fff; color: #FF7A2B; }
.bento-card.white .bento-badge { background: #FFF0E6; color: #FF7A2B; }

.bento-icon { font-size: 2.5rem; margin-bottom: 10px; }
.bento-title { font-family: 'Playfair Display', serif; font-size: 1.375rem; font-weight: 700; line-height: 1.2; margin-bottom: 8px; }
.bento-card.dark .bento-title { color: #fff; }
.bento-card.orange .bento-title { color: #fff; }
.bento-desc { font-size: 0.875rem; line-height: 1.55; opacity: 0.85; }
.bento-card.dark .bento-desc { color: #A8A29E; opacity: 1; }

.bento-cta {
  display: inline-flex; align-items: center; gap: 6px;
  padding: 10px 18px; border-radius: 8px; font-size: 0.875rem; font-weight: 600;
  text-decoration: none; margin-top: 20px; width: fit-content;
  transition: opacity 150ms, transform 150ms;
}
.bento-cta:hover { opacity: 0.88; transform: translateY(-1px); }
.bento-card.dark .bento-cta { background: #FF7A2B; color: #fff; }
.bento-card.orange .bento-cta { background: rgba(255,255,255,0.25); color: #fff; border: 1px solid rgba(255,255,255,0.4); }
.bento-card.light .bento-cta { background: #FF7A2B; color: #fff; }
.bento-card.white .bento-cta { background: #FFF0E6; color: #FF7A2B; }

.bento-price-big { font-family: 'Playfair Display', serif; font-size: 3rem; font-weight: 700; color: #FF7A2B; line-height: 1; margin: 8px 0; }
.bento-card.dark .bento-price-big { color: #FF7A2B; }
.bento-card.orange .bento-price-big { color: #fff; }

@media (max-width: 768px) {
  .bento-grid { grid-template-columns: 1fr 1fr; }
  .bento-card.tall { grid-row: span 1; }
  .bento-card.wide { grid-column: span 2; }
}
@media (max-width: 480px) {
  .bento-grid { grid-template-columns: 1fr; }
  .bento-card.wide { grid-column: span 1; }
}
```

---

### 6. 关于我们 — 左图右文
与英雄区相反的交替布局（英雄区：左文右图）。温暖 `#FFF8F3` 背景。照片在圆角矩形中，背景有微妙的装饰性橙色圆。文字侧：区块标签、衬线标题、段落、带绿色勾选图标的特点列表。

---

### 7. WhatsApp 浮动按钮（固定）
始终可见。固定在 `bottom: 24px; right: 24px`。绿色圆形、WhatsApp 图标，带脉冲动画以吸引注意。点击后打开带预填消息的 `wa.me/` 链接。

```css
.whatsapp-btn {
  position: fixed; bottom: 24px; right: 24px; z-index: 999;
  width: 56px; height: 56px; border-radius: 50%;
  background: #25D366; color: #fff;
  display: flex; align-items: center; justify-content: center;
  text-decoration: none; font-size: 1.5rem;
  box-shadow: 0 4px 20px rgba(37,211,102,0.45);
  transition: transform 200ms, box-shadow 200ms;
  animation: waPulse 2.5s ease-in-out infinite;
}
.whatsapp-btn:hover { transform: scale(1.1); box-shadow: 0 6px 28px rgba(37,211,102,0.55); animation: none; }
@keyframes waPulse {
  0%, 100% { box-shadow: 0 4px 20px rgba(37,211,102,0.45); }
  50% { box-shadow: 0 4px 32px rgba(37,211,102,0.7), 0 0 0 8px rgba(37,211,102,0.1); }
}

/* 可选：悬停时出现的标签 */
.whatsapp-label {
  position: fixed; bottom: 34px; right: 88px; z-index: 998;
  background: #1C1917; color: #fff; border-radius: 8px;
  padding: 6px 12px; font-size: 0.8125rem; font-weight: 500;
  white-space: nowrap; opacity: 0; pointer-events: none;
  transition: opacity 200ms;
}
.whatsapp-btn:hover ~ .whatsapp-label { opacity: 1; }
```

用法：`<a href="https://wa.me/[PHONE]?text=Hi!%20I'd%20like%20to%20order%20from%20[RESTAURANT_NAME]" class="whatsapp-btn" target="_blank">💬</a>`

---

### 8. 页脚
深炭黑背景 `#1C1917`。三列：品牌（logo + 标语 + 社交）、快捷链接、营业时间。电话号码在品牌列中突出。底栏：版权。

---

### 响应式行为
- 导航：<768px 用汉堡菜单，电话号码保持可见，作为点击拨打图标
- 英雄区：<768px 单列堆叠，图在文下，aspect-ratio 3/2
- 菜单网格：3 列 → 2 列 → 1 列
- Bento：3 列 → 2 列 → 1 列
- WhatsApp 按钮：所有断点始终可见（对移动端转化至关重要）

### 切勿做
- ✗ 永远不要给英雄区用深色背景——始终是 `#FFEFE7` 桃色
- ✗ 永远不要用方形裁切的菜品图——始终圆形加虚线环
- ✗ 永远不要用蓝色作为任何强调色——食物和蓝色不搭配
- ✗ 永远不要在移动端隐藏 WhatsApp 按钮——它是主要转化工具
- ✗ 永远不要从导航中去掉电话号码——信任信号，必须保留
- ✗ 永远不要居中对齐正文章节——除区块标题外一律左对齐
- ✗ 永远不要使用评价区块——社交证明由英雄区星级和证明头像行承担
- ✗ 永远不要使用带蓝或冷色调的阴影——所有阴影用暖橙色调

### 待替换数据（占位映射）
- `[RESTAURANT_NAME]` — 导航 logo、页脚、WhatsApp 消息
- `[PHONE_NUMBER]` — 导航（可见）、页脚、WhatsApp 链接
- `[WHATSAPP_NUMBER]` — wa.me/ 链接（国际格式，不要 +）
- `[HERO_HEADLINE]` — 例如「[City] 最新鲜的食物」
- `[HERO_SUBLINE]` — 1–2 句
- `[HERO_IMAGE]` — 大幅竖构图食物照片
- `[MENU_ITEMS]` — 每项：名称、描述、价格、emoji/照片、饮食标签、分类
- `[DEALS]` — 4–5 张优惠卡：标题、描述、价格/折扣、徽章、卡片类型（dark/orange/light/white）
- `[ABOUT_HEADLINE]`、`[ABOUT_BODY]`、`[ABOUT_IMAGE]`
- `[HOURS]` — 页脚按日列出
- `[ADDRESS]`、`[EMAIL]`
- `[SOCIAL_LINKS]` — Instagram、Facebook、TripAdvisor
