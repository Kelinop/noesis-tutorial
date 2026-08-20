---
name: noesis-tutorial
description: Use when the user asks for technical tutorials, concept explanations, learning notes, or exam-point study material, to be delivered as HTML learning pages. 当用户请求技术教程、概念讲解、学习笔记或考点精讲，需交付 HTML 学习页面时使用。
---

# noesis-tutorial

## Purpose

Create complete, runnable HTML learning notes for technical topics. The page should help learners understand why a concept exists, what engineering pressure shaped it, how it works, what tradeoffs it introduces, and how it connects to broader system design patterns. **Write the page in the language the user used in their request** — the request language is the page language, with no default fallback — and always follow the specific art style. If the content is too enormous for a single file, break it into multiple files divided by subtopics — the split decision is content-driven, see Large Document Strategy. Each file should be self-contained and navigable, built in the constructivist technical-editorial style unless the user states a preference otherwise.

The result should feel like a designed engineering knowledge product, not a textbook dump, Markdown-to-HTML conversion, or generic summary.

## When NOT to Use

- The user wants a brief verbal explanation or Q&A without a deliverable page → answer directly, do not apply this skill.
- The user explicitly requests Markdown / plain text / slides or another format → do not apply this skill.
- The topic is too thin (a one-sentence fact, a term lookup) → not worth a full page structure.
- The user explicitly asks for lightweight fast output ("keep it simple", "rough overview") → unless an HTML page is still confirmed, do not apply this skill. If an HTML page is confirmed but light, the only permitted lightweight variant is Cheatsheet mode (Step 0) — a deliberate, rule-governed density mode, never "sloppy work".
- Non-teaching tasks (coding, debugging, review, data analysis) → this skill does not apply.

## Teaching Architecture

Explain concepts as causal chains, not terminology lists. For each major concept, prefer this sequence:

1. **Original problem** — What was broken before? What problem could the old approach not solve?
2. **Engineering pressure** — Cost, scale, latency, security, compatibility, complexity, or hardware constraints.
3. **Failed or limited older solutions** — What did the prior approach get wrong.
4. **Essence model (delivered as the essence hook)** — A concise, forceful statement of the design's essence; prefer a physically intuitive model to aid understanding.
5. **Mechanism** — How it works, step by step; **must include a worked example with real data** — pure abstract description is not acceptable.
6. **Tradeoff** — What was gained, what was sacrificed.
7. **Formal definition** — Introduce precise terminology only after intuition is established.
8. **System impact** — What it changed, what it enabled, what it complicated.

Rules:

- Structure emerges from topic — do not force every section onto every page.
- **Analogies must declare their breaking point**: "This model breaks at X, because Y" — the breaking point is itself a teaching point.
- **Coverage**: Cross-check every item on the knowledge checklist; any omission must be declared at the top of the page.
- Definitions make earlier intuition precise — never open with a definition, unless the user explicitly wants reference-style.

## Exam-Point Teaching

For exam contexts, exam points are overlaid on the teaching base — every exam point must be taught in depth, not listed. Applied when Step 0 detects an exam scenario.

### Forbidden

- Listing point names without explanation (e.g. just "how to compute the next array" plus a formula)
- Unexplained bullet lists of exam points
- Copying textbook text verbatim without derivation and examples

### Every exam point must include

1. **Exam positioning**: how it is tested (multiple choice / big problem / fill-in), score weight
2. **Mechanism walkthrough**: step-by-step operation with concrete data
3. **Manual derivation**: trace every state change with real input (never just the final result)
4. **Common traps**: what students get wrong, why, and how to avoid it
5. **Exam techniques**: speed methods, mnemonics, verification strategies
6. **Related points**: how this point combines with others in one question

### Example comparison

| Bad (listed) | Good (taught) |
|-------------|-------------|
| "next[1]=0, next[2]=1" given directly | Derive next position by position from the "longest common prefix-suffix" definition, annotating the current overlap each step |
| "nextval is next's optimization" in one sentence | First show next's redundant comparison scenario, then demonstrate how nextval skips invalid comparisons |
| Listing time complexity O(n+m) | Analyze why brute force is O(nm), how KMP uses next to avoid text backtracking, derive to O(n+m) |

