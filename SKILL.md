---
name: noesis-tutorial
description: Use when the user asks for technical tutorials, concept explanations, learning notes, or exam-point study material, to be delivered as HTML learning pages.
---

# noesis-tutorial

## Purpose

Create complete, runnable HTML learning notes for technical topics. The page should help learners understand why a concept exists, what engineering pressure shaped it, how it works, what tradeoffs it introduces, and how it connects to broader system design patterns. Output is Chinese-first and follows the specific art style unless the user specifies otherwise. If the content is too enormous for a single file, break it into multiple files divided by subtopics. Each file should be self-contained and navigable.

The result should feel like a designed engineering knowledge product, not a textbook dump, Markdown-to-HTML conversion, or generic summary.

## When NOT to Use（何时不用）

- 用户只要简短口头解释或一问一答，不需要交付页面 → 直接回答，不套用本技能。
- 用户明确要求 Markdown / 纯文本 / 幻灯片等其他格式 → 不套用本技能。
- 主题过于单薄（单句事实、术语速查）→ 不值得完整页面结构。
- 用户显式要求轻量快速输出（「简单点」「粗略讲讲」）→ 除非确认仍要 HTML 页面，否则不套用装裱 / 密度 / 轴线体系；唯一降级通道是 Step 1 的 Cheatsheet 模式（轻装裱、全 dense、无判词），不是「随便做做」。
- 非教学类任务（编码、调试、评审、数据分析）→ 本技能不适用。

## How to Use References

- `references/visual-system.md` — design philosophy: 三原则（构造可见/色彩即职能/几何即仪器）、色层模型 L0–L5 + 叠加矩阵、轴线系统（20°）、几何仪器库（core/extended）、构图系统（双轨/图版制/天际线）、教学类型映射. **Read this first**.
- `references/style-guide.md` — design methodology + CSS tokens + component specs: Layout Specs（板面/标尺/图版三级装裱/横向构成）、Geometric Specs（G1–G8 + 轴线公式）、Instrument Specs（爆炸框/仪表盘/三角指针/剖面线/巨字判词）. **Write your own CSS based on the rules and adjust it to fit the specific needs of the context**. **Read this second**.
- `references/example-twos-complement.html` — 补码：图版制、punch card（plate-row 三码对照）、trace、blueprint callout 的完整装配；印刷族主导。
- `references/example-virtual-memory.html` — 虚拟内存：memory map、nested tree、exploded frame、gauge、rail-hang、剖面线的图纸族装配。
- `references/example-tcp.html` — TCP 三次握手：swimlane、state diagram（plate.light）、ascii、dialogue、split。
- `references/example-kmp.html` — KMP（完整 408 考点）：archival panel、stepper/step-through、causal chain、ratio bar、warning box、code block（黑底语法色）、真题演练。
- `references/example-maxwell-equations.html` — 麦克斯韦方程组：海报式页头、timetable、archive card、G5 色场、G7 stair、G8 拼贴、asym。
- `references/example-photoelectric-effect.html` — 光电效应实验：G1 切角、G3 红圆、gauge（红限）、dialogue、staggered、insight panel、split。
- `references/example-coverage.md` — 组件 × 例文覆盖矩阵（六篇合覆盖全部 core + extended 组件；落新组件前先查此矩阵）。

## Rules Source（规则来源）

所有规则以 `references/` 为唯一源：执行前**通读** `references/visual-system.md`（为什么——色层 / 轴线 / 几何语义）与 `references/style-guide.md`（怎么实现——tokens / 组件规格 / 处置动作）全文；执行中不确定处回查对应章节。数值规则以标注「数值源」处为准。

## Research Mandate

**Before writing, verify factual accuracy.** Technical tutorials lose credibility on a single wrong detail.

Verify:

