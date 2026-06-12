# Hill

山屋惊魂剧本拓展 / Custom haunts for Betrayal at House on the Hill.

## 剧本生成器 Skill / Haunt Writer Skill

本仓库内置 Claude Code skill：`.claude/skills/betrayal-haunt-writer/`。

在 Claude Code 中直接说"写一个山屋惊魂剧本"（可附主题/预兆/房间/拓展），或运行：

```
/betrayal-haunt-writer 主题=邪恶圣诞老人 预兆=Bite
```

每次生成产出三个文件到 `haunts/haunt-<编号>-<slug>/`：

- `secrets-of-survival.md` — 英雄剧本（中英双语）
- `traitors-tome.md` — 奸徒剧本（中英双语）
- `design-notes.md` — 设计说明与校验记录

特性：以官方两册剧本为格式模板；基于基础游戏规则构建；道具取自基础版及公开发售拓展
（狼人篇 The Werewolf's Journey、圣诞篇 A Yuletide Tale）；生成后自动派发 3 个
subagent 分别校验英雄剧本、奸徒剧本与双方胜利条件的逻辑性与可玩性。

示例产出见 `.claude/skills/betrayal-haunt-writer/examples/haunt-101-silent-night.md`。
