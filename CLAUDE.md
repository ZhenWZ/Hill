# CLAUDE.md

> Claude Code 在本仓库工作前读取本文件（不读 `AGENTS.md`）。其余 agent CLI（Codex、
> opencode）读取 `AGENTS.md`，内容等价。

## 这个仓库是什么

《山屋惊魂》(Betrayal at House on the Hill) 自定义剧本仓库。核心交付物是可直接上桌
游玩的剧本，由内置的"剧本生成器"产出。

## 写剧本时必须遵循的流程

当用户要求写山屋惊魂剧本时，会触发 skill `.claude/skills/betrayal-haunt-writer/`。
无论是否经 skill 触发，都遵循同一规范：

1. **先读 `shared/betrayal-haunt-writer/workflow.md`**，严格按其 Step 0–6 执行。这是
   工具无关的**单一事实源**，全部规则、组件、格式、设计与校验准则都在其 `references/`、
   `templates/`、`examples/` 中。不要凭记忆编造规则或组件。
2. `workflow.md` 内的相对路径相对于 `shared/betrayal-haunt-writer/` 目录解析。
3. **Step 4 的三路并行校验用 `Agent` 工具实现**（`subagent_type: general-purpose`，
   同一条消息内并行三次，分别承担英雄剧本 / 奸徒剧本 / 胜利条件职责），提示词模板见
   `shared/betrayal-haunt-writer/references/design-checklist.md` 的 "Validator Protocol"。

## 不可违背的铁律（摘要，完整见 workflow.md）

- 每个剧本必须同时产出**英雄剧本 (Secrets of Survival)** 与**奸徒剧本 (Traitor's Tome)** 两册。
- 一切机制建立在基础游戏规则之上，只引用真实组件，拿不准的卡牌用泛指。
- 剧本必须声明触发条件（预兆 / 房间 / 角色，各自可选、至少一项），声明项须在叙事与机制中
  扮演实质角色；未声明维度不得有硬依赖。
- 中英文剧本分文件（`en/`、`zh/`），规则数值逐条对等，英文为规则基准；交付时按需单语。
- 生成后必须并行执行三路校验，未通过不得交付。

## 输出位置

生成的剧本写到仓库根目录 `haunts/haunt-<编号>-<slug>/`（编号自 101 起；`en/` 与 `zh/`
分目录 + `design-notes.md`）。不要写进任何工具的入口目录或 `shared/`（`shared/.../examples/`
仅存放随仓库分发的示例模板）。

## 仓库约定

- 文档与剧本保持中英双语风格。
- 修改 `shared/betrayal-haunt-writer/` 下的规则或模板会让三个工具（Claude Code / Codex /
  opencode）同步生效——这是单一事实源的目的；不要为某个工具单独 fork 一份内容。
