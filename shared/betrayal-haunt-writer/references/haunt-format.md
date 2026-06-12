# 官方剧本格式 / Official Haunt Format

依据官方 Traitor's Tome 与 Secrets of Survival 实体书逐节归纳。生成的剧本必须逐节对应。

## 触发与编号 / Trigger & Numbering

- 官方剧本由 **预兆 Omen × 预兆房间 Room** 在剧本选择表 (Haunt Selection Table) 交叉索引：
  13 预兆 × 13 房间 → 编号 1–50（基础版）；Widow's Walk 拓展占 51–100。
- **自定义剧本编号从 101 起**，并仿照官方"自定义剧本最低需求表"在两册卷首声明触发条件
  (Trigger Requirements)。三个维度各自可选、至少声明一项：

  | 维度 | 写法示例 |
  |---|---|
  | Omens 预兆 | `Omens: Bite`（必须抽到咬痕触发）/ `Omens: any 任意` |
  | Rooms 房间 | `Rooms: Kitchen or Furnace Room` / `Rooms: any omen room 任意预兆房间`（为平衡可写排除项：`not Pentagram Chamber`） |
  | Characters 角色 | `Characters: requires Sara Nguyen in play` / 不声明 |

- **触发绑定原则**：声明了什么，剧本内容就必须用到什么——
  - 声明的预兆 = 故事起因或核心道具，须在机制中出场；
  - 声明的房间用 **"the haunt-revealing room / 闹鬼揭示房间"** 指代并赋予机制意义
    （怪物出生点、仪式点、逃生口……），使该维度写 "any omen room" 时对 13 间房均成立；
  - 声明的角色须有定制内容（专属叙事/能力/弱点，或在奸徒选择规则中点名）；
  - **未声明的维度不得产生硬依赖**——不要让一个 `Omens: any` 的剧本机制依赖 Girl 在场。

## 奸徒选择惯例 / Traitor Selection Conventions（官方原表用语）

从以下句式中选择其一（HR = Haunt Revealer 闹鬼揭示者）：

- `Haunt revealer`（最常用）
- `Highest/Lowest <Trait> (except for the haunt revealer)`
- `<角色名> (<爱好>) or highest/lowest <Trait>`，如 `Jenny LeClerc (reading) or highest Knowledge`
- `Left of the haunt revealer`（HR 左侧玩家）
- `None (at first)`（隐藏奸徒/无奸徒开局，剧本内文必须给出奸徒何时、如何产生）
- 平手裁定（官方固定句）：若两人同属性平手且其一是 HR，选 HR；都不是 HR，选 HR 左起第一位。

## 两册逐节结构 / Section-by-section Structure

每册产出 **英文、中文两个独立文件**（`en/`、`zh/` 目录），节次相同；下示节名以
`英文节名 / 中文节名` 并列，实际文件中只用本语言的节名。

### Traitor's Tome 奸徒剧本（先写）

```
Haunt <编号> — <标题>
<卷首触发声明 Trigger Requirements：Omens / Rooms / Characters>
<奸徒选择 Traitor selection line>

<开场叙事 Flavor>            2-3 段，第二人称，描写奸徒黑化瞬间与动机。斜体排版。

Right Now / 此时此刻          设置指令：放置怪物/物件 token（写明形状）、奸徒自身状态、
                             起始位置规则（如"与闹鬼房间同层且至少 5 格远"）、预兆/道具重分配。

What You Know About the Heroes / 你对英雄的了解
                             一句话概括英雄方目标，不泄露其具体步骤数值。

You Win When ... / 当……你便获胜
                             单一、可客观判定的胜利条件（常含"或所有英雄死亡 or else all
                             heroes are dead"）。若关键卡牌可能不在场，写官方兜底句：
                             "若 X 不在场上，下次发现带预兆符号的房间时，从预兆牌库检索抽出 X。"

<怪物名> Must Do This ... / 怪物行动规则
                             怪物回合的强制行为、特殊移动、能否携带物品等。

Special Attack Rules / 特殊攻击规则
                             攻击属性、伤害类型与转换（参考官方手法：先削某属性到底再转伤另一属性）、
                             免疫（如 immune to Speed attacks）、偷取道具等。

If You Win ... / 若你获胜     1 段结局叙事。

<怪物属性条>                  <Monster Name>  Speed X · Might Y · Sanity Z
```

### Secrets of Survival 英雄剧本（与奸徒册互补）

```
Haunt <编号> — <标题>
<卷首触发声明（与奸徒册一致）>

<开场叙事 Flavor>            同一事件的英雄视角，2-3 段。

Right Now / 此时此刻          英雄侧设置：拨出 N 个三角 Roll token、Turn/Damage Track 起始位等。

What You Know About the Bad Guys / 你对坏家伙的了解
                             一句话概括奸徒目标（与奸徒册实际目标一致，不含细节）。

You Win When ... / 当……你便获胜
                             单一、可客观判定的胜利条件。

How to <做某事> ... / 任务链  编号步骤 1..N：每步写明地点（含"该房间不在场时"的兜底）、
                             检定（trait roll of N+）、获得什么 token、
                             "每名英雄每回合只能尝试其中一步 Each hero can only attempt
                             one step each turn"。终结步骤写明终结方式（如 Sanity combat）。

If You Win ... / 若你获胜     1 段结局叙事。
```

## 写作风格 / Style Notes

- 第二人称、现在时；恐怖氛围但克制，PG-13。
- 指令句使用规则术语原文（Knowledge roll of 5+ / put the X token / at the end of each turn）。
- 两册对同一可见事实（token 位置、怪物外观、可见事件）描述必须一致；只对**意图与暗步骤**保持不对称。
- **语言分离**：英文版与中文版各自独立成文件、单语成篇，玩家只需其中一份即可游玩。
  英文为规则基准文本；中文版叙事可自由润色，但所有规则句的数值、目标值、房间名
  （首次出现附英文原名，如"五芒星密室 (Pentagram Chamber)"）、判定条件必须与英文版
  逐条对等。词汇统一用下方词汇表。

## 双语词汇表 / Glossary

| English | 中文 |
|---|---|
| Haunt | 闹鬼 / 剧本 |
| Haunt Revealer (HR) | 闹鬼揭示者 |
| Traitor / Heroes | 奸徒 / 英雄 |
| Traitor's Tome | 奸徒之书（奸徒剧本） |
| Secrets of Survival | 生存秘要（英雄剧本） |
| Explorer | 探索者 |
| Trait roll | 属性检定 |
| Speed / Might / Sanity / Knowledge | 速度 / 力量 / 精神 / 知识 |
| physical / mental damage | 物理伤害 / 精神伤害 |
| Omen / Event / Item | 预兆 / 事件 / 道具 |
| companion / custodian | 同伴 / 监护人 |
| monster turn | 怪物回合 |
| stunned | 眩晕 |
| Turn/Damage Track | 回合/伤害轨 |
| Right Now | 此时此刻 |
| You Win When… | 当……你便获胜 |
| If You Win… | 若你获胜 |
