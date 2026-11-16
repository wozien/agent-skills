# Claymorphism / 3D Soft UI

- **id:** `claymorphism`
- **别名:** 黏土拟态, 3D 软 UI, 黏土风, Claymorphism, 充气软界面
- **一句话:** 充气感。好玩。物理上令人满足。
- **适用:**
  - 面向年轻用户的消费级应用
  - 教育与学习平台
  - 健康与心理健康产品
  - 希望感觉亲切的无代码工具
  - 游戏化产品和习惯追踪器
  - 移动优先的效率应用
  - 面向儿童和家庭的产品
- **避免:**
  - 企业或专业 B2B 工具
  - 需要传达严肃感的金融产品
  - 面向开发者的工具
  - 密集仪表盘或分析界面
  - 权威比亲和更重要的产品
- **来源:** https://uidesignprompts.com/prompts/claymorphism

## Prompt

## 黏土拟态 / 3D 软 UI 设计系统

### 核心方向
创造感觉像用柔软材料物理塑形的界面——充气表面、厚实的彩色底部阴影、圆润几何，以及模拟真实世界触觉深度的按压动画。每个按钮都像能按下去。每张卡片都像被塑出来。界面情绪温暖、交互有奖励感，视觉好玩但不丢失产品清晰度。

参考感受：Duolingo 的大号可按按钮、高端玩具包装、柔软硅胶硬件。不是科幻 UI，不是扁平 Dribbble 渐变——是漫射日光下的哑光软黏土。

### 色彩系统 — 含完整阴影配对
每种黏土色必须有配对阴影色。阴影是物体更深、更饱和的版本——永不用中性灰。

**背景色调：**
- 柔薰衣草：`#F5F3FF` — 主页面背景
- 柔蓝白：`#EFF6FF`
- 柔绿白：`#F0FDF4`
- 柔桃色：`#FFF7ED`

**黏土强调色 + 精确阴影配对：**
| 物体 | 物体 Hex | 阴影 | 阴影 Hex |
|---|---|---|---|
| Clay Blue | `#60A5FA` | Deep Blue | `#1D4ED8` |
| Clay Green | `#34D399` | Deep Green | `#059669` |
| Clay Yellow | `#FCD34D` | Deep Amber | `#B45309` |
| Clay Coral | `#FB7185` | Deep Rose | `#BE123C` |
| Clay Purple | `#A78BFA` | Deep Violet | `#6D28D9` |
| Clay Teal | `#2DD4BF` | Deep Teal | `#0F766E` |
| Clay Orange | `#FB923C` | Deep Orange | `#C2410C` |
| White/Light | `#FFFFFF` | Mid Gray | `#CBD5E1` |

**文字色（永不用纯黑）：**
- 主标题：`#1E1B4B`
- 正文：`#312E81` 或 `#334155`
- 弱化：`#64748B`
- 彩色表面上：`#FFFFFF`

### 黏土阴影公式 — 最关键规则
每个抬升元素使用两层阴影：

```css
box-shadow:
  0 [depth]px 0 0 [shadow-color],      /* 实心接触阴影 — 零模糊 */
  0 [depth+6]px [blur]px rgba(0,0,0,0.12);  /* 大气纵深 */
```

**按钮静止：**
```css
box-shadow:
  0 6px 0 0 #1D4ED8,
  0 12px 20px rgba(29, 78, 216, 0.22);
```
**按钮悬停（压缩 2px）：**
```css
transform: translateY(2px);
box-shadow:
  0 4px 0 0 #1D4ED8,
  0 8px 16px rgba(29, 78, 216, 0.20);
```
**按钮激活/按下（完全按下）：**
```css
transform: translateY(6px);
box-shadow:
  0 0px 0 0 #1D4ED8,
  0 4px 8px rgba(29, 78, 216, 0.15);
```
**卡片静止：**
```css
box-shadow:
  0 8px 0 0 #1D4ED8,
  0 16px 32px rgba(29, 78, 216, 0.18);
```

规则 — 全部强制：
- 第一层阴影 blur-radius 必须为 `0` — 它是实心偏移，不是光晕
- 阴影色必须匹配元素的色族（见上表）
- 永远不要在彩色元素上使用灰色中性阴影
- 过渡：`100ms ease-out` — 干脆，永不飘
- 较大卡片：8–10px 深度；按钮：6px；小徽章：3–4px