- **Mechanism**: how the concept actually works — official documentation, specifications, authoritative sources. Do not infer internal behavior from surface API.
- **History**: real historical context, not fabricated narratives. If unsure when or why, state the pressure without inventing dates or names.
- **Code examples**: syntactically correct and runnable. Do not mix APIs from incompatible versions.
- **Tradeoffs**: real, not plausible-sounding inventions. If debatable, present as design tension rather than settled fact.

Bad: "Git was created because SVN required a constant internet connection."
Good: "Git is a distributed version control system — every clone is a full repository, enabling offline commits and branching without a central server."

If a topic is too broad to research thoroughly, narrow the scope rather than guessing and explain the rationale.

## Creation Workflow

### Step 0: Research & Inventory

Verify mechanism, history, constraints (Research Mandate). Also create a **knowledge checklist (topic inventory)**: the points this topic must cover. The page structure must address every item on the checklist, or explicitly declare omissions — the "Key Takeaways" at the end must map back to each item on the checklist.

**User-provided material**: When the user provides lecture notes, textbooks, or study material, treat them as the scope boundary and checklist source; the verification obligation is not waived — errors in the material must be corrected against authoritative sources and noted on the page.

### Step 1: Determine Context

- **Exams** (408 postgraduate entrance, campus recruiting interviews) → activate Exam-Point Teaching.
- **Engineering understanding** → use Teaching Architecture as the primary mode.
- **Cheatsheet** (user explicitly requests) → density-first: one-sentence Essence Hook, skip evolution / system-impact, use data tables, checklists, and compact code blocks as the main body; each item still needs one sentence of causal explanation — dense but not shallow. Cheatsheet = **轻装裱模式**：装裱降为 light 级、无巨字判词、无 breather、密度一律 dense、无横向构成；标尺保留。

### Step 2: Extract the Causal Chain

In 3–5 sentences: 1) What was broken before? 2) What engineering pressure forced the design? 3) What did the old approach get wrong? 4) How does the new design work? 5) What was gained, what was sacrificed? Write it down before touching any HTML.

### Step 3: Design the Essence Hook

One-two sentences, the simplest useful mental model. See Essence Hook section.

### Step 4: Plan Structure & Coverage

Decide which sections this topic genuinely needs. Not every page needs every section from the Suggested Page Structure. Force a section only when it improves understanding.

Geometry is the mapping result of these annotations (visual-system → Geometry 几何仪器库), never reverse-justified after rendering.

### Step 5: Design Diagrams & Geometry

For each spatial concept choose the diagram type (memory map / timeline / state transition / trace / inline SVG). Choose container geometry (G1–G8), instruments, and layout patterns according to Step 4's annotations — the number of focal points is determined by content semantics, and every focal point must be able to answer "why is the information it focuses on the most important here."

Then write a one-line **form rationale**（形态理由）for each mechanism component: cognitive type → form → what semantic operation the form encodes（如「指针移动 → SVG 双轨图 → 编码了主串指针的移动与回退」）. A form that degrades into a homogeneous grid array (>16 units distinguished only by color, encoding only arrangement, not movement/direction/transfer/connection) is a failed form — reselect from the existing forms (退化形式禁令, see visual-system → 形式有效性).

Then run the **mounting decision**（装裱判定）: mechanism-class components (diagram / trace / swimlane / punch card / exploded frame) default to full plate mounting (`figure.plate.full` + 图号 + 图题); archive / dialogue / checklist components stay fluid. **Every mounted plate must be cross-referenced from the prose（见图 N）or its caption must state the mechanism conclusion.**

### Step 6: Generate HTML

Build the page. For long documents, use the Large Document Strategy below.

## Large Document Strategy

Build in phases — generating a full-length technical document in one pass inevitably results in truncation and degraded quality.

