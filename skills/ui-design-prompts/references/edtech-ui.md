# Edtech UI

- **id:** `edtech-ui`
- **别名:** 教育科技 UI, 课程学院落地页, 暗色教育品牌, AI 学院界面
- **一句话:** 一张脸、一套项目、一份证明。向你看得见的人学习。
- **适用:**
  - AI 学院与 AI 技能提升机构
  - 编程训练营与技术培训项目
  - 创作者主导、创始人主导的课程业务
  - 有可见讲师的同期班项目
  - 卖会员加免费引流磁铁的社区
  - 面向创始人、学生和年轻专业人士的教育品牌
  - 需要按职业或城市做 SEO 落地页的项目
- **避免:**
  - 传统大学或认证机构（需要更冷静、更正式的系统）
  - 面向儿童的教育（需要明亮、好玩的色板和更大字体）
  - 企业合规或 LMS 门户（需要稠密、实用的仪表盘风格）
  - 没有讲师或没有视频证明可展示的项目
- **来源:** https://uidesignprompts.com/prompts/edtech-ui

## Prompt

## 教育科技 UI 设计系统

### 你在构建什么
为教育品牌做一页暗色、媒体优先的落地页：一位可见的讲师或创始人在出售知识。访客应按此顺序感受到三件事：
1. 这是真人在教真技能（面孔、视频、样机）。
2. 像我这样的人已经做到了（带姓名和账号的视频证言）。
3. 我今天就能免费开始（引流磁铁），然后再承诺加入一个项目。

用户将提供自己的品牌名、讲师、项目、资源、证言和课程。按下面结构搭建每一节，填入用户内容。绝不要保留本提示中的占位品牌名。

### 视觉识别 — 黑、光晕、青柠
- 页面是黑（`#000`），区块在纯黑与从左下角升起绿光的黑色区块之间交替。
- 只有一种强调色：电青柠 `#BFF010`。用于：标题中高亮词、主药丸按钮、播放按钮、标签、深色卡片上的文字链接 CTA、激活导航标签、卡片顶部细描边。
- 其余是白、弱白或近黑表面。
- 形状柔和大：卡片圆角 24px，按钮圆角 14–18px，药丸芯片。
- 摄影情绪化且暗：略去饱和、压暗，每块媒体磁贴底边升起橄榄-青柠渐变，让文字和芯片保持可读。

设计令牌（定义为 CSS 变量或 Tailwind v4 `@theme` 令牌）：
```
--void:        #000000
--surface:     #0A0A0A
--card:        #111010
--card-raised: #1A1A1A
--lime:        #BFF010
--lime-hover:  #D2FF2E
--lime-tint:   #26300A   /* 青柠文字后的芯片背景 */
--glow:        #0A7D0A   /* 绿光源 */
--white:       #FFFFFF
--muted:       rgba(255,255,255,0.66)
--faint:       rgba(255,255,255,0.40)
--hairline:    rgba(255,255,255,0.08)
--hairline-hot:rgba(191,240,16,0.30)
--radius-card: 24px
--radius-btn:  16px
--radius-pill: 999px
```

绿光（用在主视觉、项目、证言和最终 CTA 区块）：
```css
.glow-bottom-left {
  background:
    radial-gradient(120% 90% at 0% 100%, rgba(10,125,10,0.95) 0%, rgba(4,60,4,0.60) 35%, #000 72%),
    #000;
}
```
资源与课程区块保持纯黑或 `#050505`，让发光区块像暗室之间的亮房间。绝不要把光晕放右上，每视口绝不要超过一处光晕，也绝不要给它做动画。

### 字体排印 — 几何、中等字重
只用一个字体家族：带友好、略宽感觉的几何无衬线。
推荐：Sora、Outfit、Urbanist 或 Plus Jakarta Sans（加载字重 400、500、600、700）。
标题不是超粗。它们是 medium 到 semibold，这才让风格现代、可接近，而不是攻击性。

