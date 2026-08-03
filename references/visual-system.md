# Visual System — 设计原则 / Design Principles

构成主义视觉哲学与纪律：**为什么**这样设计。Tokens 与组件规格在 `style-guide.md`；完整实现范例在六篇例文（`references/example-*.html`，含英文旗舰 `example-kmp.en.html`）。

Constructivist visual philosophy and discipline — the **why**. Tokens and component specs live in `style-guide.md`; full implementations in the seven example pages (`references/example-*.html`, including the English flagship `example-kmp.en.html`).

> **规则制 / Rule-driven**：视觉动作由**语义规则**驱动，不做次数配额。语义动作标注发生在计划阶段（SKILL.md → Step 4），交付前按 SKILL.md 质检清单第 13 条核验「标注与实现一致」。全系统唯一的密度配额条款是「连续深色 ≤60%/屏」（结构性约束，见色彩层 L0）；板面居中对称留白是构图层面的结构性默认（见构图系统 → 对称默认规则），同样不是次数配额。
>
> Visual actions are driven by semantic rules, not quotas. Annotation happens at planning (SKILL.md Step 4); verified at delivery (checklist #13). The only density quota in the system is "continuous dark ≤60% per viewport" (structural constraint, L0 row); centered symmetric whitespace is a structural default, not a quota.

## Philosophy — 三原则（Meta-rules）

- **构造可见（Construction is visible）**：页面的网格、轴线、标尺、对版标记全部外露。读者看到的是「这页是被构造出来的」，而不是「这页被装饰过」。 The grid, axis, rulers and registration marks are exposed — readers see a page that was constructed, not decorated.
- **色彩即职能（Color is function）**：每种颜色是一个工程职能层的材料。层序固定，永不错位。 Every color is the material of one engineering role. Layer order is fixed, never swapped.
- **几何即仪器（Geometry is instrumentation）**：几何元素不做造型，做测量、指示、传动——标尺、轴线、仪表、楔子、图版框。每件仪器必须能回答「它测量什么」，答不上来就删（Art = encoded meaning 的延伸）。 Geometry measures, indicates, transmits. Every instrument must answer "what does it measure" — otherwise delete it.

参照系：**图版、工程图纸、展览展板、苏联统计图形**——不是海报。教程内容（机制图解、位格式、推演走查、读数）天生就是图版内容；内容与形式同构。 Frame of reference: plates, engineering drawings, exhibition boards, Soviet statistical graphics — not posters.

## Color System — 色层模型（Layer Model）

颜色不是可选语义清单，而是**固定层序的工程色版**，像印刷色版一样有固定叠印顺序。 Colors form a fixed-order engineering palette, like printing plates.

| 层 | 材料 | 职能 | 承载内容 | 层规则 |
|---|---|---|---|---|
| **L0** | paper `#f1ece2`（+ 材料档 olive `#cfd6c0`） | 空气 / 图底 Air / ground | 页面底色、呼吸带、正文、陈述类容器底 | 唯一图底。**连续深色（L1+L2+L3）≤60%/屏**——呼吸带是结构性约束，不是审美配额；olive 是 L0 材料档（橄榄纸 / 描图纸，构成主义次色），不新增语义层、不计入 60% 规则。 Only ground. Continuous dark (L1+L2+L3) ≤60%/viewport — breathing is structural, not aesthetic. olive is an L0 material grade (vellum), no new semantic layer, excluded from the 60% rule. |
| **L1** | ink `#1c1c1c` + steel `#637880` | 结构 Structure | ink = 主结构（边框、正文、标题带、判词、代码、图版框）；steel = 次结构（标尺刻度、图注、辅助线、caption） | ink 骨架必须连续，连成天际线而非墨点；steel 永不成面（**仅两处结构面例外：G6 内层 / G7 机制级**——钢灰面板，面上文字一律 paper 粗体，red / deep-red 禁落 steel 面；结构面计入深色 60% 规则），只做线与字级注释。 ink skeleton must be continuous — a skyline, not ink dots. steel never forms surfaces (two structural exceptions: G6 inner / G7 mechanism level — paper bold text only, reds forbidden on steel). |
| **L2** | blue `#0f4c81` | 图纸 Blueprint | 机制图解、仪表、坐标、位格式 | 只承载**可测量的内容**。L2 上禁用 ochre 与 steel（注释用 blue-note `#9db8cc`）；可加 4–6% paper 坐标网格。 Measurable content only. ochre and steel forbidden on L2 (annotations use blue-note); optional 4–6% paper grid. |
| **L3** | ochre `#b8863b` | 档案 Archive | 史料、引文、旁注 | 面积永远小于 L0；**不与 L2 相邻**（必须由 L0 隔开）；永不做文字色。 Always smaller than L0; never adjacent to L2 (separated by L0); never used as text color. |
| **L4** | white `#ffffff` | 纸卡 Card | sidebar、页面级浮起 UI、punch card 孔位 | **作用域仅三处**（sidebar / 浮起 UI / punch 孔位）。任何内容容器禁白底——内容表面：机制类 → L2 图纸底；代码类 → ink 材料面（L1）；陈述类 → L0 或 L0 材料档橄榄纸 `--olive`（仅靠边框 / 硬阴影成型）；档案类 → L3 ochre 带（steel 结构面例外见 L1 行）。 Scoped to three places only. Content surfaces: mechanism → L2; code → ink material face; statement → L0 or olive; archive → L3 band. |
| **L5** | red `#e63946` + deep-red `#cc2a26` | 红系：事件与焦点 Red: events & focus | red = **动态事件**（压力点、主动路径、进度条、关键格）；deep-red = **静态焦点**（判词词眼、关键数字、check 编号、结果格） | **双红都不成层**：只以线、点、小块、字级出现，永不成面。red 是电流，deep-red 是铆钉——一个流动，一个钉住。**红面阈值（数值源）**：纯红连通区域 **<24×24 忽略**；**≥24×24 且 <64×64 = 小块，允许**；**≥64×64（4096px²）= 面，违规**（sidebar 进度条、active/hover 等 L4 UI 交互态豁免）；每屏红系总像素 ≤1% 视口（1600×1000 屏 ≈ ≤16000px²）。**红圆唯一例外**：实心红圆直径 ≤128px、语义必须为压力/转折性结论（Rodchenko 红日）。 Neither red ever forms a layer — lines, dots, small blocks, word-level only. red is current, deep-red is a rivet. Red-surface thresholds (authoritative): <24×24 ignored; ≥24×24 & <64×64 small block allowed; ≥64×64 is a violating surface (UI interaction states exempt); total red ≤1% viewport. Sole exception: solid red circle ≤128px for pressure/turning-point conclusions. |

### 叠加矩阵（Who May Sit On Whom）

```text
red       → 可落在 L0 / L1 / L2 / L4（仅 UI 交互态：sidebar active、hover、按钮）——永远在最顶层，最薄
deep-red  → 词眼与锚点落在 L0 / L4；蓝底上的焦点改用 red（deep-red 对蓝底对比度不足）
steel     → 落在 L0 / L4 做注释；禁落 L2（改用 blue-note）；禁落 L3（改用 ink）
blue-note → 只落在 L2
ochre     → 只落在 L0（且不与 L2 相邻）；红系禁落 L3
white     → 只落在 L0（sidebar / 浮起 UI / punch card 孔位）
olive     → 只落在 L0（L0 材料档，等同图底——承接陈述类容器底）
amber     → 只落在 .code（ink 材料面上的语法色，作用域例外）
```

### 双红分工（Two Reds）

- **red = 动词 / verb**：有方向、有动作的地方——主动路径、压力点、进度、失败格、事件级红圆。red 出现时，页面在「发生」什么。
- **deep-red = 名词 / noun**：被钉住的重点——判词词眼、关键数字、check 编号、结果格、pc-key 字段。deep-red 出现时，这里「就是」重点。
- 二者同屏不互替：进度条用 red（它在生长）；词眼用 deep-red（它不流动）。相邻红系元素之间用 L0/L1 隔开。

### 双家族（Two Families）

- **印刷族 Print**：paper / ink / red / deep-red / ochre——正文、判词、档案。
- **图纸族 Blueprint**：blue / blue-note / paper / red——机制图解、位格式、推演。
- olive 是 L0 材料档、amber 是代码作用域例外——均不属两族；两族交界必须由 L0 隔开。

### 禁令（Prohibitions）

- red 小字禁置 L2（≈2.1:1）；L2 上的 red 仅限 ≥2px 线与 ≥sm 粗体标签；蓝底上的焦点改用 red。
- ochre 永不做文字色；渐变、辉光、柔化阴影禁（hard shadow 例外）。
- **非必要注释色**：steel 对 paper ≈3.9:1、ochre 对 paper ≈2.7:1，低于 WCAG AA 正文阈值（4.5:1）——只用于图注、刻度、标签、档案条等**非必要注释**，禁止承担必要正文信息。
- **steel 禁落 L3**（≈1.3:1 不可读）；落 L3 的注释一律改用 ink（≈5.3:1 达标）。steel 合法域 = 「L0 / L4 上的线级与字级注释」（结构面例外见 L1 行）。
- **L3 与 L2 禁相邻堆叠**——「相邻」= 包围盒间距 < gap-md（32px）；L3 不得进入 L2 容器内部。**禁止「同屏共现即判违规」**。
- **白卡作用域**：`--white` 仅限三处——sidebar、浮起 UI（按钮 hover、G8 拼贴浮动平面）、punch card 孔位；内容表面四类（机制 L2 / 代码 ink / 陈述 L0 或 olive / 档案 L3；steel 结构面例外见 L1 行）。禁白底容器全量清单见 style-guide → 白卡作用域。
- **红面阈值**：数值定义见 L5 行（数值源）；处置动作见 style-guide → 红面阈值。
- **深色间距表（数值源）**：任意两个深色填充（ink / blue / ochre / **steel 结构面**，面积 >900px²）——同层间距 ≥12px，跨层间距 ≥gap-md（32px）；**图版内衬** ≥ gap-md。深色贴边的判定是间距表，不是「接触视口边缘即违规」。
- 红系禁落 L3。
- **60% 规则操作化**：审查时取 3–4 个滚动位置，目测 L1+L2+L3 联合面积 ≤60% 视口；处置：判词改回 L0 或撤装裱。

### 剖面线语法（Hatching）

多角色图的**第二身份通道**——当图解需要区分 4–5 个同时出现的角色而色相不够时，用剖面线，不加新颜色。 A second identity channel for multi-role diagrams (4–5 simultaneous roles) when hues run out.

- `repeating-linear-gradient(110deg, …)`，条纹与轴线平行；period 8–12px；仅 ink/paper/red 单色系。
- 剖面线 = 材料/角色身份。非明显时必须带图例。 Hatching = material/role identity; legend required when not obvious.
- 例：负半区、共享区、未映射区、失效区。

## Axis — 轴线系统

- **全页唯一倾角 20°（自水平线量取，即与垂直成 70°）**；唯一方向：斜边自右上角向左下方（`/` 家族）。 Single 20° slant page-wide, one direction: upper-right to lower-left.
- 参与轴线的元素：楔形切角、标题带切角、kicker 切角、三角指针、对角分隔线、剖面线。全部平行于同一斜率。
- **实现**：切角深度与组件设计高度成比例（≈0.36 = tan20°），各级深度数值与 `clip-path` 逼近方法见 style-guide → Tokens → 轴线实现（数值源）。**斜切只发生在组件底部呼吸区（padding 区），禁止切入文本区**。
- **作用域**：轴线属于页面构造层，**永不进入机制图解内部**（图解内部保持正交）。
- **G1 切角豁免**：G1 是「棱角」不是「对角线动作」，固定小切角 20–24px，不参与轴线判定。
- **戳记例外**：斜置戳记（档案签）rotate(-4deg)——文字基线可读性下限，不参与轴线判定。
- 正文文字绝不斜置。轴线是「引力方向」：动势统一由此而来。 The axis is a gravity direction — all slants share it; body text is never slanted.

## Geometry — 几何仪器库（The Instruments）

矩形是构造的基本单元，圆与对角线是它的升级——构成主义 = 矩形 + 圆 + 对角线，问题是矩形是否有组织。答案：轴线、标尺、图版构成坐标系，让矩形有组织。 Rectangles are the base unit; circles and diagonals are upgrades. The axis, ruler and plates form the coordinate system that organizes rectangles.

### core（每页默认在线，没有选择余地）

| 仪器 | 形态 | 教程职能 |
|---|---|---|
| **页缘标尺 Edge ruler** | 3rem 左轨：每节锚点处静态刻度线（tick + num 编号 + 英文短词）。**无竖线、无滚动进度条**（进度条仅存在于 sidebar 底部） | 测量阅读位置；**编号单一权威** |
| **图版框 Plate** | 三级装裱：全装裱（2px ink 框 + 对版十字 + 图号 + 图题）/ 轻装裱（无框，仅对版十字 + 图号）/ 不装裱（流式） | 机制图解装裱为独立图版；**图版必须被正文引用或图题传达结论** |
| **对版十字 Registration marks** | 图版四角小直角（6–8px ink 线） | 声明「这是一块图版」 |
| **轴线 Axis** | 全页唯一倾角（20°，见上） | 对角线从「出现几次」的问题变成「属于哪个坐标系」的问题 |
| **天际线密度 Skyline density** | 每节标 `breather / standard / dense`（Step 4 标注） | breather：padding gap-lg、组件稀疏、giant-num 可用、判词巨大；dense：组件紧凑、图纸连片。dense ≠ 深色 |
| **双轨宽度 Dual rails** | 文字轨 ≈68 字符偏左；图版轨占主栏可用宽 | 文字窄、图版宽——不把文字拉宽，让展件展开 |
| **版权条 Colophon** | 页脚 mono xs：版式 / 字体 / 色版（ink·red·blue·ochre）/ 图版数 | 印刷版权条，与页头色票首尾呼应（页面使用 olive / amber 时在色版中追加） |

### extended（语义命中才用，必须通过「它测量什么」审查）

| 仪器 | 形态 | 教程职能 |
|---|---|---|
| **爆炸框 Exploded frame** | 组件沿轴线方向逐级错位分解（静态，无动画） | 机制分解为「零件陈列」：协议报文字段、位格式、栈帧、进位接力 |
| **三角指针 Triangle pointer** | 实心**斜三角**（非等边，斜边与轴线同系，`clip-path` 右角切） | 方向与起点：序列起点、仪表指针尖、消息箭头、图解指示点。**禁用对称正三角**。静止指示三态随表面：red = 事件方向、ink = L0 静止、paper = L2 静止 |
| **仪表盘 Gauge** | 圆弧 + 刻度 + 指针（SVG，径向） | 阈值型读数：负载因子、水位、利用率、开销。线性读数用 readout / ratio bar |
| **红圆 Red circle** | G3 扩展：圆框双态——普通焦点 = ink 圆框；**事件级焦点（同时是压力/转折结论）= red 圆框**（Rodchenko 红日） | 红圆 = 焦点声明 + 事件发生。**红系唯一例外条款**：直径与语义见 L5 行与 style-guide → 红面阈值。同屏不出现两个等重焦点 |
| **巨字判词 Giant verdict** | `clamp(1.75rem, 4.2vw, 3.2rem)` 整幅判词，无编号无组件 | 一页一次；机制段的结论句；≤2 行；必须被回顾段 checklist 引用 |
| **剖面线 Hatching** | 见色层模型 | 材料/角色身份 |
| **仪器带 Instrument strip** | 一组测量件横排成「仪表台」，共用一条基线与一条 steel 基线尺 | 机制节或权衡节的「控制面板」 |
| **错位双栏 Staggered** | 两栏并行但不同步（第二栏整体下移 gap-md） | 主从/先后；≤768px 塌单栏 |
| **图版横列 Plate row** | 2–3 块同主题小图版横向并置（可错位，独立图号 图 3a/3b） | 三个读数、两段对照图解；窄屏塌纵列 |
| **左轨出血 Rail-hang** | 图版左缘挂进标尺轨 1.5rem | 图版被标尺「测量」 |

### 容器词汇（G1–G8）

切角 G1 / 楔形 G2 / 圆形 G3 / 偏移 G4 / 色场 G5 / 嵌套 G6 / 阶梯 G7 / 重叠 G8——内容容器词汇（规格见 style-guide → Geometric Specs）。**机制图解内部永远保持规整精确，非矩形容器不替代图解**。 Non-rectangular containers never replace diagrams inside mechanism figures.

### 形式有效性（Form Validity）

机制组件的形态选择是**规则驱动**的管线，不是数量目标。 Form selection is rule-driven, not a numbers game.

- **规则 A：退化形式禁令**——当机制组件退化为**同构格阵**时（大量单元仅靠矩形与颜色区分，编码不了移动 / 方向 / 转移 / 连接关系），该形态已经失效，必须重选既有形态。审查辅助阈值：>16 个同构单元仅靠颜色区分即可判定退化——阈值只是审查触发线，不是使用配额。**正面例（免疫条款）**：punch card 的列位置 = 位号，位置本身携带语义——格阵数量大但位置承载信息时不触发退化判定。 A form that degrades into a homogeneous grid (>16 units by color only) is failed — reselect. punch card is immune: column position carries the bit-weight semantics.
- **规则 B：Step 5 形态理由**——每个机制组件写一行「认知类型 → 形态 → 该形态编码了什么语义操作」，质检 #13-9 逐条核验：理由站不住即打回重选形态——不是删组件，是打回形态。
- 语义没命中的页面允许全部矩形——`none` 标注本身就是合规状态；多样性是语义匹配的自然结果，不是目标。 All-rectangle pages are legal when semantics miss — diversity is a result, not a goal.

## Composition — 构图系统

### 板面（Exhibition Board）

页面是一块**展板**；板面默认**居中、左右对称留白**。双轨宽度制：

- 文字轨：正文段落 ≈68 字符，偏左对齐——可读性不动。
- 图版轨：图版、仪器带、图版横列、巨字判词占满**主栏可用宽**——展件横向展开到主栏右缘。
- 带 sidebar：`.board { max-width: 1240px; margin: 0 auto; }`；不带 sidebar：主栏 `max-width: 980px` 居中；≤768px 全部塌单栏。
- **对称默认规则**：板面与组件排布默认对称；非对称（偏左板面、右侧留白、左轨出血、非对称网格、错位双栏）仅在能论证「带来了语义增益」时使用，论证不了就回到对称。 Symmetry is the default; asymmetry must argue semantic gain.
- 留白是气质：两侧对称留白 + 组件间距构成呼吸；展件展开不等于塞满。

### 页面骨架（Page Skeleton）

```text
crop marks（四角）──────────────
│ tick──┬────────────────────┐
│  04   │ [section-tag]      │
│ MECH. │ ████ 斜切标题带 ▀▀▀▀ │
│       │ 正文段落（文字轨）    │
│       │ ┌─图 2─────────┐    │
│       │ │✛ 图纸层 L2 ✛ │    │
│       │ │  机制图解      │    │
│       │ └──────────────┘    │
│       │ 图 2：进位接力…      │
│       │ ▓▓▓ 判词（楔形）▀▀   │
│ tick──┴────────────────────┘
版权条（版式 / 字体 / 色版 / 图版数）
```

要点：**图版只装裱图解与判词，正文段落保持流式**——教程的可读性不受图版化影响；图版是内容里的「展件」。 Plates mount diagrams and verdicts only; prose stays fluid.

### 天际线节奏（Skyline Rhythm）

- 节密度三档（breather / standard / dense，Step 4 标注）。
- 巨字判词（extended）：长页中点的整幅判词，一页一次。
- 呼吸带规则：连续深色（L1+L2+L3）≤60%/屏——dense 节也必须满足。

### 横向构成（Horizontal Composition）

竖向堆叠是默认；以下横向形态由语义驱动：**非对称网格**、错位双栏、图版横列、仪器带、左轨出血。纪律：**对称是默认态**；非对称只用于主从/权重/强调语义。横向元素共享基线（仪器带）或共享轴线（错位方向与 20° 平行），不允许各自为政的漂移。

- **非对称网格 asym**：主内容 2/3 + 辅助内容 1/3，**窄栏永远在右**。语义：主从 / 权重差异；等价内容用 split；≤768px 塌单栏。与错位双栏的区别：asym 是宽度比主从，staggered 是垂直错位主从。

### 装裱与版权（Mounting & Colophon）

- 整页四角 crop marks（≥1100px 显示；不选整页外框——整页外框本身就是个新矩形）。
- colophon 为**印刷版权条**：mono xs 横排「版式 / 字体 / 色版（ink·red·blue·ochre）/ 图版数」，与页头色票首尾呼应（页面实际使用 olive / amber 时在色版中追加列明）。

## 教学类型 × 系统映射（Teaching Type × System Mapping）

| 教程段落 | 语义 | 构造表达 |
|---|---|---|
| 原始问题 | 压力 | red 事件 + 楔形（沿轴线指向） |
| 本质 | 焦点 | 圆规几何 + deep-red 词眼 + breather 密度 |
| 演进 | 档案 | L3 ochre 条带 + timetable（不进图版） |
| 机制 | 图纸 | L2 图版框（坐标网格 + 对版十字 + 图号）+ dense 密度 |
| 误解 | 纠错 | 楔形 + dialogue |
| 定义 | 精确 | L3 档案面板（archival panel）+ 档案签 |
| 权衡 | 冷静 | steel accent + 统计条/仪器带 |
| 系统影响 | 高点 | 拼贴平面 或 巨字判词 + breather 密度 |
| 回顾 | 索引 | checklist（克制，零动作；**引用巨字判词**） |

## Composition Recipes（构图食谱）

页面级骨架配方——按主题类型选择整页的节序列与密度曲线。配方全部由「教学类型 × 系统映射」与仪器库条款推出，不新增组件。 Page-level skeleton recipes derived from the mapping table; they add no new components.

### R1 红楔食谱（机制驱动型 / Mechanism-driven）

- 适用：单一机制的因果讲解；页面重心 = 机制节一块主图版。
- 配方（节序 × 密度 × 关键件）：
  1. **原始问题**（standard）：red 事件 + 楔形（G2，沿轴线指向）——压力开场；
  2. **本质**（breather）：essence-hook + deep-red 词眼；
  3. **机制**（dense）：L2 主图版全装裱（图解 / trace / punch card）+ blueprint callout；机制→权衡转折点放巨字判词；
  4. **权衡**（standard）：steel accent + 统计条 / 仪器带；
  5. **回顾**：checklist（引用巨字判词，锚点闭环）。
- 规则：楔形只给全页最强冲突点；主图版必须被正文引用；red 只落压力点与主动路径。
- 形态理由：机制因果 → 红楔 →「压力（楔）→ 图纸（版）→ 冷静（steel）」的情绪曲线与因果链同构。

### R2 蓝图食谱（机制深潜型 / Deep-dive）

- 适用：多层次子系统深潜；页面重心 = 图版集群。
- 配方：
  1. **本质**（breather）：essence-hook——深潜前先立心智模型；
  2. **机制 ×N 节**（dense）：图版连片（memory map / nested tree / exploded frame 全装裱 + 坐标网格），blueprint callout 局部放大；
  3. **推演**（dense）：trace / stepper 真实数据走查；
  4. **权衡**（standard）：仪器带（gauge + readout 共用基线）；
  5. **回顾**：checklist。
- 规则：dense ≠ 深色——60% 呼吸带始终有效；同主题小图版用 plate-row 并置；图纸族主导的页面不让 ochre 进机制节。
- 形态理由：机制深潜 → 蓝图 → 图版集群即展墙，读者沿标尺逐图推进。

### R3 档案食谱（史料演进型 / History-driven）

- 适用：演进/历史驱动；页面重心 = 档案条带 + 时间轴。
- 配方：
  1. **演进**（standard）：L3 ochre 条带 + timetable（不进图版）+ archive card；
  2. **原始问题**（standard）：red 事件——历史压力点；
  3. **机制**（dense）：L2 图版（当代机制仍是图纸）；
  4. **系统影响**（breather）：拼贴平面（G8，结论从证据浮现）；
  5. **回顾**：checklist。
- 规则：ochre 不与 L2 相邻（≥gap-md）、面积 ≤ 所在 section 一半、永不做文字色；史实经 Research Mandate 核查，不虚构日期；戳记 rotate(-4deg) 仅档案签可用。
- 形态理由：史料演进 → 档案 → ochre 档案层与「历史」语义同构。

### R4 海报食谱（短判词型 / Short-verdict）

- 适用：短页、单结论主题；海报式页头的天然搭档。
- 配方：
  1. **页头**：海报式（色票条 + clamp 标题 + em 词眼红下划线）；
  2. **本质**（breather）：essence-hook + 圆规焦点（G3）；
  3. **机制**（standard）：单块全装裱主图；
  4. **判词**：巨字判词（机制结论句，≤2 行）；
  5. **回顾**：checklist（引用判词闭环）。
- 规则：breather 为主调、组件稀疏；短页无导航需求时不加 sidebar / 标尺；页头标准式 / 海报式二选一。
- 形态理由：单点结论 → 海报 → 巨字与留白即构图。

## Diagram Rules

机制图解通则：直线直角、矩形节点、显式连接点、硬边框、简洁对齐标签；red 只用于主动路径/压力点/关键转折；SVG 为一等公民（stroke ink 3–4px 结构 / red 6–7px 主动路径 / 辅助线 1–2px——L2 图纸底用 blue-note，L0 底用 steel，steel 禁落 L2）；禁渐变、滤镜、装饰圆角；`role="img"` + `aria-label`；`<figcaption>` 一句话说清机制结论。**轴线不进入图解内部**；图解内多角色身份用剖面线或 blue-note 区分，不加新色相。

Mechanism figures: straight lines/right angles, rectangular nodes, explicit connection points, hard borders, aligned labels; red only for active paths/pressure points/key turns; SVG is first-class (ink 3–4px structure / red 6–7px active path / 1–2px guides — blue-note on L2, steel on L0, steel never on L2); no gradients, filters, decorative radii; `role="img"` + `aria-label`; caption states the mechanism conclusion in one sentence. The axis never enters a figure; multi-role identity via hatching or blue-note, never new hues.

## Typography Discipline

- 标题：weight 600，letter-spacing -0.02em，line-height 1.05–1.1。
- 正文：1rem / 1.7，行长 65–75 字符（文字轨约束）。
- mono 标签：0.75rem，letter-spacing +0.1em，英文 uppercase。
- 字重纪律：正文与标签 400–600；300 仅大字号展示；600 仅展示巨字；同屏不超过 3 种字重。
- 尺度对比是构图：4–6rem 巨型数字 ↔ 0.75rem mono 标签并置。 Scale contrast is composition: 4–6rem giant numerals against 0.75rem mono labels.