1. **Scaffold**: `<!DOCTYPE html>` + `<head>` (Font System CDN) + CSS tokens + all section containers with headings + sidebar (if needed) + ruler rail + crop marks + colophon.
2. **Fill sections**: One section at a time: causal explanation → diagram (mounted as plate if mechanism-class) → code (explain why the implementation works this way) → run each paragraph through Signal Density check.
3. **Review**: Does the causal chain flow seamlessly across sections? Do diagrams tie back to the hook? Does the rhythm vary (dense text → diagram → verdict → summary)? Are cross-references (`见图 N`), figure numbers, and sidebar anchors correct? Is the knowledge checklist fully covered? Run the 13-item Quality Checklist.

## Output Contract

- 每份交付为独立 HTML 文件，以 `<!DOCTYPE html>` 开头（内容过长时按子主题拆分多文件，每份自包含、可导航）；inline CSS；inline JS 仅在交互真正促进理解时使用。
- 文件名：小写 kebab-case 英文主题名（`twos-complement.html`、`kmp-algorithm.html`）；`<title>` 用中文主题名。
- Chinese-first explanations; semantic HTML; responsive（768px 单断点）。
- 唯一外部依赖：Google Fonts CDN（见 Font System）。
- 必有 Page Header（kicker + 标题 + metadata；标准式或海报式二选一，规格见 style-guide → Page Header（二选一））。
- 构造件必有：标尺轨（≥1100px 静态刻度，含编号，<1100px 由 `.sec-num` 承接编号；**无竖线、无滚动进度条**，进度条仅 sidebar 底部）、四角 crop marks、印刷版权条（版式 / 字体 / 色版 / 图版数 / 轴线 20°）。
- 图版约定：`<figure class="plate full|light" id="fig-N">` + `<span class="fig-num">图 N</span>` + `<figcaption class="plate-caption">`；正文用 `<a class="fig-ref" href="#fig-N">见图 N</a>` 交叉引用。
- Avoid: Markdown 转 HTML、半成品片段、伪布局、无视觉系统的平铺文章。

## Font System

| Role | Font | Source |
|------|------|--------|
| 中文 | Noto Sans SC | Google Fonts CDN |
| 英文 | IBM Plex Sans | Google Fonts CDN |
| 数字 | Urbanist | Google Fonts CDN |
| 代码 | Google Sans Code | Google Fonts CDN |

CDN `<link>`（放在 `<head>` 中；完整代码见 `references/style-guide.md` → Tokens）：

CSS 变量与完整 tokens 见 `references/style-guide.md` → Tokens。数字场景（序号、位置标记、纯数字单元格）使用 `var(--font-num)`。字重纪律（不设硬性白名单）：正文/标签 400–600；300 仅大字号展示（海报标题、巨型数字）；600 仅展示巨字（Urbanist / Noto Sans SC），不进正文；同屏不超过 3 种字重——CDN 未声明的字重不会生效，字重变更（新增或移除）需同步更新 CDN。

Windows 平台字体容易渲染过粗，必须在 `body` 中加入：

```css
body {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-rendering: optimizeLegibility;
}
```

## Teaching Architecture

Explain concepts as causal chains, not terminology lists. For each major concept, prefer this sequence:

1. **Original problem** — What was broken before? What problem could the old approach not solve?
2. **Engineering pressure** — Cost, scale, latency, security, compatibility, complexity, or hardware constraints.
3. **Failed or limited older solutions** — What did the prior approach get wrong.
4. **Essence hook** — A concise, forceful statement of the design's essence; prefer a physically intuitive model to aid understanding.
5. **Mechanism** — How it works, step by step; **must include a worked example with real data** — pure abstract description is not acceptable.
6. **Tradeoff** — What was gained, what was sacrificed.
7. **Formal definition** — Introduce precise terminology only after intuition is established.
8. **System impact** — What it changed, what it enabled, what it complicated.

Rules:

- Structure emerges from topic — do not force every section onto every page.
- **Analogies must declare their breaking point**: "This model breaks at X, because Y" — the breaking point is itself a teaching point.
- **Coverage**: Cross-check every item on the knowledge checklist; any omission must be declared at the top of the page.
- Definitions make earlier intuition precise — never open with a definition, unless the user explicitly wants reference-style.

