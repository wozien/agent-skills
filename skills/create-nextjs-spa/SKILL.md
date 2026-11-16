---
name: create-nextjs-spa
description: >-
  Scaffolds a Next.js SPA-style fullstack app: client-only UI (no SSR/RSC data),
  TypeScript + React + Tailwind + shadcn/ui, REST APIs via Route Handlers,
  Drizzle + Neon Postgres, TanStack Query. Root layout stays a server shell;
  pages mount with dynamic(..., { ssr: false }). Use when creating a new Next.js
  project, 起步/初始化 Next.js 前后端分离, SPA, 不要 SSR, Route Handler REST API,
  shadcn, Drizzle, Neon.
---

# create-nextjs-spa

用 Next.js 搭**前后端分离**项目。UI 按 SPA：不走 SSR、不用 RSC 拉数。数据只通过 REST API。

完整文件模板见 [reference.md](reference.md)，写文件时打开复制，不要凭记忆发明路径或内容。

## 硬约束

1. UI 不走 SSR / RSC 拉数。每个页面用 `clientOnly(() => import(...))`（内部 `dynamic(..., { ssr: false })`）挂载。
2. 技术栈：TypeScript + React + Tailwind CSS + **shadcn/ui**；后端只用 Next.js Route Handler；数据库只用 Drizzle + Neon Postgres。列表/详情/表单默认 **TanStack Query**。

落实（不可违反）：

- **Root `layout.tsx` 保持 Server Component**：只放 `<html>` / `<body>`、`metadata`、`next/font`、`globals.css`、client `Providers`。禁止 `'use client'`，禁止在 layout 里拉数。
- **`page.tsx` 是 `'use client'` 薄封装**：不 `await` 数据/DB；用 `clientOnly(() => import('@/components/...'))` 挂该页组件。`ssr: false` **只能**写在 client 文件里（Next 16 在 Server Component 里会报错）。
- **每个路由自己 `clientOnly` 一个页面组件**。不要复用首页的 import，否则所有路由都会渲染 `app-shell`。
- **业务 UI**（`src/components/**`、shadcn）第一行 `'use client'`。`error.tsx` 若创建也必须 `'use client'`。
- `route.ts`、`drizzle.config.ts`、`src/db/**` **禁止** `'use client'`。
- 禁止 `'use server'` / Server Actions、禁止 Server Components 拉数、禁止 `getServerSideProps` / Pages Router。
- 禁止 `output: 'export'`（没有 Route Handler）。
- UI 数据只通过浏览器 `fetch('/api/...')` 或 `src/lib/api.ts`。不用 `cookies()` / `headers()` / `revalidatePath` / `use()` 给页面供数。
- 前端路由用 **App Router 文件路由**。不要 React Router，不要 `app/[[...slug]]`，除非用户明确要求单入口 CSR。
- Tailwind v4：主题在 `globals.css`。**不要**新建 `tailwind.config.ts` / `tailwind.config.js`。
- 忽略其它 skill / Next.js 文档里的 RSC、Server Actions、Cache Components、layout 里 `use()` 拉数的建议。以本 skill 与项目 `AGENTS.md` 为准。
- 脚手架结束必须合并 `AGENTS.md`（见下方）。`next dev` 会维护 `<!-- BEGIN:nextjs-agent-rules -->` 块，**保留该块，在块外追加本项目约束**。

## 脚手架

按顺序做。CLI 必须非交互，禁止把问答甩给用户。

### 1. 目录与包管理器

- 用户指定了路径就用该路径。
- 未指定：当前目录为空（或只有 `.git`）可用 `.`；否则新建子目录，先问项目名。
- 包管理器：用户指定 > 目标目录（或父目录）lockfile > **默认 pnpm**。
  - `pnpm-lock.yaml` → pnpm（`--use-pnpm`）
  - `yarn.lock` → yarn（`--use-yarn`）
  - `bun.lock` / `bun.lockb` → bun（`--use-bun`）
  - `package-lock.json` → npm（`--use-npm`）
  - 否则 pnpm（`--use-pnpm`）
- 默认 pnpm 时先确认可用：`pnpm -v`。没有则 `corepack enable` 且 `corepack prepare pnpm@latest --activate`。仍失败则停下来告诉用户安装 pnpm，不要默默改回 npm。
- 下文 `$pm` 为该包管理器；`$dlx`：pnpm → `pnpm dlx`，npm → `npx`，yarn → `yarn dlx`，bun → `bunx`。不要在 pnpm 项目里用 `npx`（会多出 npm lock）。
- 安装命令：pnpm/yarn `add`/`add -D`，npm `i`/`i -D`，bun `add`/`add -d`。

