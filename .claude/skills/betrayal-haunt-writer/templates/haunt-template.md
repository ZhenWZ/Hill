# 剧本模板 / Haunt Template

复制下列三个文件骨架到 `haunts/haunt-<编号>-<slug>/` 并填空。`{...}` 为占位符。
英文为规则基准文本，中文紧随其后。

---

## File 1: `traitors-tome.md`

```markdown
# Haunt {N} — {English Title} / {中文标题}
**Traitor's Tome 奸徒之书** · *Do not read until the Haunt begins. 闹鬼开始前不得阅读。*

> Trigger 触发: {Omen} in {Room / any omen room}
> Traitor 奸徒: {official-style selection line, EN + 中文}

*{Flavor: 2–3 paragraphs, second person — the moment you turn. EN}*

*{开场叙事中文版}*

## Right Now / 此时此刻
{Placement & setup instructions. Token shapes, distances, redistribution. EN}

{设置指令中文版}

## What You Know About the Heroes / 你对英雄的了解
{One sentence. EN} / {一句话中文}

## You Win When ... / 当……你便获胜
... {single objective condition}{, or else all heroes are dead}. (EN)
……{中文条件}。
{Fallback line for any required card/room. 兜底句。}

## The {Monster} Must Do This ... / {怪物}行动规则
{Mandatory monster-turn behavior, movement quirks, carrying rules. EN}

{中文版}

## Special Attack Rules / 特殊攻击规则
{Attack trait, damage type/conversion, immunities, stealing. EN}

{中文版}

## If You Win ... / 若你获胜
*{Ending flavor. EN}*

*{结局叙事中文版}*

---
**{Monster Name} {怪物中文名}** — Speed {X} · Might {Y} · Sanity {Z}
```

---

## File 2: `secrets-of-survival.md`

```markdown
# Haunt {N} — {English Title} / {中文标题}
**Secrets of Survival 生存秘要**

*{Flavor: same event, heroes' viewpoint. EN}*

*{开场叙事中文版}*

## Right Now / 此时此刻
{Hero-side setup: set aside N triangular Roll tokens, Turn/Damage Track start, etc. EN}

{中文版}

## What You Know About the Bad Guys / 你对坏家伙的了解
{One sentence. EN} / {一句话中文}

## You Win When ... / 当……你便获胜
... {single objective condition}. (EN)
……{中文条件}。

## How to {Defeat/Banish/Escape ...} / 如何{……}
Each hero can only attempt one step each turn. 每名英雄每回合只能尝试其中一步。

1. {Step: location (+fallback), trait roll of N+, token gained. EN}
   {中文}
2. {...}
3. {Final blow: how the win condition is physically executed. EN}
   {中文}

## If You Win ... / 若你获胜
*{Ending flavor. EN}*

*{结局叙事中文版}*
```

---

## File 3: `design-notes.md`

```markdown
# Haunt {N} — Design Notes 设计说明

- Trigger 触发组合: {Omen} × {Room(s)}; 编号 {N}（自定义自 101 起）
- Traitor 奸徒选择: {line}
- Expansion motifs 拓展母题: {base only / 狼人篇 / 圣诞篇 …}
- Win conditions 胜利条件: Heroes — {…} / Traitor — {…}（互斥性说明）
- Pacing clock 节奏钟: {mechanism, 预计 8–12 轮收束}
- Task-chain math 任务链估算: {步骤数 × 成功率 vs 轮数 × 英雄数}
- Player-count scaling 人数适应: {…}
- Validation 校验记录: {3 个 validator 结论 + 修订轮次}
- Known issues 已知问题: {none / list}
```
