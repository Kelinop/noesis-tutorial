---
name: noesis-tutorial
description: Use when the user asks for technical tutorials, concept explanations, learning notes, or exam-point study material, to be delivered as HTML learning pages. 当用户请求技术教程、概念讲解、学习笔记或考点精讲，需交付 HTML 学习页面时使用。
---

# noesis-tutorial

## Purpose

Create complete, runnable HTML learning notes for technical topics. The page should help learners understand why a concept exists, what engineering pressure shaped it, how it works, what tradeoffs it introduces, and how it connects to broader system design patterns. **Write the page in the language the user used in their request** — the request language is the page language, with no default fallback — and always follow the specific art style. If the content is too enormous for a single file, break it into multiple files divided by subtopics. Each file should be self-contained and navigable.

The result should feel like a designed engineering knowledge product, not a textbook dump, Markdown-to-HTML conversion, or generic summary.

## When NOT to Use

- The user wants a brief verbal explanation or Q&A without a deliverable page → answer directly, do not apply this skill.
- The user explicitly requests Markdown / plain text / slides or another format → do not apply this skill.
- The topic is too thin (a one-sentence fact, a term lookup) → not worth a full page structure.
- The user explicitly asks for lightweight fast output ("keep it simple", "rough overview") → unless an HTML page is still confirmed, do not apply the mounting / density / axis system; the only degradation path is the Step 1 Cheatsheet mode (light mounting, all-dense, no verdict), not "sloppy work".
- Non-teaching tasks (coding, debugging, review, data analysis) → this skill does not apply.

## How to Use References

- `references/visual-system.md` — design philosophy: three principles (construction visible / color is function / geometry is instrumentation), layer model L0–L5 + stacking matrix, axis system (20°), geometry instrument library (core/extended), composition system (dual rails / plate system / skyline), teaching-type mapping. **Read this first.**
- `references/style-guide.md` — design methodology + CSS tokens + component specs: Layout Specs (board / ruler / three-level plate mounting / horizontal composition), Geometric Specs (G1–G8 + axis formulas), Instrument Specs (exploded frame / gauge / triangle pointer / hatching / giant verdict). **Write your own CSS based on the rules and adjust it to fit the specific needs of the context**. **Read this second.**
- `references/example-twos-complement.html` — two's complement: plate system, punch card (plate-row three-code comparison), trace, blueprint callout; print-family dominant.
- `references/example-virtual-memory.html` — virtual memory: memory map, nested tree, exploded frame, gauge, rail-hang, hatching; blueprint-family assembly.
- `references/example-tcp.html` — TCP three-way handshake: swimlane, state diagram (plate.light), ascii, dialogue, split.
- `references/example-kmp.html` — KMP (complete 408 exam points): archival panel, stepper/step-through, causal chain, ratio bar, warning box, code block (black background + syntax colors), worked exam problems.
- `references/example-maxwell-equations.html` — Maxwell's equations: poster header, timetable, archive card, G5 color field, G7 stair, G8 collage, asym.
- `references/example-photoelectric-effect.html` — photoelectric effect: G1 cut-corner, G3 red circle, gauge (threshold), dialogue, staggered, insight panel, split.
- `references/example-kmp.en.html` — KMP in English: the language & implementation template (same 10 figures, complete teaching notes; no exam-oriented framing).
- `references/example-coverage.md` — component × example coverage matrix (the six Chinese examples together cover all core + extended components; check this matrix before placing a new component).

## Rules Source

All rules live in `references/` as the single source of truth. Read both `references/visual-system.md` (why — layers / axis / geometry semantics) and `references/style-guide.md` (how — tokens / component specs / remediation actions) in full before executing; consult specific sections when in doubt during execution. Numeric rules are authoritative where marked 数值源 (numeric source).

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

- **Exams** (e.g. China's 408 postgraduate entrance, campus recruiting interviews) → activate Exam-Point Teaching.
- **Engineering understanding** → use Teaching Architecture as the primary mode.
- **Cheatsheet** (user explicitly requests) → density-first: one-sentence Essence Hook, skip evolution / system-impact, use data tables, checklists, and compact code blocks as the main body; each item still needs one sentence of causal explanation — dense but not shallow. Cheatsheet = **light-mounting mode**: mounting drops to light level, no giant verdict, no breather, all-dense density, no horizontal composition; the ruler rail stays.

### Step 2: Extract the Causal Chain

In 3–5 sentences: 1) What was broken before? 2) What engineering pressure forced the design? 3) What did the old approach get wrong? 4) How does the new design work? 5) What was gained, what was sacrificed? Write it down before touching any HTML.

