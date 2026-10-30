# Visual Language — 构成主义技术编辑视觉语言

Use this single reference to construct the page's visual argument. Do not treat it as a component catalog or a historical reconstruction kit. The examples demonstrate possibilities; they never override the Invariants.

> 自由来自边界清晰。审美对象不是红色、切角与标尺的集合，而是信息、注意力、材料与留白之间的关系。

## 1. Aesthetic Identity — 审美界定

### 1.1 Position

Define the style as **contemporary constructivist technical editorial**: the rhetorical force of constructivist graphics, the precision of technical drawing, the reading discipline of editorial grids, and the explanatory economy of information design.

Borrow methods, not costumes:

| Reference | Borrow | Do not infer |
|---|---|---|
| Rodchenko / Lissitzky / Popova | Organized force, asymmetry, scale contrast, type as structure, economical materials | A mandatory angle, a universal red-black recipe, or historical authenticity |
| Technical drawing / blueprints | Explicit coordinates, traces, registration, measurable relations | Decorative crosshairs around every element |
| Editorial grids / typography | A stable reading rail, hierarchy, cadence, alignment, deliberate rupture | Uniform cards or symmetry as the default |
| ISOTYPE / statistical graphics | Redundant encoding, countable relations, direct comparison, legends | Pictograms without an explained mapping |

A poster composition is welcome when the learning arc needs one. Avoid generic SaaS polish, propaganda pastiche, and ornament whose only justification is “constructivist.”

### 1.2 Three principles

- **构造可见 / Construction is visible** — expose the grid, joints, axes, and transitions that explain how the page is organized. Hide construction that would only add noise.
- **色彩即职能 / Color is function** — assign each material a stable local role. Never ask a hue alone to carry a distinction.
- **几何即仪器 / Geometry is instrumentation** — use geometry to measure, direct, connect, separate, or compare. Preserve the content when a form fails; reselect the form rather than deleting the lesson.

Judge beauty by four outcomes: **recognizable force, lucid hierarchy, apt form, and exact craft**. Visual excitement is not evidence of learning; aesthetic appeal and task performance require separate checks.

## 2. Invariants — 不可协商项

Only this section is visually blocking. The Delivery Contract in `SKILL.md` is separately blocking. Canon and defaults may change for a stated semantic or compositional gain; examples are never rules.

### 2.1 Material roles and palette

| Layer | Material | Function | Typical carriers |
|---|---|---|---|
| **L0** | paper `#f1ece2`; olive `#cfd6c0` | Air / exposition | Page ground, prose, explanatory and tracing-paper surfaces |
| **L1** | ink `#1c1c1c`; steel `#4a5d65` | Structure / secondary reading | Text, rules, frames, code ground; steel only on light surfaces |
| **L2** | blue `#0f4c81`; blue-note `#a8c2d4` | Measurement | Mechanism plates, derivations, readouts; blue-note on blue or ink only |
| **L3** | ochre `#b8863b` | Record | Dated evidence, quotations, definitions, conventions; ink text only |
| **L4** | white `#ffffff` | Lifted layer | Navigation, floating UI, collage planes, punch-card holes; not a general card color |
| **L5** | red `#e63946`; deep-red `#a92520` | Intervention / resolution | red = movement, pressure, active path; deep-red = settled focus, key term, result |
| Scoped | amber `#e6b04a` | Code string | Code blocks only |

Keep these roles stable within a page. Explain any non-obvious mapping with a legend, label, shape, position, or text. Treat “red = verb / deep-red = noun” as a mnemonic, not a universal grammar.

### 2.2 Contrast and redundant encoding

- Meet **4.5:1** for ordinary text and **3:1** for large text. Meet **3:1** for meaningful graphical parts, boundaries, and control states against adjacent colors.
- Use `paper` or `white` for ordinary text on blue; use `blue-note` for secondary text on blue or ink. Use `steel` only on paper or olive. Use `deep-red`, not `red`, for small emphasized text on paper or olive.
- Do not place essential red text or paper text on a red fill on blue. Keep red on blue as a supplementary stroke or marker, paired with a readable label and a non-color cue.
- Do not use `ochre` as text. Do not place `steel`, `blue-note`, or either red on an incompatible surface merely to preserve a component recipe.
- Never encode state, category, success, failure, or focus by color alone. Add text, shape, pattern, position, or line style.

