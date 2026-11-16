# NeoBrutalism

- **id:** `neobrutalism`
- **别名:** 新粗野主义, Neo-Brutalism, 粗野主义 UI, 硬边阴影
- **一句话:** 大胆、响亮、成体系，而且能用。
- **适用:**
  - 需要立刻跳出来的 SaaS 落地页
  - 开发者工具与独立黑客产品
  - 设计系统与 UI kit 营销站
  - 面向大胆、有文化自觉受众的产品
  - 任何要对抗通用企业风设计的产品
- **避免:**
  - 医疗、法律或金融等需要保守信任信号的产品
  - 买家期待精致极简的企业级 B2B 工具
  - 复杂数据可视化且边框会增加噪音的产品
  - 需要柔软、亲和或奢华感的品牌
- **来源:** https://uidesignprompts.com/prompts/neobrutalism

## Prompt

## 新粗野主义设计系统

### 气质
原始、成体系、毫不道歉。新粗野主义靠对比传达专业——每个元素可见，每条边框被声明，每道阴影都硬。感觉像同时懂瑞士网格理论和朋克音乐的人设计的。够大胆以抓住注意，够结构化以完成转化。

### 两条不可妥协的规则
在任何事之前——这两条必须出现在**每一个**元素上，没有例外:

**规则 1 — 硬边框:**
```css
border: 3px solid #0A0A0A;
border-radius: 4px; /* 最大 4px — 不能再大 */
```

**规则 2 — 硬偏移阴影（无模糊、无扩散）:**
```css
box-shadow: 5px 5px 0 #0A0A0A;
```
永远不要在 box-shadow 里用 `blur`。永远不要用 `rgba` 做阴影色。阴影始终是 100% 不透明的扁平黑。这就是新粗野主义一眼可辨的原因。

### 色彩系统

**基础色板:**
- 背景: #FFFEF0 — 纸米色，**不是**纯白。轻微暖意避免刺眼。
- 黑色: #0A0A0A — 用于**所有**边框、阴影和主文字。绝不用纯 #000000。
- 白色: #FFFFFF — 用于需要从米色背景抬起的卡片表面。

**6 种强调色（按区块轮换 — 绝不要一次全用）:**
- Electric Yellow: #FFE600 — 主 CTA、hero 徽章、区块高亮、激活状态
- Hot Magenta: #FF3EA5 — 次级强调、破坏性操作、注意标记
- Vivid Cyan: #00C2CB — 功能块、信息状态、链接强调
- Deep Purple: #7B2FBE — 数据区块、通栏对比面板
- Signal Green: #00C853 — 成功状态、勾选、正向指示
- Bright Orange: #FF6B35 — 暖强调、定价高亮

**粉彩色变体（便当卡片背景 — 更软但仍大胆）:**
- Pastel Yellow: #FFDB58
- Pastel Cyan: #87CEEB
- Pastel Pink: #FFC0CB
- Pastel Green: #BAFCA2
- Pastel Purple: #C4A1FF
- Pastel Orange: #FFA07A

**使用规则:** 每页最多选 2-3 种强调色。背景、黑、白始终在场。强调色按区块轮换。

### 字体 — 层级系统

字体: Space Grotesk（首选）或 Inter — 二者的几何感都适合新粗野网格。

```
展示 / H1:     clamp(40px, 6vw, 72px)，字重 900，letter-spacing -0.03em，大写，line-height 0.95
H2:            clamp(28px, 4vw, 44px)，字重 900，letter-spacing -0.03em，大写，line-height 1.0
H3:            clamp(20px, 2.5vw, 28px)，字重 800，letter-spacing -0.02em
正文:          16-18px，字重 400-500，line-height 1.6，颜色 #333
标签/元信息:   12-13px，字重 700，letter-spacing 0.08-0.12em，大写，颜色 #666
区块标签:      11px，字重 700，letter-spacing 0.12em，大写，白字黑底胶囊
```

**关键规则:** 展示标题**必须**大写。小写展示文字会破坏粗野美学。

### 区块标签组件
每个区块都以这个小标签开场，宣告区块是什么:
```html
<div style="
  display: inline-block;
  background: #0A0A0A;
  color: #FFFFFF;
  font-size: 11px;
  font-weight: 700;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  padding: 5px 14px;
  border-radius: 2px;
  margin-bottom: 16px;
">SECTION LABEL</div>
```

### 按钮系统 — 按压效果
新粗野主义按钮模拟实体按下交互:

```css
/* 默认状态 */
.btn {
  border: 3px solid #0A0A0A;
  border-radius: 4px;
  box-shadow: 5px 5px 0 #0A0A0A;
  font-weight: 700;
  font-size: 15px;
  letter-spacing: 0.02em;
  padding: 12px 24px;
  cursor: pointer;
  transition: transform 0.1s ease, box-shadow 0.1s ease;
}

/* 悬停 — 按下前略抬起 */
.btn:hover {
  transform: translate(2px, 2px);
  box-shadow: 3px 3px 0 #0A0A0A;
}

/* 激活 — 完全按下 */
.btn:active {
  transform: translate(5px, 5px);
  box-shadow: 0 0 0 #0A0A0A;
}
```

**按钮变体:**
- 主按钮（黄）: `background: #FFE600; color: #0A0A0A` — 主 CTA。米黄底上的黄读作最重要的动作。
- 深色: `background: #0A0A0A; color: #FFFFFF` — 次级 CTA、高对比场景。
- 白/描边: `background: #FFFFFF; color: #0A0A0A` — 任意背景上的浏览/次级操作。
- 强调: `background: [accent]; color: #0A0A0A or #FFFFFF` — 随区块语境。

### 卡片组件

**标准卡片:**
```css
.card {
  background: #FFFFFF;
  border: 3px solid #0A0A0A;
  border-radius: 4px;
  box-shadow: 5px 5px 0 #0A0A0A;
  padding: 28px;
  transition: transform 0.15s, box-shadow 0.15s;
}
.card:hover {
  transform: translate(-3px, -3px);
  box-shadow: 8px 8px 0 #0A0A0A;
}
```
悬停时卡片向左上滑、阴影变大 — 与按钮按压效果相反。卡片像被拿起；按钮像被按下。

**强调卡片（便当网格用）:**
同样的边框 + 阴影，但用粉彩或高饱和背景代替白色。相邻卡片轮换: 黄、青、粉、绿、紫、橙。

**深色卡片:**
`background: #0A0A0A; color: #FFFFFF` — 用于数据或精选项。黑底黄数字冲击最大。

### 便当网格布局
便当网格是功能区的签名布局模式:

```css
.bento-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 12px; /* 紧间距 — 边框负责视觉分隔 */
}
```

**网格尺寸变体:**
- `1×1`（普通）: 标准功能卡片
- `2×1`（宽）: 最重要功能 — 放在顶部或底部
- `1×2`（高）: 数据卡或需要大数字空间的精选功能
- `2×2`（大）: 带插图的英雄功能

**规则:** 每张便当卡背景色都不同。相邻卡片不得同色。

### 导航栏
```
白背景 | 3px 底边框 | 高度 60px
左: Logo 标记（强调色背景 + 黑边框）+ 品牌名大写
中偏左: 导航链接（纯文字，悬停 = 黄背景）
右: Ghost 链接「Log in」+ 黄色胶囊按钮「Sign up」
Sticky: 是
```
不要圆角下拉菜单。若有下拉: 全边框、扁平、硬阴影面板。

### 公告条
导航栏上方:
```css
background: #0A0A0A;
color: #FFE600;
font-size: 13px;
font-weight: 700;
letter-spacing: 0.05em;
padding: 8px 24px;
text-align: center;
```
包含: 营销文案 + 黄色 「CHECK IT OUT →」链接。立刻建立视觉优先级。

### Hero 区 — 非对称两列
```
左栏 (55%): 徽章胶囊 + 巨大 h1 + 副标题 + 按钮行 + 信任勾选
右栏 (45%): 抽象色块 / 插图 / 产品预览
```

**Hero 徽章胶囊**（h1 上方）:
```css
background: #FFE600;
border: 3px solid #0A0A0A;
border-radius: 4px;
box-shadow: 3px 3px 0 #0A0A0A;
padding: 5px 14px;
font-size: 12px;
font-weight: 700;
letter-spacing: 0.08em;
text-transform: uppercase;
```

**信任勾选**（按钮下方）:
```css
/* 每项: */
display: flex; align-items: center; gap: 6px;
/* 勾选图标: */
background: #00C853; border: 2px solid #0A0A0A; border-radius: 2px;
width: 18px; height: 18px; /* 内含 ✓ */
font-size: 13px; font-weight: 600;
```

### 功能条（hero 下方）
4 等列，每列有 border-right（最后一列没有）。每列:
- 彩色图标盒（每项不同强调色，36×36px，有边框）
- 大写功能标题
- #555 短描述
- 右下 「↗」箭头，悬停出现
- 悬停时整列背景变为黄色