The end-of-page review list may be a bullet list — the list is an index, not content; the body must already have completed the full teaching of every point.

### Component mapping

| Teaching requirement | Form |
|---------|------|
| Exam positioning | section tag + first paragraph |
| Mechanism walkthrough | causal chain / memory map / blueprint callout |
| Manual derivation | trace / stepper (real data, step by step) |
| Common traps | warning box / dialogue |
| Exam techniques | insight panel / hard shadow |
| Related points | dialogue / compare table |
| End-of-page exam list | checklist (index only) |

The mapping is an entry index for exam coverage, not a hard mapping — combination decisions still follow Step 5.

## How to Use References

All rules live in `references/` as the single source of truth — consult specific sections when in doubt during execution.

- `references/visual-system.md` — design philosophy, the **why**: three principles (construction visible / color is function / geometry is instrumentation), **visual grammar** (semantic annotation → color narrative state → combination grammar → page roles → composition precedents), layer model L0–L5 + stacking matrix, axis system (20°), geometry instrument library (core/extended), composition system (dual rails / plate system / skyline), R1–R4 composition precedents. The terminology table lives here (Combination Grammar, single authority). **Read first, in full.**
- `references/style-guide.md` — design methodology + CSS tokens + component specs, the **how**: Layout Specs (board / ruler / three-level plate mounting / horizontal composition), Geometric Specs (G1–G8 + axis formulas), Instrument Specs (exploded frame / gauge / triangle pointer / hatching / giant verdict). Each component opens with a **capability card** (主语义 / 次语义 / 替代候选 / 兼容衔接 / 冲突互斥 / 变体轴) for combination decisions. **Write your own CSS based on the rules and adjust it to fit the specific needs of the context.** The file opens with a Quick Reference card (速查卡) carrying the rule-authority index and the Numeric Gate Table — numeric rules are authoritative where marked 数值源, and any 数值源 edit must be mirrored to the gate table (the table never overrides its sources). **Read second, in full**; when the context budget is tight, you may work from the card and dip into referenced sections on demand while writing CSS — the Quality Checklist still requires consulting the specific sections it names.
- `references/example-twos-complement.html` — two's complement: plate system, punch card (plate-row three-code comparison), trace, blueprint callout; print-family dominant.
- `references/example-virtual-memory.html` — virtual memory: memory map, nested tree, exploded frame, gauge, hatching; blueprint-family assembly.
- `references/example-tcp.html` — TCP three-way handshake: swimlane, state diagram (plate.light), ascii, dialogue, rail-hang.
- `references/example-kmp.html` — KMP (complete 408 exam points): archival panel, stepper/step-through, causal chain, ratio bar, warning box, code block (black background + syntax colors), worked exam problems.
- `references/example-maxwell-equations.html` — Maxwell's equations: poster header, timetable, archive card, G5 color field, G7 stair, G8 collage, asym.
- `references/example-photoelectric-effect.html` — photoelectric effect: G1 cut-corner, G3 red circle, gauge (threshold), dialogue, staggered, insight panel, split.
- `references/example-kmp.en.html` — KMP in English: the language & implementation template (same 10 figures, complete teaching notes; no exam-oriented framing).
- `references/example-coverage.md` — canonical example × variant example index (component → 规范例 → 变体例 with value note) + composition index (topic type → teaching arc → density curve → rationale). The authoritative source for which example to consult when implementing a component; check this matrix before placing a new component. Also provides design annotations for three maximally different examples.

### On-Demand Reading Path

```text
All tasks:     SKILL.md → visual-system.md (Visual Grammar + Combination Grammar + Composition Precedents)
Need diagrams:     + style-guide → Diagram Specs + 1–2 closest examples
Need history:      + style-guide → Archive Card / Timetable / Archival Panel Specs + examples
Need geometry:     + style-guide → G1–G8 capability cards + examples
Need interaction:  + style-guide → Interaction Specs + examples
Pre-delivery:      + style-guide → 速查卡 (Numeric Gate Table) → execute Quality Checklist
```


## Creation Workflow

### Step 0: Determine Context