These are perceptual constraints, not exemptions for decorative text. Mark genuinely decorative marks `aria-hidden` and keep them out of the reading order.

### 2.3 Reading integrity

- Keep body text upright, selectable, and unclipped. Do not rotate, crop, overlap, or bleed essential reading matter for a compositional effect.
- Preserve content and operation at 200% zoom and at 320 CSS px width. Allow local two-dimensional scrolling only when the relation itself requires it, such as a trace table or diagram.
- Keep labels, captions, evidence, and controls adjacent to what they explain. Do not let a signature element interrupt the primary reading path.
- Preserve visible keyboard focus and a usable no-JS reading order.

### 2.4 Material honesty

Ban continuous color gradients, glow, soft shadows, glass effects, and rounded card containers. Allow hard-stop grids, hatching, true circles, punch holes, and a hard offset shadow only when it expresses layering or state.

Do not combine `clip-path` with border or outer shadow on the same clipped element. Put required outlines on an unclipped wrapper or construct the silhouette without them.

## 3. Generative Grammar — 生成语法

### 3.1 Compose a visual thesis

After establishing the learning arc, write one internal sentence before choosing components:

```text
[核心学习转折] → [主导形式或材料对比]；以 [稳定阅读轨 / 留白 / 正交结构] 制衡；采用 [密度节奏]。
```

Use this thesis to decide what should dominate and what should remain quiet. Do not begin with “which signature elements have not appeared yet.”

### 3.2 Annotate before styling

Annotate each section and consequential figure, not every decorative fragment.

**Required form-selection triple**

```text
[读者问题] [主要学习操作] [信息关系 + 证据状态]
例：失配后哪个指针移动？ / 追踪状态转移 / 状态×时间；具体构造输入
```

Choose one primary learning operation from: **locate, sequence, trace, compare, quantify, predict, synthesize**. Add at most one supporting operation when it directly serves the primary one. If a unit asks the reader to perform more than two distinct operations, split it or narrow its purpose.

**Optional material and attention note**

```text
[叙事状态] [强度] [阅读角色]
```

Map narrative state to material: exposition → L0, structure → L1, measurement → L2, record → L3, lifted interaction → L4, intervention or resolution → L5. Let material changes mark actual changes in reading work.

### 3.3 Select and construct forms

Select in layers. Do not compare options from different layers as if they were interchangeable:

| Layer | Decision | Examples |
|---|---|---|
| 1. Reader operation | What must the learner do? | locate, trace, compare, predict |
| 2. Relation and evidence | What is connected, and how is it known? | state × time; cause → effect; constructed input |
| 3. Encoding family | What spatial operation makes the relation visible? | trace, dual-band alignment, gauge, timeline |
| 4. Container | How is the encoding mounted? | full plate, inset panel, table shell, code block |
| 5. Rhetorical overlay | What interpretation is added after the encoding? | insight, warning, concluding verdict |

Only layer 3 competes as an explanatory form. A container or overlay must never substitute for an encoding. An essence model is content, not a visual component. Match the relation class before choosing a family: do not turn a causal claim into a chronology because a timeline is easier to draw.

**Candidate comparison.** Compare materially different candidates only when:

- the relation admits more than one encoding family;
- a candidate adds interaction, JavaScript, or substantial visual mass;
- its no-JS or narrow-screen variant changes the learner's operation;
- measured, constructed, and illustrative data require materially different treatment;
- the canonical form is operationally adequate but compositionally inert, and a materially different form could carry the visual thesis more forcefully at comparable cognitive cost.

Candidates must differ in information geometry, material logic, or compositional strategy—not merely a surface skin. Otherwise use the canonical family as a baseline and keep the decision lightweight.

**Hard gates.** Eliminate a candidate that:

- implies a false quantity, order, membership, or causal relation;
- fails contrast, legibility, or label space at its real rendered size;
- cannot preserve the learning operation without JavaScript;
- cannot recompose on a narrow viewport without destroying the relation;
- misrepresents evidence status or precision.

No aesthetic gain compensates for failure at these gates.

**Selection order.** Treat aesthetic effect as a positive selection criterion, not a decoration allowance. Among survivors, prefer in this order: exact operation match → lower cognitive and interaction cost → aesthetic and compositional effect → expressive novelty.

