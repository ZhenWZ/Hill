# 山屋惊魂剧本生成器 — 规范工作流 / Betrayal Haunt Writer — Canonical Workflow

> **这是工具无关的单一事实源 (single source of truth)。** Claude Code、Codex、opencode
> 三个工具的入口文件都指向本文件。所有相对路径均**相对于本文件所在目录**
> (`shared/betrayal-haunt-writer/`)。
>
> **Subagent / 并行校验**：Step 4 要求并行派发三个独立校验员。各工具用各自机制实现：
> - **Claude Code** → `Agent` 工具，`subagent_type: general-purpose`，同一条消息内并行三次。
> - **Codex** → 子代理 / 并行任务机制（sub-agents）。
> - **opencode** → `@betrayal-haunt-validator` 子代理（`.opencode/agents/`），分别派发三路职责。
> 机制不同，但职责、提示词与通过标准完全一致（见 `references/design-checklist.md`）。

为《山屋惊魂》（Betrayal at House on the Hill，俗称"小黑屋"）创作可直接上桌游玩的自定义剧本。
Creates table-ready custom haunts for Betrayal at House on the Hill, in the official
two-book format. 中英文剧本各自独立成册，内容严格对等。

**铁律 / Hard rules:**

1. 每个剧本必须同时产出 **英雄剧本 (Secrets of Survival)** 和 **奸徒剧本 (Traitor's Tome)** 两册。
2. 一切机制必须建立在基础游戏规则之上（见 `references/game-rules.md`），不得发明与核心规则冲突的机制。
3. 只引用真实存在的组件（见 `references/components.md`）：基础版（第二版）房间/预兆/道具/角色，以及狼人篇、圣诞篇拓展的主题元素。不确定的卡牌一律用泛指（如 "any weapon Item / 任意武器道具"），这也是官方剧本的写法。
4. **触发条件决定剧本内容**：剧本必须声明其触发条件——触发预兆 Omen、揭示房间 Room、人物角色 Character 三个维度**各自可选、至少声明一项**——且声明的每一项都必须在叙事和机制中扮演实质角色（见 Step 2 的"触发绑定"）。未声明的维度保持通用，并提供兜底规则。
5. **中英文剧本分离**：每册剧本生成英文、中文两个独立文件，规则数值与判定语句严格对等（英文为规则基准文本）。交付时按用户需要一次只提供一种语言（默认按用户对话语言；用户要求时才双语并出）。
6. 生成后**必须**执行 Step 4 的 subagent 三路校验，未通过校验不得交付。

## Workflow / 工作流程

### Step 0 — 收集参数 / Gather inputs

从用户输入中提取（缺省项自行做出合理选择并在交付时说明，不要追问）：

- **主题 theme**（如：狼人、邪恶圣诞老人、镜中人……）
- **触发条件 trigger**（一项或多项，模拟真实开局时已知的信息）：
  - **预兆 Omen**：玩家实际抽到的预兆牌（13 选一，或"任意"）
  - **房间 Room**：抽出预兆的房间（必须是 13 个预兆房间之一，或"任意预兆房间"）
  - **角色 Character**：在场或成为奸徒的特定探索者（基础版 12 名或拓展角色，可选）
  - 用户给出实际开局信息（"我在厨房翻出了咬痕"）时，触发条件即采用该信息。
- **拓展 expansion**：是否使用狼人篇 / 圣诞篇主题元素（默认：按主题自动判断）
- **语言 lang**：交付语言 zh / en / both（默认按用户对话语言）
- **奸徒选择规则 traitor selection**（默认：参考官方惯例，见 haunt-format.md）
- **编号与标题**：自定义剧本编号从 101 起（避开官方 1–50 与 Widow's Walk 51–100）

### Step 1 — 读取参考资料 / Load references

按需读取以下参考文件（路径相对本文件所在目录；不要凭记忆编造规则或组件）：

| 文件 | 内容 |
|---|---|
| `references/game-rules.md` | 基础游戏规则摘要（回合、属性检定、伤害、怪物、闹鬼触发） |
| `references/components.md` | 组件清单：房间/预兆/道具/角色/标记物 + 狼人篇、圣诞篇内容 |
| `references/haunt-format.md` | 官方两册剧本的逐节格式、触发条件声明、奸徒选择惯例、双语词汇表 |
| `references/design-checklist.md` | 可玩性与平衡设计准则 + 三个校验员的完整提示词 |
| `templates/haunt-template.md` | 分语言文件模板 |
| `examples/haunt-101-silent-night/` | 一个完整的合格示例（分语言目录结构） |

### Step 2 — 设计核心结构 / Design the core (写入 design-notes 草稿)

先写设计骨架，再写正文。骨架必须回答：

1. **触发绑定 Trigger integration**：声明的每个触发维度如何进入剧本——
   - 触发**预兆**必须是故事的起因或核心道具（如 Bite → 诅咒感染源；Girl → 被争夺的对象），并在机制中出场（被携带、被争夺、被消耗……）；
   - 触发**房间**必须成为有意义的地点（怪物出生点、仪式地点、任务链节点、逃生口……），并写"该房间"而非硬编码房间名，使任意触发房间都成立；若机制需要固定房间，写兜底；
   - 触发**角色**（如声明）必须获得定制内容（专属开场叙事、特殊能力/弱点、奸徒选择规则中点名）；
   - 未声明的维度不得在剧本中产生硬依赖。
2. **双方目标**：英雄赢 = ？奸徒赢 = ？两者必须**互斥**且**至少有一方必然在有限回合内达成**（通常靠 Turn/Damage Track 计时轨道兜底，防止僵局）。
3. **信息不对称**：两册各自隐瞒什么？（官方惯例：双方都知道对方"在做什么"，但不知道具体数值/位置/步骤细节。）
4. **奸徒是谁**：用官方惯例句式（Haunt revealer / 最高·最低某属性 except HR / 角色爱好 / HR 左侧 / None at first）。
5. **节奏钟**：什么机制迫使游戏在 ~10 回合内收束？
6. **任务链**：英雄方通常是 2–4 步任务链（找→做检定→搬运→终结一击）；奸徒方通常是怪物压制 + 自己的进度条。
7. **怪物属性**：参考官方量级（Speed 2–6, Might 2–8, Sanity 2–6；BOSS 级单体可到 8）。
8. **道具/标记物**：列出用到的 token（官方用三角 Roll token、五边形 pentagonal token、圆形怪物 token 等）与卡牌。

### Step 3 — 撰写两册剧本 / Write both books

使用 `templates/haunt-template.md`，按官方节次写作，**先写奸徒册再写英雄册**（奸徒册机制最重，英雄册需与之严格互补）；先完成英文基准版，再产出中文对等版：

- 两册的开场叙事描写同一事件的两种视角（官方手法）。
- 英雄册的 "What You Know About the Bad Guys" 必须与奸徒册实际目标一致但不泄露细节；反之亦然。
- 所有检定写明 `属性 roll of N+`；所有放置写明具体房间或放置规则（如"同层至少 5 格远"）。
- 中文版不是逐句直译：叙事可润色为流畅中文，但**规则句的数值、房间名、判定条件必须与英文版完全一致**。
- 输出文件（仓库根目录下，中英分离）：
  - `haunts/haunt-<编号>-<slug>/en/secrets-of-survival.md`（英雄剧本·英文）
  - `haunts/haunt-<编号>-<slug>/en/traitors-tome.md`（奸徒剧本·英文）
  - `haunts/haunt-<编号>-<slug>/zh/secrets-of-survival.md`（英雄剧本·中文《生存秘要》）
  - `haunts/haunt-<编号>-<slug>/zh/traitors-tome.md`（奸徒剧本·中文《奸徒之书》）
  - `haunts/haunt-<编号>-<slug>/design-notes.md`（设计骨架 + 触发绑定说明 + 平衡说明 + 校验记录）

### Step 4 — Subagent 三路校验 / Three-way validation (REQUIRED)

文件落盘后，用所在工具的并行子代理机制（见本文件顶部说明）**并行**启动三个校验员。
每个校验员的完整提示词模板在 `references/design-checklist.md` 的 "Validator Protocol" 一节，必须包含：

1. **英雄剧本校验员 Hero validator** — 读英雄册中英两个文件 + 规则/组件参考：规则合法性、任务链可完成性、指令无歧义、**中英文件规则对等**。
2. **奸徒剧本校验员 Traitor validator** — 读奸徒册中英两个文件 + 规则/组件参考：同上，外加怪物数值量级检查。
3. **胜利条件交叉校验员 Win-condition validator** — 读两册（英文基准版）+ design-notes：双方胜利条件互斥、无僵局（有限回合内必有一方获胜）、信息不对称无穿帮（两册对同一事实的描述不矛盾）、**触发绑定落实**（声明的预兆/房间/角色确实在机制与叙事中扮演实质角色，未声明维度无硬依赖）、粗略平衡估计（双方胜率应在 35%–65% 区间内）。

每个校验员必须返回结构化结论：`VERDICT: PASS` 或 `VERDICT: FAIL + 编号问题清单（每条注明文件与小节）`。

### Step 5 — 修订循环 / Revision loop

- 任一校验员 FAIL：修复所有列出的问题，**仅对失败维度重新派发校验员**，最多迭代 2 轮。
- 2 轮后仍有遗留问题：照常交付，但在 design-notes.md 和最终回复中如实列出未解决项。

### Step 6 — 交付 / Deliver

按用户选择的语言**只呈现一种语言的剧本**（另一语言文件已落盘，提示其路径即可；用户要求 both 时才双语并出）。
最终回复必须包含：剧本编号与标题、**触发条件（预兆/房间/角色）及其在剧本中的绑定方式**、奸徒是谁、双方一句话胜利条件、三个校验员的结论摘要、全部输出文件路径。