```
主视觉 H1：     clamp(44px, 6vw, 76px)   字重 500   lh 1.06   ls -0.02em
区块 H2：       clamp(30px, 3.6vw, 48px) 字重 600   lh 1.1    ls -0.015em
卡片标题：      20–24px                  字重 600   lh 1.25
大号正文：      clamp(17px, 1.6vw, 21px) 字重 400   lh 1.55   颜色 --muted
正文：          15–16px                  字重 400   lh 1.65   颜色 --muted
芯片 / 元数据： 12–13px                  字重 600   ls 0.01em
标签（大写）：  11px                     字重 700   ls 0.06em  大写
按钮：          15–16px                  字重 600   ls 0.01em
```

双色标题是标志性排印手法。每个区块 H2 有两三个词是青柠，其余白色：
```html
<h2>我们的 <span class="accent">项目</span></h2>
<h2><span class="accent">学员怎么说</span></h2>
<h2>免费 <span class="accent">资源</span></h2>
```
```css
.accent { color: var(--lime); }
```
更大的课程式标题可用青柠到橄榄的渐变填充
（`linear-gradient(90deg, #BFF010, #7A9A0A)` 配 `background-clip: text`）。
整页最多用一次该处理。

标题对齐：主视觉左对齐；其他区块标题居中，
除「按领域的课程」面板在按钮旁左对齐。

### 布局系统
- 最大内容宽：1240px，居中。水平内边距 24px（移动）/ 40px（桌面）。
- 主视觉满幅，可用满视口宽。
- 区块垂直内边距：桌面 96px，移动 64px。
- 网格间距：卡片 24px，跑马灯磁贴 28–30px。
- 区块标题块：H2、可选一句副标题（最大宽 640px，居中，弱化），然后距内容 48px。

### 页面顺序
按此顺序搭建这些区块：
```
1.  导航栏             浮动药丸胶囊 + logo
2.  主视觉             左文案 + 右双向照片跑马灯
3.  证明条             4 条短统计或媒体/合作方名称（可选但推荐）
4.  项目               2–3 张大项目卡，带讲师行
5.  免费资源           4 张引流磁铁卡，配 3D 书样机
6.  如何运作           3 步同期班流程（可选）
7.  视频证言           3 张竖版视频卡，青柠播放按钮
8.  按领域课程         大面板配 3 张 SEO 课程卡
9.  常见问题           手风琴
10. 最终 CTA          发光区块，一个标题一个按钮
11. 页脚               极简、暗色
12. 浮动聊天           固定右下药丸（WhatsApp 或在线聊天）
```

### 第 1 节 — 导航栏（浮动药丸）
导航栏不是全宽条。它是两块分开的浮动元素：
- Logo：左上，距边 24–32px。小青柠几何标记加白色品牌字标，28–32px，字重 600。
- 导航胶囊：右上，`position: fixed; top: 16px; right: 24px`。
  ```css
  .nav-capsule {
    display: flex; gap: 4px; padding: 6px;
    background: rgba(17,16,16,0.86);
    border: 1px solid var(--hairline);
    border-radius: 20px;
    backdrop-filter: blur(14px);
  }
  .nav-item { padding: 12px 20px; border-radius: 14px; font-size: 15px;
              font-weight: 500; color: #fff; }
  .nav-item:hover  { background: rgba(255,255,255,0.06); }
  .nav-item.active { background: #1A1A1A; color: var(--lime); }
  ```
- 5–6 项：首页、项目、我们的使命、AI 工具（或资源）、学员评价、学员登录。
- 低于 900px：隐藏胶囊链接，在小胶囊内显示圆形汉堡按钮。菜单以全宽暗色表打开，大号堆叠链接，底部青柠「报名」按钮。
- 激活项随滚动更新（滚动侦测）。