Define aesthetic effect as clarity of the visual thesis, decisive hierarchy, material contrast, rhythm, and fit with the page—not ornament. Define novelty as a genuinely new relation or visual argument, not merely unfamiliar styling. Reuse is a practical fallback only when it matches the current aesthetic effect; it is never an automatic priority. Novelty is not a last tie-breaker: it may decide among operationally comparable forms and may justify a new or differentiated form when it materially strengthens the visual argument without avoidable cost.

**Form budget.** Use one primary form per learning turn and one primary encoding per relation. Add a supporting form only when it serves a different operation. A new or differentiated form may be chosen even when an existing form is operationally adequate, provided it preserves the operation and materially improves the aesthetic argument. Do not create multiple variants of the same relation merely to display novelty. A component whose removal eliminates no learning operation must still perform necessary compositional or rhetorical work; if it does neither, it is decoration.

**Selection record.** Record for each primary form:

```text
读者问题:
主操作:
信息关系 / 证据:
候选（仅触发时）:
选择 / 淘汰理由:
美学 / 新颖性增益:
容器 / 修辞覆盖:
无 JS / 窄屏变体:
验证问题:
```

A minor form needs one line: operation → form → what the reader can do.

Two illustrative choices:

- If the reader must see the whole failure pattern and the current step, a trace is primary; a separate stepper is redundant unless one-step focus lowers working-memory load. Prefer a trace with a current-step highlight.
- If the reader must decompose one photon's energy, use a stacked energy bar; if the reader only needs to judge threshold crossing, use a gauge. Using both requires two declared operations.

Selection is not construction. Once an encoding family is chosen, continue to §3.4 and build the diagram brief before writing markup or CSS.

**Preconditions for common families**

| Family | Use when | Reject or reshape when | Narrow / no-JS form |
|---|---|---|---|
| Trace / matrix | finite states × steps; global pattern matters | too many dimensions; cells become unreadable | local horizontal scroll with frozen labels; show full trace without JS |
| Stepper | ordered single-path transitions; current state matters | parallel branches; whole-pattern comparison | keep all steps available without JS; preserve keyboard controls |
| Timeline / timetable | chronology or intervals are the subject | causal hierarchy without time semantics | vertical sequence; keep dates attached to events |
| Causal chain / state diagram | directed dependencies or conditional transitions | simple chronology; decoration | linearize with explicit direction and conditions |
| Dual-band alignment | two sequences share an overlap or correspondence | ordinary side-by-side comparison | preserve alignment by scrolling; never stack into unrelated rows |
| Readout | one key scalar deserves emphasis and comparison | the value lacks context; several values compete for focus | retain the number, unit, and comparison as text |
| Gauge | a scalar with a meaningful threshold | categorical comparison; no real threshold; distribution | retain the value and threshold as text |
| Ratio bar / instrument strip | part-to-whole or shared comparable baseline | different denominators; non-additive units | stack on a common scale; use a table when scale is unclear |
| Compare table | genuine two-axis lookup | narrative sequence or one-dimensional comparison | local scroll with sticky headers |
| Dialogue | competing models with real, differentiated positions | strawman positions; one voice | ordered speakers with names attached |

**After rendering.** Run three tests:

1. **Removal:** Which learning operation disappears if the figure is removed? If none, does it still perform necessary compositional or rhetorical work? If neither, remove it.
2. **Prose removal:** Can the figure support its declared operation without explanatory prose? If not, it does not encode the relation.
3. **Simpler alternative:** Does a simpler, more static, or lower-mass form preserve both the operation and the intended aesthetic effect? If yes, prefer it. If the richer form creates a distinct visual argument at acceptable cost, retain it.

Reselect a failed form rather than decorating it. Delete the unit only when it has neither a teaching nor a compositional or rhetorical purpose. Preserve truthful position, scale, and direction; a unit-count threshold never makes a grid valid or invalid.

### 3.4 Construct diagrams

A diagram is an external reasoning surface, not a decorated summary. It earns its place when spatial indexing makes a target relation easier to find, compare, or operate on; it can also make a false relation feel obvious. Construct from the proposition, not from the container or the available geometry.

**Distinguish diagram, chart, and plate.** A diagram organizes entities, states, and relations; a chart encodes quantities on scales; a plate is a mount. A decorative plate never substitutes for a missing diagrammatic structure.

**Write a diagram brief** before markup, CSS, or JavaScript:

