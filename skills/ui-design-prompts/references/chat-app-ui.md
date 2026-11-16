# Chat App UI

- **id:** `chat-app-ui`
- **别名:** 聊天应用 UI, 团队协作聊天, Slack 风格, 频道线程界面, 工作区聊天
- **一句话:** 三栏。一个目的。始终在上下文中。
- **适用:**
  - 需要应用内消息或通知流的 SaaS 产品
  - 工程或运维团队的内部工具
  - 客户支持聊天门户
  - 社区平台与创作者空间
  - 需要频道/线程 UI 模式的开发者工具
  - 任何在做 Slack 替代品或工作区产品的人
- **避免:**
  - 消费级一对一即时通讯（改用 iMessage/WhatsApp 气泡风格）
  - 更干净的是单线程无侧栏布局的 AI 聊天界面
  - 简单评论区或问答流
  - 聊天只是次要功能、不是核心界面的产品
- **来源:** https://uidesignprompts.com/prompts/chat-app-ui

## Prompt

## 聊天应用 UI 设计系统 — 团队协作

### 概念与气质
这是一套专业的团队沟通界面。设计语言目的明确、信息密度高——为每天在里面待 8 小时的人打造。每个像素都要挣得存在。深色侧栏用于寻路，白色消息区用于阅读，紫色强调用于操作和焦点状态。

三栏布局建立清晰信息层级：工作区上下文（最左）→ 频道导航（侧栏）→ 对话（主区）。用户始终知道自己在哪，切换上下文时不会丢失位置。

参考：Slack 浅色主题 + Discord 服务器轨 = 干净、熟悉、立刻能上手的界面。

### 色彩系统
两个截然不同的区域——深色导航 + 浅色内容。彼此永不渗入。

**深色区（工作区轨 + 侧栏）：**
- 工作区轨：`#1A1D21` — 带冷调的近黑
- 侧栏背景：`#19171D` — 极深紫灰
- 侧栏悬停：`#27242D` — 悬停时变浅
- 激活频道背景：`rgba(255,255,255,0.1)` — 微妙白色着色
- 侧栏文字：`#C9C3D4` — 浅紫灰
- 侧栏弱化：`#78748A` — 用于分区标题和不重要项
- 未读指示：`#E01E5A` — 红色胶囊徽章

**浅色区（消息）：**
- 消息区背景：`#FFFFFF`
- 消息悬停背景：`#F8F8F8`
- 主文字：`#1D1C1D`
- 时间戳 / 元信息：`#616061`
- 边框：`#E8E8E8`
- 输入框边框：`#C7C7C7`
- 输入焦点：`#6C5CE7` 环

**强调色（紫色 — 操作、焦点、品牌）：**
- 主色：`#6C5CE7`
- 浅色：`#8B7CF6`
- 用于：发送按钮、激活频道高亮、链接文字、焦点环、提及高亮、在线状态环

**状态色：**
- 在线：`#2BAC76` — 绿
- 离开：`#FAB005` — 黄
- 请勿打扰：`#E01E5A` — 红
- 离线：`#78748A` — 灰

### 布局架构 — 三栏

```
┌──────────┬────────────────────┬──────────────────────────────┬──────────────┐
│ 工作区    │ 频道侧栏            │ 消息线程                      │ 成员面板      │
│  轨      │                    │                              │ （可折叠）    │
│  48px    │  220px             │  flex: 1                     │  240px       │
│          │                    │                              │              │
│ [图标]   │ # general    3     │ ┌─ 频道页头 ─────────────────┐ │ 成员 (12)    │
│ [图标]   │ # design           │ │  # general · 12 位成员     │ │              │
│ [图标]   │ # dev-ops    1     │ └──────────────────────────┘ │ ● Sarah M.   │
│ [图标] ← │ # random           │                              │ ● Ahmed K.   │
│ 激活     │                    │ [消息滚动区]                  │ ○ Nadia R.   │
│          │ 私信                │                              │              │
│ ─────    │ ● Sarah M.         │ ┌─ 消息输入 ─────────────────┐ │              │
│  [+]     │ ● Ahmed            │ │  发送到 #general…  [发送]  │ │              │
└──────────┴────────────────────┴──────────────────────────────┴──────────────┘
```

### 第 1 列 — 工作区轨（宽 48px）
垂直的工作区图标条。类似 Discord 的服务器列表。
- 每个工作区：36px 方形图标，`border-radius: 10px`，悬停出 tooltip
- 激活工作区：彩色边框（紫色强调）+ 完整 `border-radius: 10px`
- 未激活：`border-radius: 10px`，灰度，悬停变亮
- 底部：添加工作区 `+` 按钮，带状态环的用户头像