- **Teaching is the base**: unless the user explicitly requests a cheatsheet, the Teaching Architecture is the backbone of every page.
- **Exam context is an overlay, not a separate track**: when the context is an exam (e.g. China's 408 postgraduate entrance, campus recruiting interviews), keep the teaching backbone and apply Exam-Point Teaching on top — each concept additionally carries exam positioning, exam-type walk-through, common traps, and speed techniques, and the knowledge checklist becomes the exam-point list.
- **Cheatsheet** (user explicitly requests) → density-first: one-sentence essence model (essence hook), skip evolution / system-impact, use data tables, checklists, and compact code blocks as the main body; each item still needs one sentence of causal explanation — dense but not shallow. Cheatsheet = **light-mounting mode**:
  - **Mounting**: mechanism figures mount as `.plate.light` (registration marks + figure number + caption, no frame); no giant verdict; no breather — every section `.density-dense`; no horizontal composition (staggered / plate-row / strip / asym / split all off);
  - **Kept**: edge ruler rail, crop marks, colophon, full page header (standard or poster); sidebar only when the page qualifies as long-form (Step 4 → Long-form judgment);
  - **Still enforced**: coverage (skipped evolution / system-impact declared at the top of the page) and the Quality Checklist (blocking + aesthetic review) with the exemptions above — exam-point depth relaxes to the one-sentence causal line, never to a bare name list.

### Step 1: Research & Inventory

**Research Mandate — verify before writing.** Technical tutorials lose credibility on a single wrong detail:

- **Mechanism**: how the concept actually works — official documentation, specifications, authoritative sources. Do not infer internal behavior from surface API.
- **History**: real historical context, not fabricated narratives. If unsure when or why, state the pressure without inventing dates or names.
- **Code examples**: syntactically correct and runnable. Do not mix APIs from incompatible versions.
- **Tradeoffs**: real, not plausible-sounding inventions. If debatable, present as design tension rather than settled fact.

Bad: "Git was created because SVN required a constant internet connection."
Good: "Git is a distributed version control system — every clone is a full repository, enabling offline commits and branching without a central server."

If a topic is too broad to research thoroughly, narrow the scope rather than guessing and explain the rationale.

Then create the **knowledge checklist (topic inventory)** — scoped by Step 0: exam overlay → the checklist is the exam-point list (each point with how it is tested and weight); engineering → mechanism / history / tradeoffs / code; cheatsheet → fact sheet (definitions, formulas, key data, common traps). The page structure must address every item on the checklist, or explicitly declare omissions — the "Key Takeaways" at the end must map back to each item on the checklist.

**User-provided material**: When the user provides lecture notes, textbooks, or study material, treat them as the scope boundary and checklist source; the verification obligation is not waived — errors in the material must be corrected against authoritative sources and noted on the page.

**Planning artifacts**: Steps 2–5 write their artifacts to `plan-<topic>.md` in the working directory as they are produced — causal chain (Step 2), essence model (Step 3), section plan with density and semantic annotations (Step 4), one-line form rationale (Step 5). This file is the resumable planning record; do not start the HTML without it. After the Quality Checklist passes and the page is delivered, delete `plan-<topic>.md` — it is a temporary construction record, not a deliverable.

### Step 2: Extract the Causal Chain

In 3–5 sentences: 1) What was broken before? 2) What engineering pressure forced the design? 3) What did the old approach get wrong? 4) How does the new design work? 5) What was gained, what was sacrificed? Write it down before touching any HTML.

### Step 3: Design the Essence Model

Design the essence model — the simplest useful mental model of the design; on the page it is delivered as the essence hook (component `.hook`, specs in style-guide → 陈述类容器通则). It should be:

- One or two sentences.
- In the page's language.
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

Four examples, one per pattern:

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

Criterion: after reading the hook, the reader should hold a reliable concrete model. A hook that offers only conclusions without mechanism, or only terminology without intuition, fails. Later diagrams, examples, and terminology should refer back to this model.

### Step 4: Semantic Orchestration

Decide which sections this topic genuinely needs. Not every page needs every beat of the Teaching Architecture. Force a section only when it improves understanding.

Consult the R1–R4 composition precedents (visual-system → Composition Precedents) when choosing the initial skeleton, but the section sequence and density curve are decided by this step's semantic annotations — precedents are a starting point, not an end point.