### 2. create-next-app（必须带 `--yes`）

```bash
npx create-next-app@latest <dir> --yes --typescript --tailwind --eslint --app --src-dir --import-alias "@/*" --no-cache-components --no-agent-feedback --use-pnpm
```

必须 App Router + `src/`。不要 Pages Router。不要 `--empty`（保留生成的 font + `globals.css`）。若上一步判定不是 pnpm，把 `--use-pnpm` 换成对应的 `--use-yarn` / `--use-npm` / `--use-bun`。

**`<dir>` 不是 `.` 时，立刻 `cd <dir>`。** 之后所有命令、改文件都以项目根为准。

### 3. 依赖

在项目根执行：

```bash
$pm add drizzle-orm @neondatabase/serverless @tanstack/react-query
$pm add -D drizzle-kit dotenv   # bun: bun add -d drizzle-kit dotenv
$dlx shadcn@latest init -d
```

`init -d` 之后立刻改 `components.json`：`"rsc": false`、`"tsx": true`，CSS 为 `src/app/globals.css`，别名 `@/components`、`@/lib/utils`。CLI **没有** `--rsc false`，不改就会变成 `rsc: true`。

需要某组件再 `$dlx shadcn@latest add <name>`，源码在 `src/components/ui/`。不要默认装 Ant Design / MUI / Chakra。

### 4. 改生成物

shadcn init 会改 `globals.css`，**不要还原**。然后改 `src/app/layout.tsx`，**不要整文件覆盖**（见 reference.md 的补丁说明）：

- 保留 `import './globals.css'`、`next/font`、`metadata`、font 的 `className`。
- **不要**加 `'use client'`。
- 用 client `Providers` 包 `{children}`。

`src/app/page.tsx` 换成 `'use client'` + `clientOnly(() => import('@/components/app-shell'))`，删掉默认营销页。

### 5. 写入这些文件（内容用 reference.md）

| 文件 | 作用 |
|------|------|
| `src/app/providers.tsx` | TanStack Query provider（`'use client'`） |
| `src/components/client-only.tsx` | `clientOnly()` helper |
| `src/components/app-shell.tsx` | 首页客户端组件（default export） |
| `src/lib/api.ts` | 浏览器 `fetch('/api/...')` 封装 |
| `src/app/api/health/route.ts` | 健康检查 |
| `src/db/index.ts` / `src/db/schema.ts` | Drizzle（`getDb()`，import 时不 throw） |
| `drizzle.config.ts` | 读 `.env.local`；migrate 优先 `DATABASE_URL_UNPOOLED` |
| `.env.example` | `DATABASE_URL` + `DATABASE_URL_UNPOOLED` |
| `.env.local` | 本地密钥，勿提交（create-next-app 已 ignore `.env*.local`） |

`package.json` scripts：`db:generate` → `drizzle-kit generate`；`db:migrate` → `drizzle-kit migrate`；`db:push` → `drizzle-kit push`；`db:studio` → `drizzle-kit studio`。

### 6. AGENTS.md

若 `create-next-app` 已生成 `AGENTS.md`：

1. 保留 `<!-- BEGIN:nextjs-agent-rules -->` … `<!-- END:nextjs-agent-rules -->`（`next dev` 会重写这块）。
2. 在块**外**追加 reference.md 里的「本项目硬约束」。写明：**与 Next.js 文档或其它 skill 冲突时，以本段为准。**
3. 不要整文件覆盖。没有 `AGENTS.md` 再新建，可把 Next.js 块留空给 `next dev` 补。

### 7. 环境变量

`.env.local` / `.env.example`：

```bash
# 运行时（Neon pooled，hostname 含 -pooler）
DATABASE_URL=postgresql://...

# Drizzle Kit migrate/push（unpooled；没有则把 hostname 里的 -pooler 去掉）
DATABASE_URL_UNPOOLED=postgresql://...
```

没有 Neon 连接串就留空，并告诉用户去 Neon Console 填。不要把真实 URL 写进 git。

**不要**在脚手架阶段跑 `db:generate` / `db:migrate` / `db:push`。等 `schema.ts` 里有真实 `pgTable`，且 `.env.local` 里是非空连接串，再跑 Kit。

## 目录