```css
.workspace-rail {
  width: 68px; background: #1A1D21;
  display: flex; flex-direction: column;
  align-items: center; padding: 12px 0; gap: 8px;
  border-right: 1px solid rgba(255,255,255,0.06);
}
.workspace-icon {
  width: 40px; height: 40px; border-radius: 10px;
  display: flex; align-items: center; justify-content: center;
  font-weight: 700; font-size: 1rem; cursor: pointer;
  transition: border-radius 150ms, filter 150ms;
  position: relative;
}
.workspace-icon.active { outline: 3px solid #6C5CE7; outline-offset: 2px; }
.workspace-icon:not(.active) { filter: grayscale(0.4); }
.workspace-icon:not(.active):hover { filter: grayscale(0); border-radius: 14px; }
```

### 第 2 列 — 频道侧栏（220px）
深色侧栏，始终可见。顶部：工作区名称 + chevron。然后：可滚动分区。

结构：
```
[工作区名称 ▾]          ← 带选项菜单触发器的页头
──────────────────
CHANNELS
  # general          [3]    ← 未读徽章
  # design
  # dev-ops          [1]
  # random
[+ 添加频道]
──────────────────
DIRECT MESSAGES
  ● Sarah M.               ← 绿点 = 在线
  ● Ahmed K.
  ○ Nadia R.               ← 灰 = 离线
[+ 新消息]
```

```css
.sidebar {
  width: 220px; background: #19171D;
  display: flex; flex-direction: column;
  overflow-y: auto; border-right: 1px solid rgba(255,255,255,0.06);
  flex-shrink: 0;
}
.sidebar-header {
  padding: 14px 16px; border-bottom: 1px solid rgba(255,255,255,0.06);
  display: flex; align-items: center; justify-content: space-between;
}
.workspace-name { font-size: 0.9375rem; font-weight: 700; color: #fff; }

.sidebar-section { padding: 20px 0 4px; }
.sidebar-section-label {
  font-size: 0.6875rem; font-weight: 700; text-transform: uppercase;
  letter-spacing: 0.08em; color: #78748A;
  padding: 0 16px; margin-bottom: 4px;
}

.channel-item {
  display: flex; align-items: center; justify-content: space-between;
  padding: 5px 16px; border-radius: 4px; margin: 1px 8px;
  cursor: pointer; font-size: 0.9375rem; color: #C9C3D4;
  transition: background 100ms;
}
.channel-item:hover { background: #27242D; }
.channel-item.active { background: rgba(108,92,231,0.2); color: #fff; }
.channel-item.unread { color: #fff; font-weight: 600; }

.channel-name { display: flex; align-items: center; gap: 6px; }
.channel-hash { color: #78748A; font-size: 1rem; font-weight: 400; }
.channel-item.active .channel-hash, .channel-item.unread .channel-hash { color: #C9C3D4; }

.unread-badge {
  font-size: 0.6875rem; font-weight: 700; min-width: 18px; height: 18px;
  padding: 0 5px; border-radius: 999px;
  background: #E01E5A; color: #fff;
  display: flex; align-items: center; justify-content: center;
}

.dm-item {
  display: flex; align-items: center; gap: 8px;
  padding: 5px 16px; border-radius: 4px; margin: 1px 8px;
  cursor: pointer; font-size: 0.9375rem; color: #C9C3D4;
  transition: background 100ms;
}
.dm-item:hover { background: #27242D; }
.dm-item.active { background: rgba(108,92,231,0.2); color: #fff; }

.status-dot {
  width: 8px; height: 8px; border-radius: 50%; flex-shrink: 0;
}
.status-dot.online { background: #2BAC76; }
.status-dot.away   { background: #FAB005; }
.status-dot.dnd    { background: #E01E5A; }
.status-dot.offline { background: #78748A; }

.sidebar-add-btn {
  display: flex; align-items: center; gap: 6px;
  padding: 5px 16px; margin: 1px 8px; border-radius: 4px;
  font-size: 0.875rem; color: #78748A; cursor: pointer;
  transition: color 100ms, background 100ms;
}
.sidebar-add-btn:hover { color: #C9C3D4; background: #27242D; }
```

### 第 3 列 — 消息线程（flex: 1）
白色背景。三个区域：顶栏、可滚动消息、粘性输入。

**顶栏：**
- 频道名（`# general`）粗体，`#1D1C1D`
- 可选：频道描述 / 主题，更小弱化文字
- 右侧：成员数、搜索图标、成员面板切换按钮