### 第 2 节 — 带双向跑马灯的主视觉
布局：全视口高（`min-height: 100vh`），左右两个等分区。
- 桌面网格：`grid-template-columns: 50% 50%`。从 900px 起保持恰好对半分；任一侧都不要宽过半个视口。
- 左 50%：垂直居中文案，左内边距 8–10vw。
- 右 50%：照片跑马灯，从屏幕右缘溢出，左缘在中线硬裁切（左侧无淡出）。
- 背景：`.glow-bottom-left`，让绿光从标题后升起。

左文案，从上到下：
1. H1，2 行，白，字重 500。用平白词语陈述机构承诺
   （示例形态：「亚洲第一所 AI 创业学院」）。
2. 副标题，20px，弱化，最大宽 520px，1–2 行
   （示例形态：「学会在真实生活中使用 AI，创办人们真正想要的公司。」）。
3. 一个主按钮，副标题下 36px：
   - 白底，黑色大写文字，16px，字重 500，letter-spacing 0.01em
   - 高 64px，padding 0 40px，圆角 16px
   - 悬停：背景青柠，transform translateY(-2px)
   - 标签针对行动：「探索 AI 项目」，绝不用「开始使用」
没有第二个按钮，没有徽章行，主视觉没有统计。一个承诺，一个行动。

跑马灯区：3 行水平叠放，间距 30px。行方向交替：
- 第 1 行向右，第 2 行向左，第 3 行向右。
- 磁贴高度：第 1 行约 210px，第 2 行约 280px，第 3 行约 215px
  （不同高度让网格像手排的）。
- 同行内宽度变化：混合 260px、340px、500px、420px 横图磁贴。
- 磁贴圆角 28px。磁贴间距 30px。
- 三行合起来略高于视口，因此第 1、3 行在主视觉上下缘被部分裁切。

每块磁贴都有橄榄渐变和暗色照片处理：
```css
.tile { position: relative; flex: 0 0 auto; border-radius: 28px; overflow: hidden;
        background: #111; }
.tile img { width: 100%; height: 100%; object-fit: cover;
            filter: saturate(0.9) brightness(0.82); }
.tile::after { content: ""; position: absolute; inset: 0;
  background: linear-gradient(to top, rgba(86,120,0,0.60) 0%, rgba(86,120,0,0) 55%); }
```

跑马灯机制（纯 CSS，无库）：
```css
.marquee-row { overflow: hidden; }
.marquee-track {
  display: flex; gap: 30px; width: max-content;
  animation: marquee-left 70s linear infinite;
}
.marquee-row.reverse .marquee-track { animation-direction: reverse; }
.marquee-row:nth-child(2) .marquee-track { animation-duration: 85s; }
@keyframes marquee-left {
  from { transform: translateX(0); }
  to   { transform: translateX(-50%); }
}
.marquee-zone:hover .marquee-track { animation-play-state: paused; }
@media (prefers-reduced-motion: reduce) {
  .marquee-track { animation: none; }
}
```
规则：每行磁贴列表在轨道内渲染两次（相同序列，第二份 `aria-hidden="true"`），这样 translateX(-50%) 无缝循环。
复制前每行至少需要 6 张不同照片。在各行以不同顺序复用同一小图库；不要为每块磁贴拉新图。每行不同速度（70s / 85s / 75s），让行在视觉上不同步。

跑马灯图像（Unsplash 或开源）：
- 使用 Unsplash 可免费使用的照片（许可允许免费使用、无需署名）或其他开源集，如 Pexels 或 Pixabay。
- 首选：用 6–8 张强图，压缩到约 800px 宽 WebP、质量 70，放进本地 images 文件夹。在跑马灯行、项目卡和故事海报上以不同裁切和顺序复用。本地引用，避免热链失败和不必要下载。独立 HTML 演示用相对路径，以便以 `file://` URL 打开时也能加载。
- 开发时若热链 Unsplash，使用格式
  `https://images.unsplash.com/photo-<REAL_PHOTO_ID>?auto=format&fit=crop&w=900&q=70`。
  从 Unsplash 搜索结果挑选真实照片 ID；绝不要编造 ID。上线前验证每个 URL 能加载。在 Next.js 中，在 `next.config` 允许该主机
  （`images.remotePatterns` 针对 `images.unsplash.com`）。
