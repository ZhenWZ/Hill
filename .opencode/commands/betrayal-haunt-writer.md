---
description: 生成《山屋惊魂》(Betrayal at House on the Hill) 中英文自定义剧本——英雄剧本+奸徒剧本两册，中英分文件、按需单语交付，由触发条件（预兆/房间/角色）决定内容，生成后用子代理三路校验。Generate a Betrayal at House on the Hill custom haunt (hero + traitor books).
agent: build
---

# 山屋惊魂剧本生成器 / Betrayal Haunt Writer (opencode)

用户参数（主题 / 预兆 / 房间 / 角色 / 语言）：$ARGUMENTS

本命令的完整工作流与全部参考资料是工具无关的单一事实源，位于仓库的
**`shared/betrayal-haunt-writer/`**。

**操作步骤：**

1. 先读 `@shared/betrayal-haunt-writer/workflow.md`，严格按其 Step 0–6 执行。
2. 该文件中所有相对路径均相对于 `shared/betrayal-haunt-writer/` 目录
   （例如 `references/game-rules.md` → `shared/betrayal-haunt-writer/references/game-rules.md`）。
3. **Step 4 的三路并行校验在 opencode 中用子代理实现**：分别以
   `@betrayal-haunt-validator` 子代理派发英雄剧本 / 奸徒剧本 / 胜利条件三路职责
   （提示词模板见 `shared/betrayal-haunt-writer/references/design-checklist.md` 的
   "Validator Protocol" 一节），每路返回 `VERDICT: PASS` 或 `VERDICT: FAIL + 编号问题清单`。

生成的剧本写到仓库根目录 `haunts/haunt-<编号>-<slug>/`（中英分目录）。
