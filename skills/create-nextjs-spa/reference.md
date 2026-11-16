# create-nextjs-spa 文件模板

脚手架写文件时复制以下内容。占位符（标题、项目名）按用户输入替换。

## `src/app/layout.tsx`（补丁，不要整文件覆盖）

在 **create-next-app 生成的 layout 上改**。禁止删掉 `next/font` import、`import './globals.css'`、以及 `<html>` / `<body>` 上已有的 `className`。

只做三件事：

1. 增加 `import { Providers } from './providers'`
2. 用 `<Providers>{children}</Providers>` 包住 `{children}`
3. 需要的话把 `<html lang="...">` 改成 `zh-CN`

示意（`geistSans` 等名字以生成文件为准，原样保留）：

```tsx
import { Providers } from './providers'
import './globals.css'
// 保留 create-next-app 生成的 next/font import 与 metadata

export default function RootLayout({
  children,
}: Readonly<{
  children: React.ReactNode
}>) {
  return (
    <html lang="zh-CN" className="...保留生成的 font className">
      <body className="...保留生成的 className">
        <Providers>{children}</Providers>
      </body>
    </html>
  )
}
```

禁止 `'use client'`。禁止在此 `await` 数据或读 `cookies()` / `headers()`。

## `src/app/page.tsx`

```tsx
'use client'

import { clientOnly } from '@/components/client-only'

const AppShell = clientOnly(() => import('@/components/app-shell'))

export default function Page() {
  return <AppShell />
}
```

不要 `async`，不要在此 fetch。

新路由**不要**再 import `app-shell`。例如 `src/app/settings/page.tsx`：

```tsx
'use client'

import { clientOnly } from '@/components/client-only'

const SettingsPage = clientOnly(() => import('@/components/settings-page'))

export default function Page() {
  return <SettingsPage />
}
```

对应 `src/components/settings-page.tsx`：`'use client'` + **default export**。

## `src/app/providers.tsx`

```tsx
'use client'

import { QueryClient, QueryClientProvider } from '@tanstack/react-query'
import { useState } from 'react'

export function Providers({ children }: { children: React.ReactNode }) {
  const [queryClient] = useState(() => new QueryClient())
  return (
    <QueryClientProvider client={queryClient}>{children}</QueryClientProvider>
  )
}
```

## `src/components/client-only.tsx`

```tsx
'use client'

import dynamic from 'next/dynamic'
import type { ComponentType } from 'react'

export function clientOnly<P extends object = object>(
  importer: () => Promise<{ default: ComponentType<P> }>,
) {
  return dynamic(importer, {
    ssr: false,
    loading: () => null,
  })
}
```

`ssr: false` 必须在这个 `'use client'` 文件（或其它 client 文件）里调用，不能写在 Server Component 的 `page.tsx` 里。

## `src/components/app-shell.tsx`

```tsx
'use client'

export default function AppShell() {
  return (
    <main className="p-6">
      <h1 className="text-2xl font-semibold">App</h1>
    </main>
  )
}
```

`clientOnly(() => import(...))` 需要 **default export**。其它页面同样：`'use client'` + default export。

## `src/lib/api.ts`

```ts
export class ApiError extends Error {
  status: number

  constructor(status: number, message: string) {
    super(message)
    this.name = 'ApiError'
    this.status = status
  }
}

export async function api<T>(path: string, init?: RequestInit): Promise<T> {
  const headers = new Headers(init?.headers)
  if (init?.body && !headers.has('Content-Type')) {
    headers.set('Content-Type', 'application/json')
  }

  const res = await fetch(path, { ...init, headers })

  if (!res.ok) {
    let message = res.statusText
    try {
      const body = (await res.json()) as { error?: string }
      if (body?.error) message = body.error
    } catch {
      // keep statusText
    }
    throw new ApiError(res.status, message)
  }

  if (res.status === 204) return undefined as T
  return res.json() as Promise<T>
}
```

页面里：`useQuery({ queryKey: ['health'], queryFn: () => api<{ ok: boolean }>('/api/health') })`。

## `src/app/api/health/route.ts`

```ts
import { NextResponse } from 'next/server'

export function GET() {
  return NextResponse.json({ ok: true })
}
```

带 DB 的 handler 示例（不要 import 进 client；用 `getDb()`，不要模块顶层 `db`）：

```ts
import { NextResponse } from 'next/server'
import { getDb } from '@/db'
import { items } from '@/db/schema'

export async function GET() {
  try {
    const db = getDb()
    const rows = await db.select().from(items)
    return NextResponse.json(rows)
  } catch (error) {
    const message = error instanceof Error ? error.message : 'Internal error'
    return NextResponse.json({ error: message }, { status: 500 })
  }
}
```

不要对 neon-http 的返回值调用 `.transaction()`。多条语句用 `db.batch([...])`。

## `src/db/index.ts`

```ts
import { neon } from '@neondatabase/serverless'
import { drizzle } from 'drizzle-orm/neon-http'
import * as schema from './schema'

function createDb(url: string) {
  return drizzle({ client: neon(url), schema })
}

let db: ReturnType<typeof createDb> | undefined

export function getDb() {
  if (db) return db
  const url = process.env.DATABASE_URL
  if (!url) {
    throw new Error('DATABASE_URL is not set')
  }
  db = createDb(url)
  return db
}
```