- 搜索匹配用户垂类、展示人物而非抽象艺术的照片：
  笔记本前的学生、导师演讲、工作坊房间、桌前的创始人、白板讨论的小团队、录视频的人、打字的手、课堂讨论。脸要大且对焦；磁贴应有人味。
- 偏好一致观感：相似的暖室内光、浅景深。避免亮白棚拍库存、握手陈词和卡通插画。
- 每张 `<img>` 需要有意义的 `alt` 文本、`loading="lazy"`（第一行除外）、显式 `width` 和 `height`，以及出错回退到 `#1A1A1A` 磁贴。

移动端主视觉：垂直堆叠。文案在上（padding-top 120px 以便 logo 和菜单让开），跑马灯在下，磁贴尺寸为原尺寸的 70%，仅 2 行。

### 第 3 节 — 证明条（可选）
主视觉下单行，背景 `#000`，上下发丝边框。
4 项由发丝竖线分隔：大数字（36px，字重 600，白）配青柠后缀，以及 13px 弱化标签。示例形态：「10,000+ 学员」「12 周」「4.9 评分」「40+ 国家」。只用用户数据中的真实数字。

### 第 4 节 — 项目（大图卡片）
背景：`.glow-bottom-left`。居中双色标题（「我们的 **项目**」）。
网格：桌面 2 列（用户有 3 个项目则 3 列），移动 1 列，间距 32px。

项目卡解剖：
```
┌────────────────────────────────┐
│  [ 图 16:10，圆角 24 ]         │  ← 讲师照片，底部橄榄渐变
│  (所有级别 • 12 周)            │  ← 黑色药丸芯片，图左下
├────────────────────────────────┤
│  (o)  项目标题                 │  ← 56px 圆图标 + 标题 600 / 讲师弱化
│       讲师：姓名               │
└────────────────────────────────┘
```
- 卡片：`background: #000; border: 1px solid var(--hairline); border-radius: 24px;
  overflow: hidden;`
- 图：aspect-ratio 16/10，`object-fit: cover`，底部橄榄渐变。
- 元数据芯片：绝对定位，底 14px，左 14px，`background: #0A0A0A`，白字，
  12px 字重 600，padding 7px 14px，圆角 999px。格式：`级别 • 时长`。
- 不可用项目可选状态药丸居中叠在图上：
  黑药丸白字加小锁图标，标签「即将推出」。
  即将推出卡片仍完全可见但不是链接；给它们 `aria-disabled`。
- 信息行：padding 20px 22px，flex，间距 14px。圆图标（56px，`#1A1A1A`，1px 发丝，
  居中 26px 字形或 logo），然后标题（20px，600，白）和第二行
  （15px，弱化），如「讲师：姓名」。
- 悬停：卡片抬起 4px，边框变成 `--hairline-hot`，图像在 400ms 内缩放到 1.03。
- 整张卡片是项目页链接（即将推出除外）。

### 第 5 节 — 免费资源（引流磁铁卡）
背景：纯 `#000`。居中双色标题（「免费 **资源**」）和一行弱白副标题列出格式：「视频、电子书、指南、模板、下载等，助你成功：」。

网格：桌面 4 列，平板 2 列，移动 1 列，间距 24px。

资源卡：
- `background: #0F0F0F; border-radius: 28px; padding: 24px 24px 20px;`
  `display: flex; flex-direction: column; align-items: center; gap: 22px;`
  `border: 1px solid rgba(255,255,255,0.04);`
- 标题：居中，18px，字重 600，白。
- 产品样机：3D 风格书或设备封面，约 190px × 250px，居中，带透视倾斜和底下椭圆「托盘」阴影：
  ```css
  .platter { width: 78%; height: 46px; border-radius: 50%;
             background: #000; margin-top: -34px; filter: blur(1px); }
  .platter.light { background: #fff; }   /* 仅用在一张精选卡上 */
  .book { transform: perspective(900px) rotateY(-14deg) rotateX(2deg);
          box-shadow: -10px 14px 28px rgba(0,0,0,0.55); border-radius: 4px 8px 8px 4px; }
  ```
