# haunts / 生成的剧本

本目录存放**生成器产出的自定义剧本**。每个剧本一个子目录，中英文分离。
This directory holds the custom haunts produced by the generator — one folder per
haunt, with Chinese and English split into separate files.

## 命名与编号 / Naming & numbering

- 子目录命名：`haunt-<编号>-<slug>/`，例如 `haunt-101-silent-night/`。
- **编号自 101 起**，避开官方编号：基础版 1–50、Widow's Walk 拓展 51–100。
- `<slug>` 用英文标题的小写连字符形式。

## 每个剧本的文件 / Files per haunt

```
haunts/haunt-<编号>-<slug>/
├── en/secrets-of-survival.md   英雄剧本·英文（规则基准）
├── en/traitors-tome.md         奸徒剧本·英文（规则基准）
├── zh/secrets-of-survival.md   英雄剧本·中文《生存秘要》
├── zh/traitors-tome.md         奸徒剧本·中文《奸徒之书》
└── design-notes.md             设计说明（触发绑定 / 平衡 / 校验记录）
```

英文为规则基准文本，中文版规则数值逐条对等；上桌时任取一种语言的两册即可游玩。

## 怎么生成 / How to generate

不要手写到本目录——用生成器产出（任一工具均可，规范流程见
`shared/betrayal-haunt-writer/workflow.md`）：

- **Claude Code**：说"写一个山屋惊魂剧本"，或 `/betrayal-haunt-writer 主题=… 预兆=…`
- **Codex**：skill `betrayal-haunt-writer`（隐式触发或显式调用）
- **opencode**：`/betrayal-haunt-writer 主题=… 预兆=…`

每个剧本生成后都会经三路子代理校验（英雄剧本 / 奸徒剧本 / 胜利条件），通过后才交付；
校验结论记录在该剧本的 `design-notes.md`。

> 完整合格示例（随仓库分发、不属于生成产物）见
> `shared/betrayal-haunt-writer/examples/haunt-101-silent-night/`。
