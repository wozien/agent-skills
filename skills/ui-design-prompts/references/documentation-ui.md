# Documentation UI

- **id:** `documentation-ui`
- **别名:** 文档站, Docs UI, 开发者文档, API 文档, 技术知识库
- **一句话:** 深色、结构清晰，为快速找到答案而设计。
- **适用:**
  - 开发者文档站点
  - API 参考页
  - 技术知识库与 Wiki
  - 开源项目文档
  - SDK 与库指南
- **避免:**
  - 营销落地页或面向消费者的产品
  - 适合明亮、温暖视觉的内容
  - 浅色模式是品牌主要预期的站点
  - 不需要深层导航的短内容
- **来源:** https://uidesignprompts.com/prompts/documentation-ui

## Prompt

## 文档 UI 设计系统

### 气质
密集、深色、为速读而生。每个元素的存在，都是为了让开发者在 30 秒内找到问题的答案。没有营销废话，没有巨大 Hero 区——只有导航、内容和上下文，始终同时可见。深色背景降低长时间技术阅读的眼疲劳，并传达「由开发者、为开发者而造」。

### 色彩系统
- Canvas（页面背景）: `#0A0A0F` — 近黑、带极淡蓝色底调，绝不用纯 `#000000`
- Surface（侧栏、卡片）: `#13131A` — 比画布略亮一点，用于侧栏背景和抬升面板
- Surface elevated（代码块、提示框、推广卡片）: `#1A1A23`
- Border: `rgba(255,255,255,0.08)` — 唯一分隔色，全局使用（1px 发丝线）
- Text primary: `#F4F4F5` — 标题、当前导航项、强调文字
- Text secondary: `#A1A1AA` — 正文、未激活导航项
- Text muted: `#6B6B7B` — 时间戳、辅助文案、面包屑分隔符
- Accent violet: `#8B7CF6` — 链接、当前导航指示、当前 TOC 项、主按钮、焦点环
- Accent violet bright（悬停）: `#A99BFF`
- 行内代码文字: `#C4B5FD`，背景 `#1E1E27`
- 成功/提示: `#4ADE80` · 警告: `#FBBF24` · 错误/危险: `#F87171` · 信息: `#60A5FA` — **仅**用于 callout 盒子内部，绝不当普通 UI 色

### 字体排印
- UI / 正文字体: Inter 或 system-ui sans-serif
- 代码字体: 'JetBrains Mono'、'Fira Code' 或 ui-monospace — 用于行内代码、代码块、版本号、键盘快捷键
- H1（页面标题）: 36-40px，字重 800，letter-spacing -0.02em，颜色 text-primary
- H2（章节标题）: 24-28px，字重 700，margin-top 40px，border-bottom 1px solid border，padding-bottom 8px
- H3（小节）: 18-20px，字重 600
- 正文: 15-16px，字重 400，line-height 1.75，颜色 text-secondary
- 侧栏导航项: 14px，字重 500
- 侧栏分区标签: 12px，字重 700，大写，letter-spacing 0.06em，颜色 text-muted
- TOC 项: 13px，字重 400-500

### 布局架构 — 三栏
```
┌──────────────────────────────────────────────────────────────┐
│  顶部导航栏（sticky，全宽）                                    │
├──────────────────────────────────────────────────────────────┤
│  公告条（可选，细条，点状背景）                                 │
├───────────────┬──────────────────────────────┬───────────────┤
│  左侧栏       │       中间内容                 │ 右侧栏         │
│  (260px)      │       (flex-1, max 760px)     │ (240px)       │
│  - 导航分组   │  - 面包屑                     │ - 「本页」TOC  │
│  - 导航项     │  - H1 标题                    │ - 嵌套 TOC    │
│  - 当前项     │  - 导语段落                   │   条目        │
│    指示器     │  - 分割线                     │ - 当前项      │
│               │  - H2/H3 章节                 │   高亮        │
│               │  - 正文                       │ - 推广/       │
│               │  - 代码块                     │   赞助        │
│               │  - Callout 盒子               │   卡片        │
│               │  - 表格                       │               │
│               │  - 上一页/下一页导航卡片       │               │
└───────────────┴──────────────────────────────┴───────────────┘
```
- 左侧栏: `position: sticky`，`top: navbar-height`，独立滚动，`border-right: 1px solid border`
- 中间: `max-width: 760px`，留白充足（桌面 40px）
- 右侧栏: `position: sticky`，`top: navbar-height`，`border-left: 1px solid border`
- 内容总最大宽度: ~1400px，居中

