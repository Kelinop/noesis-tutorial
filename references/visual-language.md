# Visual Language — 构成主义视觉语言 / Constructivist Visual Language

The single visual reference for this skill. It is not a component catalog — it is a **generative grammar**: a small set of invariants, a style canon, and a vocabulary from which you *construct* forms that fit the content. The three example pages (`example-kmp.html`, `example-maxwell-equations.html`, `example-photoelectric-effect.html`) are the living demonstrations; consult them when you need to see a principle embodied.

> 自由来自边界清晰。Invariants（§2）不可协商；其余一切都是默认值、启发与候选——可以偏离，只要能说清偏离带来的语义增益。

## 1. Philosophy — 三原则

- **构造可见（Construction is visible）**：网格、轴线、标尺、对版标记裸露在外——读者看到的是一块被构造出来的展板，不是被装饰的页面。推论：构造元素必须真的可见——一条只藏在 8px 切角里的轴线不算显形（见 §3.1）。
- **色彩即职能（Color is function）**：每种颜色是一个工程角色的材料，角色固定、永不互换。页面没有"装饰色"，只有"这种材料此刻承担什么职能"。
- **几何即仪器（Geometry is instrumentation）**：几何形测量、指示、传递。每个形式必须能回答"它编码了什么"——答不上来就删除（见 §4.3）。

参照系：展板、工程图纸、展览板、苏联统计图形——Rodchenko / Lissitzky 的构成主义材料与蓝图传统的融合。不是海报，不是 SaaS 落地页。

## 2. Invariants — 不可协商项

Only these rules are absolute. Everything else in this document is a default or a candidate.

### 2.1 色层模型（L0–L5，色值与职能固定）

| 层 | 材料 | 职能 | 承载 |
|---|---|---|---|
| **L0** | paper `#f1ece2`（+ 材料档 olive `#cfd6c0`） | 空气 / 图底 | 页面底色、正文、陈述类容器底。olive 是 L0 的描图纸档，不是新色层 |
| **L1** | ink `#1c1c1c` + steel `#637880` | 结构 | ink = 主结构（边框、标题带、判词、代码底）；steel = 次结构（刻度、图注、辅助线、字级注释），永不成面 |
| **L2** | blue `#0f4c81` + blue-note `#9db8cc` | 图纸 | 只承载**可测量的内容**（机制图解、位格式、推演、读数）；注释一律 blue-note |
| **L3** | ochre `#b8863b` | 档案 | 史料、引文、定义、约定；永不做文字色 |
| **L4** | white `#ffffff` | 纸卡 | 仅三处：sidebar、页面级浮起 UI（含 G8 浮动平面）、punch card 孔位 |
| **L5** | red `#e63946` + deep-red `#cc2a26` | 事件与焦点 | red = 动态事件（动词）；deep-red = 静态焦点（名词） |
| 例外 | amber `#e6b04a` | 代码字符串 | 仅代码块作用域内 |

### 2.2 双红分工

red = 动词：方向、动作、正在发生（主动路径、压力点、进度、失败格）。deep-red = 名词：被钉住的重点（判词词眼、关键数字、check 编号、结果格）。二者同屏不互替；相邻红系元素之间用 L0/L1 隔开。

### 2.3 叠加与对比度禁令（可读性底线）

- steel 禁落 L2（注释用 blue-note）与 L3（注释用 ink）；blue-note 只落 L2。
- deep-red 禁落蓝底（蓝底焦点改用 red）；红系禁落 L3。
- ochre 只落 L0，不与 L2 相邻（间距 ≥32px），永不做文字色；ochre 上的文字用 ink（≈5.3:1 达标）。
- steel / ochre 对比度低于 4.5:1——只做图注、刻度、标签等**非必要注释**，禁止承担必要正文。
- white 只出现在 L4 的三处；内容表面四类：机制 → L2，代码 → ink 材料面，陈述 → L0/olive，档案 → L3。

### 2.4 红面阈值

红永不成面：字级、线级（≥2px）、小块（<64×64）合法；≥64×64 的实色红面违规；红色总量 ≤1% 视口。**边界**：线框（描边）与纯线条不是"面"，不受此限——红日（§3.4）、红梁等签名姿态因此合法；唯一实面例外是 ≤128px 的实心红圆（压力/转折结论，Rodchenko 红日）。UI 交互态（hover / active）豁免。

### 2.5 呼吸规则

连续深色（L1+L2+L3 填充面）≤60% 视口——任意滚动位置成立。dense ≠ 深色；留白是结构不是剩余（见 §3.5）。

