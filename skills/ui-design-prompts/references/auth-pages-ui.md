# Auth Pages UI

- **id:** `auth-pages-ui`
- **别名:** 登录注册, Auth 页, 认证页, 注册登录流
- **一句话:** 建立信任、干净、为转化优化。
- **适用:**
  - SaaS 产品登录与注册流
  - 带社交登录（Google、Apple、邮箱）的应用
  - 注册时信任与品牌感知很重要的产品
  - 需要可信度信号（客户 logo、推荐）的 B2B 工具
  - 任何多页认证流: 注册、登录、忘记密码
- **避免:**
  - 不需要整页的简单单字段表单
  - 深色模式优先的设计系统产品
  - 简短比建立信任更重要的消费应用
  - 没有社会证明或客户 logo 可展示的产品
- **来源:** https://uidesignprompts.com/prompts/auth-pages-ui

## Prompt

## 认证页 UI 设计系统

### 气质
干净、可信、转化导向。分屏布局同时做两件事: 左侧表单去掉注册的一切摩擦，右侧品牌面板在用户提交前用社会证明建立信任。每个元素都为关键第一印象时刻优化。

### 核心布局 — 分屏
- 全视口高度: 100vh，桌面无滚动
- 两列: 左 45%（表单）+ 右 55%（品牌面板）
- 左列: 纯白背景，内容垂直居中，充裕内边距（水平 48px）
- 右列: 绿色品牌面板，大圆角卡片（border-radius 24px），略溢出视口右缘以增加纵深
- 移动端: 单列，绿色面板堆在表单**上方**，面板仅左下 + 右下圆角（顶角与视口齐平）

### 左列 — 表单区
- 背景: #FFFFFF
- 左上 logo: 橙色圆形图标（40px）+ 品牌字标（20px，字重 700，黑）
- Logo 下方标题: 「Let's create your account...」或 「Let's sign into your account...」 — 15px，字重 700，颜色 #111111
- 无导航、无多余铬件 — 只有 logo + 标题 + 表单
- 垂直间距: logo 在顶，然后 ~60px 间隙，然后标题，然后表单字段
- 底部法律文字: 居中，12px，#999999，条款与隐私链接带下划线

