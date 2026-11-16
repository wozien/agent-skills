# Terminal Design

- **id:** `terminal-design`
- **别名:** 终端风, 命令行美学, CRT终端, CLI落地页, 磷光绿终端
- **一句话:** 命令行审美。零装饰。纯信号。
- **适用:**
  - CLI 工具与贴近命令行的产品
  - 开发者基础设施与 DevOps 平台
  - 安全、渗透测试与黑客工具
  - 面向技术受众的开源项目落地页
  - 有强开发者个性的技术博客与文档
  - 目标用户整天活在终端里的任何产品
- **避免:**
  - 面向非技术用户的消费产品
  - 任何需要食物摄影、生活方式影像或插画的东西
  - 需要信任与温度的电商或高转化页
  - 无障碍与亲和力是首要价值的产品
  - 面向经理、高管或非工程买家的 SaaS
- **来源:** https://uidesignprompts.com/prompts/terminal-design

## Prompt

## 终端设计系统 — 深度规格

### 理念
这不是深色主题。这是终端 — 真的那种，渲染成产品 UI。每个决定都问：「真终端会这样做吗？」答案是否，就删掉。不要圆角，不要渐变，不要插画，不要图标（除非是 ASCII），除了等宽不要别的字体。回报是立刻向受众发出精英技术可信度信号的 UI。工程师觉得像家。其他人略感被震慑。这就是重点。

参考心智模型：你在设计 CLI 工具的落地页，仿佛落地页本身就是一次终端会话。访客是用户。产品用工程师唯一信任的语言对他们说话。

---

### 色彩系统 — 磷光绿色板
终端设计使用严格的两区色彩系统。永远不要混区。

```
背景区（深）：
  页面背景：        #0A0E0A  — 近黑，带一点绿调
  深表面：          #0D1210  — 导航、输入区
  卡片表面：        #111714  — 功能卡片、方案背景
  暗边框：          #1E2820  — 区块间细微分隔
  中边框：          #243029  — 卡片边框、盒绘线

前景区（磷光）：
  磷光绿：          #00FF41  — 主文字、标题、激活元素
  暗磷光：          #00C032  — 次级交互元素
  弱磷光：          #007A20  — 区块标签、变暗提示符
  终端白：          #CDD8CB  — 正文、描述、输出文字
  弱化文字：        #3A4A3C  — 占位、禁用、背景标签

状态色（通用终端惯例 — 永不偏离）：
  错误：            #FF3333  — [ERROR]、✗、失败态
  警告：            #FFD700  — [WARN]、⚠、谨慎态
  成功：            #00FF41  — [OK]、[DONE]、✓（与主色相同）
  信息：            #5BB8FF  — [INFO]、备注、提示（少用）
  光标：            #00FF41  — 仅闪烁块光标
```

磷光辉光：对标题与关键高亮文字应用 `text-shadow: 0 0 8px #00FF41, 0 0 16px rgba(0,255,65,0.3)`。只用于主元素 — 滥用会杀死效果。

---

### 字体 — 一律等宽
```
字体栈（全部作回退）：
  'JetBrains Mono', 'Fira Code', 'Source Code Pro', 'Courier New', monospace

字号阶：
  ASCII logo / 英雄艺术：  预格式，font-size 12–14px，white-space: pre
  H1（英雄标题）：         clamp(20px, 3.5vw, 42px) / 字重 700 / 磷光绿 / 辉光
  H2（区块标题）：         16px / 字重 700 / 磷光绿 / 无辉光
  正文 / 输出文字：        13–14px / 字重 400 / 终端白（#CDD8CB）
  元信息 / 弱化：          11–12px / 字重 400 / 弱化文字（#3A4A3C）
  提示符前缀：             13px / 字重 400 / user@host 用弱化（#3A4A3C），$ 用白
  命令文字：               13px / 字重 500 / 终端白
  区块标签：               10px / 字重 700 / 大写 / letter-spacing 0.1em / 弱磷光

规则：
  - 任何地方、任何理由都永远不要用非等宽字体
  - 行高：全程 1.5–1.6
  - 字距：保持默认（等宽自己处理）
  - 标题只是更大/更粗的正文 — 同一字体，同一规则
```

