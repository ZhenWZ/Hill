# Hill

山屋惊魂剧本拓展 / Custom haunts for Betrayal at House on the Hill.

## 剧本生成器 / Haunt Writer

剧本生成器支持三种 agent CLI，规范工作流与全部参考资料是**工具无关的单一事实源**，
集中在 `shared/betrayal-haunt-writer/`；各工具只放一个轻量入口指向它，杜绝内容漂移。

| 工具 | 入口文件 | 调用方式 |
|---|---|---|
| **Claude Code** | `.claude/skills/betrayal-haunt-writer/SKILL.md` | 说"写一个山屋惊魂剧本"，或 `/betrayal-haunt-writer 主题=邪恶圣诞老人 预兆=Bite` |
| **OpenAI Codex** | `.agents/skills/betrayal-haunt-writer/SKILL.md` | Codex skill，隐式触发或显式调用 |
| **opencode** | `.opencode/commands/betrayal-haunt-writer.md`（+ 子代理 `.opencode/agents/betrayal-haunt-validator.md`） | `/betrayal-haunt-writer 主题=… 预兆=…` |

```
shared/betrayal-haunt-writer/     # 单一事实源（三工具共用）
├── workflow.md                   # 规范工作流 Step 0–6
├── references/                   # 规则 / 组件 / 格式 / 设计与校验准则
├── templates/                    # 分语言文件模板
└── examples/haunt-101-silent-night/   # 完整合格示例
```

每次生成产出五个文件到 `haunts/haunt-<编号>-<slug>/`（中英文剧本分离，按需单语交付）：

- `en/secrets-of-survival.md` / `en/traitors-tome.md` — 英雄剧本与奸徒剧本（英文，规则基准）
- `zh/secrets-of-survival.md` / `zh/traitors-tome.md` — 《生存秘要》与《奸徒之书》（中文）
- `design-notes.md` — 设计说明与校验记录

特性：以官方两册剧本为格式模板；基于基础游戏规则构建；剧本内容由触发条件（预兆牌/
揭示房间/人物角色，可选一项或多项）决定并与之深度绑定；道具取自基础版及公开发售拓展
（狼人篇 The Werewolf's Journey、圣诞篇 A Yuletide Tale）；生成后自动派发 3 个
subagent 分别校验英雄剧本、奸徒剧本与双方胜利条件的逻辑性与可玩性。

示例产出见 `shared/betrayal-haunt-writer/examples/haunt-101-silent-night/`。
