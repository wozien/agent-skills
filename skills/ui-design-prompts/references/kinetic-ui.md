# Kinetic UI

- **id:** `kinetic-ui`
- **别名:** 动能UI, 动效优先, 运动界面, 动能设计系统, 交互动效落地页
- **一句话:** 有效的动效。有生命感的交互。
- **适用:**
  - 以打磨感传递品质的 SaaS 产品落地页
  - 想展示自身能力的开发者工具与设计工具
  - 需要强第一印象的产品发布
  - 动效本身就是能力证明的作品集
  - 随用户参与而展开的交互叙事
  - 任何「手感就是对的」构成竞争优势的产品
- **避免:**
  - 动效会造成迷失的无障碍关键应用
  - 动画会干扰读数的数据密集型仪表盘
  - 动画性能成问题的低带宽环境
  - 动效与阅读争抢注意力的内容型编辑站点
  - 面向前庭障碍用户却没有 prefers-reduced-motion 回退的产品
- **来源:** https://uidesignprompts.com/prompts/kinetic-ui

## Prompt

## 动能 UI 设计系统 — 深度规格

### 理念
动能设计是动效优先的 UI。每个会动的元素都有功能理由：引导注意、确认交互、传达状态，或按正确顺序揭示信息。动效不是装饰 — 它是沟通。

原则借自迪士尼「动画十二原则」并用于界面：动作前的预期、动作后的跟随、用挤压拉伸传达重量、用调度引导注意。以克制方式用于 SaaS 产品 UI 时，这些原则会产生「手感就是对的」的感觉，把 Stripe、Linear 和 Framer 与竞品区分开。

**动能动效层级：**
1. **微交互** — 最小单元。按钮按下反馈、输入焦点环、复选勾选。80–150ms。
2. **状态过渡** — 元素改变状态。卡片展开、标签切换、菜单打开。150–300ms。
3. **页面编排** — 元素进入视口。交错卡片显现、标题逐词动画。300–600ms。
4. **滚动动画** — 内容响应滚动位置。进度指示、视差偏移、吸附显现。连续。
5. **场景过渡** — 整段区块切换。页面路由变化、模态遮罩。400–700ms。

每一级都比上一级更快。微交互即时干脆。场景过渡有呼吸空间。

---

### 动效原则

**缓动决定一切。** 廉价动画与高端动画的差异几乎全在缓动曲线。

```css
/* 动能 UI 的四条缓动曲线 */
--ease-out-expo:   cubic-bezier(0.16, 1, 0.3, 1);    /* 快入、极慢出。用于入场。 */
--ease-out-quart:  cubic-bezier(0.25, 1, 0.5, 1);    /* 更柔。用于悬停效果。 */
--ease-in-out:     cubic-bezier(0.4, 0, 0.2, 1);     /* 对称。用于过渡。 */
--ease-spring:     cubic-bezier(0.34, 1.56, 0.64, 1); /* 轻微过冲。用于微交互。 */
```

**永远不要用 `linear` 做 UI 动画。** 线性缓动感觉机械。始终使用缓动曲线。

**时长参考：**
```
微（按钮按下、悬停）：              80–150ms
小状态变化（开关、徽章）：          150–200ms
元素入场（卡片、模态）：            200–400ms
交错组：                            每项 300ms，交错延迟 60–80ms
滚动绑定：                          0ms（绑定滚动位置，无时长）
页面过渡：                          400–600ms
```

---

### 签名元素 1 — 动画标题（逐词入场）

英雄标题拆成单个词。每个词包在带 `overflow: hidden` 的 `span` 里。内部文字从下方滑入，带交错延迟。这会形成 Framer、Loom 和 Vercel 使用的「词语抵达」效果。

```css
.word-wrap { overflow: hidden; display: inline-block; }
.word-inner {
  display: inline-block;
  transform: translateY(100%);
  opacity: 0;
  animation: wordUp 0.65s cubic-bezier(0.16, 1, 0.3, 1) forwards;
}
/* 通过 nth-child 或内联 style 延迟做交错 */
.word:nth-child(1) .word-inner { animation-delay: 0.1s; }
.word:nth-child(2) .word-inner { animation-delay: 0.19s; }
.word:nth-child(3) .word-inner { animation-delay: 0.28s; }
.word:nth-child(4) .word-inner { animation-delay: 0.37s; }
.word:nth-child(5) .word-inner { animation-delay: 0.46s; }

@keyframes wordUp {
  to { transform: translateY(0); opacity: 1; }
}
```