### 2.6 轴线唯一

全页唯一倾角 20°（自水平量取），唯一方向 `/`（自右上向左下）。所有斜切、楔形、三角指针、剖面线、对角分隔共享同一斜率。切角深度 ≈ 高度 × 0.36（tan20°），且只切入组件底部呼吸区、永不切入文本区。**轴线永不进入机制图解内部**——图解内一律正交；正文文字永不倾斜（display 字的例外见 §3.3）。

### 2.7 材料质感禁令

禁渐变、辉光、柔化阴影（硬投影例外，如 `8px 8px 0 red`）、毛玻璃、圆角容器（`border-radius` 仅两处：圆形焦点、punch 孔位）、`clip-path` 与 border/box-shadow 共存（会被裁切——切角件用剪影成型）。

## 3. Style Canon — 风格正典

The canon is how the invariants become *composition*. These are strong defaults, not gates — deviate when the content argues for it.

### 3.1 轴线三级显形（Axis at Three Scales）

The 20° axis must be *seen*, at three scales:

- **micro（修边）**：kicker、标题带、楔形、三角指针的切角——现状即合法，但它只是标点。
- **meso（构件）**：楔形块、爆炸框错位、阶梯错位、剖面线方向——构件级的轴线表达。
- **macro（页面）**：**对角时刻（Diagonal Moment）**——每页 1–2 次页面级对角构图：海报页头的斜切色块或沿轴排布的标题组、高潮处的全幅对角分隔线、一块压向图版的对角色场。没有 macro 级的页面，轴线等于不存在。

### 3.2 动态平衡（Dynamic Balance, not Symmetry）

构图的合法性判据是**平衡**，不是对称。正文轨保持稳定居中（这是阅读纪律，不是构图律）；展件与页面级元素做砝码式构图，三枚砝码可单独或组合使用：

- **面积砝码**：大对小——主图版对大留白、巨字对小注释。
- **材料砝码**：重对轻——ink 面对 paper 空、色场对呼吸带。
- **方向砝码**：对角对置——楔形指向与留白方向相反、出血与收窄对置。

判据：视线在页面上不停滞、不倒向一边。说不出哪里失衡，就是平衡了；无需再为每一次非对称写论证。

### 3.3 字即材料（Type as Material）

Display 场景（页头标题、巨字判词、巨字编号、节编号）中，字是构图材料：

- 字重开放到 **700**（CDN 链接须同步声明）；拉丁 display 词可全大写、紧凑行高（1.0–1.1）。
- 判词可**齐幅堆叠**：每行独立缩放到同一宽度（Rodchenko 字块）。
- 巨字编号可**出血**：部分溢出板面或图版边缘（Lissitzky 式），用描边或低对比填充保持背景性。
- 正文纪律不变：400–600、行高 1.7、文字轨 ≈68 字符、正文永不倾斜。display 字可沿轴线倾斜——每页至多一处，且必须是页面最强的那个词。

### 3.4 红的三姿态（Three Red Gestures）

红色的合法签名姿态，**同页每种至多一次**，与红面阈值的边界见 §2.4：

- **红日（Red Sun）**：线框红圆，直径可达 ~10rem——事件级焦点声明（压力/转折结论同时成立时）。描边不是面，不受阈值限；实心红圆 ≤128px 的例外同样保留。范式例：example-photoelectric-effect 的 E=hν。
- **红楔（Red Wedge）**：纯几何刺穿动作——一个红色楔形/三角越过容器边界、指向压力点（Lissitzky「红楔刺白圆」）。无文字、不成面（线级或小块）。它指向的内容必须有压力语义。
- **红梁（Red Beam）**：水平事件长条（高 ≤14px，宽 ≤ 板面宽），用作节间的事件分隔或页头定调。它替代了旧体系"禁止页面级线条"的绝对禁令——页面级线条合法的条件：沿轴线，或承担事件语义。

三姿态互斥同屏；与 G8 拼贴、巨字判词共用同一高潮点时，只留一个。

### 3.5 构造性留白（Designed Negative Space）

空白是图底的形状，不是内容的剩余。每屏应有一处**被设计的空白**：有方向的留白（对角通道）、有位置的留白（单边大留白构成面积砝码）、有节奏的留白（dense 节后的 breather）。60% 规则（§2.5）是下限；构造性留白是目标。检查方式：眯眼看页面，空白应当像墨块一样有形状。