## Exam-Point Teaching (考点教学)

面向考试时，每个考点必须**深度教学**，而非简单罗列。在 Step 1 识别到考试场景后激活以下规则。

### 禁止行为

- 只列出考点名称而不解释（如仅写「next 数组求法」并给一个公式）
- 将考点做成无解释的 bullet list
- 用教材原文照搬，不加推导和示例

### 每个考点必须包含

1. **考点定位**：怎么考（选择/大题/填空）、分值权重
2. **机制详解**：逐步讲解实际运作过程，用具体数据走一遍
3. **手工推演**：用真实输入追踪每一步状态变化（不能只给最终结果）
4. **易错陷阱**：学生常犯什么错？为什么？如何避免？
5. **应试技巧**：速算方法、记忆口诀、验算策略
6. **关联考点**：本考点与其他考点如何联动出题

### 示例对比

| 差（罗列式） | 好（教学式） |
|-------------|-------------|
| 「next[1]=0, next[2]=1」直接给结论 | 从「模式串最长公共前后缀」定义出发，逐位置推导 next 数组，每步标注当前前后缀 |
| 「nextval 是 next 的优化」一句话 | 先展示 next 的冗余比较场景，再演示 nextval 如何跳过无效比较 |
| 列出时间复杂度 O(n+m) | 分析暴力匹配为什么 O(nm)，KMP 如何利用 next 数组避免回溯主串，推导到 O(n+m) |

文末复习清单可以是 bullet list——清单是索引，不是内容；正文必须已完成对每个考点的完整教学。

### 组件映射

| 教学要求 | 形态 |
|---------|------|
| 考点定位 | section tag + 正文首段 |
| 机制详解 | causal chain / memory map / blueprint callout |
| 手工推演 | trace / stepper（真实数据逐步状态） |
| 易错陷阱 | warning box / dialogue |
| 应试技巧 | insight panel / hard shadow |
| 关联考点 | dialogue / compare table |
| 文末考点清单 | checklist（仅作索引） |

## Essence Hook

For complex concepts, place a short essence hook before detailed mechanisms. It should be: 

- One or two sentences.
- Chinese-first.
- Low-jargon.
- Problem-oriented.
- Memorable enough to guide the rest of the explanation.

It should answer:

```text
What is the simplest engineering and fundamental explanation for this concept?
```

Four patterns:

- **Replace definition with physical intuition**: Find a concrete model the reader can directly visualize.
- **Reframe an arbitrary-seeming mechanism as an inevitable consequence**: It is the direct outcome of constraint X — because of Y, Z follows necessarily.
- **Distinguish appearance from essence**: On the surface, it is doing X; at its core, it is Y.
- **Derive the design from its constraints**: What if it weren't done this way? X would fail, because of constraint Y.

Four examples, each demonstrating one pattern:

```text
[Replace definition with physical intuition]
Arrange 256 numbers around a clock face: 0–127 are positive, 128–255 are negative.
Addition is moving clockwise; going far enough to wrap around is subtraction —
starting at 5, advancing 251 steps nearly completes a full revolution and lands
near 0, giving 5 + (-5) = 0. The sign bit merely tells you which half of the
clock you are on.
```

```text
[Reframe an arbitrary-seeming mechanism as an inevitable consequence]
Hash table lookup is O(1), but collisions are not an accident — at a load factor
of 0.7, 23 elements already have a 50% chance of collision (the birthday paradox).
O(1) does not hold by luck; it holds because of the load factor threshold +
chaining or open addressing as a fallback.
```

```text
[Distinguish appearance from essence]
Why does sign-magnitude have two zeros? Because the sign bit is a separate label
— 00000000 is +0, 10000000 is -0, same value but different bit patterns.
Two's complement has exactly one zero because the sign bit emerges naturally
from modular arithmetic, not from an artificial label — so "two representations
for the same value" never arises.
```

