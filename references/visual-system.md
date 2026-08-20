# Visual System — 设计原则 / Design Principles

Constructivist visual philosophy and discipline — the **why**. Tokens and component specs live in `style-guide.md`; full implementations in the seven example pages (`references/example-*.html`, including the English flagship `example-kmp.en.html`).

> Visual actions are driven by semantic rules, not quotas. Annotation happens at planning (SKILL.md Step 4); verified at delivery (checklist #11). The only density quota in the system is "continuous dark ≤60% per viewport" (structural constraint, L0 row); centered symmetric whitespace is a structural default, not a quota.

## Philosophy — 三原则（Meta-rules）

- **构造可见（Construction is visible）**：The grid, axis, rulers and registration marks are exposed — readers see a page that was constructed, not decorated.
- **色彩即职能（Color is function）**： Every color is the material of one engineering role. Layer order is fixed, never swapped.
- **几何即仪器（Geometry is instrumentation）**：Geometry measures, indicates, transmits. Every instrument must answer "what does it measure" — otherwise delete it.

Frame of reference: plates, engineering drawings, exhibition boards, Soviet statistical graphics — not posters.

## Visual Grammar — 开放式视觉语法

视觉语法是"生成逻辑"的入口：在选择任何颜色、组件或布局前，先确定内容关系，再从候选空间中选择。它**约束冲突、提供候选，不建立唯一映射**。

### 生成顺序

```text
内容关系 → 教学动作 → 颜色状态 → 组件能力与组合 → 构图、装裱、密度与阅读节奏 → 可读性和语义一致性复核
```

### 语义标注（创作起点）

在选择任何颜色、组件或布局前，先为每个章节、图解或转场写一行标注。它不是模板，也不是交付给读者的内容；它是生成页面的内部设计说明。

```text
[教学动作] [信息关系] [叙事状态] [强度] [证据属性] [阅读角色]
```

| 字段 | 可选含义（可扩展） | 它影响什么 |
|---|---|---|
| 教学动作 | 提问、建立直觉、拆解、推演、比较、纠错、定义、回顾 | 组件候选集与章节顺序 |
| 信息关系 | 包含、时序、状态转移、位置编码、比例、因果、阈值、证据—结论 | 组件的主语义与图解形态 |
| 叙事状态 | 解释、测量、归档、事件、焦点、交互 | 色层和文字/注释颜色 |
| 强度 | 背景、支撑、重点、高潮 | 宽度、装裱、密度、是否使用色场/判词 |
| 证据属性 | 原理、真实数据、历史来源、规范定义、代码 | L0/L2/L3 与引用要求 |
| 阅读角色 | 开场、转场、主图、副图、旁证、回顾 | 页面位置、与前后组件的衔接 |

标注示例：

```text
手工推演 / 多变量状态变化 / 测量 / 重点 / 真实数据 / 主图
  → L2 蓝图为主；trace、stepper、swimlane 均是合法候选。
     选择哪一个取决于想突出"全局比较、单步聚焦、角色交接"中的哪一项。

历史演进 / 时间序列 / 归档 / 支撑 / 可信来源 / 转场
  → L3 档案材料；timetable、archive card、档案色场均是合法候选。
     其后若进入机制，使用 L0 留白完成材料转场。

结论抽取 / 证据—结论关系 / 焦点 / 高潮 / 综合判断 / 章节高点
  → giant verdict 与 G8 collage 都可用；二者在同一高点互斥，避免重复强调。
```

### 开放式选择原则

1. **不建立"一种内容只能使用一个组件"的硬映射。** 选择系统提供候选空间、差异与冲突约束，不把创作降为模板填空。
2. **不以组件数量衡量质量。** 丰富性来自有意义的组合、层次、转场和变体，而非机械覆盖组件。
3. **同一信息关系至少有两个可说明差异的候选形式；选择理由来自"强调什么"，不是"哪一个唯一正确"。**
4. **唯一保留的数量/面积门槛只用于可读性、视觉层次和技术稳定性**（如红面阈值、连续深色比例、固定轨格阵和移动端可用宽度）。

### 四个入口

以下四节是视觉语法的四个入口，分别对应生成顺序中的四个决策点：

- **颜色叙事状态**（本文件 → Color System → 颜色叙事状态）：颜色是内容此刻处于什么状态，不是组件专属皮肤。
- **组合关系**（本文件 → Combination Grammar）：组件可以如何搭配——协同、替代、冲突。
- **页面角色**（本文件 → Composition → 页面角色）：布局由页面叙事角色产生，而非由组件堆叠产生。
- **组件能力卡**（`style-guide.md` → 各组件 Specs）：每个组件的主语义、次语义、替代候选、兼容衔接、冲突互斥、变体轴。

## Color System — 色层模型（Layer Model）

Colors form a fixed-order engineering palette, like printing plates.

| 层 | 材料 | 职能 | 承载内容 | 层规则 |
|---|---|---|---|---|
| **L0** | paper `#f1ece2`（+ 材料档 olive `#cfd6c0`） | 空气 / 图底 Air / ground | 页面底色、呼吸带、正文、陈述类容器底 | Continuous dark (L1+L2+L3) ≤60%/viewport — breathing is structural, not aesthetic. olive is an L0 material grade (vellum), no new semantic layer, excluded from the 60% rule. |
| **L1** | ink `#1c1c1c` + steel `#637880` | 结构 Structure | ink = 主结构（边框、正文、标题带、判词、代码、图版框）；steel = 次结构（标尺刻度、图注、辅助线、caption） |  ink skeleton must be continuous — a skyline, not ink dots. steel never forms surfaces (two structural exceptions: G6 inner / G7 mechanism level — paper bold text only, reds forbidden on steel). |
| **L2** | blue `#0f4c81` | 图纸 Blueprint | 机制图解、仪表、坐标、位格式 | 只承载**可测量的内容**。L2 上禁用 ochre 与 steel（注释用 blue-note `#9db8cc`）；可加 4–6% paper 坐标网格。 |
| **L3** | ochre `#b8863b` | 档案 Archive | 史料、引文、旁注 | Always smaller than L0; never adjacent to L2 (separated by L0); never used as text color. |
| **L4** | white `#ffffff` | 纸卡 Card | sidebar、页面级浮起 UI、punch card 孔位 | Scoped to three places only. Content surfaces: mechanism → L2; code → ink material face; statement → L0 or olive; archive → L3 band. |
| **L5** | red `#e63946` + deep-red `#cc2a26` | 红系：事件与焦点 Red: events & focus | red = **动态事件**（压力点、主动路径、进度条、关键格）；deep-red = **静态焦点**（判词词眼、关键数字、check 编号、结果格） |Neither red ever forms a layer — lines, dots, small blocks, word-level only. red is current, deep-red is a rivet. Red-surface thresholds (authoritative): <24×24 ignored; ≥24×24 & <64×64 small block allowed; ≥64×64 is a violating surface (UI interaction states exempt); total red ≤1% viewport. Sole exception: solid red circle ≤128px for pressure/turning-point conclusions. |

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

 A second identity channel for multi-role diagrams (4–5 simultaneous roles) when hues run out.

- 实现：`repeating-linear-gradient` 斜纹，条纹与轴线平行，仅 ink/paper/red 单色系（周期与梯度参数见 style-guide → Hatching）。
- Hatching = material/role identity; legend required when not obvious.
- 例：负半区、共享区、未映射区、失效区。

### 颜色叙事状态（Color as Narrative State）

颜色继续是功能系统，而不是装饰色板。L0–L5 的技术规则不变；此处的视角转换是：在生成流程中，先问"内容此刻处于什么叙事状态"，再确定使用哪个色层。

| 材料层 | 叙事状态 | 典型任务 | 设计结果 |
|---|---|---|---|
| L0 paper / olive | 解释、消化、呼吸、陈述 | 正文、心智模型、权衡、回顾 | 流式阅读、留白和承接 |
| L1 ink / steel | 结构、边界、尺度、索引 | 标题、骨架、图版框、标注 | 形成可追踪的版面骨架 |
| L2 blue | 被测量、推演、验证 | 数据、机制、状态、位置、代码运行逻辑 | 图纸式精确与可操作感 |
| L3 ochre | 被记录、引用、定义、回溯 | 时间、史料、引文、约定 | 档案感与证据层 |
| L4 white | 浮起的页面级界面 | sidebar、互动控件、拼贴浮层、孔位 | 仅作为层级例外，而非内容卡片 |
| L5 red / deep-red | 正在发生 / 被钉住的重点 | 压力、主动路径、关键数字、判词词眼 | 事件轨迹与焦点锚定 |

颜色规则分为两类：

- **不可协商的语义/可读性约束**：L2 禁 steel 注释、L3 与 L2 的间隔、白卡作用域、红面阈值、必要文字的对比度。这些规则的技术数值不变（见禁令节）。
- **开放的构图策略**：是否使用 olive、图纸占比、图版大小、色场位置、red 事件在页面中的具体轨迹——由内容和强度决定，不做固定配额。

**材料转场**：L0（解释）→ L2（推演）→ L3（归档）→ L5（事件）之间的流动应当可由章节语义解释。图纸与档案不发生无意义碰撞——L2 与 L3 之间必须有 L0 间隔（≥gap-md）。red 在页面中形成事件/焦点的可追踪路径，不会成为大面积装饰。

## Axis — 轴线系统

- **全页唯一倾角 20°（自水平线量取，即与垂直成 70°）**；唯一方向：斜边自右上角向左下方（`/` 家族）。
- 参与轴线的元素：楔形切角、标题带切角、kicker 切角、三角指针、对角分隔线、剖面线。全部平行于同一斜率。
- **实现**：切角深度与组件设计高度成比例（≈0.36 = tan20°），各级深度数值与 `clip-path` 逼近方法见 style-guide → Tokens → 轴线实现（数值源）。**斜切只发生在组件底部呼吸区（padding 区），禁止切入文本区**。
- **作用域**：轴线属于页面构造层，**永不进入机制图解内部**（图解内部保持正交）。
- **G1 切角豁免**：G1 是「棱角」不是「对角线动作」，固定小切角 20–24px，不参与轴线判定。
- **戳记例外**：斜置戳记（档案签）rotate(-4deg)——文字基线可读性下限，不参与轴线判定。
- The axis is a gravity direction — all slants share it; body text is never slanted.

## Geometry — 几何仪器库（The Instruments）

Rectangles are the base unit; circles and diagonals are upgrades. The axis, ruler and plates form the coordinate system that organizes rectangles.

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
| **巨字判词 Giant verdict** | 整幅判词（流式巨字，字号数值见 style-guide → Giant Verdict），无编号无组件 | 一页一次；机制段的结论句；≤2 行；必须被回顾段 checklist 引用 |
| **剖面线 Hatching** | 见色层模型 | 材料/角色身份 |
| **仪器带 Instrument strip** | 一组测量件横排成「仪表台」，共用一条基线与一条 steel 基线尺 | 机制节或权衡节的「控制面板」 |
| **错位双栏 Staggered** | 两栏并行但不同步（第二栏整体下移 gap-md） | 主从/先后；≤768px 塌单栏 |
| **图版横列 Plate row** | 2–3 块同主题小图版横向并置（可错位，独立图号 图 3a/3b） | 三个读数、两段对照图解；窄屏塌纵列 |
| **左轨出血 Rail-hang** | 图版左缘挂进标尺轨 1.5rem | 图版被标尺「测量」 |

### 容器词汇（G1–G8）

切角 G1 / 楔形 G2 / 圆形 G3 / 偏移 G4 / 色场 G5 / 嵌套 G6 / 阶梯 G7 / 重叠 G8——内容容器词汇（规格见 style-guide → Geometric Specs）。**机制图解内部永远保持规整精确，非矩形容器不替代图解**。

### 形式有效性（Form Validity）

机制组件的形态选择是**规则驱动**的管线，不是数量目标。

- **规则 A：退化形式禁令**——当机制组件退化为**同构格阵**时（大量单元仅靠矩形与颜色区分，编码不了移动 / 方向 / 转移 / 连接关系），该形态已经失效，必须重选既有形态。审查辅助阈值：>16 个同构单元仅靠颜色区分即可判定退化——阈值只是审查触发线，不是使用配额。**正面例（免疫条款）**：punch card 的列位置 = 位号，位置本身携带语义——格阵数量大但位置承载信息时不触发退化判定。
- **规则 B：Step 5 形态理由**——每个机制组件写一行「认知类型 → 形态 → 该形态编码了什么语义操作」，质检 #11-4 逐条核验：理由站不住即打回重选形态——不是删组件，是打回形态。
- 语义没命中的页面允许全部矩形——`none` 标注本身就是合规状态；多样性是语义匹配的自然结果，不是目标。

## Combination Grammar — 组合关系

### 术语表（能力卡与组合语法共用，单一权威）

| 术语 | 定义 |
|---|---|
| **主语义** | 组件最擅长编码的信息关系——它是该组件存在的首要理由。 |
| **次语义** | 组件还可以强调的次要信息关系——扩展用途，但不替代主语义。 |
| **适用条件** | 什么信息特征使该组件特别有效——何时选它比选替代项更自然。 |
| **替代候选** | 同一信息关系可以用哪些其他组件表达，突出不同侧面。 |
| **兼容衔接** | 该组件常在哪些组件之前或之后出现，形成自然的前后关系。 |
| **冲突 / 互斥** | 何时两个组件争夺同一视觉或叙事角色，不应同屏出现。 |
| **变体轴** | 材料、装裱、宽度、密度、位置、互动性等可变化维度。 |
| **页面角色** | 组件在页面叙事结构中承担的功能：定位 / 定锚 / 展示 / 拆解 / 对照 / 转场 / 高潮 / 闭环。 |
| **协同组合** | 不同组件分别补充不同认知任务的前后序列。 |
| **替代组合** | 表达同一主关系但突出不同侧面的候选集。 |
| **冲突组合** | 两个形式争夺同一叙事角色或违反材料语义的搭配。 |
| **构图先例** | 已验证的整页骨架配方（R1–R4），可被变体化，不是强制模板。 |

组件之间的搭配关系分为三种。组合规则不设"每页最多 N 个组件"之类的数量配额；唯一保留的数量/面积门槛只用于可读性和技术稳定性。

### 协同组合（Synergistic）

不同组件分别补充不同认知任务，形成前后序列。每个组件承担不同的教学动作，互不争夺同一叙事角色。

```text
hook → trace → insight panel → checklist
  直觉 → 推演 → 解释 → 回顾
```

其他协同例：
- `essence hook → causal chain → gauge → giant verdict`：心智模型 → 因果序列 → 阈值读数 → 结论
- `archive card → L0 留白 → memory map → blueprint callout`：史料 → 材料转场 → 地址布局 → 局部放大
- `dialogue → trace → warning box`：误解纠正 → 手工推演 → 陷阱标注

### 替代组合（Alternative）

表达同一主关系但突出不同侧面。选择哪一个取决于"想强调什么"。

| 信息关系 | 候选组件 | 各自强调的侧面 |
|---|---|---|
| 多变量状态变化 | trace / stepper / swimlane | 全局并置比较 / 单步聚焦 / 角色交接 |
| 时间序列 | timetable / archive card / L3 色场 | 精确时序 / 史实引文 / 段落级档案归属 |
| 层级包含 | nested tree / G6 nested panel / G7 stair | 完整树形图解 / 语境×内容面板 / 递进构建 |
| 结论抽取 | giant verdict / G8 collage / readout | 整幅判词 / 证据浮现 / 数值权重 |
| 零件分解 | exploded frame / punch card / ASCII | 沿轴线逐级陈列 / 位置×二值状态 / 等宽字符排布 |
| 比例分布 | ratio bar / readout / instrument strip | 分段比例 / 大数字权重 / 仪表台横排 |

### 冲突组合（Conflict）

两个形式争夺同一叙事角色，或违反材料语义。以下搭配在同一页面中应避免：

| 冲突 | 原因 |
|---|---|
| giant verdict + G8 collage 同页 | 两种高潮形态争夺"系统影响"高点——二选一 |
| L3 档案与 L2 图纸无 L0 间隔 | 材料语义碰撞（色层禁令） |
| 多个楔形同时宣称"最强冲突" | 楔形只承担全页最强转折——多了就均匀了 |
| trace + stepper 同时展示同一推演 | 全表并置与单步递进争夺同一"手工推演"角色——选一个 |
| archive card + archival panel 表达同一定义 | 前者证明"发生过"，后者声明"应当如此"——定义用 archival panel |
| exploded frame + punch card 同时拆解同一位格式 | 整卡读值用 punch card，拆零件用 exploded frame——不混用 |
| 多个 red circle 同屏 | 同屏不出现两个等重焦点互抢 |
| 巨字判词 + 楔形块承载同一结论 | 判词用 giant verdict，≤2 行强冲突用楔形——不叠加 |

### 组合与页面角色

组合关系关注"组件之间如何搭配"，页面角色关注"组件在页面叙事中承担什么功能"。一个协同组合中的每个组件应分别承担不同的页面角色（见 Composition → 页面角色）。如果两个组件承担同一角色，即进入冲突组合的判定范围。

## Composition — 构图系统

### 板面（Exhibition Board）

页面是一块**展板**；板面默认**居中、左右对称留白**。双轨宽度制：

- 文字轨：正文段落 ≈68 字符，偏左对齐——可读性不动。
- 图版轨：图版、仪器带、图版横列、巨字判词占满**主栏可用宽**——展件横向展开到主栏右缘。
- 带 sidebar：板面限宽居中（`--board-max`）；不带 sidebar：主栏限宽居中（`--main-max`）；≤768px 全部塌单栏（数值见 style-guide → Tokens）。
- **对称默认规则**：板面与组件排布默认对称；非对称（偏左板面、右侧留白、左轨出血、非对称网格、错位双栏）仅在能论证「带来了语义增益」时使用，论证不了就回到对称。
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
│       │ 巨字判词（L0 整幅文字） │
│ tick──┴────────────────────┘
版权条（版式 / 字体 / 色版 / 图版数）
```

要点：**图版只装裱机制图解，正文段落与判词保持流式**——教程的可读性不受图版化影响；图版是内容里的「展件」。

> **骨架注记（先例而非模板）**：上图是 R1 红楔先例的典型机制节形态示意，不是逐节通用模板；节的实际组成由 Step 4 语义标注决定。图中要素各有频度条款：斜切标题带一页最多一节、巨字判词一页一次（L0 整幅文字，无编号无组件）、楔形属 problem 节且只给全页最强冲突点——不把任一要素当作每节必配项。

### 天际线节奏（Skyline Rhythm）

- 节密度三档（breather / standard / dense，Step 4 标注）。
- 巨字判词（extended）：长页中点的整幅判词，一页一次。
- 呼吸带规则：连续深色（L1+L2+L3）≤60%/屏——dense 节也必须满足。

### 横向构成（Horizontal Composition）

竖向堆叠是默认；以下横向形态由语义驱动：**非对称网格**、错位双栏、图版横列、仪器带、左轨出血。纪律：**对称是默认态**；非对称只用于主从/权重/强调语义。横向元素共享基线（仪器带）或共享轴线（错位方向与 20° 平行），不允许各自为政的漂移。

- **非对称网格 asym**：主内容 2/3 + 辅助内容 1/3，**窄栏永远在右**。语义：主从 / 权重差异；等价内容用 split；≤768px 塌单栏。与错位双栏的区别：asym 是宽度比主从，staggered 是垂直错位主从。

### 装裱与版权（Mounting & Colophon）

- 整页四角 crop marks（≥1100px 显示；不选整页外框——整页外框本身就是个新矩形）。
- colophon：内容结构与色版呼应规则见 Geometry core → 版权条行；实现（含多文件按单文件标准报告）见 style-guide → Colophon。

### 页面角色（Page Roles）

每一页的组件应分别承担不同的页面角色。同一角色可由多种组件承担；同一组件也可以承担不同角色。优化的是"角色是否缺失或重复争夺"，不是限制每页能使用哪些组件。

| 页面角色 | 作用 | 可由哪些形式承担 |
|---|---|---|
| 定位 | 告诉读者当前讨论的范围和压力 | page header、problem section、wedge block、archive card |
| 定锚 | 建立可反复返回的心智模型 | essence hook、circle callout、readout、G1 |
| 展示 | 让机制可见、可测量、可推演 | 任意机制图解、plate、蓝图容器 |
| 拆解 | 将整体拆成关系或部件 | exploded frame、nested tree、G6、punch card |
| 对照 | 让差异和取舍可见 | split、dialogue、compare table、staggered、ratio bar |
| 转场 | 改变材料、速度或论证视角 | L0 留白、archive card / timetable、color field、inset panel |
| 高潮 | 固定结论或让结论从证据中出现 | giant verdict、G8 collage、readout、red circle |
| 闭环 | 回到知识清单和页面承诺 | checklist、fig-ref、verdict anchor、colophon |

**角色缺失与重复争夺**：审查时检查每页是否缺少某个角色（如"有机制但无定锚"→ 补 essence hook；"有高潮但无闭环"→ 补 checklist 引用判词）。同时检查是否有两个组件争夺同一角色（如"两个高潮"→ 巨字判词与 G8 二选一）。

## Composition Precedents — 构图先例（R1–R4）

页面级骨架配方——按主题类型选择整页的节序列与密度曲线。配方全部由色层模型（颜色叙事状态）、仪器库条款与组件能力卡推出，不新增组件。

> **先例而非模板**：以下 R1–R4 是已验证的构图先例，可被变体化和跨配方组合。它们不是唯一流程——主题的内容关系决定节序和密度曲线，配方提供的是"已验证有效的骨架"，不是"必须遵循的模板"。变体化的方式包括：调整节序（如把本质放在问题之前）、替换组件（如用 stepper 替代 trace）、合并或拆分节、跨配方借鉴某一段密度曲线。任何变体必须能论证语义增益。

### R1 红楔先例（机制驱动型 / Mechanism-driven）

- 适用：单一机制的因果讲解；页面重心 = 机制节一块主图版。
- 配方（节序 × 密度 × 关键件）：
  1. **原始问题**（standard）：red 事件 + 楔形（G2，沿轴线指向）——压力开场；
  2. **本质**（breather）：essence-hook + deep-red 词眼；
  3. **机制**（dense）：L2 主图版全装裱（图解 / trace / punch card）+ blueprint callout；机制→权衡转折点放巨字判词；
  4. **权衡**（standard）：steel accent + 统计条 / 仪器带；
  5. **回顾**：checklist（引用巨字判词，锚点闭环）。
- 规则：楔形只给全页最强冲突点；主图版必须被正文引用；red 只落压力点与主动路径。
- 形态理由：机制因果 → 红楔 →「压力（楔）→ 图纸（版）→ 冷静（steel）」的情绪曲线与因果链同构。

### R2 蓝图先例（机制深潜型 / Deep-dive）

- 适用：多层次子系统深潜；页面重心 = 图版集群。
- 配方：
  1. **本质**（breather）：essence-hook——深潜前先立心智模型；
  2. **机制 ×N 节**（dense）：图版连片（memory map / nested tree / exploded frame 全装裱 + 坐标网格），blueprint callout 局部放大；
  3. **推演**（dense）：trace / stepper 真实数据走查；
  4. **权衡**（standard）：仪器带（gauge + readout 共用基线）；
  5. **回顾**：checklist。
- 规则：dense ≠ 深色——60% 呼吸带始终有效；同主题小图版用 plate-row 并置；图纸族主导的页面不让 ochre 进机制节。
- 形态理由：机制深潜 → 蓝图 → 图版集群即展墙，读者沿标尺逐图推进。

### R3 档案先例（史料演进型 / History-driven）

- 适用：演进/历史驱动；页面重心 = 档案条带 + 时间轴。
- 配方：
  1. **演进**（standard）：L3 ochre 条带 + timetable（不进图版）+ archive card；
  2. **原始问题**（standard）：red 事件——历史压力点；
  3. **机制**（dense）：L2 图版（当代机制仍是图纸）；
  4. **系统影响**（breather）：拼贴平面（G8，结论从证据浮现）；
  5. **回顾**：checklist。
- 规则：ochre 不与 L2 相邻（≥gap-md）、面积 ≤ 所在 section 一半、永不做文字色；史实经 Research Mandate 核查，不虚构日期；戳记 rotate(-4deg) 仅档案签可用。
- 形态理由：史料演进 → 档案 → ochre 档案层与「历史」语义同构。

### R4 海报先例（短判词型 / Short-verdict）

- 适用：短页、单结论主题；海报式页头的天然搭档。
- 配方：
  1. **页头**：海报式（色票条 + clamp 标题 + em 词眼红下划线）；
  2. **本质**（breather）：essence-hook + 圆规焦点（G3）；
  3. **机制**（standard）：单块全装裱主图；
  4. **判词**：巨字判词（机制结论句，≤2 行）；
  5. **回顾**：checklist（引用判词闭环）。
- 规则：breather 为主调、组件稀疏；短页无导航需求时不加 sidebar / 标尺；页头标准式 / 海报式二选一。
- 形态理由：单点结论 → 海报 → 巨字与留白即构图。
