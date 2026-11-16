# Newsletter UI

- **id:** `newsletter-ui`
- **别名:** 通讯 UI, Newsletter, 订阅落地页, 独立媒体, 编辑向首页
- **一句话:** 编辑气质、订阅者优先，把读者变成粉丝。
- **适用:**
  - Newsletter 落地页与刊物首页
  - 独立媒体品牌与内容创作者
  - 博客平台与个人刊物
  - 思想领导力与长文内容产品
  - 需要编辑向展示的创作者工具
- **避免:**
  - 阅读不是主行为的 SaaS 产品
  - 电商或交易型产品
  - 需要高能量、强转化压迫感设计的产品
  - 开发者工具或技术产品
- **来源:** https://uidesignprompts.com/prompts/newsletter-ui

## Prompt

## Newsletter UI 设计系统

### 气质
编辑向、温暖、订阅者优先。感觉像一份认真对待读者的刊物——而不是碰巧带了注册表单的 SaaS 落地页。每个设计决策都服务于阅读：充裕的行高、衬线正文、让人想点进去的文章预览。布局传达：「这里有真正的思考。」

### 核心色彩系统
- 纸张背景: #FAF7F2 — 温暖米白，像陈年纸。绝不用纯白。
- 墨色: #1A1410 — 近黑带暖底调。绝不用纯 #000000。
- 锈红强调: #C4442A — 唯一表情色。用于: 分类标签（悬停）、CTA 按钮、引文、作者名、期号、当前导航状态。
- 弱化文字: #6B6560 — 用于日期、阅读时长、作者简介、次级标签。
- 暖边框: #E8E0D5 — 所有分割线与卡片边框。暖米色调。
- 标签背景: #F0EBE3 — 胶囊标签填充、代码背景、精选徽章。
- 深色面板: #1A1410 — 用于 newsletter 订阅区。通栏深色配暖白文字。
- 白色: #FFFFFF — 文章卡片表面，从纸张背景上抬起。

### 字体系统 — 编辑向字族
两套字体，精确分工:

**展示 / 标题 — 衬线:**
- 字体: Playfair Display、Lora 或 Georgia（衬线分量与编辑权威）
- H1 hero: clamp(40px, 5vw, 68px)，字重 700，letter-spacing -0.02em，line-height 1.1
- H2 章节标题: clamp(28px, 3vw, 40px)，字重 700，letter-spacing -0.02em
- H3 文章标题: 20-24px，字重 600，letter-spacing -0.01em，line-height 1.3
- 文章卡片标题悬停: 颜色转为锈红 (#C4442A)
- 衬线用于: hero 大标题、文章标题、引文、大场景下的作者名

**正文 / UI — 无衬线:**
- 字体: Inter、system-ui 或 DM Sans
- 正文: 16px，字重 400，line-height 1.75，颜色 #1A1410
- 文章摘要: 15px，字重 400，颜色 #6B6560，line-height 1.65
- 分类标签: 11px，字重 600，letter-spacing 0.08em，大写
- 导航链接: 14px，字重 500
- 元信息（日期、阅读时长）: 13px，字重 400，颜色 #6B6560
- 图注 / 脚注: 13px，颜色 #6B6560，font-style italic

### 布局架构
页面由目的清晰的水平条带构成:

```
┌─────────────────────────────────────────────┐
│  期号条  （细条，期号 # + 日期）              │
├─────────────────────────────────────────────┤
│  导航栏  （logo + 导航 + 订阅 CTA）           │
├─────────────────────────────────────────────┤
│  HERO  （精选文章，全宽）                     │
│  ┌──────────────────────────┬──────────┐    │
│  │  精选文章 (60%)          │ 侧栏     │    │
│  │  分类标签                │ (40%)    │    │
│  │  大衬线标题              │ 本期精选 │    │
│  │  摘要 + 元信息           │          │    │
│  └──────────────────────────┴──────────┘    │
├─────────────────────────────────────────────┤
│  数据条  （订阅者 · 期数 · 等）               │
├─────────────────────────────────────────────┤
│  文章网格  （「最新刊期」）                    │
│  混合布局: 每行 1 宽 + 2 窄                  │
├─────────────────────────────────────────────┤
│  主题标签  （横向筛选条）                     │
├─────────────────────────────────────────────┤
│  作者区  （水平分割条带）                     │
├─────────────────────────────────────────────┤
│  NEWSLETTER 订阅  （深色通栏）                │
├─────────────────────────────────────────────┤
│  页脚                                        │
└─────────────────────────────────────────────┘
```

### 期号条（报头细条）
导航栏上方的细条——真正刊物的签名元素:
- 背景: #1A1410（深墨）
- 高度: 36px
- 内容: 左 — 「ISSUE #47 · JUNE 10, 2026」小 caps + 弱化文字；右 — 社交链接 + RSS
- 字体: 11px，字重 600，letter-spacing 0.1em，大写
- 颜色: 文字 rgba(255,255,255,0.6)，期号 #C4442A
- 分隔符: 「 · 」用锈红色

### 导航栏
- 背景: #FAF7F2（与页面背景相同——无抬升）
- Border-bottom: 1px solid #E8E0D5
- 高度: 64px
- 左: 刊物 logo（衬线字标 **或** 图标 + 字标）
- 中: 导航链接 — Topics、Archive、About、Podcast（14px，字重 500）
- 右: 「Subscribe free →」按钮，锈红 (#C4442A)，胶囊形，白字
- 当前导航项: 锈红下划线（2px border-bottom）
- 滚动时 sticky

### Hero 区 — 精选文章
两列非对称布局（60/40 分割）:

**左栏（精选文章）:**
- 分类标签胶囊: 大写，11px，字重 700，letter-spacing 0.08em，锈红字 + 标签背景填充
- 期号: 小，锈红色，字重 600，在标题上方
- 标题: 大衬线，clamp(36px, 4vw, 56px)，字重 700，紧字距，墨色，line-height 1.1
- 摘要: 16-17px 无衬线，#6B6560，最多 3 行，line-height 1.65
- 元信息行: 作者头像（32px 圆）+ 作者名 + 「 · 」+ 日期 + 「 · 」+ 阅读时长
- CTA: 「Read this issue →」 — 锈红色，无按钮背景，悬停下划线
- 装饰: 巨大期号作背景水印（opacity 0.04，超大衬线字）

**右栏（侧栏本期）:**
- 标签: 「ALSO IN THIS ISSUE」 — 10px，大写，letter-spacing 0.1em，弱化
- 3-4 条小文章项: 每条之间细分割线
- 每项: 分类标签 + 标题（16px 衬线，2 行截断）+ 阅读时长
- 简洁，无摘要、无图 — 与左侧大精选形成对比

### 数据条
Hero 与文章网格之间的通栏细带:
- 背景: #F0EBE3（标签背景 — 比页面略深）
- Border-top + border-bottom: 1px solid #E8E0D5
- 4 个数据横向 flex: 订阅者、已发期数、平均阅读时长、运营年数
- 每项: 衬线加粗数字 (#1A1410) + 下方 12px 弱化无衬线标签
- 分隔: 数据之间 1px 竖线 #E8E0D5
- Padding: 20px 40px

### 文章网格 — 「最新刊期」
页面的编辑心脏。**不是**均匀卡片网格 — 使用混合尺寸:

**行模式（交替）:**
```
第 1 行: [宽卡片 2/3] [窄卡片 1/3]
第 2 行: [窄 1/3] [窄 1/3] [窄 1/3]
第 3 行: [宽卡片 1/3] [窄卡片 2/3]
```

**文章卡片解剖:**
- 背景: #FFFFFF（从 #FAF7F2 上抬起）
- 边框: 1px solid #E8E0D5
- Border-radius: 8px
- 默认无 box-shadow
- 悬停: box-shadow: 0 4px 20px rgba(26,20,16,0.08)，轻微 translateY(-2px)
- 图区: aspect-ratio 16/9（宽）或 4/3（窄），object-fit cover，border-radius 6px 6px 0 0，border-bottom 1px solid #E8E0D5
- 卡片正文 padding: 20px 24px 22px
- 分类标签: 胶囊，悬停锈红背景，默认标签背景
- 标题: 衬线，18-22px（宽）或 16-18px（窄），字重 600，墨色，悬停 → 锈红
- 摘要: 14px 无衬线，弱化，2 行截断
- 元信息: 作者 + 日期 + 阅读时长，12px 弱化，flex 行用圆点分隔

**宽卡片额外:**
- 标题略大（20-22px）
- 摘要 3 行而非 2 行
- 精选徽章选项: 右上角 「EDITOR'S PICK」标签

### 分类标签组件
全局使用 — 文章卡片、hero、主题条:
```css
.tag {
  display: inline-flex;
  align-items: center;
  background: #F0EBE3;
  color: #6B6560;
  border: 1px solid #E8E0D5;
  border-radius: 100px;
  padding: 3px 12px;
  font-size: 11px;
  font-weight: 600;
  letter-spacing: 0.08em;
  text-transform: uppercase;
  text-decoration: none;
  transition: background 0.15s, color 0.15s;
}
.tag:hover {
  background: #C4442A;
  color: #FFFFFF;
  border-color: #C4442A;
}
```

### 主题标签条
文章网格与作者区之间的横向可滚动筛选条:
- 背景: #FAF7F2（与页面相同）
- Border-top + border-bottom: 1px solid #E8E0D5
- Padding: 16px 40px
- 「Browse by topic:」标签 13px 弱化，后接标签胶囊
- 标签: 使用上方标准标签组件
- 当前标签: 锈红背景、白字（与 .tag:hover 相同）
- 溢出: 移动端横向滚动隐藏，桌面 flex-wrap

### 作者区
通栏水平条带 — 两列分割:

**左: 作者身份**
- 作者头像: 80px 圆，border 2px solid #E8E0D5
- 下方: 作者名衬线 24px 字重 700，悬停锈红
- 角色/标语: 14px 弱化无衬线
- 短简介: 15px 无衬线，最多 100 词，#6B6560，line-height 1.7
- 社交链接: Twitter/X、LinkedIn、RSS — 文字链接，13px，弱化，悬停锈红
- 资质: 展示专长的小胶囊标签

**右: 作者数据 + CTA**
- 3 个数据瓦片: 已写文章、订阅者、写作年数 — 每块有边框
- 「Get every issue →」CTA 按钮: 锈红、胶囊、白字
- 近期文章迷你列表: 3 个标题，衬线，15px，带期号

**分割线:** 1px solid #E8E0D5，区块上下通栏

### Newsletter 订阅区 — 转化时刻
通栏深色区块。最重要的转化元素:

**布局:** 两列 — 左: 价值主张；右: 表单
- 背景: #1A1410（深墨）
- Padding: 72px 40px
- 顶部: 小锈红标签 「JOIN THE COMMUNITY」 — 11px 大写 letter-spacing

**左栏:**
- 标题: 衬线，clamp(28px, 3.5vw, 44px)，白色，字重 700，line-height 1.15
- 副标题: 16px 无衬线，rgba(255,255,255,0.65)，line-height 1.65，max-width 380px
- 信任信号行（文字下方）:
  - 订阅数: 「12,400+ readers」配头像堆叠
  - 频率: 「Published weekly」
  - 承诺: 「Unsubscribe anytime」
- 每条信任信号: flex 行，锈红勾选图标，14px 白字

**右栏（注册表单）:**
- 姓名输入（可选）+ 邮箱输入 — 垂直堆叠
- 输入样式:
  - Background: rgba(255,255,255,0.08)
  - Border: 1px solid rgba(255,255,255,0.2)
  - Border-radius: 6px
  - Padding: 14px 16px
  - Color: white
  - Placeholder: rgba(255,255,255,0.4)
  - Focus: border-color: #C4442A, box-shadow: 0 0 0 3px rgba(196,68,42,0.2)
- 提交按钮: 全宽，#C4442A 背景，白字，border-radius 6px，font-weight 600
- 隐私行: 「No spam. Unsubscribe at any time.」 — 12px，rgba(255,255,255,0.35)，text-align center

### 页脚
- 背景: #1A1410（延续订阅区深色）
- 上段: 左 logo + 标语；右分组导航链接（3-4 列）
- 链接列: 标题 rgba(255,255,255,0.4) 11px 大写；链接 rgba(255,255,255,0.6) 14px
- 分割线: 1px solid rgba(255,255,255,0.1)
- 底部: 左版权，右社交图标（简单文字链接）
- 不要重边框 — 深色背景本身提供分隔

### 引文组件（用于文章预览）
当网格中的文章带引文时:
```css
.pull-quote {
  border-left: 3px solid #C4442A;
  padding: 12px 20px;
  font-family: [serif font];
  font-size: 17px;
  font-style: italic;
  color: #1A1410;
  background: #F0EBE3;
  border-radius: 0 6px 6px 0;
  margin: 16px 0;
}
```

### 头像堆叠（社会证明）
用于订阅区和 hero:
```css
.avatar-stack { display: flex; align-items: center; }
.avatar-stack .av {
  width: 32px; height: 32px;
  border-radius: 50%;
  border: 2px solid #1A1410; /* 深色背景上改为白色 */
  margin-left: -8px;
  background: #E8E0D5;
  overflow: hidden;
  flex-shrink: 0;
}
.avatar-stack .av:first-child { margin-left: 0; }
```

### 响应式规则
- 移动 (<768px): hero 单列堆叠（精选在上，侧栏消失），文章网格 → 1 列，作者区堆叠，订阅表单堆叠
- 平板 (768-1024px): 文章网格 → 2 列（宽卡片全宽，然后 2 列网格）
- 移动端隐藏期号条 — 信息密度对过小屏幕过高
- 数据条 → 移动端 2×2 网格
- 主题条 → 横向滚动，-webkit-overflow-scrolling: touch

### 不要这样做
- 不要用全部等大的卡片网格 — 尺寸变化才有编辑感
- 不要用无衬线做文章标题 — 衬线是刊物气质的承重结构
- 不要把页面做成纯白 — 暖纸色调 (#FAF7F2) 必不可少
- 不要超过一种强调色 — 锈红 (#C4442A) 是唯一表情色
- 不要让订阅表单看起来像获客小部件 — 应像加入一件有意义的事
- 导航链接不要超过 3 个 — 编辑导航关乎主题，不是产品功能
- 文章卡片圆角不要大于 8px — 这是编辑设计，不是 App 设计
- 不要居中文章正文 — 始终左对齐