### 社交登录按钮
- Google 按钮: 白背景，border 1.5px solid #E0E0E0，border-radius 10px，高度 52px，全宽，flex center，图标与文字间距 gap 10px
- Apple 按钮: 黑背景 (#111111)，border 1.5px solid #111111，border-radius 10px，高度 52px，全宽，白字，flex center
- 文字: 「Continue with Google」 / 「Continue with Apple」 / 「Continue with Email」 — 15px，字重 500
- 「or」分割: 两侧水平线，居中 「or」文字 #999999，13px
- 邮箱按钮: 绿 (#3DBE6C) 背景，白字，border-radius 10px，高度 52px，全宽，左邮件图标，右文字

### 邮箱/密码表单（登录 / 忘记密码）
- 每个输入上方标签: 14px，字重 500，颜色 #111111，必填星号 #E53E3E
- 输入框: 背景 #F5F5F5，border: none，border-radius 10px，高度 52px，padding 0 16px，font-size 15px，占位色 #AAAAAA
- 输入聚焦: border 2px solid #3DBE6C，背景仍为 #F5F5F5
- 密码输入: 右侧眼睛图标切换（显示/隐藏），图标色 #999999
- 「Forgot Password?」链接: 密码字段下方右对齐，14px，字重 500，颜色 #111111，无下划线
- 主 CTA 按钮: 全宽，背景 #3DBE6C，颜色 white，border-radius 10px，高度 52px，font-size 16px，font-weight 600，悬停: 背景 #2EA85A
- 底部链接: 居中 — 「Don't have an account? Sign Up」，其中 「Sign Up」颜色 #F5A623，font-weight 600

### 右列 — 绿色品牌面板
- 背景: #3DBE6C（纯绿）
- Border-radius: 桌面 24px（四角），形成浮卡效果
- 装饰元素: 大植物/叶片 SVG 形，极低透明度（rgba(255,255,255,0.12)）置于背景 — 有机曲线，不是几何
- 顶部 logo 行: 同一橙色圆形图标 + 「Flexy UI」白色，font-weight 700
- 标题: 2 行，非常大（clamp(32px, 3.5vw, 44px)），font-weight 800，颜色 white
  - 第 1 行: 「Built for 」+ 品牌词用橙 (#F5A623) 斜体: 「simplicity.」
  - 第 2 行: 「Powered by you.」白色
- 副标题: 15px，font-weight 300，颜色 rgba(255,255,255,0.85)，max-width 380px，line-height 1.65
- 推荐卡片: 白背景，border-radius 16px，padding 20px 24px，margin-top 32px
  - 引语: 14px，font-weight 700，颜色 #111111，带引号
  - 正文: 13px，颜色 #555555，line-height 1.6，margin-top 8px
  - 作者行: 32px 圆形头像（照片或首字母）+ 姓名 13px 字重 600，颜色 #111111
- 卡片下方轮播点: 3 点，激活 = #F5A623（更宽胶囊形 20px），未激活 = rgba(255,255,255,0.4)，gap 6px
- 「SOME OF OUR TRUSTED CLIENTS」标签: 11px，font-weight 600，letter-spacing 0.1em，颜色 rgba(255,255,255,0.7)，margin-top 32px
- 客户 logo 网格: 2 行，绿底上深色/白色 logo — 用 filter: brightness(0) invert(1) 做绿底白 logo。间距: flex-wrap，gap 20px 32px

### 忘记密码页
- 同一分屏布局
- 左表单: logo + 标题 「Reset your password...」+ 仅邮箱字段 + 「Send Reset Link」绿色按钮
- 副文: 「Enter your email and we'll send you a link to reset your password.」用 #666666
- 返回链接: 底部 「← Back to Sign In」用 #3DBE6C
- 右面板: 同一绿色面板、同一标题与推荐

### 表单校验状态
- 错误状态: 输入边框 2px solid #E53E3E，输入下方红色辅助文字（12px，#E53E3E）
- 成功状态: 输入边框 2px solid #3DBE6C，右侧绿色勾选图标
- 加载状态: 按钮显示 spinner，opacity 0.85，cursor not-allowed

### 字体排印
- 字体: Inter、system-ui、sans-serif
- 品牌标题: clamp(32px, 3.5vw, 44px)，字重 800，line-height 1.1
- 区块标题（表单）: 15px，字重 700，颜色 #111111
- Logo 字标: 20px，字重 700
- 按钮文字: 15-16px，字重 500-600
- 输入文字: 15px，字重 400
- 标签: 14px，字重 500
- 法律文字: 12px，字重 400，颜色 #999999

### 响应式 — 移动
- 垂直堆叠: 绿色面板全宽在**顶部**，表单在下
- 绿色面板: 仅左下和右下圆角（24px），顶角齐平
- 面板高度: auto，展示完整标题 + 推荐 + 点 + 客户 logo
- 表单区: 白，全宽，padding 32px 20px
- 面板中的 logo: 显示。表单区 logo: 移动端隐藏（面板 logo 已足够）
- 客户 logo: flex-wrap，更小字体，每行 2 个

### 不要这样做
- 不要把绿色 CTA 按钮用于次级操作 — 只留给主操作
- 不要加导航链接或顶栏 — 认证页应无干扰
- 单个认证表单不要超过 3 个输入字段
- 橙色除以下用途外不要用: 品牌 logo 圆、 「simplicity.」一词、登录/注册交叉链接、轮播激活点
- 不要给左（表单）列加装饰 — 保持完全干净
- 不要在同一屏同时展示社交登录 **和** 邮箱字段 — 用 「Continue with Email」展开