- 样机来源，从好到差：(1) 真实 3D 书渲染导出为透明 PNG，
  (2) 平面封面图包在上面的 CSS 书变换中，左侧 10px 更深「书脊」条，
  (3) 用粗体标题的样式化 div 封面。
- 底部全宽操作按钮：`background: #1A1A1A; border-radius: 18px;
  height: 56px; color: var(--lime); font-weight: 600; font-size: 17px;`
  悬停：`background: #222;` 标签右移 2px。
  标签要具体：「获取免费访问」「立即加入我们」「开始聊天」。绝不用「下载」。
- 恰好一张卡可用白托盘制造焦点。

### 第 6 节 — 如何运作（可选）
背景：`#050505`。居中双色标题（「如何 **运作**」）。
3 列，每列一张卡（`#0F0F0F`，圆角 24，padding 28）。内部：44px 圆中的青柠数字（`border: 1px solid var(--hairline-hot)`，青柠数字），20px semibold 标题，15px 弱化描述。桌面用数字圆后 1px 虚线发丝连接卡片。除数字外无图标。

### 第 7 节 — 视频证言
背景：`.glow-bottom-left`。居中双色标题
（「**学员怎么说**」）加两行居中弱白副标题（最大宽 560px）。

网格：桌面 3 列，移动 1 列（或平板横向 scroll-snap），
最大宽 1100px，间距 28px。桌面一次看见所有卡。无轮播箭头。

视频卡解剖：
- 容器：圆角 24px，`overflow: hidden`，1px 发丝边框，背景 `#050505`。
- 媒体区：aspect-ratio 3/4（竖版）。海报图 `object-fit: cover`，略压暗（`brightness(0.9)`）。
- 播放按钮：居中，54px 圆，`background: var(--lime)`，内部描边黑播放三角（描边 2px，无填充），尺寸 22px。
  ```css
  .play { position: absolute; inset: 0; margin: auto; width: 54px; height: 54px;
          border-radius: 50%; background: var(--lime); display: grid; place-items: center;
          transition: transform .2s, background .2s; }
  .play:hover { transform: scale(1.1); background: var(--lime-hover); }
  ```
  点击打开可访问的模态，嵌入视频（YouTube/Vimeo iframe，打开自动播放，Escape 关闭，焦点困住）。
- 仅一张卡上的「精选」标签：青柠药丸，左上，12px，字重 600，黑字。
- 媒体下信息块（从透明到深绿的渐变）：
  ```css
  .t-info { padding: 18px 20px 22px;
            background: linear-gradient(to bottom, rgba(0,40,0,0.0), rgba(0,60,0,0.55)); }
  ```
  姓名 18px semibold 白；角色 14px 弱化（「商业与创业教练」）；
  引言 14px，行高 1.55，`rgba(255,255,255,0.78)`，最多 3 行（line-clamp 3）。
  平台字形（YouTube 红、Instagram 渐变）在块右下，24px。
- 引言是学员口吻的具体成果，不是空泛赞美。

### 第 8 节 — 每个领域的 AI 课程（SEO 课程面板）
用于按职业或城市链接一页落地页。背景：页面 `#000`，
容器内一块大面板：
- 面板：`background: linear-gradient(180deg, #0A0A0A, #050505);
  border: 1px solid var(--hairline); border-radius: 32px; padding: 48px;`
- 标题行：左为左对齐 H2（clamp 38px 到 64px，字重 600），用青柠到橄榄渐变文字填充，下方 18px 弱化副标题（最大宽 520px）；右为青柠药丸按钮「查看全部课程 →」
  （`background: var(--lime); color: #000; height: 54px; padding: 0 28px;
  border-radius: 16px; font-weight: 600`）。