---

### 布局规则
```
最大内容宽：      800px（模拟终端列宽）
页面内边距：      桌面水平 24px，移动端 14px
区块分隔：        border-top: 1px solid #1E2820（永远不要只用留白）
对齐：            一切左对齐。终端是左对齐的。
网格：            CSS grid 仅用于功能/定价卡片。不要 flex 花招。
无圆角：          处处 0px。终端没有圆角。
无 box-shadow：   用辉光（text-shadow）而不是 box-shadow 做深度。
```

---

### 签名元素 1 — 启动序列动画
页面以启动序列加载：文字一行行出现，模拟系统启动。序列完成后，主页面内容淡入。这是最有冲击力的终端效果，也是本风格的签名开场。

```javascript
// 启动序列行 — 按产品定制
const bootLines = [
  { text: 'BIOS v2.4.1 — System initializing...', delay: 0 },
  { text: 'Loading kernel modules... [OK]', delay: 120 },
  { text: 'Mounting filesystems... [OK]', delay: 240 },
  { text: 'Starting network services... [OK]', delay: 360 },
  { text: 'Checking dependencies... [OK]', delay: 480 },
  { text: 'forge v3.2.1 ready.', delay: 620 },
  { text: '', delay: 750 },
];

// 每行在其 delay 时刻用 opacity: 0 → 1 淡入
// 最后一行 + 400ms 后，淡出启动屏，揭示主页面
```

```css
.boot-screen {
  position: fixed; inset: 0; z-index: 9999;
  background: #0A0E0A;
  display: flex; flex-direction: column;
  justify-content: center; padding: 40px;
  font-family: 'JetBrains Mono', monospace;
  transition: opacity 0.4s ease;
}
.boot-screen.fade-out { opacity: 0; pointer-events: none; }
.boot-line {
  font-size: 13px; color: #00FF41; line-height: 1.8;
  opacity: 0; transition: opacity 0.15s ease;
}
.boot-line.visible { opacity: 1; }
.boot-line .ok { color: #00FF41; }
.boot-line .dim { color: #3A4A3C; }
```

---

### 签名元素 2 — 打字机英雄标题
启动序列之后，英雄标题逐字符打出。用 JavaScript 打字循环 — 不要单独用 CSS 动画（它无法干净处理可变长度字符串）。

```javascript
function typeWriter(element, text, speed = 38) {
  let i = 0;
  element.textContent = '';
  const cursor = document.createElement('span');
  cursor.className = 'cursor';
  element.appendChild(cursor);
  const timer = setInterval(() => {
    if (i < text.length) {
      cursor.insertAdjacentText('beforebegin', text[i]);
      i++;
    } else {
      clearInterval(timer);
      // 打字完成后光标继续闪烁
    }
  }, speed);
}
```

```css
.cursor {
  display: inline-block; width: 10px; height: 1em;
  background: #00FF41; vertical-align: text-bottom;
  animation: blink 1s step-end infinite;
}
@keyframes blink { 50% { opacity: 0; } }
```

---

### 签名元素 3 — 交互式 Shell
本风格被复制最多的元素。假交互终端，访客可输入命令并得到预编程输出。通过假 CLI 回应展示产品个性。

```javascript
const shellCommands = {
  'help': [
    '  Available commands:',
    '  install    — Install the CLI tool',
    '  status     — Check system status',
    '  deploy     — Deploy to production',
    '  version    — Show version info',
    '  clear      — Clear the terminal',
  ],
  'install': [
    '  $ npm install -g @forge/cli',
    '  + @forge/cli@3.2.1',
    '  [OK] Installation complete.',
    '  [OK] Run `forge init` to get started.',
  ],
  'status': [
    '  System:     online',
    '  API:        [OK] responding in 42ms',
    '  Database:   [OK] 3 nodes healthy',
    '  CDN:        [OK] 99.98% uptime',
  ],
  'version': ['  forge v3.2.1 (node 20.11.0, linux x64)'],
  'clear': ['__CLEAR__'],
  // 未知命令回退：
  '__unknown__': (cmd) => [`  bash: ${cmd}: command not found`, '  Type "help" to see available commands.'],
};
```