### 顶部导航栏
- 背景: `#0A0A0F`，`border-bottom: 1px solid border`，高度 56-64px，顶部 sticky
- 左侧: logo 标记（小图标，24-28px）+ 文字标（字重 800，16px）+ 可选 「/」分隔 + 分区标签（如 「Docs」）
- 中部/中偏左: 导航链接 — Guide、Config、Plugins、Blog — 14px 字重 500，`color: text-secondary`，当前链接 `color: accent-violet`
- 右侧: 搜索栏（宽 240px，`background: surface`，`border: 1px solid border`，`border-radius: 8px`，占位符 「Search documentation...」，右对齐 `Ctrl K` kbd 徽章）+ 版本下拉（如 「v16.2.9」带 chevron）+ GitHub/社交图标链接 + 可选主题切换
- 搜索栏聚焦: `border-color: accent-violet`，轻微光晕 `box-shadow: 0 0 0 3px rgba(139,124,246,0.15)`

### 公告条（可选）
- 紧贴导航栏下方的细条，高度 ~40px
- 背景: `#0A0A0F`，带极淡重复点阵（低透明度 `radial-gradient` 圆点）增加质感
- 内容: 小图标 + 加粗大写活动/公告文字 + 次要细节 + 右侧小胶囊按钮（`border: 1px solid border`，`border-radius: 100px`，文字 `accent-violet`，悬停背景 `surface`）
- 字体: 12px，字重 600，letter-spacing 0.05em，主标签使用大写

### 左侧栏 — 导航
- 宽度: 260px，`background: canvas`（与页面相同——侧栏**不**靠颜色与页面分离，只靠边框）
- 顶部可选「精选卡片」项: 图标（24px，放在彩色圆角方块内）+ 加粗标题 + 弱化副标题 + 上下 chevron 图标 — 用于 「Using App Router」/「Latest Version」这类提示
- 分区标签: 12px 大写，字重 700，`color: text-muted`，`margin: 20px 0 8px`，letter-spacing 0.06em
- 导航项: `padding: 6px 12px`，`border-radius: 6px`，`font-size: 14px`，`color: text-secondary`，`text-decoration: none`
- 导航项悬停: `color: text-primary`，`background: rgba(255,255,255,0.04)`
- 导航项当前: `color: text-primary`，`font-weight: 600`，左侧强调边 — 用 `border-left: 2px solid accent-violet` 加负 margin，或 `::before` 伪元素条
- 嵌套/子项: 额外 `padding-left: 24px`
- 滚动指示: 侧栏最外侧一条 2px 竖线表示滚动位置（装饰性，可用简单 `::after` 渐变条）

### 中间内容栏
- `max-width: 760px`，`padding: 40px 48px`
- 面包屑（可选）: `font-size: 13px`，`color: text-muted`，段之间用 `/` 分隔，最后一段 `color: text-secondary`
- H1: 36-40px，字重 800，`margin-bottom: 12px`
- 导语段落（紧跟 H1 下方的介绍句）: 17px，`color: text-secondary`，略大于正文
- 水平分割线: `border-top: 1px solid border`，`margin: 32px 0`
- H2: 26px，字重 700，`border-bottom: 1px solid border`，`padding-bottom: 10px`，`margin: 40px 0 16px`
- 正文段落: 15.5px，`color: text-secondary`，`line-height: 1.75`，`margin-bottom: 16px`
- 链接: `color: accent-violet`，`text-decoration: underline`，`text-decoration-color: rgba(139,124,246,0.4)`，悬停 `color: accent-violet-bright`
- 行内代码: `background: #1E1E27`，`color: #C4B5FD`，`padding: 2px 6px`，`border-radius: 4px`，`font-size: 13px`，`font-family: mono`
- 无序列表: `padding-left: 22px`，`color: text-secondary`，`line-height: 1.8`，自定义项目符号 `::marker { color: accent-violet }`

### 代码块组件
- 容器: `background: #16161D`，`border: 1px solid border`，`border-radius: 10px`，`overflow: hidden`，`margin: 20px 0`
- 顶栏: `background: #1A1A23`，`border-bottom: 1px solid border`，`padding: 8px 14px`，flex 行 — 左: 文件名或语言标签（12px，mono，`color: text-muted`），右: 复制按钮（图标，`color: text-muted`，悬停 `color: text-primary`）
- 代码区: `padding: 16px`，`font-family: mono`，`font-size: 13.5px`，`line-height: 1.7`，必要时横向滚动
- 语法高亮色（精简调色）: 关键字 `#8B7CF6`，字符串 `#A3E635`，注释 `#6B6B7B`，函数 `#60A5FA`，纯文本 `#F4F4F5`

### Callout / 提示框
四种变体，结构相同:
- `border-radius: 10px`，`padding: 14px 16px`，`border-left: 3px solid [variant-color]`，`background: rgba([variant-color], 0.08)`，`margin: 20px 0`
- 标题行: 图标（16px，变体色）+ 加粗标签（如 「Note」「Warning」「Tip」「Danger」）用变体色
- 正文: `color: text-secondary`，14px
- 变体:
  - Info/Note: 边框+图标 `#60A5FA`，标签 「Note」
  - Tip: 边框+图标 `#4ADE80`，标签 「Tip」
  - Warning: 边框+图标 `#FBBF24`，标签 「Warning」
  - Danger: 边框+图标 `#F87171`，标签 「Danger」

