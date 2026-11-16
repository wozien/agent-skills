# Developer Portfolio

- **id:** `developer-portfolio`
- **别名:** 开发者作品集, 程序员简历站, 工程师作品集, 暗色作品集, 技术作品集
- **一句话:** 暗色。克制。为被录用而建。
- **适用:**
  - 正在寻找下一份工作的软件工程师
  - 希望同时展示项目与经历的全栈开发者
  - 用暗色高级审美建立可信度的自由职业者
  - 希望作品集超出当前级别观感的初级工程师
  - 申请产品公司和创业公司的开发者
  - 任何希望作品集读起来像产品、而不是 Word 文档的人
- **避免:**
  - 想展示视觉/品牌作品的设计师——改用浅色画廊布局
  - 代码能力不是主线的非技术创意从业者
  - 需要正式、文档式 CV 格式的企业顾问
  - 目标雇主期望传统一页简历布局的人
- **来源:** https://uidesignprompts.com/prompts/developer-portfolio

## Prompt

## 开发者作品集设计系统

### 概念与气质
暗色、编辑感、安静自信。这是给软件工程师的作品集——应像精心打造的产品，而不是把简历扔进网页。布局传达技术品味：分屏构图、克制用色，以及两种状态（闪屏 → 作品集）构成一段微型叙事。访客先落在姓名上，再进入作品集。

参考感受：终端交叉高级 SaaS 落地页。深海军蓝背景，一种青色强调色节制使用（链接、激活标签、激活页签），灰白正文，零装饰噪音。克制即自信。

### 布局架构 — 两种状态

**状态 1 — 闪屏（全视口，自动过渡）**
- 全视口深海军蓝覆盖层
- 开发者姓名以巨大粗体居中
- 姓名通过缩放动画出现：从约 40px 开始，1.2s 内增长到 80–120px（ease-out cubic）
- 动画完成后（总计 ≈1.5s），闪屏淡出，揭示主布局
- 闪屏无其他内容——只有姓名，在暗色上

```css
/* 闪屏动画 */
@keyframes nameReveal {
  0%   { font-size: 2.5rem; opacity: 0; letter-spacing: -0.02em; }
  30%  { opacity: 1; }
  100% { font-size: clamp(5rem, 12vw, 9rem); letter-spacing: -0.04em; }
}

.splash-name {
  font-family: 'Inter', sans-serif;
  font-weight: 800;
  color: #E2E8F0;
  animation: nameReveal 1.2s cubic-bezier(0.22, 1, 0.36, 1) forwards;
  text-align: center;
}

.splash {
  position: fixed; inset: 0; z-index: 999;
  background: #0F172A;
  display: flex; align-items: center; justify-content: center;
  animation: splashFade 0.5s ease-in 1.5s forwards;
  opacity: 1;
}

@keyframes splashFade {
  to { opacity: 0; pointer-events: none; }
}
```

**状态 2 — 主作品集布局（闪屏后揭示）**
```
┌────────────────────────────────────────────────────────┐
│  导航（可选，极简 — 仅姓名/logo）                       │
├──────────────────────┬─────────────────────────────────┤
│                      │                                 │
│   左栏                │   右栏                          │
│   （粘性，约 40%）     │   （可滚动，约 60%）             │
│                      │                                 │
│   • 姓名              │   [ 经历 ] [ 项目 ]             │
│   • 角色 + 地点       │                                 │
│   • 简介段落          │   时间线条目 或                 │
│   • 技能标签          │   项目卡片                      │
│   • 社交链接          │                                 │
│   • 状态徽章          │                                 │
│   • 邮箱 + 电话       │                                 │
│                      │                                 │
└──────────────────────┴─────────────────────────────────┘
```

左栏使用 `position: sticky; top: 0; height: 100vh`，永不滚动。右栏是滚动上下文。这是核心布局创新——招聘官浏览作品时，简介始终可见。

### 色彩系统
- 页面背景：`#0F172A` — 深海军蓝，一切的基底
- 左栏背景：`#0F172A` — 与页面相同，栏与背景之间无可见边框
- 右栏背景：`#0F172A` — 相同，无缝
- 卡片 / 条目悬停背景：`#1E2A3A` — 略浅海军蓝，仅悬停出现
- 强调青：`#2DD4BF` — 用于：角色高亮文字、激活页签下划线、链接悬停、标签文字、状态点、雇主名称链接
- 白（标题）：`#E2E8F0` — 灰白，永不用纯白
- 正文：`#94A3B8` — slate-400，用于简介和描述
- 标签背景：`rgba(45, 212, 191, 0.12)` — 极暗青色着色
- 标签文字：`#2DD4BF` — 完整青色
- 边框：`#1E293B` — 几乎看不见，仅用于页签分割
- 社交图标默认：`#64748B` — slate-500
- 社交图标悬停：`#E2E8F0` — 悬停变亮

**单一规则：青色一次只触碰一件事。** 不要在同一视觉块中同时使用青色标题、青色标签和青色链接。把它当作焦点。

### 字体
使用 Inter 或类似几何无衬线——干净、技术、现代。

