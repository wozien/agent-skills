# agent-skills

个人 Agent Skills 合集，兼容 Cursor、Claude Code、Codex、OpenCode、DSH 等支持 [Agent Skills](https://agentskills.io) 的 coding agent。

## 安装使用

用 [skills CLI](https://skills.sh/) 安装（Node.js 22.20+）。不指定 `-a` 时，会检测本机已装的 agent。不加 `-g` 则只装到当前项目。

```bash
# 全局：装到本机已检测到的 agent（推荐）
npx skills add wozien/agent-skills -g

# 全局：本仓库全部 skill，装到 CLI 支持的全部 agent
npx skills add wozien/agent-skills -g --all

# 只装某一个
npx skills add wozien/agent-skills --skill create-nextjs-spa -g -y

# 指定若干主流 agent
npx skills add wozien/agent-skills -g -a cursor -a claude-code -a codex -a opencode
```

列出仓库里的 skills：`npx skills add wozien/agent-skills --list`。

## 已有 skills

| Skill                                                  | 简述                                                                              |
| ------------------------------------------------------ | --------------------------------------------------------------------------------- |
| [create-nextjs-spa](skills/create-nextjs-spa/SKILL.md) | Next.js 前后端分离起步：客户端 SPA、shadcn/ui、Route Handler REST、Drizzle + Neon |
| [ui-design-prompts](skills/ui-design-prompts/SKILL.md) | 33 套网站 UI 设计风格（中文 prompt）；按适用/避免选型后原文执行                   |