### 表格
- `width: 100%`，`border-collapse: collapse`，`font-size: 14px`，`margin: 20px 0`
- `th`: `background: surface`，`color: text-primary`，`font-weight: 600`，`text-align: left`，`padding: 10px 14px`，`border-bottom: 1px solid border`
- `td`: `padding: 10px 14px`，`color: text-secondary`，`border-bottom: 1px solid border`
- 行悬停: `background: rgba(255,255,255,0.02)`

### 上一页 / 下一页导航
- 放在内容栏底部，`margin-top: 48px`，`padding-top: 24px`，`border-top: 1px solid border`
- 两列网格（1fr 1fr），gap 16px
- 每张卡片: `border: 1px solid border`，`border-radius: 10px`，`padding: 16px 20px`，`background: surface`
- 「Previous」卡片: 左对齐，上方小弱化标签 「Previous」，下方加粗标题，标签前加 `←` 箭头
- 「Next」卡片: 右对齐（text-align right），结构相同，标签后加 `→` 箭头，位于网格第 2 列
- 悬停: `border-color: accent-violet`，轻微 `transform: translateY(-2px)`

### 右侧栏 — 本页目录
- 宽度: 240px，`position: sticky`，`border-left: 1px solid border`，`padding: 40px 24px`
- 标题: 「ON THIS PAGE」 — 12px，字重 700，大写，`color: text-muted`，letter-spacing 0.06em，左侧小列表图标
- TOC 列表: `font-size: 13px`，`line-height: 2`，`color: text-secondary`
- 嵌套 TOC 项（h2 下的 h3）: `padding-left: 16px`，`font-size: 12.5px`，略更弱化
- 当前 TOC 项: `color: accent-violet`，`font-weight: 500`
- TOC 下方分割线: `border-top: 1px solid border`，`margin: 20px 0`
- 「Edit this page on GitHub」链接: `font-size: 13px`，`color: text-muted`，图标 + 文字，悬停 `color: text-secondary`

### 推广 / 赞助卡片（右侧栏，TOC 下方）
- `background: surface-elevated`，`border: 1px solid border`，`border-radius: 10px`，`padding: 16px`，`margin-bottom: 12px`
- 可包含: 小 logo/图标 + eyebrow 标签（弱化，11px 大写）+ 加粗标题（14px）+ 可选强调紫链接文字
- 垂直堆叠 2-3 张，形成「赞助商」感

### 按钮
- 主按钮: `background: accent-violet`，`color: #0A0A0F`，`border-radius: 8px`，`padding: 8px 16px`，`font-weight: 600`，`font-size: 13px`，悬停 `background: accent-violet-bright`
- 次级/描边: `background: transparent`，`border: 1px solid border`，`color: text-primary`，悬停 `border-color: accent-violet`
- 胶囊（公告条风格）: `border: 1px solid border`，`border-radius: 100px`，`padding: 4px 12px`，`font-size: 12px`，`color: accent-violet`

### 响应式行为 — 关键模式
这是整套系统最重要的响应式模式:

- **桌面 (>1280px):** 三栏同时可见
- **平板 (1024-1280px):** 右侧栏（TOC）隐藏；左侧栏 + 内容保留
- **移动 (<1024px):** **两侧栏都隐藏**。导航栏正下方出现次级条，含两个切换按钮:
  - 左: 「Menu」配列表图标 — 从左侧滑出全高 overlay 抽屉打开左侧栏
  - 右: 「On this page」配 chevron — 从右侧滑出 overlay 抽屉打开右侧栏
- 抽屉: `position: fixed`，`background: canvas`，`z-index: 100`，滑动过渡 `transform: translateX()`，背后半透明遮罩 `rgba(0,0,0,0.6)`
- 移动端内容栏变为全宽，内边距减至 (20px)

### 不要这样做
- 不要用纯黑 `#000000` — 始终用 `#0A0A0F` 或类似带轻微色调的近黑
- 交互元素不要超过一种强调色 — 紫色是唯一「行动」色
- 平板上不要去掉左侧栏 — 先隐藏的是 TOC 侧栏
- 正文不要用纯白 — 标题用 `#F4F4F5`，正文用 `#A1A1AA` 以维持层级
- 不要用投影 — 纵深来自背景分层（`canvas` → `surface` → `surface-elevated`）和仅 1px 边框
- 不要居中正文 — 始终左对齐，这是阅读向内容
- 任何地方都不要用衬线体 — 文档只有无衬线 + 等宽