```
Developer name (splash):   clamp(5rem, 12vw, 9rem) / weight 800 / #E2E8F0
Developer name (left panel): 1.75rem–2rem / weight 700 / #E2E8F0
Role tagline:              1rem / weight 500 / #2DD4BF (cyan)
Location/status:           0.875rem / weight 400 / #94A3B8
Bio body:                  0.9375rem / weight 400 / #94A3B8 / line-height 1.7
Section heading:           0.75rem / weight 700 / #94A3B8 / letter-spacing 0.1em / UPPERCASE
Job title (entry):         1rem / weight 600 / #E2E8F0
Company name (link):       1rem / weight 600 / #2DD4BF
Date range:                0.8125rem / weight 400 / #64748B
Entry description:         0.875rem / weight 400 / #94A3B8 / line-height 1.65
Tag text:                  0.75rem / weight 600 / #2DD4BF / letter-spacing 0.025em
```

### 左栏 — 粘性简介
左栏静止。招聘官判断「这个人值不值得联系」所需的一切都在这里。

组件（从上到下）：
1. **开发者姓名** — 突出，`#E2E8F0`，weight 700
2. **角色行** — 例如「Full-Stack Software Engineer」，`#2DD4BF`
3. **地点行** — 「Karachi, Pakistan」，`#94A3B8`
4. **简介段落** — 最多 2–4 句，诚实语气，`#94A3B8`，line-height 1.7
5. **技能标签云** — 胶囊标签，`rgba(45,212,191,0.12)` 背景和 `#2DD4BF` 文字
6. **状态徽章** —「● Available for Work」带脉冲绿点（或「● Open to Opportunities」）
7. **社交图标行** — GitHub、LinkedIn、YouTube、Twitter、Instagram — 使用六边形或圆形图标容器，默认 `#64748B`，悬停 `#E2E8F0`
8. **联系行** — 邮箱 + 电话，底部小号 `#94A3B8`

```css
/* 技能标签 */
.skill-tag {
  display: inline-flex;
  align-items: center;
  padding: 4px 12px;
  border-radius: 999px;
  font-size: 0.75rem;
  font-weight: 600;
  letter-spacing: 0.025em;
  background: rgba(45, 212, 191, 0.12);
  color: #2DD4BF;
}

/* 状态徽章 */
.status-badge {
  display: inline-flex; align-items: center; gap: 8px;
  font-size: 0.8125rem; font-weight: 500; color: #94A3B8;
}
.status-dot {
  width: 8px; height: 8px; border-radius: 50%;
  background: #22C55E;
  animation: pulse 2s ease-in-out infinite;
}
@keyframes pulse {
  0%, 100% { opacity: 1; }
  50% { opacity: 0.4; }
}

/* 社交图标容器（六边形裁切或圆形） */
.social-icon {
  width: 40px; height: 40px;
  border: 1.5px solid #1E293B;
  border-radius: 50%;
  display: flex; align-items: center; justify-content: center;
  color: #64748B;
  transition: color 200ms, border-color 200ms;
}
.social-icon:hover { color: #E2E8F0; border-color: #475569; }
```

### 右栏 — 页签内容
两个页签：**经历** 和 **项目**。同一时间只显示一个。

**页签条：**
- 简单文字页签，无胶囊或盒子
- 激活页签：`#E2E8F0` 文字 + `2px #2DD4BF` 底边
- 未激活页签：`#64748B` 文字，无边框
- 页签条有 `1px solid #1E293B` 底边（非常微妙）
- 页签无背景——浮在分割线之上

```css
.tab-btn {
  padding: 12px 0;
  font-size: 0.9375rem; font-weight: 500;
  color: #64748B; background: none; border: none; cursor: pointer;
  border-bottom: 2px solid transparent;
  transition: color 150ms, border-color 150ms;
}
.tab-btn.active {
  color: #E2E8F0;
  border-bottom-color: #2DD4BF;
}
.tab-btn:hover:not(.active) { color: #94A3B8; }
```

### 经历条目（时间线）
每条是日期 + 职位 + 雇主 + 描述 + 标签栈。

每条布局：
```
[日期区间]            [职位 @ 雇主链接]
                    石板色描述文字
                    [标签] [标签] [标签]
```

桌面：两列，日期在左（约 25% 宽），内容在右（约 75%）。移动端：垂直堆叠，日期在标题上方。

悬停：整张条目卡获得非常微妙的 `#1E2A3A` 背景（8px border-radius），平滑过渡轻微扩大。无边框、无阴影——只有暗高亮。

```css
.exp-entry {
  display: grid;
  grid-template-columns: 1fr 2fr;
  gap: 16px 24px;
  padding: 20px;
  border-radius: 8px;
  transition: background 150ms;
}
.exp-entry:hover { background: #1E2A3A; }

.exp-date {
  font-size: 0.8125rem; font-weight: 500;
  color: #64748B; padding-top: 4px;
  text-transform: uppercase; letter-spacing: 0.05em;
}

.exp-title { font-size: 1rem; font-weight: 600; color: #E2E8F0; }
.exp-company { color: #2DD4BF; text-decoration: none; }
.exp-company:hover { text-decoration: underline; }
.exp-desc { font-size: 0.875rem; color: #94A3B8; line-height: 1.65; margin-top: 8px; }
.exp-tags { display: flex; flex-wrap: wrap; gap: 8px; margin-top: 12px; }
```