### Step 3: Design the Essence Hook

One-two sentences, the simplest useful mental model. See Essence Hook section.

### Step 4: Plan Structure & Coverage

Decide which sections this topic genuinely needs. Not every page needs every section from the Suggested Page Structure. Force a section only when it improves understanding.

Geometry is the mapping result of these annotations (visual-system → Geometry instrument library), never reverse-justified after rendering.

### Step 5: Design Diagrams & Geometry

For each spatial concept choose the diagram type (memory map / timeline / state transition / trace / inline SVG). Choose container geometry (G1–G8), instruments, and layout patterns according to Step 4's annotations — the number of focal points is determined by content semantics, and every focal point must be able to answer "why is the information it focuses on the most important here."

Then write a one-line **form rationale** for each mechanism component: cognitive type → form → what semantic operation the form encodes (e.g. "pointer movement → SVG dual-rail diagram → encodes the main-string pointer's advance and retreat"). A form that degrades into a homogeneous grid array (>16 units distinguished only by color, encoding only arrangement, not movement/direction/transfer/connection) is a failed form — reselect from the existing forms (degraded-form prohibition, see visual-system → Form Validity).

Then run the **mounting decision**: mechanism-class components (diagram / trace / swimlane / punch card / exploded frame) default to full plate mounting (`figure.plate.full` + figure number + caption); archive / dialogue / checklist components stay fluid. **Every mounted plate must be cross-referenced from the prose (see Fig. N) or its caption must state the mechanism conclusion.**

### Step 6: Generate HTML

Build the page. For long documents, use the Large Document Strategy below.

## Large Document Strategy

Build in phases — generating a full-length technical document in one pass inevitably results in truncation and degraded quality.

1. **Scaffold**: `<!DOCTYPE html>` + `<head>` (Font System CDN) + CSS tokens + all section containers with headings + sidebar (if needed) + ruler rail + crop marks + colophon.
2. **Fill sections**: One section at a time: causal explanation → diagram (mounted as plate if mechanism-class) → code (explain why the implementation works this way) → run each paragraph through Signal Density check.
3. **Review**: Does the causal chain flow seamlessly across sections? Do diagrams tie back to the hook? Does the rhythm vary (dense text → diagram → verdict → summary)? Are cross-references, figure numbers, and sidebar anchors correct? Is the knowledge checklist fully covered? Run the 13-item Quality Checklist.

## Output Contract

- Every deliverable is a standalone HTML file starting with `<!DOCTYPE html>` (split into subtopic files when too large; each self-contained and navigable); inline CSS; inline JS only when interaction genuinely aids understanding.
- kebab-case English filenames (`twos-complement.html`, `kmp-algorithm.html`); `<title>` in the page's language.
- Explanations in the requested language; semantic HTML; responsive (single 768px breakpoint).
- Sole external dependency: Google Fonts CDN (see Font System).
- Required Page Header (kicker + title + metadata; standard or poster, see style-guide → Page Header).
- Required construction items: edge ruler rail (≥1100px static ticks with numbers; <1100px numbering taken over by `.sec-num`; **no vertical line, no scroll progress bar** — progress bar only in the sidebar footer), four corner crop marks, print colophon (layout / fonts / palette / figure count / 20° axis).
- Plate convention: `<figure class="plate full|light" id="fig-N">` + `<span class="fig-num">Fig. N</span>` + `<figcaption class="plate-caption">`; prose cross-references with `<a class="fig-ref" href="#fig-N">see Fig. N</a>`.
- Avoid: Markdown-to-HTML conversion, half-finished fragments, pseudo-layout, flat articles without the visual system.

## Font System

| Role | Font | Source |
|------|------|--------|
| Chinese | Noto Sans SC | Google Fonts CDN |
| Latin | IBM Plex Sans | Google Fonts CDN |
| Numerals | Urbanist | Google Fonts CDN |
| Code | Google Sans Code | Google Fonts CDN |

CDN `<link>` goes in `<head>`; the full snippet lives in `references/style-guide.md` → Tokens.