- 网格中 3 张课程卡，间距 24px，上边距 56px：
  ```css
  .course-card { position: relative; background: #121111; border-radius: 28px;
                 padding: 28px; border: 1px solid var(--hairline); overflow: hidden; }
  .course-card::before { content: ""; position: absolute; top: 0; left: 0; right: 0;
    height: 5px; background: linear-gradient(90deg, #7FA10A, #BFF010 50%, #4E6606); }
  ```
  内部：标签芯片（「AI 课程」：`background: var(--lime-tint); color: var(--lime);
  11px, 700, 大写, padding 7px 14px, 圆角 999px`），24px semibold 白标题
  （2–3 行），15px 弱化描述截到 3 行，然后文字链接
  「探索课程 →」白色（悬停：青柠）配 16px 箭头图标。
- 标题遵循 SEO 模式：「[课程] for [职业] in [地点] | [品牌]」。

### 第 9 节 — 常见问题
背景：`#050505`。居中双色标题（「经常被 **问到**」）。
单列，最大宽 820px。每项：`background: #0F0F0F; border-radius: 20px;
padding: 22px 26px; border: 1px solid var(--hairline); margin-bottom: 12px;`
问题 17px semibold 白，打开时青柠「+」旋转 45deg。
答案 15px 弱化，行高 1.7，高度过渡动画 250ms。
默认打开一项。使用带 `aria-expanded` 的真实按钮元素。

### 第 10 节 — 最终 CTA
`.glow-bottom-left` 区块，居中，padding 120px。主视觉尺度的双色 H2
（「今天就开始用 **AI 构建**」），一句弱化句子，一颗与主视觉相同的白色药丸按钮。可选一行 4 个重叠圆形学员头像（44px，2px 黑边，-12px 重叠）配「加入 10,000+ 学员」。

### 第 11 节 — 页脚
背景 `#000`，顶发丝。4 列：品牌块含 logo、两行描述加社交图标（36px 圆，`#1A1A1A`）；项目；资源；公司。
底行：左版权，右法律链接，13px 淡白。这里没有大 CTA。

### 第 12 节 — 浮动聊天按钮
`position: fixed; bottom: 24px; right: 24px; z-index: 60;`
绿底药丸（`#0E7A12`），白字 14px 字重 500，28px 聊天或 WhatsApp 字形，标签「来聊一聊！」，padding 12px 20px，圆角 999px，
1px `rgba(255,255,255,0.15)` 边框，柔绿光晕
（`box-shadow: 0 8px 30px rgba(14,122,18,0.45)`）。链接到 WhatsApp 或用户聊天。
移动端只显示字形（56px 圆）。

### 组件参考

**主白色按钮（主视觉、最终 CTA）：**
```css
.btn-white { height: 64px; padding: 0 40px; border-radius: 16px; background: #fff;
  color: #000; font-weight: 500; font-size: 16px; text-transform: uppercase;
  letter-spacing: .01em; transition: background .2s, transform .2s; }
.btn-white:hover { background: var(--lime); transform: translateY(-2px); }
.btn-white:focus-visible { outline: 2px solid var(--lime); outline-offset: 3px; }
```

**青柠药丸按钮（区块级操作）：**
```css
.btn-lime { height: 54px; padding: 0 28px; border-radius: 16px; background: var(--lime);
  color: #000; font-weight: 600; font-size: 16px; display: inline-flex;
  align-items: center; gap: 10px; transition: background .2s, transform .2s; }
.btn-lime:hover { background: var(--lime-hover); transform: translateY(-2px); }
```

**深色卡操作按钮（资源卡内部）：**
```css
.btn-dark { width: 100%; height: 56px; border-radius: 18px; background: #1A1A1A;
  color: var(--lime); font-weight: 600; font-size: 17px; }
.btn-dark:hover { background: #222; }
```

