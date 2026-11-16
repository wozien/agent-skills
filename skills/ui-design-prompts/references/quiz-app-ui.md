# Quiz App UI

- **id:** `quiz-app-ui`
- **别名:** 测验应用, Quiz UI, 答题界面, 计时测验
- **一句话:** 计时、计分、漂亮的紫色。
- **适用:**
  - 测验与 trivia Web 应用
  - 教育评估工具
  - 游戏化引导流程
  - 限时挑战应用
  - 知识测试类 SaaS 产品
- **避免:**
  - 需要中性/企业色板的产品
  - 多用户仪表盘或分析工具
  - 长文内容或文档
  - 紫色品牌与既有识别冲突的产品
- **来源:** https://uidesignprompts.com/prompts/quiz-app-ui

## Prompt

## 测验应用 UI 设计系统

### 气质
有能量、专注、游戏化。每个屏幕都在传达进度、挑战与奖励。紫到粉的渐变是品牌能量——出现在闪屏、题目背景和所有主 CTA。白色卡片浮在柔和薰衣草背景上，把视线留在内容上。设计足够干净，能在压力下阅读（计时器在跑），又足够鲜活，像一场游戏。

### 色彩系统
- 品牌紫: #8B00B0 — 最深品牌色，用于题号、图标、激活边框
- 品牌粉: #E040A0 — 渐变终点、强调
- 主渐变: linear-gradient(135deg, #8B00B0 0%, #E040A0 100%) — **所有**主 CTA 按钮、已选答案状态、闪屏背景
- 背景色调: #F5F3FF — 除闪屏与答题屏外所有屏幕的整页背景
- 白色卡片: #FFFFFF — 所有内容容器；浮在着色背景上
- 主文字: #1A1A2E — 近黑带极淡蓝紫底调
- 次文字: #6B6B8D — 弱化紫灰，用于副标题和元信息
- 答案默认边框: #E8E0FF — 所有未选答案选项
- 答案已选背景: #F8E0FF — 已选项上的浅紫粉着色
- 答案已选边框: #8B00B0 — 已选品牌紫边框
- 正确答案（回顾）: 背景 #D4EDDA，边框 #28A745，文字 #155724
- 错误答案（回顾）: 背景 #FFD6E8，边框 #E040A0，文字 #8B00B0
- 计时器文字: #8B00B0 紫
- 分数高亮: 统计数字用 #8B00B0 紫

### 品牌渐变 — 使用规则
用于:
- 闪屏全背景
- 答题屏全背景（白卡片之后）
- **所有**主 CTA 按钮（Continue、START、Next、Show Results、Retry）
- 已选答案选项状态（淡着色版本）
- 进度条填充

**不**用于:
- 正文任何文字
- 默认状态的答案选项边框
- 卡片背景
- 浅色背景上的 logo（只用紫色）

### Logo / 品牌标记
- 2×2 网格四个圆角方块，各 28×28px，border-radius 6px
- 每块有边框（浅色背景 1.5px solid 品牌紫，深色背景白色）
- 每块一个字母: Q、U、I、Z — font-weight 700，font-size 13px
- 渐变/深色背景: 白边框 + 白字母
- 白/浅色背景: 紫边框 + 紫字母
- Logo 始终与右侧品牌名一起出现: font-size 18px，字重 700，颜色匹配语境
- Logo 图标尺寸: 闪屏 ~52px，欢迎卡片 44px，导航栏 32px

### 屏幕 1 — 闪屏
- 全视口，无滚动
- 背景: linear-gradient(135deg, #8B00B0 0%, #C040B0 50%, #F8B4D9 100%) — 左到右对角
- 内容: 垂直水平居中
- Logo 标记 + 品牌名并排，白色
- 无按钮、无内容 — 纯粹加载/品牌时刻
- 时长: 自动过渡（1.5-2s）或点击继续

### 屏幕 2 — 欢迎 / 模式选择
- 页面背景: #F5F3FF（薰衣草着色）
- 白色居中卡片: max-width 600px，border-radius 16px，box-shadow: 0 4px 24px rgba(139,0,176,0.08)，padding 40px 48px
- Logo 居中于标题上方
- 标题: 「WELCOME TO [App Name]」 — font-size 22px，字重 700，颜色 #1A1A2E，letter-spacing 0.02em
  - App 名部分用渐变文字: background-clip: text，-webkit-text-fill-color: transparent，套用渐变
- 副标题: 「Select any one version to start your Quiz.」 — 14px，#6B6B8D
- 模式选择卡片: 2 列网格，gap 16px
  - 卡片: border-radius 12px，border 2px solid #E8E0FF，padding 24px 20px，text-align center，cursor pointer
  - 默认: 白背景，#E8E0FF 边框，图标弱化紫，标签 #6B6B8D
  - 已选: #F8E0FF 背景，#8B00B0 边框 (2px)，图标鲜紫，标签 #8B00B0 加粗
  - 图标: 40px SVG 秒表/计时器，标签上方居中
  - 标签: 13px，字重 600，text-align center
- Continue 按钮: 全渐变胶囊，居中，width fit-content，padding 12px 48px

### 屏幕 3 — 测验信息 / 开始
- 与屏幕 2 相同的 #F5F3FF 背景 + 白色居中卡片
- Logo 居中，下方品牌名用渐变文字（font-size 20px，字重 700）
- 统计块: 3 行，每行居中，font-size 15px，颜色 #1A1A2E
  - 标签: 常规字重，#6B6B8D
  - 数值: font-weight 700，颜色 #8B00B0（数字）
  - 示例: 「Total questions to attempt: [20]」 — 数值用紫色
- START 按钮: 渐变，border-radius 8px，padding 12px 48px，「START」文字左侧播放图标 (▶)，大写，letter-spacing 0.1em

### 屏幕 4 — 进行中题目（测验进行中）
- 全视口渐变背景: 与闪屏相同
- Logo + 品牌名居中于顶栏，白色
- 白色题目卡片: max-width 620px，居中，border-radius 16px，padding 32px 36px，无阴影（渐变背景提供对比）
- 进度指示（卡片左下）: 4px 高条，border-radius 0 0 0 16px，渐变填充表示完成百分比
- 卡片顶行:
  - 左: 题号 — 大号 「01」用渐变文字（font-size 40px，字重 800，letter-spacing -0.02em）+ 「/08」用 #9B9BB0（font-size 20px，字重 400）
  - 右: 计时器 — 秒表 SVG 图标（24px，#8B00B0）+ 「00:07」格式时间（font-size 18px，字重 700，#8B00B0）
- 题目文字: font-size 17px，字重 500，颜色 #1A1A2E，line-height 1.65，margin 20px 0
- 答案选项: 垂直堆叠，gap 10px
  - 选项: flex 行，border-radius 8px，border 1.5px solid #E8E0FF，padding 14px 18px，cursor pointer
  - 字母标签（A.、B.、C.）: font-size 14px，字重 600，颜色 #9B9BB0，margin-right 12px，flex-shrink 0
  - 选项文字: font-size 15px，字重 500，颜色 #1A1A2E
  - 默认: 白背景，#E8E0FF 边框
  - 悬停: #F8F0FF 背景，#C080E0 边框
  - 已选: #F8E0FF 背景，#8B00B0 边框 (2px)，字母标签变为 #8B00B0，文字加粗
- Next 按钮: 右下，深紫背景 (#6B0090)，白字，border-radius 8px，padding 12px 24px，文字右侧 chevron-right 图标

### 计时器显示规则
- 秒表 SVG 图标: 22-24px，描边风格，颜色 #8B00B0
- 时间格式: MM:SS — 始终各位两位数，零填充（「00:07」不是 「7」）
- 正常状态: #8B00B0 紫字，字重 700
- 警告状态（≤10 秒）: 颜色变为 #E040A0 粉，轻微脉冲动画
- 危急状态（≤5 秒）: 颜色 #DC3545 红，更快脉冲

### 屏幕 5 — 结果回顾
- 背景: #F5F3FF（同一薰衣草着色）
- 无卡片包裹 — 内容全宽，max-width 700px，居中
- 顶部: logo + 品牌名，导航栏风格（左对齐）
- 分数摘要（居中）: 「You attempted questions: [12] / 20」和 「Score secured: [60] / 100」
  - 数字用紫 (#8B00B0)，字重 700，font-size 16px
- 题目回顾列表: 编号（1.、2.、3...），每题块垂直堆叠，gap 24px
  - 题号 + 文字: font-size 15px，字重 500，颜色 #1A1A2E
  - 该题得分: 右对齐，font-size 14px，字重 600
    - 正确得分: #28A745 绿
    - 零分: #E040A0 粉
  - 答案选项: 与答题屏相同布局但更小（padding 10px 14px）
    - 正确答案（无论是否选中）: 绿背景 + 边框
    - 选错的答案: 粉底 + 边框
    - 未选选项: 默认白
- Retry 按钮: 右下，渐变，左侧刷新图标，大写，padding 10px 24px

### 屏幕 6 — 时间到
- 背景: #FFFFFF 或 #F5F3FF — 干净、极简
- 内容居中，无卡片包裹
- 图标: 秒表 SVG，48px，描边色 #8B00B0，居中
- 标题: 「Your time is up!」 — font-size 24px，字重 700，颜色 #8B00B0 或渐变文字
- 副文: 描述性信息 — font-size 15px，颜色 #6B6B8D
- Show Results 按钮: 渐变，居中

### 屏幕 7 — 完成
- 与「时间到」相同的极简布局
- 图标: 勾选圆圈 SVG，48px，描边色 #8B00B0（不填充 — 只有描边圆圈内含 ✓）
- 标题: 「Done!」 — font-size 28px，字重 700，渐变文字
- 副文: 「You have attempted X questions in total.」 — 15px，#6B6B8D
- Show Results 按钮: 渐变，居中

### 按钮系统
所有按钮使用以下三种样式之一:

**主渐变按钮:**
- background: linear-gradient(135deg, #8B00B0 0%, #E040A0 100%)
- color: white
- border: none
- border-radius: 8px
- padding: 12px 32px
- font-size: 15px, font-weight: 600
- letter-spacing: 0.05em
- 悬停: opacity 0.9 + translateY(-1px)
- 激活: translateY(1px)

**深紫按钮（Next）:**
- background: #5A0080
- color: white
- border-radius: 8px
- padding: 12px 20px
- 右侧有图标（chevron ›）

**Ghost 按钮（次级）:**
- background: transparent
- border: 2px solid #8B00B0
- color: #8B00B0
- border-radius: 8px
- 用于 Cancel 或 Back 操作

### 字体排印
- 字体: Inter，或 system-ui，sans-serif
- 题号: 40-48px，字重 800，渐变文字
- 题目文字: 16-17px，字重 500，#1A1A2E
- 答案选项文字: 14-15px，字重 500，#1A1A2E
- 按钮文字: 14-15px，字重 600，主 CTA 用大写
- 标签/元信息: 13-14px，字重 400-500，#6B6B8D
- 统计数值: 14-16px，字重 700，#8B00B0

### 卡片容器
- 所有主卡片 border-radius: 16px
- 背景: #FFFFFF
- Box-shadow: 0 4px 24px rgba(139, 0, 176, 0.08) — 紫色调阴影
- Padding: 32-48px，视内容密度
- Max-width: 560-640px，居中，margin auto

### 响应式规则
- 移动: 卡片全宽（padding 20px），字号略缩小
- 题号: 移动端从 48px 缩到 32px
- 模式选择: 小屏 2 列网格收成 1 列
- 计时器保持右对齐，移动端缩到 14px
- 答案选项: 始终全宽，padding 减至 12px 14px

### 进度指示
- 题目卡片底部细条（4px 高）
- 宽度: 卡片 100%，border-radius 0 0 16px 16px
- 填充: 从左渐变，百分比基于当前题 / 总题
- 轨道背景: #E8E0FF

### 动画
- 屏幕过渡: 淡入（300ms ease）
- 答案选择: 背景色过渡 150ms ease
- 按钮悬停: transform translateY(-1px) + opacity 150ms
- 计时器警告脉冲: @keyframes pulse { 0%,100% { opacity:1 } 50% { opacity:0.5 } }
- 完成图标（勾选/时钟）: scale(0) → scale(1) 带 bounce，400ms

### 不要这样做
- 不要把渐变用在限时压力下需要可读的文字上
- 每题不要超过 5 个答案选项 — 3-4 个最优
- 答题进行中不要加复杂动画 — 保持无干扰
- 答题进行中不要显示对/错状态 — 只在回顾屏显示
- 不要把粉色渐变当文字背景 — 对比失败
- 不要在题目卡片内加导航链接 — 唯一动作是选题或点 Next