Shell 输入样式：
```css
.shell {
  background: #0D1210; border: 1px solid #243029;
  padding: 0; overflow: hidden;
}
.shell-titlebar {
  background: #111714; border-bottom: 1px solid #1E2820;
  padding: 8px 14px; display: flex; align-items: center; gap: 8px;
  font-size: 11px; color: #3A4A3C;
}
.shell-dot { width: 9px; height: 9px; border-radius: 0; /* 方，不圆 */ background: #1E2820; }
.shell-title { margin-left: auto; font-size: 10px; letter-spacing: 0.06em; }
.shell-output { padding: 14px; min-height: 200px; max-height: 320px; overflow-y: auto; font-size: 12px; line-height: 1.65; }
.shell-input-row {
  display: flex; align-items: center; gap: 8px;
  padding: 10px 14px; border-top: 1px solid #1E2820;
  background: #0D1210;
}
.shell-prompt { color: #3A4A3C; white-space: nowrap; flex-shrink: 0; }
.shell-prompt .user { color: #007A20; }
.shell-prompt .sep { color: #3A4A3C; }
.shell-prompt .dir { color: #00C032; }
.shell-prompt .sym { color: #CDD8CB; }
.shell-field {
  flex: 1; background: transparent; border: none; outline: none;
  font-family: 'JetBrains Mono', monospace; font-size: 12px;
  color: #CDD8CB; caret-color: #00FF41;
}
```

---

### CRT 扫描线效果
应用到 `body::after` — 极低不透明度的细水平线制造 CRT 显示器感。2–4% 不透明度时是潜意识效果。永远不要超过 5%，否则会分心。

```css
body::after {
  content: '';
  position: fixed; inset: 0; pointer-events: none; z-index: 9998;
  background: repeating-linear-gradient(
    0deg,
    rgba(0, 0, 0, 0.025) 0px, rgba(0, 0, 0, 0.025) 1px,
    transparent 1px, transparent 2px
  );
}
```

可选：暗角效果（边缘更暗，中心更亮）：
```css
body::before {
  content: '';
  position: fixed; inset: 0; pointer-events: none; z-index: 9997;
  background: radial-gradient(ellipse at center, transparent 60%, rgba(0,0,0,0.4) 100%);
}
```

---

### 导航
粘性、极简、满宽。无内边距空隙 — 导航感觉像标题栏。

```
┌────────────────────────────────────────────────────────────┐
│ [forge]          # 文档  # 安装  # 定价  # github          │
│                                    [ $ 登录 ] [ $ 开始 ]   │
└────────────────────────────────────────────────────────────┘
```

```css
nav {
  position: sticky; top: 0; z-index: 100;
  background: #0D1210; border-bottom: 1px solid #1E2820;
  padding: 10px 24px;
  display: flex; align-items: center; justify-content: space-between;
}
.nav-logo { font-weight: 700; color: #00FF41; font-size: 14px; }
.nav-logo::before { content: '['; color: #3A4A3C; }
.nav-logo::after  { content: ']'; color: #3A4A3C; }
.nav-link { color: #3A4A3C; font-size: 12px; text-decoration: none; }
.nav-link::before { content: '# '; color: #1E2820; }
.nav-link:hover { color: #00FF41; }
```

---

### 英雄区块
三部分：提示符行 → 打字机标题 → 输出块 → 命令块 → 操作。

```
user@forge:~$ ./launch --prod

Ship infrastructure at the speed
of your terminal█

# Deploy, scale, and monitor your entire stack
# from the command line. No dashboards. No drag-and-drop.
# Just your keyboard and a cursor.

┌──────────────────────────────────────────────┐
│ $ npm install -g @forge/cli && forge init    │
└──────────────────────────────────────────────┘

[ 安装 CLI ]     [ 阅读文档 ]

# v3.2.1 · MIT · Node 18+ · 4.2k ★ on GitHub
```