**JavaScript 做法（更灵活）：**
```javascript
function animateHeadline(el) {
  const words = el.textContent.split(' ');
  el.innerHTML = words.map((w, i) =>
    `<span class="word-wrap" style="display:inline-block;overflow:hidden;margin-right:0.25em">
      <span class="word-inner" style="display:inline-block;animation-delay:${0.1 + i * 0.09}s">${w}</span>
    </span>`
  ).join('');
}
```

---

### 签名元素 2 — 滚动触发显现

元素进入视口时用 IntersectionObserver 做动画。每个元素从不可见开始，被观察到时变换到自然位置。

```javascript
const observer = new IntersectionObserver((entries) => {
  entries.forEach(entry => {
    if (entry.isIntersecting) {
      entry.target.classList.add('in-view');
      observer.unobserve(entry.target); // 只执行一次
    }
  });
}, { threshold: 0.15, rootMargin: '0px 0px -40px 0px' });

document.querySelectorAll('[data-reveal]').forEach(el => observer.observe(el));
```

**显现变体（通过 data 属性应用）：**
```css
/* 上滑（默认） */
[data-reveal] { opacity: 0; transform: translateY(24px); transition: opacity 0.55s var(--ease-out-expo), transform 0.55s var(--ease-out-expo); }
[data-reveal].in-view { opacity: 1; transform: translateY(0); }

/* 从左滑入 */
[data-reveal="left"] { opacity: 0; transform: translateX(-24px); }
[data-reveal="left"].in-view { opacity: 1; transform: translateX(0); }

/* 缩放入场 */
[data-reveal="scale"] { opacity: 0; transform: scale(0.94); }
[data-reveal="scale"].in-view { opacity: 1; transform: scale(1); }

/* 交错组 — 用序号延迟 */
[data-reveal-group] [data-reveal]:nth-child(1) { transition-delay: 0s; }
[data-reveal-group] [data-reveal]:nth-child(2) { transition-delay: 0.08s; }
[data-reveal-group] [data-reveal]:nth-child(3) { transition-delay: 0.16s; }
[data-reveal-group] [data-reveal]:nth-child(4) { transition-delay: 0.24s; }
```

---

### 签名元素 3 — 形变悬停按钮

悬停时物理扩张的按钮 — 标签右移，箭头图标从左侧滑入，背景以动画渐变扫过填充。这是 Linear 和 Arc 使用的动能按钮处理。

```css
.kinetic-btn {
  position: relative; overflow: hidden;
  display: inline-flex; align-items: center; gap: 0;
  padding: 12px 20px; border-radius: 10px;
  background: #F97316; color: #fff;
  font-weight: 600; font-size: 14px;
  transition: padding 250ms cubic-bezier(0.25,1,0.5,1), gap 250ms cubic-bezier(0.25,1,0.5,1), box-shadow 250ms ease;
  border: none; cursor: pointer;
}
.kinetic-btn::before {
  content: ''; position: absolute; inset: 0;
  background: linear-gradient(90deg, rgba(255,255,255,0) 0%, rgba(255,255,255,0.12) 50%, rgba(255,255,255,0) 100%);
  transform: translateX(-100%);
  transition: transform 0s;
}
.kinetic-btn:hover {
  padding-right: 14px; gap: 8px;
  box-shadow: 0 0 0 1px rgba(249,115,22,0.4), 0 8px 32px rgba(249,115,22,0.35);
}
.kinetic-btn:hover::before {
  transform: translateX(100%);
  transition: transform 550ms cubic-bezier(0.4,0,0.2,1);
}
.btn-arrow {
  width: 0; overflow: hidden; opacity: 0;
  transition: width 250ms cubic-bezier(0.25,1,0.5,1), opacity 200ms ease;
}
.kinetic-btn:hover .btn-arrow { width: 16px; opacity: 1; }
```

---

### 签名元素 4 — 浮动 UI 元素

卡片与元素用 CSS `animation: float` 轻微浮动。运动缓慢（4–6s）、柔和（垂直行程 6–12px）。多个元素用不同时长与延迟，异步运动，形成有机感。