Use `var(--font-num)` for numeric contexts (indices, position markers, pure-number cells). Weight discipline (no hard whitelist): body/labels 400–600; 300 only for large display (poster headlines, giant numerals); 600 only for display giant text (Urbanist / Noto Sans SC), never in body copy; ≤3 weights per screen — weights not declared in the CDN link do not render, so any weight change must be synced to the CDN link.

Windows renders fonts too bold — the following must be in `body`:

```css
body {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-rendering: optimizeLegibility;
}
```

For Latin-only pages you may trim the Noto Sans SC weights from the CDN link to shrink payload (the four-font stack stays the default).

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

## Exam-Point Teaching

For exam contexts, every exam point must be taught in depth, not listed. Activated when Step 1 detects an exam scenario.

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

## Essence Hook

For complex concepts, place a short essence hook before detailed mechanisms. It should be:

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

Criterion: after reading the hook, the reader should hold a reliable concrete model. A hook that offers only conclusions without mechanism, or only terminology without intuition, fails. Later diagrams, examples, and terminology should refer back to this hook.

## Signal Density Rule

Every paragraph should introduce at least one of: engineering constraint / tradeoff / failure mode / system behavior / design consequence / causal relationship / mental model.

Avoid paragraphs that merely restate previous ideas. Remove prose that sounds insightful but does not add new operational understanding.

## Writing Standards

**Prefer**: causal reasoning; mental models; state changes over time; implementation pressure; engineering consequences; cross-concept tensions (abstraction↔control, safety↔flexibility, latency↔throughput, simplicity↔scalability, consistency↔availability).

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
| Strict formal definitions / fixed rules | archival panel (definition tag) |
| Key readings / state / verdict figures | readout |
| Threshold readings (load factor, water level, utilization) | gauge |
| Precise time series | timetable |
| Close-up annotation of a mechanism diagram | blueprint callout |
| Bit patterns / encodings / instruction formats | punch card |
| Part-level decomposition of a mechanism (fields, stack frames, carry chain) | exploded frame |
| Proportion / frequency / distribution | ratio bar |
| Genuine two-dimensional comparison (gain × sacrifice, A × B) | tradeoff / compare / data table |

Specifications in `references/style-guide.md` → Form Specs.

## Visual System & Art Direction

Default is a constructivist technical-editorial style (defer to user preferences when stated). The frame of reference is **plates / engineering drawings / exhibition boards / Soviet statistical graphics** — not posters. Tutorial content (mechanism figures, bit formats, trace walkthroughs, readings) is inherently plate content; content and form are isomorphic.

Core rules (one-line summaries; authoritative specs in the references):

| Discipline | One line | Source |
|---|---|---|
| **Layer model** | Six fixed layers, order never swapped: L0 ground → L1 structure → L2 blueprint (measurable content only) → L3 archive (never adjacent to L2) → L4 white card (sidebar / floating UI / punch holes only) → L5 reds (never surfaces). Thresholds: visual-system → layer model | visual-system |
| **Axis** | Single 20° slant page-wide (measured from horizontal), one direction; cuts only in component bottom breathing areas, **never into text**, never inside figures; body text never slanted; G1 small corner and stamps (rotate(-4deg)) exempt | visual-system → Axis |
| **Instrument tiers** | core instruments always on; extended only when semantics hit, each must pass "what does it measure". **Diversity is the natural result of semantic matching, not a goal** | visual-system → Geometry |
| **Mounting** | Mechanism-class components default to plates (full mount + figure number + caption); **every plate must be cross-referenced from the prose or its caption must state the mechanism conclusion** — an unreferenced plate is decoration | style-guide → Plate Specs |
| **Geometry semantics** | Non-rectangular elements (G1–G8) and instruments chosen by Step 4 semantic annotations, no quotas; repeated identical forms = form not encoding semantic difference; a homogeneous grid (>16 units by color only) is a failed form — reselect | visual-system → Form Validity |
| **Hard geometry** | `border-radius: 0` (two exceptions: punch card holes, G3 circle); asymmetric 4–16px borders, right-angle panels, hard shadows without blur | style-guide → Geometric Specs |

**Visual prohibitions (Avoid)**: gradients, glow, soft bubbles, rounded-corner mind maps, noisy animations, card-stack templates, UI copy that explains its own design (writing prohibitions in Writing Standards).

## Inline Style Policy