```text
图表主张:
实体 / 状态 / 数量:
关系与方向:
证据与来源:
边界 / 失效 / 对照:
省略项:
数量 → 通道 / 尺度 / 单位:
标注计划:
无 JS / 窄屏变体:
读图验证问题:
```

**Build the proposition skeleton first.**

- Keep only the entities, states, and relations required for the declared inference. Collapse secondary entities into labels or adjacent prose.
- Define what each spatial relation means before drawing it: alignment = correspondence, overlap = shared membership or intersection, containment = subset or ownership, sequence = time or operation order, distance = difference or quantity only when intended, arrow = direction of dependency.
- If the intended relation cannot be expressed by a truthful spatial relation, do not force it into a diagram.
- Distinguish absence from zero, unknown from measured zero, and illustrative values from observed values.
- Give the diagram one primary inference. If it needs more, use aligned panels, small multiples, or a secondary layer; do not make every relation compete in one frame.
- Include the boundary, equality, failure, or comparison case when the model's meaning depends on it.

**Assign channels and scales.**

- Choose the coordinate system before the visual skin: time/sequence, common quantitative scale, state graph, part-to-whole, containment, or categorical grouping.
- For quantitative judgments, prefer position on a common scale, then length. Use area or angle only for approximate magnitude, never for precise comparison. Use shape and hue primarily for categories. Do not use perspective, 3D depth, or shadow to encode magnitude.
- Start length and area from a meaningful zero. Label log or transformed scales explicitly. Keep intervals truthful and units visible.
- Use direct labels where they remain readable. Use a legend only for repeated category mapping or intentional lookup; never make color the only identifier.
- Show uncertainty, sample size, or missing-data treatment when they affect the claimed inference. Do not display more precision than the evidence supports.
- Make measured data, constructed inputs, and illustrative diagrams visibly distinct in the caption or plan. For constructed inputs, expose the generating parameters or derivation; for measured data, cite the source, time window, and transformations.
- Use channel accuracy as an empirical default, not an unconditional law. A deliberate deviation must have a task-based reason and must pass the false-inference test.
- Aesthetic hierarchy may change spacing, weight, contrast, or the placement of the main gesture; it must not change the quantitative geometry.

**Design the diagram architecture.**

- Separate the primary relation from reference marks, annotations, and production marks. Secondary layers must not compete with the encoded relation.
- Attach labels to the marks or relations they explain. Use arrows for direction, not decoration. Reserve the strongest red gesture or scale jump for the primary inference.
- Captions should state the inference, unit, boundary, or provenance the figure supports; they should not merely repeat its category.
- Use negative space to isolate the turning point, not to float unrelated marks. Asymmetry must preserve the reading order and the truthful position of every mark.
- Remove any mark whose absence would make the diagram clearer. A signature gesture is justified only when it reveals the relation at the main learning turn.

**Decide interaction and responsive behavior.**

- Prefer the static diagram. Add interaction only when progressive state disclosure reduces working-memory load or enables a comparison that cannot be held in one frame.
- With JavaScript disabled, the full sequence, labels, values, and conclusion must remain available. Never encode the current state by color alone.
- On narrow screens, verticalize sequences, split aligned panels, provide local scrolling with frozen labels, or fall back to a table. Do not shrink labels below readability or break a correspondence by stacking related tracks into unrelated rows.
- If the relation cannot survive the narrow layout, change diagram family rather than forcing the desktop geometry into a smaller box.

**Verify the diagram.**

1. **Read-off:** Without explanatory prose, can the reader state the intended relation, not merely recognize the topic?
2. **False inference:** Does any position, length, overlap, order, arrow, or color imply a quantity, cause, grouping, or precision that the model does not support?
3. **Boundary:** Are the equality, failure, omission, or comparison conditions visible where the inference requires them?
4. **Label recovery:** Can every mark be matched to a label and every label to a mark, with units and direction intact?
5. **Scientific integrity:** Are source, evidence status, precision, axis/scale, and uncertainty adequate for the claim?
6. **Accessibility:** Does a short identifier plus a visible long description or caption convey the essential structure, values, and conclusion to readers who cannot see the marks?
7. **Aesthetic test:** Does the strongest gesture land on the primary inference? If removing a decorative mark improves both clarity and force, remove it.