```css
@keyframes float {
  0%, 100% { transform: translateY(0px) rotate(0deg); }
  33% { transform: translateY(-8px) rotate(0.5deg); }
  66% { transform: translateY(-4px) rotate(-0.3deg); }
}
@keyframes floatSlow {
  0%, 100% { transform: translateY(0px); }
  50% { transform: translateY(-12px); }
}

.float-1 { animation: float 5s ease-in-out infinite; }
.float-2 { animation: float 4.2s ease-in-out infinite 0.8s; }
.float-3 { animation: floatSlow 6.5s ease-in-out infinite 1.5s; }
```

---

### 签名元素 5 — 滚动进度指示

页面顶部（或左缘）的细线随用户滚动填充。绑定 `window.scrollY`，而不是 `transition` — 即时响应，无滞后。

```javascript
const bar = document.getElementById('scroll-bar');
window.addEventListener('scroll', () => {
  const pct = window.scrollY / (document.body.scrollHeight - window.innerHeight);
  bar.style.width = `${Math.min(pct * 100, 100)}%`;
}, { passive: true });
```

```css
#scroll-bar {
  position: fixed; top: 0; left: 0; height: 2px; z-index: 999;
  background: linear-gradient(90deg, #F97316, #06B6D4);
  width: 0%; transition: none; /* 无过渡 — 精确镜像滚动 */
}
```

---

### 签名元素 6 — 交错卡片网格

功能卡片以交错序列进入视野，每张比上一张略延迟。效果像卡片被「发」到屏幕上。

```css
.card-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 16px; }
.feature-card {
  border: 1px solid rgba(255,255,255,0.08); border-radius: 14px;
  padding: 24px; background: #111113;
  opacity: 0; transform: translateY(20px) scale(0.98);
  transition: opacity 0.5s var(--ease-out-expo), transform 0.5s var(--ease-out-expo),
              border-color 200ms ease, box-shadow 200ms ease;
}
.feature-card.in-view { opacity: 1; transform: translateY(0) scale(1); }
.feature-card:nth-child(1) { transition-delay: 0s; }
.feature-card:nth-child(2) { transition-delay: 0.07s; }
.feature-card:nth-child(3) { transition-delay: 0.14s; }
.feature-card:hover {
  border-color: rgba(249,115,22,0.35);
  box-shadow: 0 0 0 1px rgba(249,115,22,0.15), 0 8px 32px rgba(249,115,22,0.12);
}
```

---

### 导航

粘性导航，模糊背景随滚动更不透明。Logo 左、链接中、CTA 右。页面最顶端跑一条细渐变进度条。

```css
nav { position: sticky; top: 0; z-index: 100; padding: 0 32px; height: 60px; display: flex; align-items: center; justify-content: space-between; transition: background 300ms ease, border-color 300ms ease; }
nav.scrolled { background: rgba(9,9,11,0.88); border-bottom: 1px solid rgba(255,255,255,0.08); backdrop-filter: blur(16px); }
```

---

### 色彩系统

```
背景：            #09090B  — 近黑，底色
表面：            #111113  — 卡片、抬升面板
表面 2：          #18181B  — 嵌套元素、悬停状态
默认边框：        rgba(255,255,255,0.08)
悬停边框：        rgba(249,115,22,0.35)  — 悬停时的橙色调
主文字：          #FAFAFA
次级文字：        #A1A1AA  — zinc-400；深色背景上可读，不发灰
弱化文字：        #71717A  — 说明、标签、时间戳（原 text2）

橙：              #F97316  — 主强调、CTA、激活态、光晕源
浅橙：            #FB923C  — 深色上的文字更浅（orange-400）
橙淡彩：          rgba(249,115,22,0.15)  — 背景、标签
橙光晕：          rgba(249,115,22,0.4)   — 按钮阴影色
青：              #06B6D4  — 次强调，仅用于数据图表
绿：              #10B981  — 成功态、微交互确认
琥珀：            #FBBF24  — 进度条与滚动条的渐变端点
```

**色彩规则：**
- 橙（`#F97316`）是唯一交互强调色。不要紫色按钮，不要蓝色 CTA。
- 次级文字（`#A1A1AA`）相对 `#09090B` 对比度 4.6:1 — 通过 WCAG AA 全部字号。深色背景正文永远不要低于此。
- 弱化文字（`#71717A`）是 3.5:1 — 可用于标签、大写与大号元数据，不可用于正文段落。
- 进度条与滚动指示渐变用橙 → 琥珀（`#F97316 → #FBBF24`）而非青绿配对，保持暖色内聚。
- 状态色（绿/琥珀/红）只出现在日志输出、警示指示与状态徽章。绝不进入结构 UI。

