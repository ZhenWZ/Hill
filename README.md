# Hill

山屋惊魂剧本拓展 / Custom haunts for Betrayal at House on the Hill.

## 剧本生成器 Skill / Haunt Writer Skill

本仓库内置 Claude Code skill：`.claude/skills/betrayal-haunt-writer/`。

在 Claude Code 中直接说"写一个山屋惊魂剧本"（可附主题/预兆/房间/拓展），或运行：

```
/betrayal-haunt-writer 主题=邪恶圣诞老人 预兆=Bite
```

每次生成产出五个文件到 `haunts/haunt-<编号>-<slug>/`（中英文剧本分离，按需单语交付）：

- `en/secrets-of-survival.md` / `en/traitors-tome.md` — 英雄剧本与奸徒剧本（英文，规则基准）
- `zh/secrets-of-survival.md` / `zh/traitors-tome.md` — 《生存秘要》与《奸徒之书》（中文）
- `design-notes.md` — 设计说明与校验记录

特性：以官方两册剧本为格式模板；基于基础游戏规则构建；剧本内容由触发条件（预兆牌/
揭示房间/人物角色，可选一项或多项）决定并与之深度绑定；道具取自基础版及公开发售拓展
（狼人篇 The Werewolf's Journey、圣诞篇 A Yuletide Tale）；生成后自动派发 3 个
subagent 分别校验英雄剧本、奸徒剧本与双方胜利条件的逻辑性与可玩性。

示例产出见 `.claude/skills/betrayal-haunt-writer/examples/haunt-101-silent-night/`。