A diagram that fails a semantic test cannot be repaired by styling. Reselect the diagram family, simplify the proposition, or move the unsupported claim back into prose.

### 3.5 Allocate attention

- Give the current reading unit one dominant destination. Subordinate competing accents rather than distributing equal emphasis everywhere.
- Reserve the strongest scale contrast, red gesture, or diagonal rupture for the page's main learning turn. Repetition turns rhetoric into wallpaper.
- Use redundancy selectively: repeat a cue when it supports decoding or recall, not to restate identical prose in several containers.
- Place signals before or beside the operation they explain. Separate decorative marks from instructional marks by position and visual weight.

### 3.6 Build composition at three scales

- **Macro — page:** establish a readable route, a dominant mass, and a counterweight. Use one or two meaningful compositional turns rather than constant rupture.
- **Meso — section:** alternate dense analysis with spacious synthesis; let a dense section end in a conclusion, not merely another container.
- **Section index:** when a display numeral accompanies a heading, bind them into one asymmetric index block: set the numeral in a narrow structural column, align its cap line with the kicker or headline, and keep the heading as the reading anchor. Do not park the numeral below the title as an orphan. On narrow screens, retain the numeral as a gutter element beside the heading rather than turning it into another full-width row.
- **Micro — component:** align edges, baselines, ticks, labels, and figure numbers. Precision at this scale makes bold composition credible.

Use dynamic balance, not symmetry, while keeping the prose rail stable. Test balance through focal competition, reading order, and directional force; “no obvious imbalance” is not a sufficient review.

Treat **20° `/`** as the canonical house axis, not a historical law. Use one dominant oblique family across conspicuous cuts, wedges, and separators. Permit a different angle when mechanism geometry, data truth, or a deliberate compositional counterforce requires it; record the gain. Keep mechanism diagrams internally truthful and normally orthogonal.

### 3.7 Design negative space and dark mass

Shape negative space as a pause, channel, margin, or counterweight. Do not fill it simply because it is available. Break long dark runs at meaningful teaching boundaries, and preserve enough light surface for the next focal gesture to register.

Use no universal percentage for red or dark coverage. Judge area, duration, contrast, adjacency, and reading task together at representative viewports.

## 4. Typography and Language — 字体与语言

### 4.1 Build hierarchy before choosing display tricks

Distinguish display, section title, body, caption, label, and code through size, weight, spacing, and position. Use no more than three simultaneous text weights unless a fourth has a distinct reading role.

Default to body weight 400–500, display weight 600–700, body line-height around 1.65–1.8, and a readable measure chosen by script. Start near 60–75 Latin characters or 34–42 Han characters per line, then adjust from actual font metrics and content. Treat these as starting points, not compliance thresholds.

Use full-width display stacking, oversized numerals, or bleeding type only when they strengthen the visual thesis. Keep explanatory text out of those effects.

### 4.2 Respect script and locale

Set the correct `lang`; choose fonts for the page's scripts and include system fallbacks. Do not apply Latin tracking, capitalization, italics, or line-breaking habits to Chinese text.

For Chinese pages, use locale-appropriate punctuation and glyph forms; prevent prohibited line-start or line-end punctuation where the platform supports it; keep numbers with units and short formulas together where possible. Prefer weight, emphasis marks, or underlining over synthetic italics. Avoid decorative full-width Latin or digits.

Use English labels only when they add terminology or navigation value, never as texture. Make headings assert one defensible idea; make captions explain the mechanism or relation rather than repeat a category.

### 4.3 Let typography carry the rhetoric

Favor exact verbs, meaningful scale changes, deliberate line breaks, and parallel structure for parallel ideas. Do not manufacture profundity through oversized type, slogan-like fragments, or a concluding verdict unsupported by the preceding derivation.

## 5. Form and Component Vocabulary — 形式与组件词汇

Treat entries as candidates within their layer, not as interchangeable options. Only **encoding forms** compete during form selection; containers, layouts, and rhetorical overlays are chosen afterward. Use no form as a skin: each choice must answer the question of its layer.

### 5.1 Encoding forms

- **Process and change:** trace (time × state), stepper (guided decomposition), swimlane (actor × time), state diagram (transition × condition), timetable (ordered events).
- **Structure:** memory map (interval × ownership), nested tree (containment), exploded frame (assembly), punch card (position × binary state), ASCII diagram (monospace position).
- **Correspondence and cause:** dual-band alignment (overlap × correspondence), causal chain (pressure → mechanism → consequence → tradeoff), compare table (two-axis lookup only).
- **Quantity:** readout (weighted value), gauge (value against threshold), ratio bar (share), instrument strip (values on a common baseline).
- **Discourse:** dialogue (competing predictions and positions).

