# Launchpad / Directory UI

- **id:** `launchpad-ui`
- **别名:** 产品目录, Launchpad, Product Hunt 风格, 投票排行, 发现站
- **一句话:** 社区驱动、可投票，把最好的推到前面。
- **适用:**
  - 产品发布与目录平台
  - 社区策展资源列表
  - 应用商店与工具发现站
  - 点赞与排名平台
  - Newsletter 目录与创作者社区
- **避免:**
  - 单产品落地页
  - 个人作品集或博客
  - 电商店面
  - 不涉及列表、信息流或社区投票机制的产品
- **来源:** https://uidesignprompts.com/prompts/launchpad-ui

## Prompt

## Launchpad / 目录 UI 设计系统

### 气质
信息密集、社区驱动、可扫读。每个元素都为发现优化 — 用户应能在 30 秒内扫过 20 个产品，并立刻知道哪些值得点。信任信号无处不在: 票数、排名徽章、用户头像、倒计时。设计干净、编辑向，不花哨。

### 核心布局架构 — 三栏
```
┌─────────────┬──────────────────────────┬────────────────┐
│ 左 (240px)  │   中 (flex-1)            │ 右 (260px)     │
│             │                          │                │
│ 统计        │   Tab 导航               │ 搜索           │
│ 最新帖      │   倒计时                 │ 提交 CTA       │
│ 社区        │   产品信息流             │ 合作广告       │
│             │   （排名列表）            │ 更多广告       │
└─────────────┴──────────────────────────┴────────────────┘
```
- 左侧栏: 220-240px，白背景，border-right 1px solid border
- 中栏: flex-1，主内容，padding 0 24px
- 右侧栏: 240-280px，白背景，border-left 1px solid border
- 三栏独立滚动，或主内容滚动、侧栏 sticky
- 移动: 侧栏收起，单列信息流

### 备选布局 — 左导航 + 信息流 + 右广告
更偏 App 的 launchpad（ScrollLaunch 风格）:
- 左: 常驻导航侧栏（240px），图标 + 标签导航项
- 中: 主信息流，带周/周期导航 tab
- 右: 赞助/推广广告列（260px）
- 顶栏: 品牌居中，搜索在左，CTA 在右

### 背景与表面
- 页面背景: #F9F9F7 — 暖近白，略偏离纯白
- 卡片/面板表面: #FFFFFF — 纯白从背景抬起
- 边框: #E8E8E4 — 无处不在的 1px 分隔，全局一致
- 悬停状态: #F5F5F3 — 略深暖灰
- 头名产品高亮行: #FFFBEB — 极浅暖黄着色，用于 #1 产品