### 顶光充气表面效果
每个彩色表面都要有微妙顶部高光，模拟从上方照亮的黏土：

```css
/* 径向高光 — 最适合按钮和小卡片 */
background:
  radial-gradient(
    ellipse at 50% 0%,
    rgba(255, 255, 255, 0.35) 0%,
    rgba(255, 255, 255, 0) 60%
  ),
  #60A5FA; /* 底色 */
```

**内缘高光（增加真实感 — 与阴影组合）：**
```css
box-shadow:
  inset 0 1px 0 rgba(255, 255, 255, 0.50), /* 顶部边缘 */
  0 6px 0 0 #1D4ED8,                        /* 接触 */
  0 12px 20px rgba(29, 78, 216, 0.22);       /* 大气 */
```

渐变不透明度：最高 0.25–0.40。应感觉像光线从圆面上弹开，而不是光泽塑料。

### 圆角 — 圆润系统
锐利边缘会立刻打破黏土错觉。

```
区块包裹 / 页面容器:  24px–32px
功能卡片:              20px–28px
主按钮:                14px–18px
胶囊按钮 / CTA:        999px
输入框:                12px–16px
图标容器:              16px–20px
统计 / 数字徽章:       14px–18px
进度条:                999px（始终全胶囊）
头像:                  50%（圆形）
模态框:                24px–32px
导航项（激活）:        12px–14px
```

任何可见卡片或按钮永远不要用低于 12px 的 border-radius。界面应感觉是塑出来的，不是搭出来的。

### 字体
使用一种圆润、友好的字体——不要几何无衬线或衬线。

**推荐（按顺序）：**
1. Nunito — 最温暖，全能最佳
2. Poppins — 略偏几何，仍然友好
3. Quicksand — 更软，适合标题

**层级：**
- 英雄 H1：56–72px，weight 900，`#1E1B4B`，letter-spacing -0.02em
- 区块 H2：36–48px，weight 800，`#1E1B4B`，letter-spacing -0.015em
- 卡片 H3：20–24px，weight 700，`#1E1B4B`
- 正文：16–18px，weight 500，`#312E81`，line-height 1.65
- 标签/弱化：13–14px，weight 600，`#64748B`
- 按钮文字：16–18px，weight 700，彩色上的白色

### 按钮系统 — 标志性黏土组件

**主黏土按钮：**
```css
.clay-btn {
  font-weight: 700; font-size: 17px;
  color: white; border: none; cursor: pointer;
  padding: 16px 32px; border-radius: 16px;
  background:
    radial-gradient(ellipse at 50% 0%,
      rgba(255,255,255,0.35) 0%,
      rgba(255,255,255,0) 60%),
    #60A5FA;
  box-shadow:
    inset 0 1px 0 rgba(255,255,255,0.50),
    0 6px 0 0 #1D4ED8,
    0 12px 22px rgba(29,78,216,0.24);
  transition: transform 100ms ease-out, box-shadow 100ms ease-out;
}
.clay-btn:hover {
  transform: translateY(2px);
  box-shadow:
    inset 0 1px 0 rgba(255,255,255,0.50),
    0 4px 0 0 #1D4ED8,
    0 8px 16px rgba(29,78,216,0.22);
}
.clay-btn:active {
  transform: translateY(6px);
  box-shadow:
    inset 0 1px 0 rgba(255,255,255,0.40),
    0 0px 0 0 #1D4ED8,
    0 4px 8px rgba(29,78,216,0.15);
}
```

**白色/次按钮（不是幽灵描边 — 用白色黏土表面）：**
```css
background: white;
color: #1E1B4B;
box-shadow:
  inset 0 1px 0 rgba(255,255,255,1),
  0 6px 0 0 #CBD5E1,
  0 12px 20px rgba(0,0,0,0.08);
```

永远不要用：仅描边幽灵按钮、扁平无边按钮、或只有渐变没有阴影的按钮。

### 卡片系统

**彩色黏土卡：**
```css
background:
  radial-gradient(ellipse at 50% 0%,
    rgba(255,255,255,0.30) 0%,
    rgba(255,255,255,0) 55%),
  #60A5FA;
border-radius: 24px;
padding: 28px;
box-shadow:
  inset 0 1px 0 rgba(255,255,255,0.45),
  0 8px 0 0 #1D4ED8,
  0 16px 32px rgba(29,78,216,0.18);
```

