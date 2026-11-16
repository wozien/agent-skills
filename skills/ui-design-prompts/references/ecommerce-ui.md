# E-Commerce UI

- **id:** `ecommerce-ui`
- **别名:** 电商 UI, 商城, 购物车结账, 产品优先店面
- **一句话:** 温暖、转化导向、产品优先。
- **适用:**
  - 销售实体或数字产品的在线商店
  - 科技与电子零售站点
  - 多品类商品市场
  - D2C 品牌店面
  - 任何需要购物车与结账流程的产品优先站点
- **避免:**
  - 没有实体库存的 SaaS 或服务型产品
  - 博客或编辑刊物等内容优先站点
  - 购买流程在站外完成的 B2B 工具
  - 需要深色或高对比美学的产品
- **来源:** https://uidesignprompts.com/prompts/ecommerce-ui

## Prompt

## 电商 UI 设计系统

### 气质
温暖、转化导向、产品优先。一切都为了让产品好看、降低购买摩擦。橙色强调传达能量与紧迫，但不具攻击性。干净白表面让产品图呼吸。每个组件都有职责: 发现、评估、加入、结账。

### 色彩系统
- 页面背景: #F8F8F8 — 极浅偏白，不是纯白
- 卡片表面: #FFFFFF — 纯白卡片从页面抬起
- 品牌橙: #FB991C — CTA、折扣徽章、价格、激活状态、newsletter 条、图标
- 产品图背景: #F6DAB0 — 暖桃/琥珀，专用于产品图背后
- 主文字: #022539 — 深海军蓝，用于标题和重要文字
- 次文字: #575757 — 正文与描述
- 删除线 / 弱化: #C9C9C9 — 划掉的旧价
- 「加入购物车」按钮: 背景 #EFF6FF（blue-50），文字 #1C7690（青绿） — 有意**不是**橙色，把橙色留给主 CTA
- 边框: #E2E2E2 或 border-blue-100 — 极淡，几乎看不见
- Newsletter 条: 纯 #FB991C 背景，白字与描边输入

### 导航栏
- 背景: 白，全宽，sticky
- 左: 汉堡菜单图标（用于移动/侧栏导航）
- 中偏左: 品牌 logo（图标 + 橙色字标）
- 右: 「My Account」胶囊按钮（橙底、白字、下拉箭头）+ 带徽章的心形收藏图标 + 带徽章的购物车图标
- 无 border-bottom — 页面背景已足够分隔
- 高度: ~60px