```css
.hero { padding: 48px 24px 40px; border-bottom: 1px solid #1E2820; }
.hero-prompt { font-size: 12px; color: #3A4A3C; margin-bottom: 20px; }
.hero-prompt .user { color: #007A20; }
.hero-prompt .dir  { color: #00C032; }
.hero-prompt .sym  { color: #CDD8CB; }
.hero-prompt .cmd  { color: #CDD8CB; }
h1.hero-heading {
  font-size: clamp(20px, 3.5vw, 42px); font-weight: 700;
  color: #00FF41; line-height: 1.2; margin-bottom: 18px;
  text-shadow: 0 0 8px #00FF41, 0 0 20px rgba(0,255,65,0.25);
  letter-spacing: -0.02em;
}
.hero-output { color: #CDD8CB; font-size: 13px; opacity: 0.65; line-height: 1.75; margin-bottom: 26px; max-width: 580px; }
.hero-cmd-box {
  border: 1px solid #243029; background: #0D1210;
  padding: 12px 16px; margin-bottom: 22px;
  display: flex; align-items: center; gap: 10px;
  max-width: 520px;
}
.hero-cmd-box .sym { color: #CDD8CB; flex-shrink: 0; }
.hero-cmd-box code { color: #CDD8CB; font-size: 12px; white-space: nowrap; overflow-x: auto; }
.copy-btn {
  margin-left: auto; font-size: 10px; font-family: inherit;
  border: 1px solid #243029; background: transparent; color: #3A4A3C;
  padding: 3px 8px; cursor: pointer; flex-shrink: 0;
  transition: color 120ms, border-color 120ms;
}
.copy-btn:hover { color: #00FF41; border-color: #00FF41; }
.hero-actions { display: flex; gap: 10px; flex-wrap: wrap; margin-bottom: 16px; }
.hero-note { font-size: 11px; color: #3A4A3C; }
```

---

### ASCII 数据区块
带 ASCII 进度条的紧凑数据行。这替代典型「大数字指标」区块，是终端处理数据最鲜明的方式。

```
## 数据 ─────────────────────────────────────────

日部署量            ████████████████████░░░░   4,821
可用性              █████████████████████████  99.98%
平均部署时间        ██████░░░░░░░░░░░░░░░░░░░  4.2s
活跃用户            █████████████████░░░░░░░░  12.4k
开源星标            ████████████░░░░░░░░░░░░░  4.2k ★
```

```css
.stats-section { padding: 32px 24px; border-bottom: 1px solid #1E2820; }
.stat-row { display: grid; grid-template-columns: 160px 1fr 60px; gap: 12px 16px; align-items: center; padding: 5px 0; font-size: 12px; }
.stat-label { color: #3A4A3C; }
.stat-bar { color: #007A20; letter-spacing: -1px; /* 更紧的条 */ font-size: 11px; }
.stat-bar .filled { color: #00C032; }
.stat-bar .empty  { color: #1E2820; }
.stat-value { color: #CDD8CB; text-align: right; }
```

用填充/空心块字符构建进度条：
- 填充：`█`（U+2588）
- 空心：`░`（U+2591）
- 总块数：25
- 填充数 = Math.round(percentage / 4)

---

### 功能网格 — 盒绘边框
每张功能卡片用 ASCII 盒绘字符作视觉框架。网格以 1px 间隙分隔卡片（无沟槽 — 卡片像终端面板一样贴在一起）。

```
┌─── [核心] ──────────────────────────┐  ┌─── [插件] ────────────────────────┐
│ 零配置部署                           │  │ 插件架构                           │
│                                      │  │                                    │
│ 检测你的技术栈，合理配置，           │  │ 用社区插件扩展，或                 │
│ 然后发布。不需要 YAML。              │  │ 用 20 行写出自己的。               │
│                                      │  │                                    │
│ $ forge deploy                       │  │ $ forge plugin install name        │
└──────────────────────────────────────┘  └────────────────────────────────────┘
```

