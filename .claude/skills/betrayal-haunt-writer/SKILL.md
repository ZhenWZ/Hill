---
name: betrayal-haunt-writer
description: 生成《山屋惊魂》(Betrayal at House on the Hill) 中英双语自定义剧本 (Custom Haunt)。每次生成均包含英雄剧本 (Secrets of Survival) 与奸徒剧本 (Traitor's Tome) 两册，以官方剧本为格式模板，基于基础游戏规则构建，道具可取自基础版及公开发售拓展（狼人篇 The Werewolf's Journey、圣诞篇 A Yuletide Tale），生成后自动调用 subagent 校验英雄剧本、奸徒剧本及双方胜利条件的逻辑性与可玩性。Use when the user asks to write or generate a Betrayal at House on the Hill haunt, 山屋惊魂剧本, 小黑屋剧本, 山中小屋剧本, custom haunt, or a hero/traitor scenario for this game.
argument-hint: [主题 theme] [预兆 omen] [房间 room] [拓展 expansion]
---

# 山屋惊魂剧本生成器 / Betrayal Haunt Writer

为《山屋惊魂》（Betrayal at House on the Hill，俗称"小黑屋"）创作可直接上桌游玩的自定义剧本。
Creates table-ready custom haunts for Betrayal at House on the Hill, in the official
two-book format, fully bilingual (中文 + English).

**铁律 / Hard rules:**

1. 每个剧本必须同时产出 **英雄剧本 (Secrets of Survival)** 和 **奸徒剧本 (Traitor's Tome)** 两册。
2. 一切机制必须建立在基础游戏规则之上（见 `references/game-rules.md`），不得发明与核心规则冲突的机制。
3. 只引用真实存在的组件（见 `references/components.md`）：基础版（第二版）房间/预兆/道具/角色，以及狼人篇、圣诞篇拓展的主题元素。不确定的卡牌一律用泛指（如 "any weapon Item / 任意武器道具"），这也是官方剧本的写法。
4. 全文中英双语：每个小节先英文后中文（或并排），术语对照见 `references/haunt-format.md` 末尾的词汇表。
5. 生成后**必须**执行第 4 步的 subagent 三路校验，未通过校验不得交付。

## Workflow / 工作流程

### Step 0 — 收集参数 / Gather inputs

从用户输入中提取（缺省项自行做出合理选择并在交付时说明，不要追问）：

- **主题 theme**（如：狼人、邪恶圣诞老人、镜中人……）
- **触发组合 trigger**：预兆 Omen × 房间 Room（必须是 13 个预兆房间之一）
- **拓展 expansion**：是否使用狼人篇 / 圣诞篇主题元素（默认：按主题自动判断）
- **奸徒选择规则 traitor selection**（默认：参考官方惯例，见 haunt-format.md）
- **编号与标题**：自定义剧本编号从 101 起（避开官方 1–50 与 Widow's Walk 51–100）

### Step 1 — 读取参考资料 / Load references

按需读取本 skill 的参考文件（不要凭记忆编造规则或组件）：

| 文件 | 内容 |
|---|---|
| `references/game-rules.md` | 基础游戏规则摘要（回合、属性检定、伤害、怪物、闹鬼触发） |
| `references/components.md` | 组件清单：房间/预兆/道具/角色/标记物 + 狼人篇、圣诞篇内容 |
| `references/haunt-format.md` | 官方两册剧本的逐节格式、剧本选择表与奸徒选择惯例、双语词汇表 |
| `references/design-checklist.md` | 可玩性与平衡设计准则 + 校验评分标准 |
| `templates/haunt-template.md` | 双语填空模板 |
| `examples/haunt-101-silent-night.md` | 一个完整的合格示例 |

### Step 2 — 设计核心结构 / Design the core (写入 design-notes 草稿)

先写设计骨架，再写正文。骨架必须回答：

1. **双方目标**：英雄赢 = ？奸徒赢 = ？两者必须**互斥**且**至少有一方必然在有限回合内达成**（通常靠 Turn/Damage Track 计时轨道兜底，防止僵局）。
2. **信息不对称**：两册各自隐瞒什么？（官方惯例：双方都知道对方"在做什么"，但不知道具体数值/位置/步骤细节。）
3. **奸徒是谁**：用官方惯例句式（Haunt revealer / 最高·最低某属性 except HR / 角色爱好 / HR 左侧 / None at first）。
4. **节奏钟**：什么机制迫使游戏在 ~10 回合内收束？
5. **任务链**：英雄方通常是 2–4 步任务链（找→做检定→搬运→终结一击）；奸徒方通常是怪物压制 + 自己的进度条。
6. **怪物属性**：参考官方量级（Speed 2–6, Might 2–8, Sanity 2–6；BOSS 级单体可到 8）。
7. **道具/标记物**：列出用到的 token（官方用三角 Roll token、五边形 pentagonal token、圆形怪物 token 等）与卡牌。

### Step 3 — 撰写两册剧本 / Write both books

使用 `templates/haunt-template.md`，按官方节次写作，**先写奸徒册再写英雄册**（奸徒册机制最重，英雄册需与之严格互补）：

- 两册的开场叙事描写同一事件的两种视角（官方手法）。
- 英雄册的 "What You Know About the Bad Guys" 必须与奸徒册实际目标一致但不泄露细节；反之亦然。
- 所有检定写明 `属性 roll of N+`；所有放置写明具体房间或放置规则（如"同层至少 5 格远"）。
- 输出文件（仓库根目录下）：
  - `haunts/haunt-<编号>-<slug>/secrets-of-survival.md`（英雄剧本，双语）
  - `haunts/haunt-<编号>-<slug>/traitors-tome.md`（奸徒剧本，双语）
  - `haunts/haunt-<编号>-<slug>/design-notes.md`（设计骨架 + 触发组合 + 奸徒选择 + 平衡说明）

### Step 4 — Subagent 三路校验 / Three-way validation (REQUIRED)

文件落盘后，**在同一条消息中并行**调用 Agent 工具（subagent_type: `general-purpose`）启动三个校验员。
每个校验员的完整提示词模板在 `references/design-checklist.md` 的 "Validator Prompts" 一节，必须包含：

1. **英雄剧本校验员 Hero validator** — 只读英雄册 + 规则/组件参考：规则合法性、任务链可完成性、指令无歧义、双语一致。
2. **奸徒剧本校验员 Traitor validator** — 只读奸徒册 + 规则/组件参考：同上，外加怪物数值量级检查。
3. **胜利条件交叉校验员 Win-condition validator** — 读两册 + design-notes：双方胜利条件互斥、无僵局（有限回合内必有一方获胜）、信息不对称无穿帮（两册对同一事实的描述不矛盾）、粗略平衡估计（双方胜率应在 35%–65% 区间内）。

每个校验员必须返回结构化结论：`PASS` 或 `FAIL + 编号问题清单（每条注明文件与小节）`。

### Step 5 — 修订循环 / Revision loop

- 任一校验员 FAIL：修复所有列出的问题，**仅对失败维度重新派发校验员**，最多迭代 2 轮。
- 2 轮后仍有遗留问题：照常交付，但在 design-notes.md 和最终回复中如实列出未解决项。

### Step 6 — 交付 / Deliver

最终回复必须包含：剧本编号与标题（中英）、触发组合、奸徒是谁、双方一句话胜利条件、三个校验员的结论摘要、输出文件路径。