### Hero 区
- 全宽，白/浅灰背景
- 边缘大装饰几何形（三角/多边形），极浅灰 (#EEEEEE) — 纯装饰，CSS clip-path 或 SVG
- 居中标题: 大、深海军蓝、加粗
- 副标题: 橙，字重较轻
- 搜索栏: 居中，宽 ~600px，白背景，rounded-full，左搜索图标，右橙色 「Search」按钮
- 搜索下方分类胶囊: 「All」（橙底白字），其余（白底、灰边、深字）
- 胶囊上方左对齐 「Explore our categories」标签，右对齐 「More →」

### 分类筛选胶囊
- 胶囊形: border-radius 100px，padding 6px 16px
- 激活: 背景 #FB991C，颜色 white
- 未激活: 背景 white，border 1px solid #E2E2E2，颜色 #575757
- 悬停: 背景 #FFF3E0，border-color #FB991C

### 产品卡片
- 容器: border-radius 16px（rounded-2xl），border 1px solid border-blue-100，白背景，padding 6px
- 图区: border-radius 12px，背景 #F6DAB0，aspect-ratio 1:1，padding 16px，flex center
- 折扣徽章: position absolute 左上，背景 #FB991C，颜色 white，border-radius 6px，padding 4px 8px，font-size 12px，文字 「-25%」
- 「New」徽章: 同位置、同样式，标签 「New」
- 产品标题: 2 行截断，font-size 14px，font-weight 500，颜色 #022539，margin 16px 0 8px
- 价格行: 现价 #FB991C（font-size 16px，字重 600）+ 删除线旧价 #C9C9C9
- 操作行（底部）: flex 行带 gap
  - 信息按钮: 方形，背景 blue-50 (#EFF6FF)，图标 <BadgeInfo> 用 #C9C9C9，border-radius 8px，悬停: bg #E1E2E6
  - 加入购物车按钮: flex-1，背景 blue-50 (#EFF6FF)，文字 #1C7690，font-weight 500，border-radius 8px，悬停: bg #E1E2E6

### 产品网格
- 区块标题: 加粗、大、左对齐（「Featured products」「New Products」）
- 标题行右侧: 搜索输入（小，灰边）+ Filter 按钮（橙色图标 + 文字）
- 网格: 桌面 4 列，平板 2 列，移动 1 列
- Gap: 20px
- 网格下方 「View All」链接: 居中，橙字，无背景

### 横向产品列表（新品）
- 带 prev/next 箭头按钮的区块
- 每项: 并排图 + 内容卡
- 图: 圆角卡内暖背景（桃或粉着色）
- 内容: 标题、带橙点的要点功能列表、带删除线的价格、信息 + 加入购物车按钮
- 卡片可滚动行或轮播

### 产品详情页
- 页面标题居中于面包屑上方
- 面包屑: 左对齐 「Home / Products / Name」，右对齐 「Category: Computer」
- 左列:
  - 缩略图条（4 张小图，纵向，左侧）
  - 主图在大桃色背景卡内，右上放大镜图标
- 右列:
  - 产品标题: 大、深海军蓝、加粗
  - 价格行: 折扣徽章（橙色胶囊）+ 现价（橙，大）+ 旧价（删除线灰）
  - 描述段: 次文字色
  - 功能要点列表: 橙点标记
  - 「Add to cart」按钮: 橙，全宽，圆角
  - 「Share」按钮: ghost 风格带图标，在加入购物车旁
- 下方: tab 导航 「Description」 | 「Additional information」（当前 tab 下划线）
- Tab 内容: 段落 + 橙标记要点列表

### 购物车页
- 页面标题: 居中、大、深海军蓝（「My Cart」）
- 面包屑行: 左 「Home / My Cart」，右 「3 Courses in Cart」
- 两列布局: 左 ~70% 购物车项，右 ~30% 摘要
- 购物车项容器: border 1px solid #E2E2E2，border-radius 12px
- 每行购物车项:
  - 左: 64×64 桃色方 (#F6DAB0) 内的图，border-radius 12px，padding 8px
  - 中: 产品标题（font-weight 500）+ 短描述（弱化）
  - 右: 现价橙色 + 旧价删除线 + 橙色圆形移除按钮（X 图标）
  - 项之间底边: 1px solid #E2E2E2
- 购物车摘要侧栏:
  - 「Total:」标签（小，次级）
  - 总价: 非常大，深海军蓝，加粗
  - 旧合计: 灰删除线
  - 折扣百分比: 「20% off」用次级色
  - 结账按钮: 全宽，橙，圆角，font-weight 500
  - 优惠券行: 输入（bg #F6F7FB，左圆角，占位弱化）+ Apply 按钮（橙，右圆角）

### Newsletter 条
- 通栏区块，背景 #FB991C
- 左: 「Newsletter」标题（白，加粗，大）+ 「Freebies, news & promos directly in your inbox」副标题（白，更轻字重）
- 背景大号 「subscribe」水印文字，低透明度
- 右: 邮箱输入（白边框，透明背景，白占位）+ 「Subscribe」按钮（白边框，白字，透明背景）
- Padding: 充裕，上下 60px

### 页脚
- 浅背景（白或 #F8F8F8）
- 三列:
  1. 联系信息: Phone、Email、Address — 每项带橙色图标
  2. 有用链接: 标题 + 带橙点标记的要点列表
  3. 品牌: logo + 品牌描述段 + 橙色 「Read More」
- 底栏: 左版权，右社交图标（Facebook、Instagram）
- 底栏上方分割线

### 微交互与细节
- 产品图: 悬停放大（transform: scale(1.05)）
- 加入购物车按钮: 悬停背景加深 (#E1E2E6)
- 购物车移除按钮: 橙圆配白 X
- 搜索按钮: 橙背景，白字，搜索栏右侧
- 所有价格: 绝不要单独显示货币符号 — 始终 「Rs. XX,XXX」或 「$XX」
- 折扣徽章始终显示负数: 「-25%」
- 收藏心形和购物车图标都显示数字徽章（计数）

### 响应式规则
- 导航栏: 移动端汉堡收起导航，logo 保留，账户+购物车图标保留
- Hero 搜索: 移动端全宽，分类胶囊横向滚动
- 产品网格: 4 列 → 2 列 → 1 列
- 购物车: 移动端堆成单列（摘要移到商品下方）
- 页脚: 移动端堆成单列

### 字体排印
- 字体: Inter、system-ui、sans-serif
- Hero 标题: 36-48px，字重 700，颜色 #022539
- Hero 副文: 16px，字重 400，颜色 #FB991C
- 区块标题: 24px，字重 700，颜色 #022539
- 产品标题: 14-16px，字重 500，颜色 #022539
- 价格: 16-18px，字重 600，颜色 #FB991C
- 正文: 14px，字重 400，颜色 #575757
- 徽章: 12px，字重 500

### 不要这样做
- 不要把橙色用在 「Add to cart」按钮上 — 橙色留给主 CTA（Checkout、Search、Subscribe）
- 主页面任何地方都不要用深色背景
- 产品卡片圆角不要大于 16px
- 单个组件不要超过 2 种字重
- 不要只显示现价而不对比旧价/折扣价
- 不要从产品图背景去掉暖桃 (#F6DAB0) — 这是视觉签名