**元数据芯片：**
```css
.chip { background: #0A0A0A; color: #fff; font-size: 12px; font-weight: 600;
        padding: 7px 14px; border-radius: 999px; }
.chip-lime { background: var(--lime-tint); color: var(--lime); text-transform: uppercase;
             letter-spacing: .06em; font-size: 11px; font-weight: 700; }
```

**卡片基础：**
```css
.card { background: var(--card); border: 1px solid var(--hairline);
        border-radius: var(--radius-card); transition: transform .25s, border-color .25s; }
.card:hover { transform: translateY(-4px); border-color: var(--hairline-hot); }
```

### 动效
- 跑马灯行：连续，每圈 70–85s，悬停暂停，减少动效时关闭。
- 区块进入视口时上移 24px 淡入（不透明度 0 到 1，600ms，ease-out），
  每张卡错开 80ms。
- 按钮和卡片悬停抬起 2 到 4px。没有弹跳、旋转或抖动。
- 播放按钮悬停缩放到 1.1。
- 总动画预算：一个循环效果（跑马灯）。其余都是一次性或悬停驱动。

### 响应式规则
- 1200px 及以上：完整布局如所述。
- 900 到 1199px：资源网格 2 列，项目网格 2 列，主视觉跑马灯磁贴 80% 缩放。
- 低于 900px：导航收成汉堡，主视觉堆叠，所有网格变 1 列
  （资源在 560px 前保持 2 列），课程面板 padding 降到 28px，
  证言卡变成横向 scroll-snap 行（每卡 82vw）。
- 主视觉 H1 从不低于 40px。按钮从不低于 52px 高。

### 无障碍
- 黑底青柠通过 AAA 对比。绝不要把青柠文字放在白底或浅色照片上。
- 青柠按钮上的文字始终是黑。
- 跑马灯是装饰：包在 `aria-hidden="true"` 中，确保没有关键内容只活在里面；提供 `prefers-reduced-motion` 支持。
- 视频卡是按钮，`aria-label` 如「播放来自姓名的证言」。
- 所有焦点态使用 `outline: 2px solid var(--lime); outline-offset: 3px`。

### 内容槽位（由用户提供）
把下面每一项替换成用户自己的内容：
- `[BRAND_NAME]`、logo 标记和品牌色（除非用户提供，否则保持青柠）
- `[HERO_HEADLINE]`、`[HERO_SUBTITLE]` 和 `[HERO_BUTTON_LABEL]`
- `[MARQUEE_IMAGES]` 6–8 张图，在各行和相关卡片中复用（见上面的取材规则）
- `[PROGRAMS]` 列表：标题、级别、时长、讲师、图、链接、状态
- `[RESOURCES]` 列表：标题、封面图、按钮标签、链接
- `[TESTIMONIALS]` 列表：姓名、角色、引言、海报图、视频 URL、平台
- `[COURSES]` 列表：SEO 标题、两句描述、链接
- `[FAQ]` 列表：6 个真实问答
- `[CHAT_LINK]` WhatsApp 或聊天 URL

### 不要做
- 没有全宽导航栏。logo 和导航胶囊是分开的浮动件。
- 没有第二种强调色。任何地方都没有紫、蓝或橙。
- 没有超粗（800 到 900）标题；这种风格活在 500 到 600。
- 没有浅色或白色区块。页面始终保持黑色和绿光。
- 任何区块顶部或卡片后都没有光晕。
- 没有尖角；除小芯片和书样机外，没有任何东西圆角小于 14px。
- 没有库存图陈词：握手、竖拇指、漂浮全息、机器人插画。
- 没有插画或图标网格功能区块；证明来自面孔、视频和数字。
- 桌面没有带箭头的证言轮播。三张卡都保持可见。
- 没有泛按钮标签：「了解更多」「开始使用」「提交」。
- 没有全部同一方向的跑马灯；行必须交替。
- 没有完美网格中等大的跑马灯磁贴。
- 卡片没有投影；用边框和表面对比。唯一柔阴影是资源书托盘、书本身和浮动聊天按钮光晕。
- 最终页面不留下本提示中的占位品牌名。