### 3.6 图文咬合（Text-Geometry Interlock）

- 标注引线沿轴线方向，不进入图解内部；图版标签可**骑缝压框**（标签块压住图版边框线，Lissitzky 式），不必全部缩在框内。
- 图版必须被正文引用（见图 N / see Fig. N），或图题本身传达机制结论——无人引用的图版是装饰。
- 词眼（deep-red 字级焦点）落在 L0；蓝底上的焦点用 red 字级标签。

### 3.7 生产痕迹签名（Production Signatures）

默认在线的页面签名：四角 crop marks（≥1100px）、页缘标尺刻度（静态 tick + 编号，无竖线、无滚动条）、图版对版十字、页脚 colophon（版式 / 字体 / 色版 / 图版数 / 轴线 20°）。它们是"艺术进入生产"的直接声明，短页可减配（标尺随 sidebar 一起省略），但 colophon 永不省略。

## 4. Generative Grammar — 生成语法

### 4.1 生成顺序

```text
内容关系 → 教学动作 → 语义标注 → 叙事状态（色层）→ 形式构造（词汇表为候选，不自限于词汇表）→ 构图（动态平衡 + 密度节奏）→ 不变量复核
```

### 4.2 语义标注（创作起点）

选择任何颜色、组件或布局之前，为每个章节与图解单元写一行内部标注（不交付给读者）：

```text
[教学动作] [信息关系] [叙事状态] [强度] [证据属性] [阅读角色]
例：手工推演 / 多变量状态变化 / 测量 / 重点 / 真实数据 / 主图
```

叙事状态映射色层：解释 → L0、结构 → L1、被测量/推演 → L2、被记录/定义 → L3、浮起 UI → L4、正在发生/被钉住 → L5。材料转场（L0→L2→L3→L5 的流动）应能被章节语义解释。

### 4.3 形式有效性（Form Validity）

- **编码自查（规则 B）**：每个机制组件写一行 `信息关系 → 形式 → 该形式编码了什么语义操作`（例：指针移动 → 双轨图 → 编码主串指针的前进与不退）。答不上来 → 打回重选形式，不是删组件。
- **退化禁令（规则 A）**：形式退化为同构格阵（>16 个单元仅靠颜色区分，编码不了移动/方向/转移/连接）即失效。**免疫条款**：位置本身携带语义时（punch card 的位号、条带对齐的重叠位置）不算退化。
- 语义没命中的页面允许全部矩形——多样性是语义匹配的自然结果，不是目标。

### 4.4 组合关系

- **协同**：组件承担不同的教学动作与页面角色，形成序列（直觉 → 推演 → 解释 → 回顾）。
- **替代**：同一信息关系至少有两个可说明差异的候选；选择理由是"想强调什么"，不是"哪个唯一正确"。
- **冲突**：两个形式争夺同一叙事角色或同一视觉高点 → 二选一（巨字判词 vs G8、trace vs stepper 展示同一推演、多个等重焦点同屏）。
- **重点唯一性**：每页的强形式各一次——一个巨字判词、一个楔形（给全页最强冲突）、每种红姿态各一、每节最多一个高潮。

## 5. Form Vocabulary — 形式词汇表

Entry points, not a catalog. One line each: what it encodes. Construct new forms freely when none fits — the vocabulary is proof of territory, not its border.

**推演类**：trace（行=时间步 × 列=状态维的全表并置）· stepper（单步递进与当前焦点）· swimlane（角色 × 时序交接）· causal chain（压力传递方向，必须闭合到权衡）
**结构类**：memory map（地址区间 × 归属）· nested tree（层级包含）· exploded frame（零件沿轴陈列）· punch card（位置 × 二值状态）· ASCII 图（等宽位置语义）· state diagram（状态转移与条件）
**对齐类**：双条错位图（两条带的滑动对齐，重叠段即公共结构——prefix/suffix、序列比对）
**读数类**：readout（数值的权重，尺度对比即构图）· gauge（阈值型读数，弧形刻度+阈值刻度+指针）· ratio bar（份额的相对量）· instrument strip（多件共用基线的仪表台）
**陈述类**：essence hook（最小心智模型，定锚）· insight panel（分析性结论）· warning box（单向陷阱警示）· dialogue（立场交锋，正解从交锋浮现）· giant verdict（整幅判词，一页一次）
**档案类**：archive card（证明"发生过"）· archival panel（声明"应当如此"的定义/约定）· timetable（精确时序）
**对照类**：compare table（仅真正的二维查找）· split（等价并置）· asym（主从 2:1）· staggered（错位主从）
**容器几何**：G1 切角（工业精度）· G2 楔（全页最强冲突的力量方向）· G3 圆（焦点声明；红圆=红日）· G5 色场（段落级材料归属，只用 ink/ochre）· G6 嵌套（语境 × 内容）· G7 阶梯（递进构建，≤4 级，级位即进度）· G8 拼贴（结论从证据浮现，与巨字判词二选一）
**闭环**：checklist（索引即闭环，引用判词锚点；清单是索引不是内容）