Then **annotate each section and diagram unit** with a one-line semantic annotation (visual-system → Visual Grammar → 语义标注):

```text
[教学动作] [信息关系] [叙事状态] [强度] [证据属性] [阅读角色]
```

This annotation is the creation starting point — it precedes any color, component, or layout choice. It is an internal design note, not reader-facing content.

From the annotation, determine:
1. **阅读角色** (page role) for each unit: 定位 / 定锚 / 展示 / 拆解 / 对照 / 转场 / 高潮 / 闭环 (visual-system → Composition → 页面角色). Check for missing or duplicate roles.
2. **强度与密度**: breather / standard / dense for each section.
3. **材料转场**: how L0 (解释) → L2 (推演) → L3 (归档) → L5 (事件) flow between sections (visual-system → 颜色叙事状态).

**Signal density** (per-paragraph rule): every paragraph introduces at least one of — engineering constraint / tradeoff / failure mode / system behavior / design consequence / causal relationship / mental model. Paragraphs that merely restate previous ideas are cut; prose that sounds insightful but adds no new operational understanding is removed.

**Long-form judgment**: a plan with ≥4 top-level sections is a long-form page and takes the left-column sticky table of contents (specs in style-guide → Sidebar); shorter pages get no sidebar — navigation does not exist to fill space.

**Split judgment**: if the section plan decomposes into two or more complete teaching arcs, decide the multi-file split here — one file per arc, per the Large Document Strategy.

Geometry is the mapping result of these annotations (visual-system → Geometry instrument library), never reverse-justified after rendering.

### Step 5: Open-Ended Component Selection & Geometry

**Select components by information relationship, not by "which component to use"** — query the candidate space from the semantic annotation, then choose based on "what to emphasize" (visual-system → Combination Grammar → 替代组合).

**Candidate entry index** — from the Step 4 annotation identify the information's cognitive type and enter the candidate space via its default candidate. The index is an entry point, not a mapping: each listed form is the default candidate (主语义), alternatives live in the component capability cards, and the selection procedure below decides the final form. **Tables are only for genuine two-dimensional lookups** — do not default to tables as a container.

| Cognitive type | Default candidate |
|---|---|
| Contrast / debate / misconception correction | dialogue |
| Multi-role / multi-stage process handoff | swimlane |
| Hierarchical containment (address space, scope) | nested tree |
| Evidence / historical fact / quotation | archive card |
| Strict formal definitions / fixed rules | archival panel (definition tag) |
| Key readings / state / verdict figures | readout |
| Threshold readings (load factor, water level, utilization) | gauge |
| Precise time series | timetable |
| Close-up annotation of a mechanism diagram | blueprint callout |
| Bit patterns / encodings / instruction formats | punch card |
| Part-level decomposition of a mechanism (fields, stack frames, carry chain) | exploded frame |
| Proportion / frequency / distribution | ratio bar |
| Genuine two-dimensional comparison (gain × sacrifice, A × B) | tradeoff / compare / data table |

1. For each main mechanism unit, query candidate components by information relationship — start from the index row, then expand via the capability cards (style-guide → 主语义 / 替代候选).
2. Choose one primary semantic and one secondary emphasis direction.
3. Write a one-line **form rationale**: `信息关系 → 形式 → 读者应看见的操作` (e.g. "pointer movement → SVG dual-rail diagram → encodes the main-string pointer's advance and retreat"). A form that degrades into a homogeneous grid array (>16 units distinguished only by color, encoding only arrangement, not movement/direction/transfer/connection) is a failed form — reselect from the existing forms (degraded-form prohibition, see visual-system → Form Validity).
4. Check协同 / 替代 / 冲突 relationships (visual-system → Combination Grammar); adjust only when a conflict appears.
5. Consult the corresponding spec (style-guide → Form Specs) and one closest example implementation as needed (example-coverage.md → 规范例).

Then run the **mounting decision**: mechanism-class components (diagram / trace / swimlane / punch card / exploded frame) default to full plate mounting (`figure.plate.full` + figure number + caption); archive / dialogue / checklist components stay fluid. **Every mounted plate must be cross-referenced from the prose (见图 N / see Fig. N) or its caption must state the mechanism conclusion.**