```css
.features { padding: 32px 24px; border-bottom: 1px solid #1E2820; }
.feature-grid { display: grid; grid-template-columns: repeat(2, 1fr); gap: 1px; background: #1E2820; }
.feature-card { background: #111714; padding: 20px; }
.feature-card:hover { background: #141A15; }
.feature-tag { font-size: 10px; color: #007A20; letter-spacing: 0.08em; margin-bottom: 8px; }
.feature-tag::before { content: '['; color: #243029; }
.feature-tag::after  { content: ']'; color: #243029; }
.feature-title { font-size: 14px; font-weight: 700; color: #00FF41; margin-bottom: 8px; }
.feature-desc  { font-size: 12px; color: #3A4A3C; line-height: 1.65; margin-bottom: 10px; }
.feature-cmd   { font-size: 11px; color: #007A20; }
.feature-cmd::before { content: '$ '; color: #243029; }
@media (max-width: 560px) { .feature-grid { grid-template-columns: 1fr; } }
```

---

### 日志流区块
实时（或模拟实时）日志输出面板。新条目每隔几秒出现，自动滚到底。终端 UI 最「活」的区块。

```
## 实时输出 ──────────────────────────────────────

09:14:02  [OK]    Connected to cluster us-east-1
09:14:03  [OK]    Pulled latest image sha256:a3f7b...
09:14:05  [WARN]  Memory at 78% — consider scaling
09:14:07  [INFO]  Health check passed on 3/3 nodes
09:14:08  [OK]    Deployed v3.2.1 in 4.2s
09:14:09  [OK]    SSL certificate renewed (90 days)
09:14:11  [WARN]  Rate limit threshold at 89%
09:14:13  [OK]    Backup snapshot created
```

```css
.log-section { padding: 32px 24px; border-bottom: 1px solid #1E2820; }
.log-stream { background: #0D1210; border: 1px solid #1E2820; padding: 14px; max-height: 220px; overflow-y: auto; }
.log-entry { display: grid; grid-template-columns: 70px 56px 1fr; gap: 10px; padding: 2px 0; font-size: 12px; line-height: 1.6; }
.log-time  { color: #3A4A3C; }
.log-ok    { color: #00C032; }
.log-warn  { color: #FFD700; }
.log-info  { color: #5BB8FF; }
.log-error { color: #FF3333; }
.log-msg   { color: #CDD8CB; opacity: 0.7; }
.log-new   { animation: logSlide 0.2s ease; }
@keyframes logSlide { from { opacity: 0; transform: translateY(-4px); } to { opacity: 1; transform: translateY(0); } }
```

---

### 定价 — ASCII 表格式
定价显示为带 ASCII 边框的表。三列，数据行，当前方案用绿色高亮。月付/年付切换用做成 CLI 标志样式的按钮组。

```
[ --monthly ]  [ --annual  ]

┌──────────────────────────────────────────────────────────────┐
│  方案          免费          专业           企业             │
│  ─────────────────────────────────────────────────────────── │
│  价格          $0/mo        $29/mo        联系               │
│  服务          3            不限          定制               │
│  内存          1 GB         16 GB         不限               │
│  支持          社区         优先          专属 SLA           │
│  日部署        10           不限          不限               │
├──────────────────────────────────────────────────────────────┤
│                [ 开始使用 ] [▶ 安装专业版] [ 联系 ]         │
└──────────────────────────────────────────────────────────────┘
```