## 6. Composition — 构图启发

- **板面**：页面是一块展板——文字轨 ≈68 字符偏左（可读性不动），图版轨占主栏可用宽（展件展开）。带 sidebar 时限宽居中；≤768px 全部塌单栏。
- **天际线密度**：节密度三档 breather / standard / dense，形成节奏；dense 节之间用 L0 呼吸带分隔。
- **页面角色**：定位 / 定锚 / 展示 / 拆解 / 对照 / 转场 / 高潮 / 闭环——检查缺失与重复争夺，不限制组件种类。
- **构图先例（启发，不是模板）**：R1 红楔（单机制因果：问题压力 → 本质 → 主图版 → 判词 → 回顾）；R2 蓝图（多机制深潜：本质 → 图版集群 → 推演 → 仪器带）；R3 档案（史料驱动：ochre 时间线 → 压力 → 当代机制 → 拼贴影响）；R4 海报（短页单结论：海报页头 → 本质 → 单主图 → 判词）。

## 7. Defaults — 可偏离的默认值

Deviating is legal; state the gain.

- **字体栈**：Latin IBM Plex Sans · 中文 Noto Sans SC · 数字 Urbanist · 代码 Google Sans Code（Google Fonts CDN，字重 300–700 按需声明，display 700 见 §3.3）。字重纪律：正文 400–600，700 仅 display，同屏 ≤3 种字重。
- **Token 建议值**：`--gap: 0.5/1/2/4rem`；板面 1240px（带 sidebar）/ 980px（不带）；标尺轨 3rem；文字轨 46rem；图版网格 24px。
- **页头**：标准式（kicker + 标题 + 4rem×8px 红梁 + 副题 + meta）或海报式（色票条 + clamp 标题 + 词眼红下划线 + meta）；meta 四字段：日期 · 学科 · 时长 · 范围声明。
- **装裱**：机制图解默认全装裱（2px ink 框 + 对版十字 + 图号 + 图题），陈述/档案类保持流式；装裱图版必须被引用或图题传达结论。
- **响应式**：单 768px 断点——多栏塌单栏、标尺与角标隐藏（编号移交节内前缀）、巨字收小、宽表横向滚动。
- **交互**：仅当交互帮助理解（步进演示、scroll-spy）；渐进增强，无 JS 页面完整可读；禁装饰性动画。
- **工程惯例**：单文件 inline CSS、kebab-case 文件名、`<title>` 用页面语言、 sole external dependency = Google Fonts。

## 8. Traps — 高频陷阱（一句话各）

- `clip-path` 会裁掉 border 与 box-shadow——切角件用剪影，不要加边框。
- 固定轨 grid：行内单元数必须严格等于轨数（多一个少一个都静默错位）——写完数一遍。
- 圆形孔位单元必须 `box-sizing: border-box`，否则孔与环外径不一致、阵列错位。
- 蓝底注释用 blue-note、焦点用 red；deep-red 落蓝底不可读。
- 表格只给二维查找；单维数据用列表/readout，主从用 asym。
- SVG 辅助线随表面换色（L2 上 blue-note，L0 上 steel）；结构线 ink，主动路径 red。
- 深色面之间保持间距（同层 ≥12px，跨层 ≥32px）；图版内衬 ≥32px。

## 9. Examples — 示例索引

- **example-kmp.html** — 考点密集型 / 图纸族主导：真实数据 trace、步进演示、双条错位重叠图、档案面板、红梁与判词。
- **example-maxwell-equations.html** — 海报式 + 档案族：色票页头、ochre 时间线、G7 层级色阶、镜像对置构图、连续谱带、G8 拼贴。
- **example-photoelectric-effect.html** — 短判词型 + 对话：红日（E=hν 线框红圆）、阈值仪表、立场对话、装置图、红楔指针。

三篇覆盖差异最大化的三种页面气质；写新页面前，找气质最近的一篇通读其 CSS 与图版结构。