### Step 6: Generate HTML

Build the page. For long documents, use the Large Document Strategy below.

#### Font System

| Role | Font | Source |
|------|------|--------|
| Chinese | Noto Sans SC | Google Fonts CDN |
| Latin | IBM Plex Sans | Google Fonts CDN |
| Numerals | Urbanist | Google Fonts CDN |
| Code | Google Sans Code | Google Fonts CDN |

CDN `<link>` goes in `<head>`; the full snippet lives in `references/style-guide.md` → Tokens.

Use `var(--font-num)` for numeric contexts (indices, position markers, pure-number cells). Weight discipline (no hard whitelist): body/labels 400–600; 300 only for large display (poster headlines, giant numerals); 600 only for display giant text (Urbanist / Noto Sans SC), never in body copy; ≤3 weights per screen — weights not declared in the CDN link do not render, so any weight change must be synced to the CDN link.

Cross-platform weight normalization — the following must be in `body`:

```css
body {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-rendering: optimizeLegibility;
}
```

For Latin-only pages you may trim the Noto Sans SC weights from the CDN link to shrink payload (the four-font stack stays the default).

#### Writing Standards

**Prefer**: causal reasoning; mental models; state changes over time; implementation pressure; engineering consequences; cross-concept tensions (abstraction↔control, safety↔flexibility, latency↔throughput, simplicity↔scalability, consistency↔availability).

**Avoid**: definition-first writing; hollow motivation; textbook tone; intuition-free jargon stacking; false profundity; tautology; mechanical Markdown conversion; SaaS card layouts; gradients / glassmorphism / glow / soft bubbles; decorative or noisy animations; rounded-corner mind maps; card-stack templates; UI copy that explains its own design.

##### Good vs Bad

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

## Large Document Strategy

When the planned content exceeds what one page can teach without degradation, split it by content. The split decision is made at **Step 4 planning time, from content semantics — never from a line count**:

- **One file = one complete teaching arc**: its own problem → pressure → mechanism → tradeoff closure, its own essence model, its own figure cluster (≈3+ plates). A file boundary is legitimate exactly where an arc closes — never split mid-arc, never inside a section; a long single-arc topic stays in one file and carries its length through the skyline rhythm (breather / standard / dense).
- **Exam mode**: exam points group into independently teachable clusters, each still taught in depth (mechanism + derivation + trap) — splitting is not an excuse for listing.
- **Structure**: create a `<kebab-case-topic>/` folder in the target directory and write one HTML file per arc inside it, each named for its subtopic in kebab-case English.
- **Each file follows the single-file standard**: the full Output Contract applies per file — page header, inline CSS, construction items, sidebar when long-form (Step 4 → Long-form judgment), figure numbers starting at 1, one giant verdict, colophon reporting its own figure count. No series-level numbering, index file, or cross-file navigation.

Within each file, build in phases: write the scaffold first (`<!DOCTYPE html>` + `<head>` + CSS tokens + section containers), then fill one section at a time — never hold more than one section in memory. If generation is interrupted, re-read `plan-<topic>.md` and the partial file and continue from the first incomplete section — never regenerate from scratch.

## Output Contract