```text
[Derive the design from its constraints]
TCP's three-way handshake is not convention but a mathematical minimum.
With two messages, the server cannot confirm the client received its SYN-ACK
and would allocate resources for a dead connection. Three is the lower bound
for bidirectional confirmation — one fewer is unsafe, one more is redundant.
```

Criterion: after reading the hook, the reader should hold a reliable concrete model. A hook that offers only conclusions without mechanism, or only terminology without intuition, fails. Later diagrams, examples, and terminology should refer back to this hook.

## Signal Density Rule

Every paragraph should introduce at least one of: engineering constraint / tradeoff / failure mode / system behavior / design consequence / causal relationship / mental model.

Avoid paragraphs that merely restate previous ideas. Remove prose that sounds insightful but does not add new operational understanding.

## Writing Standards

**Prefer**: causal reasoning; mental models; state changes over time; implementation pressure; engineering consequences; cross-concept tensions（abstraction↔control、safety↔flexibility、latency↔throughput、simplicity↔scalability、consistency↔availability）。

**Avoid**: definition-first writing; hollow motivation; textbook tone; intuition-free jargon stacking; false profundity; tautology; mechanical Markdown conversion; SaaS card layouts; gradients / glassmorphism / glow / decorative animations.

### Good vs Bad

| Bad (textbook tone) | Good (engineering causality) |
|---|---|
| Opens with a formal definition | Opens with the engineering problem that forced the design |
| Lists features as bullet points | Traces each feature back to an engineering pressure |
| Shows code without explaining why | Shows code and explains why the simpler approach fails |
| Diagrams only label box names | Diagrams reveal mechanism (memory layout, state transitions, data flow) |
| Decorative cards and gradients | Structural color and hard-geometry-encoded meaning |
| Repeats the same insight in different words | Each paragraph adds new operational understanding |
| Vague "best practices" | Specific tradeoffs: what is gained, sacrificed, and why it is worth it |
| Uniform section rhythm | Alternating density: long analysis → short verdict → diagram → summary |
| Explains concepts in isolation | Connects to broader system patterns and cross-cutting tensions |

**Code examples** must explain why the implementation exists, what problem it solves, why simpler alternatives fail, and how state changes step by step.

## Form Selection

First ask what cognitive type this information is, then choose the form — **tables are only for genuine two-dimensional lookups**; do not default to tables as a container.

| Cognitive type | Form |
|---|---|
| Contrast / debate / misconception correction | dialogue |
| Multi-role / multi-stage process handoff | swimlane |
| Hierarchical containment (address space, scope) | nested tree |
| Evidence / historical fact / quotation | archive card |
| Strict formal definitions / fixed rules | archival panel（档案面板，定义签） |
| Key readings / state / verdict figures | readout |
| Threshold readings (load factor, water level, utilization) | gauge（仪表盘） |
| Precise time series | timetable |
| Close-up annotation of a mechanism diagram | blueprint callout |
| Bit patterns / encodings / instruction formats | punch card |
| Part-level decomposition of a mechanism (fields, stack frames, carry chain) | exploded frame（爆炸框） |
| Proportion / frequency / distribution | ratio bar |
| Genuine two-dimensional comparison (gain × sacrifice, A × B) | tradeoff / compare / data table |

Specifications in `references/style-guide.md` → Form Specs（认知形态）.

## Visual System & Art Direction（色层 + 轴线 + 仪器）

Default is a constructivist technical-editorial style (defer to user preferences when stated). 参照系是**图版 / 工程图纸 / 展板 / 苏联统计图形**，不是海报——技术教程与图版内容天生同构。

Core rules（一句话总纲；规范源见 references）：

