# 基础游戏规则摘要 / Base Game Rules Summary

来源：官方规则书（第二版规则与第一版规则一致处合并）。剧本中的一切机制都必须与本文兼容。
Source: official rulebook. Every haunt mechanic must be compatible with this document.

## 1. 角色与属性 / Explorers & Traits

- 每位玩家一名探索者 (explorer)，角色卡上有 4 条属性轨：**Speed 速度、Might 力量、Sanity 精神、Knowledge 知识**，用卡扣标记当前值。
- 属性轨为一串数字（约 1–8），起始值为绿色数字；轨道最左端是**骷髅符号**。
- 闹鬼 (Haunt) 开始前，属性最低只能降到轨道最低数字；闹鬼开始后，任何属性降到骷髅符号则**角色死亡**。
- 属性伤害分两类：**physical damage 物理伤害**（自行分配到 Speed/Might）、**mental damage 精神伤害**（自行分配到 Sanity/Knowledge）。未注明类型的"damage N"由规则文本指明属性。

## 2. 回合流程 / Turn Order

每个玩家回合可按任意顺序执行任意多项：

1. **移动 Move**：最多走等于当前 Speed 的格数（房间数）。至少永远可以移动 1 格。
2. **发现新房间 Discover a room**：走到没有房间的门口时翻开牌库顶的房间板块；层符号匹配当前楼层才放置。房间上有牌符号（牛头=Omen，螺旋=Event，公牛头骨=Item）则**停止移动**并抽对应卡。
3. **尝试检定 Attempt a die roll**：同一检定每回合只能尝试一次。
4. **使用道具/预兆卡 Use Items or Omens**。
5. **攻击 Attack**（仅闹鬼后，每回合一次）。

## 3. 骰子与检定 / Dice & Trait Rolls

- 本游戏骰子为特制六面骰，面值 **0 / 1 / 2**（各两面）。N 个骰子的期望值 = N。
- 属性检定：投等于当前属性值的骰数，与目标值比较。剧本写法：`Knowledge roll of 5+`。
- 设计参考：目标值 4+ 对属性 4 的角色约 62% 成功；6+ 对属性 5 约 30%。任务链检定目标建议 4+ 到 6+。

## 4. 卡牌 / Cards

- **Event 事件卡**：立即执行后弃掉（除非卡面要求保留）。
- **Item 道具卡**：面朝上保留；可使用、给予同房间愿意接受的探索者、丢弃（放道具堆标记）、捡起、（闹鬼后）抢夺。
- **Omen 预兆卡**：面朝上保留并执行；抽到预兆的玩家在**回合结束时做闹鬼检定 (Haunt roll)**。
- 部分预兆是**同伴 (companion)**（Girl, Dog, Madman）：跟随监护人 (custodian)，不能被丢弃/交易，但可按剧本规则转移监护权。

## 5. 闹鬼触发 / The Haunt Roll

- 闹鬼检定：投 6 骰，若结果 **小于** 场上已抽出的预兆卡总数，闹鬼开始。投出该结果的玩家是 **Haunt Revealer（闹鬼揭示者，HR）**。
- 用 **预兆 × 抽出预兆的房间** 在剧本选择表上交叉索引得到剧本编号（见 haunt-format.md）。
- 奸徒 (traitor) 按该剧本指定的规则产生；奸徒带 Traitor's Tome 离开房间阅读，其余玩家（英雄 heroes）共读 Secrets of Survival 同编号剧本。
- 双方读完后先执行各自册子的 "Right Now" 设置；首个回合从**奸徒左手边玩家**开始，顺时针进行；奸徒回合后是**怪物回合 (monster turn)**。

## 6. 闹鬼后战斗 / Combat (after the Haunt)

- 基本攻击：双方各投 **Might** 骰，点数高者获胜，差值即对输家造成的物理伤害（攻击者输了同样受伤）。
- 剧本可指定用其他属性攻击/防御（如 Sanity combat 精神战斗），并可指定伤害类型。
- 距离攻击（如左轮手枪 Revolver 用 Speed）：防御方仍用 Might，且防御方获胜时**不**反伤攻击方。
- 探索者被打死即死亡；死亡探索者的道具留在原房间（放道具堆标记），同伴在原房间等待新监护人。

## 7. 怪物 / Monsters

- 怪物由奸徒在怪物回合统一操控；怪物移动 = 投等于其 Speed 的骰数（同种怪物群体投一次）。
- 怪物被击败时通常只是**眩晕 (stunned)**：翻面，下个怪物回合结束翻回。眩晕的怪物不阻挡移动、被攻击获胜也不造成伤害。剧本可以规定某怪物能被杀死。
- 除非剧本特别说明，怪物**不能携带或使用道具**、无视若干房间的特殊规则（Crypt、Furnace Room）、无视障碍房间（Vault/Tower/Chasm/Catacombs 的通行检定）。
- 闹鬼后经过敌对者：离开同房间的每个敌对者（未眩晕）多花 1 点移动。
- 奸徒死亡后，只要怪物仍能达成奸徒目标，怪物回合继续进行。

## 8. 常用计时与标记 / Timers & Tokens

- **Turn/Damage Track 回合/伤害轨**（1–8 带卡扣）：官方剧本最常用的"节奏钟"，用于倒计时、累积进度、怪物成长等。
- 三角 Roll token（用作进度/任务记号）、五边形 token（大型物件，如石棺）、圆形怪物 token（多编号）、Item Pile / Vault Empty 等专用 token。
- 自定义剧本只应使用以上这些实体可得的标记物。

## 9. 楼层与特殊房间要点 / Floors & Special Rooms (选摘)

- 三层：Ground 地面层（Entrance Hall/Foyer/Grand Staircase 起始）、Upper 楼上（Upper Landing 起始）、Basement 地下室（Basement Landing 起始）。
- Grand Staircase ↔ Upper Landing 永远连通；Stairs from Basement ↔ Foyer 经秘门连通（发现后可用）。
- Coal Chute：地面层单向滑到 Basement Landing。Collapsed Room：地面层踩塌掉到地下室（Might roll 3+ 免伤）。Mystic Elevator：每回合一次随骰子去任意层。
- 障碍房间 (barrier rooms)：Vault、Tower、Chasm、Catacombs——需检定才能通过，每回合一次。
- 前门永远锁死——"逃出大宅"类剧本必须提供剧本内的逃生通道。

## 10. 设计红线 / Design Red Lines

剧本机制**不得**：

- 改变骰子面值、属性轨结构或回合基本顺序（可以"新增"动作，不可重定义基础动作）。
- 要求基础版+所用拓展之外的实体组件。
- 在闹鬼前生效（剧本文本从 "Right Now" 起才存在）。
- 让任何一方在 "Right Now" 阶段即被判定死亡/失败（官方剧本保证开局双方均有行动空间）。