- Every deliverable is a standalone HTML file starting with `<!DOCTYPE html>` (when the topic decomposes into multiple teaching arcs, one self-contained file per arc inside a `<kebab-case-topic>/` folder — see Large Document Strategy); inline CSS; inline JS only when interaction genuinely aids understanding. Write the page to `<kebab-case-topic>.html` in the current working directory (a split series writes into the `<kebab-case-topic>/` folder instead); report the file path(s) to the user when done.
- kebab-case English filenames (`twos-complement.html`, `kmp-algorithm.html`); `<title>` in the page's language.
- Explanations in the requested language; semantic HTML; responsive (single 768px breakpoint).
- Sole external dependency: Google Fonts CDN (see Font System).
- Required Page Header (kicker + title + metadata; standard or poster, see style-guide → Page Header).
- Required construction items: edge ruler rail, four corner crop marks, print colophon — specs in style-guide → Edge Ruler / Crop Marks / Colophon (colophon presence verified by blocking item #9). Exemptions: only the R4 short-verdict precedent (visual-system → R4) may drop the ruler rail together with the sidebar; crop marks and colophon are never exempt.
- Plate convention: figures mount as `<figure class="plate" id="fig-N">` with `.fig-num` / `.plate-caption`, cited from prose via `.fig-ref` — mounting tiers, citation rule, numbering-label language, and the ASCII `id` requirement in style-guide → Plate Specs; full class list in the 类名注册表.
- Avoid: Markdown-to-HTML conversion, half-finished fragments, pseudo-layout, flat articles without the visual system.

## Inline Style Policy

Inline `style=""` is only permitted for **one-off micro-adjustments** (non-recurring spacing, font sizes, ratio bar widths, etc.). If the same style appears more than twice, extract it into a CSS class.

## Responsive Design

Single `768px` breakpoint — do not add breakpoints unless the design genuinely breaks at an intermediate width.

At `≤768px`: headings scale down (3xl→2xl, 2xl→xl); giant figures scale down (5rem→3rem); trace cell sizes reduce (2.2rem→1.8rem); multi-column collapses to single column (staggered / plate-row / strip included); sidebar becomes a full-width **vertical** list at the top (never collapse to a horizontal strip); edge ruler collapses (numbering taken over by `.sec-num`); crop marks hidden; wide tables and diagrams scroll horizontally. Standard @media skeleton in style-guide → Responsive Spec.

## Quality Checklist

Verify every item before delivery. The checklist is split into **blocking items** (must pass — factual/technical correctness) and **aesthetic & semantic review** (should pass — visual grammar and teaching quality).

### Blocking Items (must pass)

1. **Causal chain**: Does every major concept walk through problem → pressure → mechanism → tradeoff?
2. **Essence model**: A mental or physically intuitive model before detailed mechanism, with later diagrams and terminology tying back? Analogies declare their breaking point?
3. **Coverage**: Is the knowledge checklist fully covered or omissions explicitly declared? Does the Key Takeaways map back to every checklist item?
4. **Signal density**: At least one new engineering insight per paragraph? Every mechanism paired with a worked example using real data?
5. **Tradeoffs and boundaries**: Gains and sacrifices stated bidirectionally?
6. **Facts**: Mechanisms, history, and code are verified? Code is syntactically correct and runnable?
7. **Exam depth** (if applicable): Each exam point taught in depth (mechanism + derivation + trap), not merely listed?
8. **Language**: No typos or grammar errors? Terminology used accurately?
9. **Delivery**: Page Header complete (kicker + title + metadata)? `<title>` in the page's language? kebab-case filename? Colophon present (layout / fonts / palette / figure count / 20° axis)?

### Aesthetic & Semantic Review (should pass)

10. **Navigation**: Long pages have a left-column TOC (full-width vertical on narrow screens)? Anchors correspond one-to-one with section IDs? Edge ruler ticks match section order and numbers?
11. **Rule-driven review (four checks, screen by screen)** — each with its criterion and remediation:
    - **11-1 Layers**: No non-L0 layers stack directly adjacent; ochre sits only on L0 and never within gap-md (32px) of any L2 component (bounding-box distance — "both on screen = violation" is forbidden); olive (L0 material grade) is not a layer-order violation — verify against visual-system layer rows L0/L1; consistent with Step 4 annotations. Red quantities → 11-3.
    - **11-2 Axis**: Every slanted element (wedge / section band / kicker / exploded frame / separators / triangle pointers) shares the page axis and direction; cuts never enter text areas; no slants inside mechanism figures; body text never slanted.
    - **11-3 Red surfaces**: Verify against the red-surface row of the Numeric Gate Table (style-guide → 速查卡). Remediation: ratio-bar red segments become outlines or ≤24px tall; table headers never red-filled (deep-red text + red left rule).
    - **11-4 Form validity**: Every mechanism component must answer "what semantic operation does this form encode" — verify each Step 5 form rationale; a rationale that does not hold sends the form back for reselection (not deletion); a homogeneous grid (>16 units by color only, encoding no movement/direction/transfer/connection) is degenerate. Do not police the number of geometry types — diversity is not the goal; form-semantics correspondence is.