| 纪律 | 一句话 | 规范源 |
|---|---|---|
| **色层模型** | 六层固定叠印、层序永不错位：L0 图底 → L1 结构 → L2 图纸（只承载可测量内容）→ L3 档案（不与 L2 相邻）→ L4 白卡（仅 sidebar / 浮起 UI / punch 孔位三处）→ L5 红系（双红不成面）。阈值细节见 visual-system → 色层模型 | visual-system → 色层模型 |
| **轴线纪律** | 全页唯一倾角 20°（自水平线量取），唯一方向；斜切只在组件底部呼吸区，**禁入文本区**、禁入图解内部；正文文字绝不斜置；G1 小切角与戳记（rotate(-4deg)）豁免 | visual-system → Axis |
| **仪器分级** | core 每页在线；extended 语义命中才用，每个必须通过「它测量什么」审查。**多样性是语义匹配的自然结果，不是目标** | visual-system → Geometry |
| **装裱** | 机制类组件默认进图版框（全装裱 + 图号 + 图题）；**图版必须被正文引用（见图 N）或图题传达机制结论**——无人引用的图版是装饰 | style-guide → Plate Specs |
| **几何语义** | 非矩形件（G1–G8）与仪器由 Step 4 语义动作标注选择，无次数配额；同型连续出现 = 形态未编码语义差异；同构格阵（>16 单元仅靠颜色区分）即形态失效，必须重选既有形态 | visual-system → 形式有效性 |
| **硬几何** | `border-radius: 0`（两处例外：punch card 孔位 + G3 圆形标注）；4–16px 非对称边框、直角面板、硬投影无模糊 | style-guide → Geometric Specs |

**视觉禁令（Avoid）**：gradients、glow、soft bubbles、rounded-corner mind maps、noisy animations、card-stack templates、UI copy that explains its own design（写作向禁令见 Writing Standards）。

## Inline Style Policy

Inline `style=""` is only permitted for **one-off micro-adjustments** (non-recurring spacing, font sizes, ratio bar widths, etc.). If the same style appears more than twice, extract it into a CSS class.

## Responsive Design

Single `768px` breakpoint — do not add breakpoints unless the design genuinely breaks at an intermediate width.

At `≤768px`: headings scale down (3xl→2xl, 2xl→xl); giant figures scale down (5rem→3rem); trace cell sizes reduce (2.2rem→1.8rem); multi-column collapses to single column (staggered / plate-row / strip included); sidebar becomes a full-width **vertical** list at the top (never collapse to a horizontal strip); edge ruler collapses (numbering taken over by `.sec-num`); crop marks hidden; wide tables and diagrams scroll horizontally. Standard @media skeleton in style-guide → Responsive Spec.

## Long-Form Reading Support

Alternate dense explanation, diagrams, visual separators, insight blocks, walkthroughs, and concise summaries — rhythmic variation combats reading fatigue. The **天际线节奏**（breather / standard / dense 标注 + 巨字判词）就是该原则的系统化。

Canonical long-form navigation: **left-column sticky table of contents** (click-to-jump + scroll-spy highlighting the active section + red progress bar, specifications in style-guide → Sidebar（canonical 导航）) + **页缘标尺**（定位/编号，specifications in style-guide → Edge Ruler）. Short pages get no navigation — navigation does not exist to fill space.

## Quality Checklist

Verify every item before delivery (13 items):