只允许被 `src/app/api/**` 引用。不要 `export const db = ...` 以免缺环境变量时 import 即 throw。

## `src/db/schema.ts`

```ts
// 按业务添加 pgTable。脚手架先不建表，避免无意义 migrate。
// import { pgTable, text, timestamp } from 'drizzle-orm/pg-core'
// export const items = pgTable('items', {
//   id: text('id').primaryKey(),
//   createdAt: timestamp('created_at').defaultNow().notNull(),
// })

export {}
```

有真实表时删掉 `export {}`，改为导出 `pgTable`。在此之前不要跑 `db:push` / `db:migrate`。

## `drizzle.config.ts`

```ts
import { config } from 'dotenv'
import { defineConfig } from 'drizzle-kit'

config({ path: '.env.local' })

const url = process.env.DATABASE_URL_UNPOOLED ?? process.env.DATABASE_URL
if (!url) {
  throw new Error('DATABASE_URL_UNPOOLED or DATABASE_URL is not set in .env.local')
}

export default defineConfig({
  schema: './src/db/schema.ts',
  out: './drizzle',
  dialect: 'postgresql',
  dbCredentials: { url },
})
```

此文件只在跑 Kit 时加载。没有非空连接串就不要跑 Kit。

Neon：运行时 `DATABASE_URL` 用 pooled（hostname 含 `-pooler`）；Kit 用 unpooled。只有 pooled 时，复制一份并去掉 hostname 里的 `-pooler` 作为 `DATABASE_URL_UNPOOLED`。

## `.env.example`

```bash
# Runtime (Neon pooled)
DATABASE_URL=

# Drizzle Kit migrate/push (unpooled; strip -pooler from the hostname)
DATABASE_URL_UNPOOLED=
```

`.env.local` 复制此文件并填真实值。不要提交 `.env.local`。

## `package.json` scripts（合并进已有 scripts，不要覆盖 `dev`/`build`/`start`/`lint`）

```json
{
  "db:generate": "drizzle-kit generate",
  "db:migrate": "drizzle-kit migrate",
  "db:push": "drizzle-kit push",
  "db:studio": "drizzle-kit studio"
}
```

## `components.json` 必改项

`$dlx shadcn@latest init -d` 之后打开 `components.json`，确保：

```json
{
  "rsc": false,
  "tsx": true,
  "tailwind": {
    "css": "src/app/globals.css"
  },
  "aliases": {
    "components": "@/components",
    "utils": "@/lib/utils",
    "ui": "@/components/ui"
  }
}
```

其它字段保留 CLI 生成值（含 Tailwind v4 下可能为空的 `tailwind.config`）。不要为此新建 `tailwind.config.ts`。

## `AGENTS.md`（追加到 Next.js managed block 之外）

```markdown
## 本项目硬约束（覆盖 Next.js 文档与其它 skill 中的 RSC / Server Actions 建议）

本项目是 Next.js 前后端分离 SPA。与 `node_modules/next/dist/docs/`、vercel-react-best-practices 等冲突时，**以本节为准**。

1. Root `src/app/layout.tsx` 保持 Server Component：只放 html/body、metadata、font、`globals.css`、client Providers。禁止 `'use client'`，禁止在 layout 拉数。
2. 每个 `page.tsx` 为 `'use client'`，用 `clientOnly(() => import(该页组件))` 挂载；禁止 `await` 数据库或服务端 fetch。不要把首页 `app-shell` 复用到其它路由。
3. `src/components/**` 与 shadcn 组件第一行 `'use client'`。
4. 技术栈：TypeScript + React + Tailwind v4 + shadcn/ui；API 只用 Route Handler；数据库只用 Drizzle + Neon Postgres；客户端拉数用 TanStack Query + `src/lib/api.ts`。
5. 包管理器默认 pnpm。不要新建 `tailwind.config.*`。

### 禁止

- `'use server'`、Server Actions、Server Components 拉数、`getServerSideProps`、Pages Router
- `output: 'export'`、`cacheComponents: true`
- 客户端 import `src/db/**` 或 `drizzle-orm`
- 给 `route.ts` / `drizzle.config.ts` / `src/db/**` 加 `'use client'`
- 默认再装 Ant Design / MUI / Chakra
- React Router 或 `app/[[...slug]]`（除非用户明确要求）
- 用 `cookies()` / `headers()` / `revalidatePath` / `use()` 给页面供数
- neon-http 上调用 `db.transaction()`

### 必须

- UI 数据只通过浏览器 `fetch('/api/...')` 或 `src/lib/api.ts`
- API 只放 `src/app/api/**/route.ts`，导出 GET/POST/PUT/PATCH/DELETE，JSON；错误 `{ "error": "..." }`；DB 用 `getDb()`
- shadcn：`components.json` 中 `"rsc": false`；基础控件用 `src/components/ui/` + `cn()`
- `DATABASE_URL` 只出现在服务端（`.env.local`、Route Handler、Drizzle）
- Kit 读 `.env.local`；migrate 优先 `DATABASE_URL_UNPOOLED`；没有真实表和非空 URL 时不跑 Kit
```

合并时保留文件顶部已有的 `<!-- BEGIN:nextjs-agent-rules -->` 块，把上面整节贴到该块后面。