```css
.channel-header {
  height: 56px; padding: 0 20px;
  display: flex; align-items: center; justify-content: space-between;
  border-bottom: 1px solid #E8E8E8;
  background: #fff; flex-shrink: 0;
}
.channel-title { font-size: 1rem; font-weight: 700; color: #1D1C1D; display: flex; align-items: center; gap: 6px; }
.channel-topic { font-size: 0.8125rem; color: #616061; margin-left: 12px; padding-left: 12px; border-left: 1px solid #E8E8E8; }
.header-actions { display: flex; align-items: center; gap: 8px; }
.header-icon-btn { width: 32px; height: 32px; border-radius: 6px; border: none; background: none; cursor: pointer; display: flex; align-items: center; justify-content: center; color: #616061; transition: background 100ms; }
.header-icon-btn:hover { background: #F8F8F8; color: #1D1C1D; }
```

**消息列表：**
每组消息：头像 + 发送者名 + 时间戳，然后是消息行。同一发送者的消息成组（5 分钟内不重复头像）。

```css
.messages-area { flex: 1; overflow-y: auto; padding: 20px 20px 0; }

.message-group { display: flex; gap: 12px; padding: 8px 8px; border-radius: 6px; transition: background 80ms; }
.message-group:hover { background: #F8F8F8; }
.message-group + .message-group.same-sender { padding-top: 2px; }

.avatar {
  width: 36px; height: 36px; border-radius: 50%; flex-shrink: 0;
  display: flex; align-items: center; justify-content: center;
  font-size: 0.875rem; font-weight: 700; color: #fff;
}
.avatar-spacer { width: 36px; flex-shrink: 0; } /* 用于连续消息 */

.message-meta { display: flex; align-items: baseline; gap: 8px; margin-bottom: 3px; }
.sender-name { font-size: 0.9375rem; font-weight: 700; color: #1D1C1D; cursor: pointer; }
.sender-name:hover { text-decoration: underline; }
.message-time { font-size: 0.75rem; color: #616061; }

.message-text { font-size: 0.9375rem; color: #1D1C1D; line-height: 1.5; }
.message-text a { color: #6C5CE7; text-decoration: none; }
.message-text a:hover { text-decoration: underline; }
.mention { color: #6C5CE7; background: rgba(108,92,231,0.1); padding: 0 3px; border-radius: 3px; font-weight: 500; }
.code-inline { background: #F4F4F4; border: 1px solid #E8E8E8; border-radius: 4px; padding: 1px 6px; font-family: 'JetBrains Mono', monospace; font-size: 0.8125rem; color: #E01E5A; }

/* 反应 */
.reactions { display: flex; gap: 6px; margin-top: 6px; flex-wrap: wrap; }
.reaction {
  display: inline-flex; align-items: center; gap: 4px;
  padding: 3px 8px; border-radius: 999px;
  border: 1px solid #E8E8E8; background: #FAFAFA;
  font-size: 0.8125rem; color: #616061; cursor: pointer;
  transition: border-color 100ms, background 100ms;
}
.reaction:hover, .reaction.mine { border-color: #6C5CE7; background: rgba(108,92,231,0.08); color: #6C5CE7; }
.reaction-emoji { font-size: 0.9375rem; }

/* 文件附件 */
.attachment {
  margin-top: 8px; padding: 10px 14px;
  border: 1px solid #E8E8E8; border-radius: 8px;
  display: flex; align-items: center; gap: 10px;
  background: #FAFAFA; max-width: 320px;
}
.attachment-icon { font-size: 1.5rem; }
.attachment-name { font-size: 0.875rem; font-weight: 600; color: #1D1C1D; }
.attachment-meta { font-size: 0.75rem; color: #616061; }
```

**正在输入指示：**
```css
.typing-indicator { padding: 6px 20px; font-size: 0.8125rem; color: #616061; height: 28px; }
.typing-dots span { display: inline-block; width: 6px; height: 6px; border-radius: 50%; background: #78748A; margin: 0 1px; animation: typingBounce 1.4s infinite; }
.typing-dots span:nth-child(2) { animation-delay: 0.2s; }
.typing-dots span:nth-child(3) { animation-delay: 0.4s; }
@keyframes typingBounce { 0%,60%,100%{transform:translateY(0)} 30%{transform:translateY(-4px)} }
```

**消息输入：**
底部富输入条。顶边框，白背景。