1. **Causal chain**: Does every major concept walk through problem → pressure → mechanism → tradeoff?
2. **Essence hook**: A mental or physically intuitive model before detailed mechanism, with later diagrams and terminology tying back? Analogies declare their breaking point?
3. **Coverage**: Is the knowledge checklist fully covered or omissions explicitly declared? Does the Key Takeaways map back to every checklist item?
4. **Signal density**: At least one new engineering insight per paragraph? Every mechanism paired with a worked example using real data?
5. **Tradeoffs and boundaries**: Gains and sacrifices stated bidirectionally?
6. **Facts**: Mechanisms, history, and code are verified? Code is syntactically correct and runnable?
7. **Exam depth** (if applicable): Each exam point taught in depth (mechanism + derivation + trap), not merely listed?
8. **Form**: Cognitive type matches form? Tables only for two-dimensional lookups? No table-stuffing?
9. **Language**: No typos or grammar errors? Terminology used accurately?
10. **Navigation**: Long pages have a left-column TOC (full-width vertical on narrow screens)? Anchors correspond one-to-one with section IDs? Edge ruler ticks match section order and numbers?
11. **Technical**: Single file starting with `<!DOCTYPE html>`? Only Google Fonts CDN? Font weights follow the discipline (400–600 for body/labels, 300/600 display-only, ≤3 weights per screen)? Semantic tags? 768px responsive? Inline styles for one-off only? Scroll-progress JS is progressive enhancement (page fully readable without JS)?
12. **Delivery**: Page Header complete (kicker + title + metadata)? Chinese `<title>`? kebab-case filename? Colophon present（版式 / 字体 / 色版 / 图版数）?
13. **Rule-driven review（规则驱动审查，九项核验）**：逐屏核验九项纪律，每项「判定标准 + 违规处置」如下。
    - **13-1 色层**：非 L0 层不直接相邻堆叠；双红只以线/点/小块/字级出现（永不成面）；ochre 只落 L0；图版内无 L4 白卡；与 Step 4 标注一致。ochre-blue「相邻」按包围盒间距判定（< gap-md 32px），**禁「同屏共现即判违规」**。olive（L0 材料档）与 steel 结构面例外（G6 内层 / G7 机制级）不属层序违规——按 visual-system → 色层模型 L0/L1 行核验。
    - **13-2 轴线**：所有斜切件（楔形/标题带/kicker/爆炸框/分隔线/三角指针）与全页轴线同系同向；斜切不切进文本区；机制图解内部无斜线；正文文字不斜置。
    - **13-3 装裱**：机制类组件按 Step 5 判定进图版框；分级合理（主图全装裱/次图轻装裱/小件不装裱）；图版框无多余装饰动作。
    - **13-4 60% 密度**：取 3–4 个滚动位置，目测 L1+L2+L3 联合面积 ≤60% 视口。处置：判词改回 L0 或撤装裱。
    - **13-5 图版引用**：图版须被正文交叉引用（见图 N）或图题传达机制结论；无人引用则删除；巨字判词须被回顾段引用（锚点闭环）。
    - **13-6 红面**：按 style-guide → 红面阈值 定义核验（≥64×64 即面违规、每屏 ≤1% 视口、红圆 ≤128px 唯一例外）。处置：ratio bar 红段改描边或 ≤24px 高；表头禁红底（deep-red 文字 + 红左划线）。
    - **13-7 白卡作用域**：内容区（trace/swimlane/stepper/ascii/code-block/punch-card/inset/essence-hook/dialogue 答案/warning/stair/circle-callout）出现 white 填充即违规；豁免仅三处：sidebar、页面级浮起 UI（含 G8 拼贴浮动平面）、punch 孔位。内容表面按 style-guide → 白卡作用域四类执行：机制 → L2 图纸底 / 代码 → ink 材料面 / 陈述 → L0 或 olive 橄榄纸 / 档案 → L3 ochre 带；steel 结构面例外（G6 内层 / G7 机制级）与 G7 层级色阶（级 3 steel / 级 4 ink）见对应 Specs。禁白底容器全量清单见 style-guide → 白卡作用域。
    - **13-8 深色间距**：按 visual-system → 禁令·深色间距表（数值源）核验——同层 ≥12px、跨层 ≥gap-md（32px）、图版内衬 ≥gap-md。
    - **13-9 形态有效性**：每个机制组件须能回答「这个形态编码了什么语义操作」，按 Step 5 形态理由逐条核验，站不住即打回重选形态（不是删组件）；同构格阵（>16 单元仅靠颜色、编码不了移动/方向/转移/连接）即退化。不查几何种类数量——多样性不是目标，形态与语义的对应才是。
