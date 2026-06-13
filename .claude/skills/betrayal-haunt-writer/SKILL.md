---
name: betrayal-haunt-writer
description: 生成《山屋惊魂》(Betrayal at House on the Hill) 中英文自定义剧本 (Custom Haunt)，中英文剧本分文件输出、按需单语交付。每次生成均包含英雄剧本 (Secrets of Survival) 与奸徒剧本 (Traitor's Tome) 两册，以官方剧本为格式模板，基于基础游戏规则构建，剧本内容由触发条件（预兆牌/揭示房间/人物角色，可选一项或多项）决定并与之深度绑定，道具可取自基础版及公开发售拓展（狼人篇 The Werewolf's Journey、圣诞篇 A Yuletide Tale），生成后自动调用 subagent 校验英雄剧本、奸徒剧本及双方胜利条件的逻辑性与可玩性。Use when the user asks to write or generate a Betrayal at House on the Hill haunt, 山屋惊魂剧本, 小黑屋剧本, 山中小屋剧本, custom haunt, or a hero/traitor scenario for this game.
argument-hint: [主题 theme] [预兆 omen] [房间 room] [角色 character] [语言 lang=zh/en/both]
---

# 山屋惊魂剧本生成器 / Betrayal Haunt Writer (Claude Code)

本 skill 的完整工作流与全部参考资料是工具无关的单一事实源，位于仓库的
**`shared/betrayal-haunt-writer/`**。

**操作步骤：**

1. 先读 `shared/betrayal-haunt-writer/workflow.md`，严格按其 Step 0–6 执行。
2. 该文件中所有相对路径均相对于 `shared/betrayal-haunt-writer/` 目录
   （例如 `references/game-rules.md` → `shared/betrayal-haunt-writer/references/game-rules.md`）。
3. **Step 4 的并行校验在 Claude Code 中用 `Agent` 工具实现**：在同一条消息内并行调用
   三次，`subagent_type: general-purpose`，分别承担英雄剧本 / 奸徒剧本 / 胜利条件三路职责，
   提示词模板见 `shared/betrayal-haunt-writer/references/design-checklist.md` 的
   "Validator Protocol" 一节。

生成的剧本写到仓库根目录 `haunts/haunt-<编号>-<slug>/`（中英分目录），不要写进本 skill 目录。