```css
.message-input-wrap {
  padding: 12px 20px 20px;
  border-top: 1px solid #E8E8E8; background: #fff; flex-shrink: 0;
}
.input-box {
  display: flex; align-items: center; gap: 0;
  border: 1.5px solid #C7C7C7; border-radius: 8px;
  background: #fff; transition: border-color 150ms;
}
.input-box:focus-within { border-color: #6C5CE7; box-shadow: 0 0 0 3px rgba(108,92,231,0.1); }
.input-actions-left { display: flex; padding: 0 8px; gap: 2px; }
.input-icon-btn { width: 30px; height: 30px; border: none; background: none; cursor: pointer; border-radius: 4px; display: flex; align-items: center; justify-content: center; color: #616061; font-size: 1rem; transition: background 100ms, color 100ms; }
.input-icon-btn:hover { background: #F4F4F4; color: #1D1C1D; }
.input-field { flex: 1; border: none; outline: none; font-size: 0.9375rem; color: #1D1C1D; font-family: 'Inter', sans-serif; padding: 10px 8px; background: transparent; resize: none; line-height: 1.5; min-height: 42px; }
.input-field::placeholder { color: #C7C7C7; }
.send-btn { margin: 6px; width: 32px; height: 32px; border-radius: 6px; border: none; background: #6C5CE7; color: #fff; cursor: pointer; display: flex; align-items: center; justify-content: center; transition: background 150ms; flex-shrink: 0; }
.send-btn:hover { background: #5B4BD6; }
.send-btn:disabled { background: #E8E8E8; color: #C7C7C7; cursor: not-allowed; }
```

### 第 4 列 — 成员面板（240px，可折叠）
右侧面板，按状态分组显示频道成员（在线、离开、离线）。由顶栏按钮切换。以 `transition: width 200ms, opacity 200ms` 滑入/滑出。

```css
.member-panel {
  width: 240px; background: #fff;
  border-left: 1px solid #E8E8E8;
  overflow-y: auto; flex-shrink: 0;
  transition: width 200ms, opacity 200ms;
}
.member-panel.hidden { width: 0; opacity: 0; overflow: hidden; }
.member-panel-header { padding: 16px; font-size: 0.875rem; font-weight: 700; color: #1D1C1D; border-bottom: 1px solid #E8E8E8; }
.member-group-label { font-size: 0.6875rem; font-weight: 700; text-transform: uppercase; letter-spacing: 0.08em; color: #616061; padding: 14px 16px 6px; }
.member-item { display: flex; align-items: center; gap: 10px; padding: 6px 16px; transition: background 100ms; cursor: pointer; }
.member-item:hover { background: #F8F8F8; }
.member-avatar { width: 28px; height: 28px; border-radius: 50%; display: flex; align-items: center; justify-content: center; font-size: 0.75rem; font-weight: 700; color: #fff; position: relative; flex-shrink: 0; }
.member-status-ring { position: absolute; bottom: -1px; right: -1px; width: 10px; height: 10px; border-radius: 50%; border: 2px solid #fff; }
.member-status-ring.online { background: #2BAC76; }
.member-status-ring.away   { background: #FAB005; }
.member-status-ring.offline { background: #78748A; }
.member-name { font-size: 0.875rem; color: #1D1C1D; font-weight: 500; }
.member-role { font-size: 0.75rem; color: #616061; }
```

### 响应式行为
- 桌面（≥1024px）：四列全部可见
- 平板（768–1023px）：成员面板默认隐藏，工作区轨收成仅图标
- 移动端（<768px）：侧栏变为由汉堡触发的底部抽屉或抽屉；消息区全屏；成员面板隐藏

```css
@media (max-width: 768px) {
  .workspace-rail { display: none; }
  .sidebar { position: fixed; left: -100%; top: 0; bottom: 0; z-index: 200; transition: left 250ms; }
  .sidebar.open { left: 0; }
  .member-panel { display: none; }
  .channel-header { padding: 0 12px; }
  .messages-area { padding: 12px; }
  .message-input-wrap { padding: 8px 12px 16px; }
}
```

### 切勿做
- ✗ 永远不要给侧栏用浅色背景——此模式深色侧栏不可协商
- ✗ 永远不要居中对齐消息——聊天从左到右阅读，全宽
- ✗ 永远不要用带尾巴的对话气泡——那是个人聊天模式，不是团队聊天
- ✗ 永远不要使用超过一种强调色——紫色是唯一品牌色
- ✗ 永远不要给消息线程加动画（平滑滚动除外）——会打断阅读流
- ✗ 永远不要在每条消息上显示时间戳——只在每组第一条
- ✗ 永远不要给消息区加背景图——只许白色
- ✗ 永远不要在移动端默认显示成员面板——始终隐藏

### 待替换数据（占位映射）
- `[WORKSPACE_NAME]` — 显示在侧栏页头
- `[WORKSPACE_ICONS]` — 工作区头像数组（字母 + 颜色）
- `[CHANNELS]` — 数组：频道名、未读数、is-active 布尔
- `[DM_LIST]` — 数组：姓名、状态（online/away/offline）
- `[MESSAGES]` — 数组：发送者名、头像颜色、消息文本、时间戳、反应、附件
- `[MEMBERS]` — 数组：姓名、头像颜色、角色、状态
- `[CHANNEL_TOPIC]` — 顶栏中显示的短描述行
- `[CURRENT_USER]` — 登录用户姓名 + 显示在侧栏页脚的头像
