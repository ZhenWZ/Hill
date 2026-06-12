# AGENTS.md

> 本文件由 Codex、opencode 等 agent CLI 在开始工作前自动读取。Claude Code 读取
> `CLAUDE.md`（见文末说明）。This file is auto-read by Codex, opencode, and other
> agentic CLIs before they start work.

## 这个仓库是什么 / What this repo is

《山屋惊魂》(Betrayal at House on the Hill) 自定义剧本仓库。核心交付物是**可直接上桌
游玩的剧本**，由内置的"剧本生成器"产出。
A repository of custom haunts for Betrayal at House on the Hill. The deliverable is
table-ready haunts produced by the built-in haunt generator.

## 写剧本时必须遵循的流程 / How to write a haunt

当用户要求"写一个山屋惊魂剧本 / 小黑屋剧本 / custom haunt / hero+traitor scenario"时：

1. **先读 `shared/betrayal-haunt-writer/workflow.md`**，严格按其 Step 0–6 执行。这是
   工具无关的**单一事实源**，全部规则、组件、格式、设计与校验准则都在其 `references/`、
   `templates/`、`examples/` 中。不要凭记忆编造规则或组件。
2. `workflow.md` 内的相对路径相对于 `shared/betrayal-haunt-writer/` 目录解析。
3. **不要**在多个工具目录里复制工作流内容——只通过下方入口指向 `shared/`。

各工具的入口文件（仅适配 Step 4 的子代理派发机制，其余共用 `shared/`）：

| 工具 | 入口 |
|---|---|
| Codex | `.agents/skills/betrayal-haunt-writer/SKILL.md` |
| opencode | `.opencode/commands/betrayal-haunt-writer.md`（+ 子代理 `.opencode/agents/betrayal-haunt-validator.md`） |
| Claude Code | `.claude/skills/betrayal-haunt-writer/SKILL.md` |

## 不可违背的铁律 / Hard rules（摘要，完整见 workflow.md）

- 每个剧本必须同时产出**英雄剧本 (Secrets of Survival)** 与**奸徒剧本 (Traitor's Tome)** 两册。
- 一切机制建立在基础游戏规则之上（`shared/betrayal-haunt-writer/references/game-rules.md`），
  只引用真实组件（`.../references/components.md`），拿不准的卡牌用泛指。
- 剧本必须声明触发条件（预兆 Omen / 揭示房间 Room / 人物角色 Character，各自可选、至少
  一项），且声明的每一项都要在叙事与机制中扮演实质角色；未声明维度不得有硬依赖。
- **中英文剧本分文件**（`en/`、`zh/`），规则数值逐条对等，英文为规则基准；交付时按需单语。
- 生成后**必须**用所在工具的子代理机制并行执行三路校验（英雄剧本 / 奸徒剧本 / 胜利条件），
  未通过不得交付。校验提示词见 `.../references/design-checklist.md` 的 "Validator Protocol"。

## 输出位置 / Where output goes

生成的剧本写到仓库根目录 `haunts/haunt-<编号>-<slug>/`（编号自 101 起；`en/` 与 `zh/`
分目录 + `design-notes.md`）。**不要**把生成的剧本写进任何工具的入口目录或 `shared/`
（`shared/.../examples/` 仅存放随仓库分发的示例模板）。

## 仓库约定 / Repo conventions

- 文档与剧本保持中英双语风格，与现有文件一致。
- 修改 `shared/betrayal-haunt-writer/` 下的规则或模板时，三个工具会同步生效——这正是
  单一事实源的目的；不要为某个工具单独 fork 一份内容。

> **Claude Code 用户注意**：Claude Code 不读本文件，请确保等价指引也存在于 `CLAUDE.md`。
> Claude Code does not read AGENTS.md; keep equivalent guidance in `CLAUDE.md`.