Inline `style=""` is only permitted for **one-off micro-adjustments** (non-recurring spacing, font sizes, ratio bar widths, etc.). If the same style appears more than twice, extract it into a CSS class.

## Responsive Design

Single `768px` breakpoint — do not add breakpoints unless the design genuinely breaks at an intermediate width.

At `≤768px`: headings scale down (3xl→2xl, 2xl→xl); giant figures scale down (5rem→3rem); trace cell sizes reduce (2.2rem→1.8rem); multi-column collapses to single column (staggered / plate-row / strip included); sidebar becomes a full-width **vertical** list at the top (never collapse to a horizontal strip); edge ruler collapses (numbering taken over by `.sec-num`); crop marks hidden; wide tables and diagrams scroll horizontally. Standard @media skeleton in style-guide → Responsive Spec.

## Long-Form Reading Support

Alternate dense explanation, diagrams, visual separators, insight blocks, walkthroughs, and concise summaries — rhythmic variation combats reading fatigue. The **skyline rhythm** (breather / standard / dense annotations + giant verdict) is the systematized form of this principle.

Canonical long-form navigation: **left-column sticky table of contents** (click-to-jump + scroll-spy highlighting the active section + red progress bar, specs in style-guide → Sidebar) + **edge ruler rail** (position/numbering, specs in style-guide → Edge Ruler). Short pages get no navigation — navigation does not exist to fill space.

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
12. **Delivery**: Page Header complete (kicker + title + metadata)? `<title>` in the page's language? kebab-case filename? Colophon present (layout / fonts / palette / figure count / 20° axis)?
13. **Rule-driven review (nine checks, screen by screen)** — each with its criterion and remediation:
    - **13-1 Layers**: No non-L0 layers stack directly adjacent; the two reds appear only as lines / dots / small blocks / word-level (never surfaces); ochre sits only on L0; no L4 white cards inside plates; consistent with Step 4 annotations. ochre-blue "adjacency" is judged by bounding-box distance (< gap-md 32px); **"both on screen = violation" is forbidden**. olive (L0 material grade) and the steel structural-surface exceptions (G6 inner / G7 mechanism level) are not layer-order violations — verify against visual-system layer rows L0/L1.
    - **13-2 Axis**: Every slanted element (wedge / section band / kicker / exploded frame / separators / triangle pointers) shares the page axis and direction; cuts never enter text areas; no slants inside mechanism figures; body text never slanted.
    - **13-3 Mounting**: Mechanism-class components mounted per Step 5; tiering sensible (main figure full / secondary light / small items fluid); no decorative extras on plate frames.
    - **13-4 60% density**: At 3–4 scroll positions, visually estimate L1+L2+L3 combined area ≤60% of the viewport. Remediation: verdict back to L0 or unmount.
    - **13-5 Plate references**: Every plate cross-referenced from prose (see Fig. N) or its caption states the mechanism conclusion; unreferenced plates are deleted; the giant verdict must be referenced from the review section (anchor closure).
    - **13-6 Red surfaces**: Verify against style-guide → red-surface thresholds (≥64×64 is a violating surface, ≤1% viewport total, red circle ≤128px sole exception). Remediation: ratio-bar red segments become outlines or ≤24px tall; table headers never red-filled (deep-red text + red left rule).
    - **13-7 White-card scope**: White fill in content areas (trace/swimlane/stepper/ascii/code-block/punch-card/inset/essence-hook/dialogue answers/warning/stair/circle-callout) is a violation; exemptions are exactly three: sidebar, page-level floating UI (incl. G8 collage float), punch holes. Content surfaces follow the four classes in style-guide → white-card scope: mechanism → L2 blueprint / code → ink material face / statement → L0 or olive / archive → L3 ochre band; steel structural-surface exceptions (G6 inner / G7 mechanism level) and the G7 level color ramp (level 3 steel / level 4 ink) per their specs.
    - **13-8 Dark spacing**: Verify against visual-system → prohibitions · dark-spacing table (numeric source): same-layer ≥12px, cross-layer ≥gap-md (32px), plate padding ≥gap-md.
    - **13-9 Form validity**: Every mechanism component must answer "what semantic operation does this form encode" — verify each Step 5 form rationale; a rationale that does not hold sends the form back for reselection (not deletion); a homogeneous grid (>16 units by color only, encoding no movement/direction/transfer/connection) is degenerate. Do not police the number of geometry types — diversity is not the goal; form-semantics correspondence is.