### 5.2 Containers, layouts, and geometry

- **Containers:** full or light plate, inset panel, archive card (evidence that something occurred), archival panel (definition or convention), code block, table shell, review index (closure that links to anchors).
- **Compositional layouts:** split (equivalent alternatives), asym / staggered (primary-secondary relation), nest (context × content), stair (ordered progression), collage (synthesis from evidence).
- **Geometric gestures:** cut (precision), wedge (directed pressure), circle (focus), field (material territory). They modulate composition; they do not replace an encoding.

### 5.3 Rhetorical overlays

Use after the encoding is valid: **insight panel** (earned synthesis), **warning box** (specific failure), **concluding verdict** (earned rhetorical closure). The essence model / 本质模型 is content, not a component. Overlays interpret or compress an existing relation; they never stand in for the trace, comparison, or derivation that proves it.

## 6. Composition and Production Defaults — 可偏离默认值

- **Rails:** stable prose rail plus a wider exhibit rail; collapse to one column when space no longer supports the relation.
- **Spacing:** derive from a small scale such as `0.25 / 0.5 / 1 / 1.5 / 2 / 3 / 4 / 6rem`; use larger intervals for changes in reading work, not arbitrary card separation.
- **Fonts:** IBM Plex Sans for Latin, Noto Sans SC for Chinese, Urbanist for display numerals, Google Sans Code for code; substitute appropriate fonts for other scripts.
- **Board:** 1240px with navigation or 980px without; 24px diagram grid. Use a 768px collapse as a starting hypothesis, not the only permissible breakpoint.
- **Header:** standard or poster composition. Include title, scope, discipline, and useful reading metadata; omit fields that would require invention.
- **Mounting:** frame a mechanism plate when registration or separation aids reading. Cite it from prose or make its caption carry the mechanism conclusion.
- **Production marks:** use crop marks, rulers, and registration crosses only when they reinforce scale, sequence, or construction. Short pages may omit them.
- **Colophon:** close with a compact production or source note. Report only real values; do not turn the colophon into ornamental metadata.
- **Interaction:** use steppers, scroll-spy, or controls only for an identifiable learning operation. Preserve semantic HTML, keyboard operation, reduced-motion behavior, and complete no-JS content.
- **Engineering:** prefer single-file, no-build HTML with inline CSS and minimal inline JS. Use Google Fonts when network access is acceptable; provide local fallbacks and honor an offline request.

A deviation needs one useful reason, not an essay. Record consequential deviations in the planning file.

## 7. Aesthetic Review — 审美复核

Review the actual rendered page at three distances and at desktop and mobile widths. This is a design critique, not a second copy of the Delivery Self-Check.

1. **Thumbnail / 缩略：** identify the dominant mass, current focal point, and directional route. Check whether the page still has a coherent identity when small decorative marks disappear.
2. **Reading / 阅读：** follow the page as a learner. Check whether headings predict content, signals arrive in time, dense sections release into synthesis, and the strongest gesture lands on the main learning turn.
3. **Detail / 细部：** inspect type metrics, punctuation, alignment, caption adjacency, color contrast, truthful scales, and accidental tangencies. Remove marks that cannot explain their role.
4. **Recomposition / 重组：** verify that narrow screens reorder and simplify the composition rather than merely shrinking desktop rhetoric. Preserve the reading route and essential relations.

If the page is attractive but the learner cannot predict, trace, compare, or transfer the model, return to the learning and form decisions rather than adding polish.

## 8. Examples — 示例索引

Read only the example and sections closest to the required **mode + content relation + temperament**; never copy a complete scaffold by default.

- `example-kmp.html` — exam-dense, blueprint-led: concrete trace, stepper, alignment, archival conventions.
- `example-maxwell-equations.html` — historical arc, poster-led: timeline, stair, asymmetric composition, evidence collage.
- `example-photoelectric-effect.html` — threshold mechanism, instrument-led: circular focus, threshold axis, dialogue, annotated apparatus.

These examples demonstrate different content emphases, not the limits of the language.