---

### 字体

```
标题字体：       'Inter', system-ui  — 展示用字重 800–900
正文字体：       'Inter', system-ui  — 字重 300–400
等宽：           'JetBrains Mono'    — 用于代码样例、指标

H1:   clamp(3rem, 6vw, 5.5rem) / 字重 800 / 行高 1.05 / 字距 -0.04em
H2:   clamp(1.75rem, 3vw, 2.5rem) / 字重 700 / 字距 -0.03em
正文： 15–16px / 字重 300–400 / 颜色 #71717A / 行高 1.72
标签： 11px / 字重 700 / 大写 / 字距 0.1em / 橙色
```

标题动画要求每个词单独包裹 — 见签名元素 1。800 字重标题与 300 字重正文的对比，制造让动能入场更戏剧的视觉张力。

---

### 微交互库

**开关：**
```css
.toggle { width: 44px; height: 24px; border-radius: 999px; background: #71717A; position: relative; cursor: pointer; transition: background 200ms ease; }
.toggle.on { background: #F97316; }
.toggle-thumb { width: 18px; height: 18px; border-radius: 50%; background: #fff; position: absolute; top: 3px; left: 3px; transition: transform 220ms cubic-bezier(0.34,1.56,0.64,1), box-shadow 200ms ease; box-shadow: 0 1px 4px rgba(0,0,0,0.3); }
.toggle.on .toggle-thumb { transform: translateX(20px); }
```

**带勾选描边的复选框：**
```css
.checkbox { width: 18px; height: 18px; border-radius: 5px; border: 1.5px solid #71717A; display: flex; align-items: center; justify-content: center; transition: background 150ms ease, border-color 150ms ease; }
.checkbox.checked { background: #F97316; border-color: #F97316; }
.checkbox svg { stroke-dasharray: 14; stroke-dashoffset: 14; transition: stroke-dashoffset 200ms cubic-bezier(0.16,1,0.3,1) 50ms; }
.checkbox.checked svg { stroke-dashoffset: 0; }
```

**输入焦点环：**
```css
.kinetic-input { transition: border-color 150ms ease, box-shadow 150ms ease; }
.kinetic-input:focus { border-color: #F97316; box-shadow: 0 0 0 3px rgba(249,115,22,0.2), 0 0 0 1px #F97316; outline: none; }
```

---

### 签名元素 7 — 带空间方向的页面过渡

用户在路由间导航时，离场页沿行进方向滑出，入场页从对侧滑入。这建立空间心智模型：页面存在于水平空间中，导航在其中移动。

```javascript
function transitionTo(outEl, inEl, direction = 1) {
  // direction: 1 = 前进（从左到右），-1 = 后退
  outEl.style.transform = `translateX(${direction * -32}px)`;
  outEl.style.opacity = '0';
  outEl.style.transition = 'transform 420ms cubic-bezier(0.25,1,0.5,1), opacity 320ms ease';

  inEl.style.transform = `translateX(${direction * 32}px)`;
  inEl.style.opacity = '0';
  inEl.style.transition = 'none';
  inEl.offsetHeight; // 强制回流

  inEl.style.transition = 'transform 420ms cubic-bezier(0.25,1,0.5,1), opacity 320ms ease';
  inEl.style.transform = 'translateX(0)';
  inEl.style.opacity = '1';
}
```

地址栏更新为新路由路径。标签指示器用强调色底边显示当前路由。过渡时长 `420ms`，缓动 `cubic-bezier(0.25,1,0.5,1)` — 快到感觉即时，慢到能传达空间变化。

---

### 签名元素 8 — 交错编排模式

三种不同情境的交错模式：

**从左滑入（60ms 交错）：** 项目水平入场。用于列表项、日志行与数据流。左向原点暗示项目从画外抵达。
```css
.item { opacity: 0; transform: translateX(-12px); }
.item.in { opacity: 1; transform: translateX(0); }
/* 延迟：80ms + (index * 60ms) */
```