**彩色背景上的白色卡：**
```css
background: #FFFFFF;
border-radius: 24px;
padding: 28px;
box-shadow:
  inset 0 1px 0 rgba(255,255,255,1),
  0 8px 0 0 #CBD5E1,
  0 16px 32px rgba(0,0,0,0.08);
```

**轻微旋转增加玩味（仅装饰卡）：**
```css
transform: rotate(-1.5deg); /* 第一张卡 */
transform: rotate(0deg);    /* 中间卡 */
transform: rotate(1.5deg);  /* 第三张卡 */
```

### 布局规则 — 空间是强制的
黏土拟态一旦拥挤就会立刻崩坏。

- 区块内边距：上下 `80px–120px`
- 卡片间距：最少 `24px–32px`
- 最大内容宽度：`1100px`
- 每行永远不超过 3 张卡
- 英雄区：单列居中 — 英雄内容中不要网格
- 每个区块只有一个主导 CTA
- 标题到卡片间距：最少 `40px`

### 色块/形状装饰
柔软背景色块在不与内容竞争的前提下制造纵深：

```css
.blob {
  position: absolute;
  border-radius: 60% 40% 70% 30% / 50% 60% 40% 50%;
  filter: blur(48px);
  pointer-events: none;
  z-index: 0;
  opacity: 0.18–0.25;
}
```

- 每页最多用 2–4 个色块
- 颜色：仅用页面强调色的着色版
- 始终在内容后面（`z-index: 0`，内容在 `z-index: 1`）
- 尺寸：280px–520px，极低不透明度

### 图标容器系统
图标坐在黏土形状容器里——永远不要直接贴在背景上。

```css
.clay-icon {
  width: 56px; height: 56px;
  border-radius: 18px;
  display: flex; align-items: center; justify-content: center;
  font-size: 26px;
  background:
    radial-gradient(ellipse at 50% 0%,
      rgba(255,255,255,0.35) 0%,
      rgba(255,255,255,0) 60%),
    #34D399;
  box-shadow:
    inset 0 1px 0 rgba(255,255,255,0.50),
    0 4px 0 0 #059669,
    0 8px 16px rgba(5,150,105,0.20);
}
/* 彩色卡片背景上，用半透明白： */
.clay-icon.on-colored {
  background: rgba(255,255,255,0.22);
  box-shadow:
    inset 0 1px 0 rgba(255,255,255,0.50),
    0 3px 0 0 rgba(0,0,0,0.20);
}
```

### 进度 / 统计组件
此风格原生能力——游戏化住在这里。

**进度条：**
```css
.track {
  height: 14px; border-radius: 999px;
  background: rgba(0,0,0,0.08);
  box-shadow: inset 0 2px 4px rgba(0,0,0,0.10);
}
.fill {
  height: 100%; border-radius: 999px;
  background: linear-gradient(90deg, #34D399, #60A5FA);
  box-shadow: 0 2px 0 0 #059669;
}
```

**统计数字卡：**
```css
.stat-card {
  background: white; border-radius: 22px; padding: 26px;
  box-shadow: 0 6px 0 0 #CBD5E1, 0 12px 24px rgba(0,0,0,0.07);
}
.stat-num { font-size: 44px; font-weight: 900; color: #1E1B4B; letter-spacing: -0.02em; }
```

### 切勿做
- ✗ 永远不要在彩色元素上使用灰色中性阴影
- ✗ 永远不要用仅描边/幽灵按钮做主操作
- ✗ 永远不要在卡片或按钮上使用低于 12px 的 border-radius
- ✗ 永远不要让按压动画慢于 150ms
- ✗ 永远不要挤布局——大间距不可协商
- ✗ 永远不要用纯 `#000000` 文字
- ✗ 永远不要用霓虹或过饱和颜色
- ✗ 永远不要把黏土阴影直接加到文字或裸 SVG 上
- ✗ 永远不要用玻璃拟态模糊/透明——黏土是不透明实心的
- ✗ 永远不要每行堆超过 3 张功能卡

### 间距参考（8px 网格）
```
区块垂直内边距:          80px–120px
卡片内部内边距:          24px–32px
卡片之间间距:            24px–32px
按钮内边距:              16px 32px
H2 到第一张卡间距:       40px–52px
统计数字间距:            40px–56px
```