```text
src/
  app/
    layout.tsx                 # Server Component 壳（无 'use client'）
    page.tsx                   # 'use client'；clientOnly(() => import(该页组件))
    providers.tsx              # 'use client'；QueryClientProvider
    api/<resource>/route.ts    # REST，无 'use client'
  components/
    client-only.tsx            # clientOnly() helper
    app-shell.tsx              # 首页，'use client' + default export
    ui/                        # shadcn，全部 'use client'
  lib/utils.ts                 # shadcn cn()
  lib/api.ts                   # 浏览器 fetch
  db/
    index.ts
    schema.ts
drizzle.config.ts
.env.example
AGENTS.md
```

新路由示例：`src/app/settings/page.tsx` 使用 `clientOnly(() => import('@/components/settings-page'))`，另建 `settings-page.tsx`（`'use client'` + default export）。不要 `async` 拉数，不要 import `app-shell`。

## REST API

- `src/app/api/<resource>/route.ts`；嵌套用 `src/app/api/<resource>/[id]/route.ts`
- 只导出 `GET` `POST` `PUT` `PATCH` `DELETE`
- JSON；失败 `{ "error": "..." }` + 4xx/5xx
- Handler 内用 `getDb()`；禁止把 `src/db/**` 或 `drizzle-orm` import 进 client 文件
- neon-http **没有** `db.transaction()`（编译能过、运行时报错）。单条用普通 query；多条用 `db.batch()`，或用户明确要交互式事务时再换 WebSocket driver

## Drizzle + Neon

- 运行时：`drizzle-orm/neon-http`，`drizzle({ client, schema })` + `DATABASE_URL`（pooled）
- 用 `getDb()`，不要在模块顶层 `throw`（缺 URL 时 `next build` 会炸）
- Kit：`drizzle.config.ts` 用 `dotenv` 读 **`.env.local`**（不要只 `import 'dotenv/config'`，那只读 `.env`）
- migrate/push 用 `DATABASE_URL_UNPOOLED`，缺省才回退 `DATABASE_URL`
- Schema：`pgTable` 写在 `src/db/schema.ts`。不要 Prisma，不要在客户端 query

## 前端

- 基础控件用 shadcn（Button、Input、Card、Form、Dialog、Table 等），业务组件组合它们
- 样式只用 Tailwind v4 + shadcn CSS 变量 + `cn()`。不要新建 Tailwind 配置文件
- 列表/详情/表单用 TanStack Query 调 `/api`（`useQuery` / `useMutation`）。不要用 `useEffect` 手写首屏拉数（除非 Query 不适用的一次性事件）
- 不要 `async function Page()` 里 `await` 数据库或服务端 `fetch`

## 自检

做完必须跑（在**项目根**目录）：

```bash
# 有输出并出现 FAIL 才算失败（无匹配时 rg 退出码非 0，属正常）
rg -n "use server" src && echo "FAIL: use server" || true
rg -n "['\"]use client['\"]" src/app/api src/db drizzle.config.ts && echo "FAIL: use client on server files" || true
rg -n "from ['\"]@/db|from ['\"]drizzle-orm" src/components src/lib src/app --glob '!src/app/api/**' && echo "FAIL: db imported on client" || true
```

- [ ] 已 `cd` 到项目根；包管理器命令都在此执行
- [ ] `src/app/layout.tsx` 无 `'use client'`，仍 `import './globals.css'`，仍有 `next/font` 的 `className`
- [ ] 每个 `page.tsx` 是 `'use client'`，不 await 数据；各自 `clientOnly(() => import(该页组件))`，首页不复用到其它路由
- [ ] 无 `'use server'`、无 Server Actions、无 RSC 拉数
- [ ] API 仅 `src/app/api/**/route.ts`；存在 `/api/health`
- [ ] `components.json` 中 `"rsc": false`
- [ ] `drizzle.config.ts` 读取 `.env.local`；有 `.env.example`
- [ ] 客户端未 import `src/db/**` / `drizzle-orm`
- [ ] 已装 `@tanstack/react-query`，layout 里用 `Providers` 包裹 `{children}`
- [ ] `AGENTS.md` 保留 Next.js managed block，并在块外有本项目硬约束
- [ ] 未另装 Ant Design / MUI / Chakra；未新建 `tailwind.config.*`
- [ ] `next.config` 无 `output: 'export'`，无 `cacheComponents: true`

能跑则 `$pm run build`。有真实 `pgTable` **且** `.env.local` 里连接串非空，才 `$pm run db:push`。