**自上而下瀑布（80ms 交错）：** 项目垂直落入位置。用于导航菜单、下拉选项与卡片网格。自上而下的序列读作顺序与优先级。
```css
.item { opacity: 0; transform: translateY(12px); }
.item.in { opacity: 1; transform: translateY(0); }
/* 延迟：80ms + (index * 80ms) */
```

**缩放入场（100ms 交错）：** 项目从 90% 长到 100%。用于网格卡片、画廊项与定价方案等彼此对等的项目。缩放入场传达「抵达」而非「落下」或「滑入」。
```css
.item { opacity: 0; transform: scale(0.9); }
.item.in { opacity: 1; transform: scale(1); }
/* 延迟：80ms + (index * 100ms) — 最慢的交错，最从容 */
```

三种都用同一 `cubic-bezier(0.16,1,0.3,1)` 缓动。交错延迟决定节奏；缓动决定手感。

---

### 签名元素 9 — 显现时打字机文字

评价与引语进入视口时逐字打出。这是功能性动能手法：放慢读者、迫使他们在文字成形时阅读，并制造真正的注意。与淡入不同，打字机效果无法扫读。

```javascript
function typeWrite(element, text, speed = 18) {
  element.textContent = '';
  let i = 0;
  const interval = setInterval(() => {
    if (i < text.length) { element.textContent += text[i]; i++; }
    else clearInterval(interval);
  }, speed);
}

// 通过 IntersectionObserver 触发
const obs = new IntersectionObserver(entries => {
  entries.forEach(e => {
    if (e.isIntersecting) {
      const text  = e.target.dataset.typewriter;
      const quote = e.target.querySelector('.quote-target');
      if (text && quote) setTimeout(() => typeWrite(quote, text, 18), 200);
      obs.unobserve(e.target);
    }
  });
}, { threshold: 0.3 });
```

速度：每字符 `18ms` 是甜点 — 快到不必等待就能读，慢到能被识别为「打字」。短句降到 `10ms`，很长引语升到 `28ms`。

始终尊重 `prefers-reduced-motion`，回退为即时显示文字：
```javascript
const speed = window.matchMedia('(prefers-reduced-motion: reduce)').matches ? 0 : 18;
```

---

每个动画都必须尊重系统偏好。这不是可选项。

```css
@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after {
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
    transition-duration: 0.01ms !important;
  }
  .word-inner { transform: translateY(0); opacity: 1; }
  [data-reveal] { opacity: 1; transform: none; }
  .float-1, .float-2, .float-3 { animation: none; }
}
```

---

### 不要做什么
- ✗ 永远不要用 `linear` 缓动做 UI 动画 — 始终使用缓动曲线
- ✗ 永远不要同时动画超过 3 个元素 — 交错它们
- ✗ 永远不要让装饰动画循环快于 3s — 会分心
- ✗ 永远不要用 `animation: all` 或 `transition: all` — 指定确切属性
- ✗ 永远不要动画 `width`、`height` 或 `margin` — 性能上只动画 `transform` 与 `opacity`
- ✗ 永远不要忘记 `prefers-reduced-motion` — 让所有动画可选
- ✗ 永远不要在一次交互响应中动画用户并未交互的元素
- ✗ 永远不要对大于 40px 的东西用弹跳缓动（`cubic-bezier(0.34,1.56,0.64,1)`）— 会显得卡通
- ✗ 永远不要在同一元素上叠加多种滚动绑定动画 — 只选一种
- ✗ 永远不要让悬停动画长于 300ms — 会显得迟钝
- ✗ 永远不要每种模式都用相同交错延迟 — 让延迟匹配内容节奏
- ✗ 永远不要打字机超过 200 个字符 — 看起来会乏味
- ✗ 永远不要在方向性页面过渡中设错方向 — 前进始终左出/右入，后退右出/左入

### 待替换数据（占位映射）
- `[PRODUCT_NAME]` — 显示在导航、英雄区、页脚
- `[TAGLINE]` — 英雄标题，拆成词做动画
- `[HERO_SUB]` — 1–2 句，标题完成后动画进入
- `[FEATURES]` — 6 项：图标 emoji、标题、描述，用于交错卡片网格
- `[MICRO_DEMOS]` — 交互元素：开关、复选框、输入、按钮变体
- `[SCROLL_SECTIONS]` — 随滚动渐进显现的内容
- `[CTA_TEXT]` — 形变按钮标签
- `[METRICS]` — 3–4 个带标签的数字，用于数据行