### 数据区
通栏深紫 (`#7B2FBE`) 背景。项之间白色边框。四列:
- 第 1-3 列: 数据数字用 `#FFE600`（巨大），标签用 `rgba(255,255,255,0.8)`
- 第 4 列: 「TRUSTED BY」标签 + 品牌名徽章（白字半透明背景）

### 推荐卡片
白背景、硬边框、硬阴影。三列:
- 超大开场引号 `#FFE600`，font-family Georgia，font-size 48px
- 正文 #333，font-size 14px
- 作者: 圆形头像（按强调色轮换）+ 姓名 + 角色
- 悬停: 卡片抬起 (-3px, -3px) 且阴影更大

### Newsletter / CTA 条带
两种模式:

**通栏黄色 CTA（页脚前）:**
- 背景: `#FFE600`，border-top + border-bottom: `3px solid #0A0A0A`
- 大加粗标题（大写、巨大、左侧）+ 正文 + 按钮（右侧）
- 区块本身无 border-radius — 通栏贴边

**Newsletter 条（页脚上方）:**
- 背景: `#0A0A0A`
- 标题白色，副标题 `rgba(255,255,255,0.6)`
- 邮箱输入: 白背景、硬左边框，与订阅按钮熔合（黄背景，右侧）
- 输入 `border-right: none` + 按钮 `border-radius: 0 4px 4px 0`

### 页脚
- 背景: `#0A0A0A`
- 4 列网格: 品牌（带 logo 标记）+ 3 个链接列
- 列标题: `#FFE600`，大写，12px，letter-spacing 0.1em
- 链接: `rgba(255,255,255,0.55)`，悬停 → 白色
- 分隔: `1px solid rgba(255,255,255,0.15)`（**不是** 3px — 页脚要安静）

### 箭头惯例
新粗野主义用箭头作为通用「跟这条链接 / 展开 / 前往」信号:
- 外链: `↗`（斜向右上）
- 站内导航: `→`（向右）
- 展开/更多: `↓`
- 返回: `←`
- 绝不用 chevron（`>`） — 太弱。始终用粗方向箭头。

### 输入框
```css
.input {
  border: 3px solid #0A0A0A;
  border-radius: 4px;
  background: #FFFFFF;
  padding: 12px 16px;
  font-family: [same as body];
  font-size: 15px;
  font-weight: 500;
  outline: none;
}
.input:focus {
  box-shadow: 4px 4px 0 #0A0A0A;
}
/* 错误状态: */
.input.error {
  border-color: #FF3EA5;
  box-shadow: 4px 4px 0 #FF3EA5;
}
```

### 间距系统（严格 8pt 网格）
```
4px  — 微间隙（图标到文字）
8px  — 紧间距（徽章内边距、小间隙）
12px — 便当网格间距
16px — 组件内部间距
24px — 相关组件之间
32px — 区块次级间距
48px — 区块内边距（移动）
64px — 区块内边距（桌面）
96px — 主区块分隔
```
绝不用奇数间距（5px、7px、11px 等）。每个尺寸都能被 4 整除。

### 响应式行为
- 移动: hero 单列堆叠，hero 右块隐藏，导航链接隐藏，功能条 2 列 → 1 列
- 便当网格: 3 列 → 2 列 → 1 列。单列时宽/高卡片失去 span 覆盖
- 数据: 4 列 → 2 列 → 1 列
- 字号全程用 `clamp()` — 展示文字绝不用写死像素
- 内边距缩放: 桌面 64px → 平板 40px → 移动 20px
- 触控设备禁用所有悬停效果（`:hover` 仅在指针设备激活）

### 不要这样做
- 结构元素的 `border-radius` 绝不要大于 4px（8px+ = 新粗野主义开始死亡）
- 绝不要带 blur 值的 `box-shadow`（例如 `0 4px 12px rgba(0,0,0,0.1)` 禁止）
- 绝不要把渐变当主背景（仅强调填充，不要渐变 CTA 按钮）
- 绝不要居中正文（仅 hero 标题和通栏数据区居中）
- 单页绝不要超过 3 种强调色
- 绝不要用 `#eee`、`#f0f0f0` 或低饱和蓝这类软色 — 每种颜色都必须有意图且强烈
- 绝不要破坏网格 — 列间距必须一致（便当 12px，标准布局 16px）
- 绝不要只用颜色传达状态 — 始终把颜色与形状/图标变化配对（无障碍）
