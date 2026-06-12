# 剧本模板 / Haunt Template

每个剧本输出 **5 个文件** 到 `haunts/haunt-<编号>-<slug>/`：

```
haunts/haunt-<N>-<slug>/
├── en/secrets-of-survival.md   英雄剧本·英文（规则基准）
├── en/traitors-tome.md         奸徒剧本·英文（规则基准）
├── zh/secrets-of-survival.md   英雄剧本·中文《生存秘要》
├── zh/traitors-tome.md         奸徒剧本·中文《奸徒之书》
└── design-notes.md             设计说明（设计者自用，可中文为主）
```

`{...}` 为占位符。中文版与英文版**节次相同、规则数值逐条对等**，叙事独立成篇（不留另一语言文字）。
交付时按用户所选语言提供其中一种语言的两册。

---

## File: `en/traitors-tome.md`

```markdown
# Haunt {N} — {English Title}
**Traitor's Tome** · *Do not read until the Haunt begins.*

> **Trigger Requirements** — Omens: {Bite / any}; Rooms: {Kitchen / any omen room
> (not …)}; Characters: {requires … in play / —}
> **Traitor**: {official-style selection line}

*{Flavor: 2–3 paragraphs, second person — the moment you turn.}*

## Right Now
{Placement & setup. Token shapes, distances, redistribution. If the trigger
declares a Room dimension, anchor placement to "the haunt-revealing room"
where it serves the design.}

## What You Know About the Heroes
{One sentence.}

## You Win When ...
... {single objective condition}{, or else all heroes are dead}.
{Fallback line for any required card/room.}

## The {Monster} Must Do This ...
{Mandatory monster-turn behavior, movement quirks, carrying rules.}

## Special Attack Rules
{Attack trait, damage type/conversion, immunities, stealing.}

## If You Win ...
*{Ending flavor.}*

---
**{Monster Name}** — Speed {X} · Might {Y} · Sanity {Z}
```

## File: `zh/traitors-tome.md`

```markdown
# 剧本 {N} — {中文标题}
**奸徒之书** · *闹鬼开始前不得阅读。*

> **触发条件** — 预兆：{咬痕 (Bite) / 任意}；房间：{厨房 (Kitchen) / 任意预兆房间
> （…除外）}；角色：{需要…在场 / —}
> **奸徒**：{官方惯例句式中文版}

*{开场叙事：2–3 段，第二人称——你黑化的瞬间。}*

## 此时此刻
{设置指令。token 形状、距离、重新分配。房间名首次出现附英文原名。}

## 你对英雄的了解
{一句话。}

## 当……你便获胜
……{单一可客观判定的条件}{，或所有英雄全部死亡}。
{关键卡牌/房间的兜底句。}

## {怪物}行动规则
{怪物回合强制行为、特殊移动、携带规则。}

## 特殊攻击规则
{攻击属性、伤害类型与转换、免疫、偷取。}

## 若你获胜
*{结局叙事。}*

---
**{怪物中文名} ({Monster Name})** — 速度 {X} · 力量 {Y} · 精神 {Z}
```

## File: `en/secrets-of-survival.md`

```markdown
# Haunt {N} — {English Title}
**Secrets of Survival**

> **Trigger Requirements** — {same line as the Traitor's Tome}

*{Flavor: same event, heroes' viewpoint.}*

## Right Now
{Hero-side setup: set aside N triangular Roll tokens, Turn/Damage Track start, etc.}

## What You Know About the Bad Guys
{One sentence.}

## You Win When ...
... {single objective condition}.

## How to {Defeat/Banish/Escape ...}
Each hero can only attempt one step each turn.

1. {Step: location (+fallback), trait roll of N+, token gained.}
2. {...}
3. {Final blow: how the win condition is physically executed.}

## If You Win ...
*{Ending flavor.}*
```

## File: `zh/secrets-of-survival.md`

```markdown
# 剧本 {N} — {中文标题}
**生存秘要**

> **触发条件** — {与奸徒之书一致}

*{开场叙事：同一事件的英雄视角。}*

## 此时此刻
{英雄侧设置：拨出 N 个三角检定标记、回合/伤害轨起始位等。}

## 你对坏家伙的了解
{一句话。}

## 当……你便获胜
……{单一可客观判定的条件}。

## 如何{……}
每名英雄每回合只能尝试其中一步。

1. {步骤：地点（含兜底）、属性检定 N+、获得的标记。}
2. {……}
3. {终结一击：胜利条件的实际执行方式。}

## 若你获胜
*{结局叙事。}*
```

## File: `design-notes.md`

```markdown
# Haunt {N} — Design Notes 设计说明

- Trigger 触发条件: Omens {…} / Rooms {…} / Characters {…}（声明维度 + 各自可选）
- Trigger integration 触发绑定: {声明的每个维度在机制与叙事中的落点；未声明维度无硬依赖的说明}
- Traitor 奸徒选择: {line}
- Expansion motifs 拓展母题: {base only / 狼人篇 / 圣诞篇 …}
- Win conditions 胜利条件: Heroes — {…} / Traitor — {…}（互斥性说明）
- Pacing clock 节奏钟: {mechanism, 预计 8–12 轮收束}
- Task-chain math 任务链估算: {步骤数 × 成功率 vs 轮数 × 英雄数}
- Player-count scaling 人数适应: {…}
- Language parity 语言对等: {en 为规则基准；zh 对等校验结果}
- Validation 校验记录: {3 个 validator 结论 + 修订轮次}
- Known issues 已知问题: {none / list}
```