### 项目卡片
每张项目卡展示名称、「New 🔥」或「Client Work 💼」徽章、元数据（年龄或访客数 + 星级）、缩略图、描述和链接。

```
┌─────────────────────────────────────────┐  [缩略图]
│  项目名称  [New 🔥]                      │
│  ⏱ 3 天前                               │
│                                         │
│  项目做什么的描述。                       │
│  2–3 句。                               │
│                                         │
│  👁 Live Preview    🐙 GitHub Link       │
└─────────────────────────────────────────┘
```

卡片容器：`background: #0F172A`（静止时与页面相同，悬停 `#1E2A3A`），`border: 1px solid #1E293B`，`border-radius: 8px`，`padding: 20px`。缩略图：80×60px，border-radius 4px，位于右上。

```css
.project-card {
  display: grid;
  grid-template-columns: 1fr auto;
  gap: 12px 16px;
  padding: 20px;
  border: 1px solid #1E293B;
  border-radius: 8px;
  transition: background 150ms, border-color 150ms;
}
.project-card:hover {
  background: #1E2A3A;
  border-color: #2D3B4E;
}

.project-name { font-size: 1rem; font-weight: 600; color: #E2E8F0; }
.project-badge {
  font-size: 0.7rem; font-weight: 600; padding: 2px 8px;
  border-radius: 999px; background: rgba(45,212,191,0.15);
  color: #2DD4BF; display: inline-flex; align-items: center; gap: 4px;
}

.project-meta { font-size: 0.8rem; color: #64748B; margin-top: 6px; }
.project-desc { font-size: 0.875rem; color: #94A3B8; line-height: 1.6; margin-top: 10px; }

.project-link {
  display: inline-flex; align-items: center; gap: 6px;
  font-size: 0.8125rem; font-weight: 500;
  color: #2DD4BF; text-decoration: none;
  transition: color 150ms;
}
.project-link:hover { color: #5EEAD4; }

.project-thumbnail {
  width: 80px; height: 60px;
  border-radius: 4px; object-fit: cover;
  border: 1px solid #1E293B;
  grid-row: 1 / 3;
}
```

### 响应式行为
**桌面（≥768px）：** 左栏粘性，右栏滚动。经历两列网格。
**移动端（<768px）：** 单列堆叠。左栏不再粘性——变成普通顶部区块。右栏跟在下方。页签条变全宽。经历条目日期叠在内容上方。

```css
.portfolio-layout {
  display: flex;
  min-height: 100vh;
}
.left-panel {
  width: 40%;
  position: sticky;
  top: 0;
  height: 100vh;
  overflow-y: auto;
  padding: 64px 40px;
}
.right-panel {
  width: 60%;
  padding: 64px 48px;
  overflow-y: auto;
}

@media (max-width: 768px) {
  .portfolio-layout { flex-direction: column; }
  .left-panel, .right-panel {
    width: 100%;
    position: static;
    height: auto;
    padding: 40px 24px;
  }
  .exp-entry { grid-template-columns: 1fr; }
}
```

### 切勿做
- ✗ 永远不要用浅色或白色背景——此风格活在深海军蓝上
- ✗ 永远不要用超过一种强调色——青色是唯一强调
- ✗ 永远不要加装饰插画、色块或背景图案
- ✗ 永远不要让左栏在桌面随页面滚动
- ✗ 永远不要用带颜色的阴影——暗色 UI 用无阴影扁平卡片
- ✗ 永远不要过度动画——只有闪屏姓名放大，其余都是 150ms 过渡
- ✗ 永远不要加英雄图或头像照片——此布局不用
- ✗ 永远不要加页脚——左栏联系行就是页脚
- ✗ 永远不要超过两个页签——复杂度会毁掉布局

### 待替换数据（占位映射）
为真实用户生成此布局时，替换：
- `[DEVELOPER NAME]` — 闪屏和左栏显示的全名
- `[ROLE]` — 例如「Full-Stack Software Engineer」或「Frontend Developer」
- `[LOCATION]` — 例如「Karachi, Pakistan」
- `[BIO]` — 2–4 句诚实第一人称
- `[SKILLS]` — 逗号分隔：Python, JavaScript, React, Node.js, etc.
- `[STATUS]` — 「Available for Work」或「Open to Opportunities」或「Currently @ [Company]」
- `[EXPERIENCE_ENTRIES]` — 每条含：日期区间、职位、公司名、公司 URL、2–3 条要点描述、技能标签
- `[PROJECT_ENTRIES]` — 每条含：名称、徽章类型、年龄或统计、缩略图、描述、链接
- `[EMAIL]`、`[PHONE]` — 左栏底部联系方式
- `[SOCIAL_LINKS]` — GitHub、LinkedIn、YouTube、Twitter、Instagram URLs