```css
.pricing { padding: 32px 24px; border-bottom: 1px solid #1E2820; }
.plan-toggle { display: flex; gap: 0; margin-bottom: 20px; }
.toggle-btn { border: 1px solid #243029; padding: 6px 14px; font-size: 11px; font-family: inherit; background: transparent; color: #3A4A3C; cursor: pointer; transition: 120ms; }
.toggle-btn:first-child { border-right: none; }
.toggle-btn.active { background: #00FF41; color: #0A0E0A; border-color: #00FF41; font-weight: 700; }
.toggle-btn:hover:not(.active) { color: #00FF41; border-color: #00C032; }

.price-table { border: 1px solid #243029; width: 100%; border-collapse: collapse; }
.price-table th, .price-table td { border: 1px solid #1E2820; padding: 9px 14px; font-size: 12px; text-align: left; }
.price-table th { color: #3A4A3C; font-weight: 400; background: #0D1210; font-size: 10px; letter-spacing: 0.06em; text-transform: uppercase; }
.price-table td { color: #CDD8CB; }
.price-table .col-pro { color: #00FF41; font-weight: 700; }
.price-table tr:hover td { background: #111714; }
.price-row-label { color: #007A20 !important; font-size: 11px !important; }
```

---

### 按钮
每个按钮看起来都像 CLI 命令。文字是 `[ 方括号 ]` 格式。无图标。默认基于边框、无填充，悬停反转填充。

```css
.btn {
  border: 1px solid #00FF41; padding: 8px 16px;
  font-size: 12px; font-family: 'JetBrains Mono', monospace;
  background: transparent; color: #00FF41; cursor: pointer;
  transition: background 120ms, color 120ms;
  white-space: nowrap; letter-spacing: 0.02em;
}
.btn::before { content: '[ '; }
.btn::after  { content: ' ]'; }
.btn:hover { background: #00FF41; color: #0A0E0A; }
.btn-dim { border-color: #243029; color: #3A4A3C; }
.btn-dim:hover { border-color: #00FF41; color: #00FF41; background: transparent; }
.btn-danger { border-color: #FF3333; color: #FF3333; }
.btn-danger:hover { background: #FF3333; color: #0A0E0A; }
```

---

### 页脚
极简。一行提示符，然后两列：链接左，版本/状态信息右。

```
─────────────────────────────────────────────────────────
user@forge:~$ _

--docs    --github    --status    --privacy    --terms

                                  forge v3.2.1 · MIT License
                                  © 2026 Forge Systems Inc.
```

---

### 不要做什么
- ✗ 永远不要在任何地方用非等宽字体 — 连 logo 也不行
- ✗ 永远不要用圆角 — 哪怕 1px — 终端零曲线
- ✗ 永远不要用 box-shadow — 辉光效果只用 text-shadow
- ✗ 永远不要用 CSS 渐变作背景 — 只要纯深色
- ✗ 永远不要用 SVG 图标或 emoji 图标 — 只用 ASCII 字符
- ✗ 永远不要用超过一种强调色 — 磷光绿是唯一品牌色
- ✗ 永远不要居中对齐任何文字 — 无一例外全部左对齐
- ✗ 永远不要用制造大块留白的内边距 — 终端是密的
- ✗ 永远不要加启动序列却不可跳过（点击或按键跳过）
- ✗ 永远不要让交互 shell 对每个未知命令都报错 — 应感觉有趣

### 待替换数据（占位映射）
- `[PRODUCT_NAME]` — 显示在导航 logo `[product]`、英雄提示符 `user@product:~$`、页脚
- `[TAGLINE]` — 2–3 词英雄标题，自行打出
- `[HERO_SUBTEXT]` — 2–3 行以 `#` 开头的注释风格
- `[INSTALL_CMD]` — 英雄框中显示的 npm/brew/curl 安装命令
- `[VERSION]` — 例如 `v3.2.1`，显示在英雄备注与页脚
- `[BOOT_LINES]` — 5–8 条针对产品的启动序列消息
- `[SHELL_COMMANDS]` — 访客可输入的假 CLI 命令对象
- `[FEATURES]` — 数组：标签（core/plugin/security）、标题、描述、示例命令
- `[STATS]` — 数组：标签、百分比（0–100）、显示值
- `[LOG_ENTRIES]` — 数组：时间、级别（OK/WARN/INFO/ERROR）、消息
- `[PRICING]` — 3 档：名称、价格、功能行
- `[GITHUB_URL]`、`[DOCS_URL]`、`[TWITTER_URL]`