### Hero 区（launchpad 首页）
- 背景: #F9F9F7 带极淡方格网格叠加
  - 网格: 重复 CSS 网格线，间距 28-32px，颜色 rgba(0,0,0,0.05)，1px
  - 做法: background-image: linear-gradient(#e8e8e4 1px, transparent 1px), linear-gradient(90deg, #e8e8e4 1px, transparent 1px); background-size: 32px 32px
- 标题: 大衬线字体（Playfair Display、Georgia 或类似），字重 700-800，#0D0D0D，font-size clamp(36px, 5vw, 64px)
- 副标题: 无衬线，#666，居中，max-width 560px，font-size 17px，line-height 1.7
- 社会证明行: 重叠圆形头像（5-6 位用户，各 36px，-8px 重叠）+ 星级（橙色 ★★★★★）+ 「join X,XXX makers」文字
- CTA 按钮: 橙色胶囊，左图标（火箭 🚀），白字，padding 12px 28px，border-radius 100px
- Hero 下方区块: 立刻过渡到产品信息流（无空隙 — 网格背景过渡到一条边框线）

### 导航栏
- 白背景，border-bottom 1px solid #E8E8E4，高度 56px
- 左: logo（字标，可含小图标/emoji） — font-weight 700
- 中: 导航链接 — 当前链接用橙色下划线胶囊或橙字
  - 当前导航项: 当前文字外包橙色胶囊徽章 **或** 橙色下划线
  - 未激活: #444，字重 500，font-size 15px
  - 「Products」「More」类项带下拉箭头
- 右: 「Log in」文字链接（橙）+ 「Register」橙色胶囊按钮

### Tab 导航（周期选择器）
- 横向 tab: Daily / Weekly / Monthly / Yearly
- 当前 tab: 橙字 (#F5852A)，underline border-bottom 2px solid orange
- 未激活 tab: #666，无下划线，悬停: #333
- Tab 行右侧: 「Daily Archives」按钮带日历图标
- 字体: 15px，字重 500
- 整个 tab 行 border-bottom: 1px solid #E8E8E4

### 周导航（备选 tab 风格）
- 可横向滚动的周胶囊: 「Week 19」「Week 20」等
- 当前周: 深色胶囊（#0D0D0D 背景，白字，border-radius 100px）
- 未激活周: 仅文字，颜色 #666
- 两端 prev/next 箭头按钮

### 倒计时
- 显示为: 「New launches in [20 hours] [35 mins] [34 secs]」
- 标签: font-weight 600，#0D0D0D，font-size 15px
- 时间盒: border 1px solid #E8E8E4，border-radius 6px，padding 4px 12px，font-size 14px，font-weight 500，颜色 #333
- 盒子与标签文字在同一 flex 行内联

### 产品列表行
这是最重要的组件。每个细节都重要:

**布局:**
```
[应用图标 48px] [产品名 + 排名徽章 + 优惠徽章]  [↑ 投票]
                [描述文字]                      [票数]
```

**应用图标:**
- 48px × 48px（Uneed 风格）或 56-64px（ScrollLaunch 风格）
- Border-radius: 12px
- Border: 1px solid #E8E8E4
- 背景: 白或彩色（产品品牌）

**排名数字（图标左侧，ScrollLaunch 风格）:**
- 小 emoji 或火焰图标: 前 3 名用 🔥
- 数字: #4 起为弱化色纯数字
- 字体: 13px，字重 600，颜色 #999

**产品名:**
- 字体: 16px，字重 700，颜色 #0D0D0D
- 悬停: 下划线

**排名徽章（名称旁，Uneed 风格）:**
- #1: 皇冠 emoji 👑 + 「#1」橙字
- #2: 麦克风 🎤 + 「#2」文字
- #3: 红点 🔴 + 「#3」文字
- Font-size: 13px，font-weight: 600

**优惠徽章:**
- Border: 1.5px solid #16A34A，颜色 #16A34A，border-radius 100px
- Padding: 2px 10px，font-size: 12px，font-weight: 500
- 文字: 「Deals」前缀 🔗 图标

**Premium 徽章:**
- 背景: #FFF3E0，颜色: #F5852A，border-radius: 4px
- Padding: 2px 8px，font-size: 12px，font-weight: 500

**描述:**
- 字体: 14px，字重 400，颜色 #666，最多 1 行
- Margin-top: 4px

**分类标签（ScrollLaunch 风格）:**
- 描述下方胶囊标签
- 背景: transparent，border: 1px solid #E8E8E4
- 颜色: #666，font-size: 12px，padding: 2px 8px，border-radius: 100px

**评论数:**
- 对话气泡图标 + 数字，颜色 #999，font-size 13px

**upvote 按钮:**
- 右对齐，flex 列: ▲ 箭头在数字上方
- 默认: border 1px solid #E8E8E4，颜色 #666，背景白
- 已投: 橙边框、橙字、橙箭头
- 宽度: 40-48px，border-radius: 8px，padding: 8px 0
- 数字: font-size 14px，字重 600，颜色 #333

**行容器:**
- Padding: 16px 0
- Border-bottom: 1px solid #F0F0ED
- 悬停: 背景 #FAFAF8
- #1 产品: 背景 #FFFBEB（浅黄高亮）

### 左侧栏组件

**统计面板:**
- 分区标签: 「2026 STATISTICS」 — 11px，字重 700，大写，letter-spacing 0.08em，颜色 #999
- 统计卡片: 白背景，border 1px solid #E8E8E4，border-radius 8px，padding 12px 16px
- 统计数字: font-size 22px，字重 700，颜色 #0D0D0D
- 统计标签: font-size 12px，颜色 #999
- 两张统计卡 2 列网格

**最新帖 / 社区信息流:**
- 分区标签: 与 「LATEST POSTS」相同风格
- 帖子卡片: 白背景，border 1px solid #E8E8E4，border-radius 8px，padding 12px
- 头像: 32px 圆
- 作者名: 13px，字重 600，#0D0D0D
- 时间: 12px，#999
- 帖文: 13px，#444，line-height 1.5，3 行截断
- 产品标签: 小文字带链接图标
- 互动: 心形图标 + 计数 + 评论图标 + 计数，12px，#999

**推广/CTA 卡片（左侧栏）:**
- 背景: 浅着色（绿着色 #F0FFF4 或品牌着色）
- Border: 1px solid tint-border
- Border-radius: 12px
- 标题: 15px，字重 700，#0D0D0D
- 描述: 13px，#666
- CTA 链接: 「Browse X →」 — font-size 14px，字重 500，品牌色，无按钮背景

### 右侧栏组件

**搜索栏:**
- 全宽，border 1px solid #E8E8E4，border-radius 8px，高度 40px
- 左: 搜索图标 #999
- 右: 键盘快捷徽章 「CTRL K」 — border 1px solid #E8E8E4，border-radius 4px，font-size 11px，padding 2px 6px
- 占位符: 「Search a product」用 #999

**提交 CTA 按钮:**
- 全宽，橙背景 (#F5852A)，白字
- Border-radius: 8px，高度 44px
- 左: ⊕ 图标，文字 「Submit a product」
- 字体: 15px，字重 600

**分区标题（右侧栏）:**
- 「OUR PARTNERS」 — 11px，字重 700，大写，letter-spacing 0.08em，颜色 #999

**合作/赞助卡片:**
- 白背景，border 1px solid #E8E8E4，border-radius 10px，padding 14px
- Logo: 36-40px 方，border-radius 8px，可有品牌背景
- 「Visit ↗」按钮: 右上，border 1px solid #E8E8E4，border-radius 6px，font-size 12px，padding 4px 10px
- 产品名: 14px，字重 700，#0D0D0D
- 描述: 13px，#666，2 行截断

**赞助广告位:**
- 与合作卡片相同风格
- 「Promoted」标签: 右上，#999，font-size 11px
- 「Advertise ↗」链接: 12px，#999

**「上周最佳」面板:**
- 标题: 「Last week's best」配橙色奖杯图标 + #999 周标签 + 「→」链接
- 迷你产品行: 32px 图标 + 名称（截断）+ upvote 数
- 名称: 13px，字重 500，#333
- 计数: 13px，#999，火焰或心形图标

### 左导航侧栏（App 风格）
- 宽度: 240px，白背景，border-right 1px solid #E8E8E4
- 导航项: 图标（20px，#666）+ 标签（14px，字重 500，#444）
- 当前项: 图标和文字加深到 #0D0D0D，font-weight 600
- 悬停: 背景 #F5F5F3，border-radius 8px
- Padding: 每项 10px 16px，项间距 gap: 2px

### 字体排印
- 字体: 所有 UI 文字用 Inter、system-ui、sans-serif
- Hero 标题例外: Playfair Display 或 Georgia 衬线以增加编辑分量
- 产品名: Inter 700，15-16px
- 正文/描述: Inter 400，14px，#666
- 分区标签: Inter 700，11px，大写，#999，letter-spacing 0.08em
- 导航链接: Inter 500，15px
- 徽章文字: Inter 600，12px

### 色彩系统
- 背景: #F9F9F7
- 表面: #FFFFFF
- 边框: #E8E8E4（主）/ #F0F0ED（细行分隔）
- 品牌橙: #F5852A — CTA、当前 tab、已投票状态、排名指示、星星
- 文字: #0D0D0D（主），#444（次），#666（正文），#999（弱化/元信息）
- 绿: #16A34A — 「Deals」徽章、成功状态
- 黄着色: #FFFBEB — 头名产品行背景
- 绝不用: 重渐变、主内容深色背景、橙色以外的鲜艳强调色

### Upvote 交互状态
- 默认: ▲ 箭头 + 数字，边框 #E8E8E4，文字 #666
- 悬停: 边框 #F5852A 50% 透明度，文字 #F5852A
- 已投: 边框 #F5852A，背景 #FFF5EE，文字 #F5852A，箭头填橙
- 动画: 点击时短暂 scale(1.1)，数字递增

### 响应式规则
- 移动 (<768px): 隐藏两侧栏，单列信息流
- 左侧栏: 通过汉堡抽屉访问
- 右侧栏: 隐藏，「Submit」按钮移到 sticky 底栏
- 产品行: 图标保留，名称 + 描述堆叠，upvote 移到右侧
- Tab: 横向可滚动

### 不要这样做
- 不要用渐变或重阴影 — 处处扁平 1px 边框
- 不要超过一种强调色（橙色是唯一品牌色）
- 产品行高度不要超过 80-90px — 可扫读是全部意义
- 不要隐藏 upvote 数 — 它是主要信任信号
- 产品信息流不要用卡片网格 — 始终列表/表格布局
- 除 #1 高亮和悬停外，不要给单行产品加背景色
- 应用图标圆角不要大于 12px，卡片不要大于 10px
