---
name: noesis-tutorial
description: Use only when the user asks for a learning artifact — a complete, self-contained HTML learning page (technical tutorial, concept study page, learning notes, exam-point review material). Conversational "explain X" / Q&A / "tell me about X" requests do NOT trigger this skill; answer them directly. 仅当用户明确要求交付 HTML 学习页面（技术教程、概念精讲、学习笔记、考点精讲页面）时使用；聊天式的"讲讲 X / 解释一下 X"问答不触发本技能，直接回答即可。
---

# noesis-tutorial

## Purpose

Create complete, runnable HTML learning pages for technical topics — pages that teach why a concept exists, what engineering pressure shaped it, how it works, what it trades off, and how it connects to broader system design. **Write the page in the language of the user's request** (no default fallback). The result should feel like a designed engineering knowledge product, not a textbook dump, Markdown-to-HTML conversion, or generic summary. If the content is too large for one file, split by teaching arc — see Large Document Strategy.

## When NOT to Use

**Default posture: the chat answer is the default; the page is the exception.** This skill exists only to produce a complete, designed HTML learning artifact. Any request that a direct explanation can satisfy must be answered directly — "the user asks to have a concept explained" alone never triggers the skill.

**Decision rule: a match in any group below vetoes the skill; beyond that, invoking the skill requires a positive fit** — the task must genuinely suit this skill's learning-page scope and constructivist style, not merely involve HTML or styling words. When the mode is ambiguous (conversational vs. deliverable), do NOT build a page to resolve the ambiguity — answer briefly in chat and offer once ("需要我把这个整理成 HTML 学习页面吗?"). Only an explicit yes starts the workflow.

### A. Chat-mode Q&A — no deliverable requested

- The user asks to 讲讲 / 解释一下 / 介绍一下 X, or asks "what is X", "how does X work", "X 和 Y 有什么区别" — in-chat explanation is the expected medium, regardless of how deep a full treatment would be.
- The user wants to understand something right now (reading a doc, interview prep, a homework doubt) rather than obtain material to keep / reuse / print / share.
- The message is a follow-up question or a one-off doubt in an ongoing conversation — answer it directly even when it concerns the very topic a page was or would be built for.
- The subject is not a technical / learning topic (general advice, opinion, news, life questions) — no page, no skill.

### B. Another output format is requested or implied

- The user names a format: Markdown / md, plain text, slides / PPT / PDF / Word, Jupyter notebook, 思维导图, 飞书 / Notion doc, etc.
- The request is "写一篇 X 的文章 / 总结 / 学习笔记" without web-page intent — produce Markdown text in chat unless the user then confirms they want an HTML page.
- The user asks for an HTML page with a suitable / beautiful / appropriate style ("用合适的页面风格", "排版好看一点", "做个漂亮的页面", "style it nicely") — this skill is one candidate style among many, never a requirement. Invoke it only when the task genuinely fits this skill's constructivist technical-editorial learning-page style (a technical concept taught at full depth). Otherwise build the page directly in an appropriate way WITHOUT this skill.
- The skill's visual system must not be forced onto pages that do not fit it (marketing / landing pages, dashboards, portfolios, simple article pages, non-teaching notes) merely because they are HTML and mention style — those are built directly, with the style the task calls for.

### C. Non-teaching work

- Coding, debugging, error diagnosis, code review, refactoring, test writing, algorithm implementation, performance / data analysis, project scaffolding, tooling, git / DevOps questions, architecture proposals — the skill does not apply even when the task involves explaining something along the way.

### D. Topic too thin — judged by content, not by wording

- A one-sentence fact or term lookup: a definition fitting in ≤3 sentences (e.g. "什么是乐观锁"), a keyword gloss, a single data point.
- No mechanism to walk through step by step, no worked example with real data, no engineering pressure / failure mode / tradeoff dimension to unpack.
- The full causal treatment of the topic fits comfortably in a few chat paragraphs — a designed page would unlock no additional depth.

### E. Lightweight / quick intent

- The user asks 简单说说 / 大概讲一下 / 不用太细 / keep it simple / rough overview / short answer — treat as chat mode; an HTML page is not "still confirmed" merely because the topic is technical.
- Only an explicit confirmation that a page is wanted starts the skill — and the sole permitted lightweight variant is then Cheatsheet mode (Step 0), a deliberate density mode. A "quick HTML page" that is the full workflow done sloppily is forbidden.
- The heavier the implied workflow, the more explicit the user's page intent must be. 普通的一句"帮我讲讲 X"不等于页面授权。

### F. Work on existing artifacts

- Typo fixes, restyling, rephrasing, adding one section to, or questions about an already-delivered page or its `plan-<topic>.md` — handle as a direct edit / direct answer, not a full-workflow rerun.

## Teaching Architecture

Explain concepts as causal chains, not terminology lists. For each major concept, prefer this sequence:

1. **Original problem** — what was broken before? What could the old approach not solve?
2. **Engineering pressure** — cost, scale, latency, security, compatibility, complexity, hardware constraints.
3. **Failed or limited older solutions** — what the prior approach got wrong.
4. **Essence model** — a concise, physically intuitive statement of the design's essence (delivered on-page as the essence hook).
5. **Mechanism** — how it works, step by step; **must include a worked example with real data** — pure abstract description is not acceptable.
6. **Tradeoff** — what was gained, what was sacrificed.
7. **Formal definition** — precise terminology only after intuition is established.
8. **System impact** — what it changed, enabled, complicated.

Rules:

- Structure emerges from topic — do not force every beat onto every page.
- **Analogies must declare their breaking point**: "This model breaks at X, because Y" — the breaking point is itself a teaching point.
- **Coverage**: cross-check every item on the knowledge checklist; omissions must be declared at the top of the page.
- Definitions make earlier intuition precise — never open with a definition, unless the user explicitly wants reference-style.

## Exam-Point Teaching

When Step 0 detects an exam context (e.g. 408 考研, campus recruiting interviews), exam points are overlaid on the teaching base — every exam point taught in depth, never listed. Each must include:

1. **Exam positioning**: how it is tested, score weight.
2. **Mechanism walkthrough**: step-by-step operation with concrete data.
3. **Manual derivation**: trace every state change with real input, never just the final result.
4. **Common traps**: what students get wrong, why, and how to avoid it.
5. **Exam techniques**: speed methods, mnemonics, verification strategies.
6. **Related points**: how this point combines with others in one question.

Forbidden: listing point names without explanation; unexplained bullet lists of exam points; textbook text copied without derivation and examples. The end-of-page review list may be a bullet list — the list is an index, not content; the body must already have completed the full teaching of every point.

## Visual Language

`references/visual-language.md` is the single visual reference: philosophy, **Invariants** (§2 — the only non-negotiable rules: L0–L5 layer semantics, dual-red division, stacking/contrast bans, red-surface threshold, 60% breathing rule, single 20° axis, material-texture bans), the generative grammar (semantic annotation → narrative state → form construction), a form vocabulary, composition heuristics, and deviable defaults. **Read it before writing CSS.** Only the Invariants are absolute; everything else is a default you may deviate from when you can state the semantic gain. Three example pages are the living demonstrations — before building a new page, read the one closest in temperament:

- `references/example-kmp.html` — exam-dense, blueprint family: real-data trace, stepper, alignment diagram, archival panels.
- `references/example-maxwell-equations.html` — poster header, geometric freedom: ochre timeline, G7 stair, mirrored composition, G8 collage.
- `references/example-photoelectric-effect.html` — short verdict, dialogue, instruments: red sun, threshold gauge, stance dialogue.

## Creation Workflow

### Step 0: Determine Context

- **Teaching is the base**: unless the user explicitly requests a cheatsheet, the Teaching Architecture is the backbone.
- **Exam context is an overlay, not a separate track**: keep the teaching backbone and apply Exam-Point Teaching on top; the knowledge checklist becomes the exam-point list.
- **Cheatsheet** (explicit user request only) is a density mode: one-sentence essence hook, tables / checklists / compact code as the main body, each item still carrying one causal sentence — dense but not shallow. Mechanism figures mount light (no frame), no giant verdict, every section dense; skipped beats declared at the top; the Delivery Self-Check still applies.

### Step 1: Research & Inventory

**Verify before writing** — technical tutorials lose credibility on a single wrong detail:

- **Mechanism**: official documentation, specifications, authoritative sources; never infer internal behavior from surface API.
- **History**: real context, no invented dates or names — if unsure, state the pressure without the narrative.
- **Code**: syntactically correct and runnable; no mixing APIs across incompatible versions.
- **Tradeoffs**: real, not plausible-sounding inventions; if debatable, present as design tension.

Too broad to research thoroughly → narrow the scope and explain why.

Build the **knowledge checklist** scoped by Step 0 (exam → exam-point list with question types and weights; engineering → mechanism / history / tradeoffs / code; cheatsheet → fact sheet). The page structure must address every item or declare the omission; the end-of-page takeaways map back to each item. User-provided material defines the scope boundary but does not waive verification — correct its errors against authoritative sources and note the corrections on the page.

Write planning artifacts to `plan-<topic>.md` as they are produced (causal chain, essence model, annotated section plan, form rationales) — the resumable planning record; do not start the HTML without it. Delete the file after delivery: it is a temporary construction record, not a deliverable.

### Step 2: Extract the Causal Chain

In 3–5 sentences: what was broken → what engineering pressure forced the design → what the old approach got wrong → how the new design works → what was gained and sacrificed. Write it down before touching any HTML.

### Step 3: Design the Essence Model

The simplest useful mental model of the design: one or two sentences, in the page's language, low-jargon, problem-oriented, memorable enough to guide the rest of the explanation. Four patterns:

- **Replace definition with physical intuition** — a concrete model the reader can directly visualize (two's complement as a clock face).
- **Reframe an arbitrary mechanism as an inevitable consequence** — the direct outcome of a constraint (O(1) holds because of the load-factor threshold, not by luck).
- **Distinguish appearance from essence** — on the surface it does X; at its core it is Y.
- **Derive the design from its constraints** — TCP's three-way handshake is the mathematical minimum for bidirectional confirmation: one fewer is unsafe, one more is redundant.

Criterion: after reading the hook, the reader holds a reliable concrete model; a hook of conclusions without mechanism, or terminology without intuition, fails. Later diagrams, examples, and terminology tie back to it.

### Step 4: Semantic Orchestration

Decide which sections this topic genuinely needs — force a beat only when it improves understanding; the R1–R4 composition precedents (visual-language §6) are starting points, not templates. Then annotate each section and diagram unit (internal design note, not reader-facing):

```text
[教学动作] [信息关系] [叙事状态] [强度] [证据属性] [阅读角色]
```

From the annotations determine: page role per unit (定位 / 定锚 / 展示 / 拆解 / 对照 / 转场 / 高潮 / 闭环 — check for missing or duplicated roles); density rhythm (breather / standard / dense); material transitions across L0 → L2 → L3 → L5, each explainable by section semantics.

**Signal density**: every paragraph introduces at least one of — engineering constraint / tradeoff / failure mode / system behavior / design consequence / causal relationship / mental model. Cut paragraphs that merely restate.

**Long-form judgment**: ≥4 top-level sections → left-column sticky TOC; shorter pages get no sidebar. **Split judgment**: a plan decomposing into ≥2 complete teaching arcs → multi-file split (Large Document Strategy).

### Step 5: Form Construction

Construct forms from the annotation, not from a catalog — the form vocabulary (visual-language §5) is the candidate space, not its border; build new forms freely when none fits. For each mechanism unit write a one-line **form rationale**: `信息关系 → 形式 → 该形式编码了什么语义操作`. A form degraded into a homogeneous grid array (>16 units distinguished only by color, encoding no movement / direction / transfer / connection) is invalid — reselect, don't delete. Check combination relations (协同 / 替代 / 冲突) and the one-strong-form-per-page discipline (one giant verdict, one wedge, each red gesture at most once). Tables are only for genuine two-dimensional lookups. Mechanism figures default to full plate mounting; **every plate must be cited from prose (见图 N / see Fig. N) or carry the mechanism conclusion in its caption**.

### Step 6: Generate HTML

Build the page per the Output Contract. Write the scaffold first (`<!DOCTYPE html>` + `<head>` + CSS tokens + section containers), then fill one section at a time — never hold more than one section in memory. If interrupted, re-read `plan-<topic>.md` and the partial file and continue from the first incomplete section — never regenerate from scratch.

**Writing standards** — prefer: causal reasoning; mental models; state changes over time; engineering consequences; cross-concept tensions (abstraction↔control, safety↔flexibility, latency↔throughput, simplicity↔scalability, consistency↔availability). Avoid: definition-first writing; hollow motivation; textbook tone; intuition-free jargon stacking; false profundity; tautology; mechanical Markdown conversion; decorative SaaS styling. Code examples must explain why the implementation exists, why simpler alternatives fail, and how state changes step by step.

## Large Document Strategy

Split at **Step 4 planning time, from content semantics — never from a line count**:

- **One file = one complete teaching arc**: its own problem → pressure → mechanism → tradeoff closure, its own essence model, its own figure cluster (≈3+ plates). Never split mid-arc or inside a section; a long single-arc topic stays in one file, carried by the density rhythm. Exam mode: exam points group into independently teachable clusters, each still taught in depth — splitting is not an excuse for listing.
- Create a `<kebab-case-topic>/` folder and write one self-contained HTML per arc, named for its subtopic in kebab-case English. Each file fully satisfies the Output Contract (figure numbers from 1, own page header and colophon). No series-level numbering, index file, or cross-file navigation.

## Output Contract

- Every deliverable is a standalone HTML file starting with `<!DOCTYPE html>`; inline CSS; inline JS only when interaction genuinely aids understanding (progressive enhancement — the page reads complete without JS). Write to `<kebab-case-topic>.html` in the working directory (split series → the topic folder); report the path(s) when done.
- kebab-case English filenames; `<title>` in the page's language; semantic HTML; single `768px` responsive breakpoint.
- Sole external dependency: Google Fonts CDN (font stack in visual-language §7).
- Required: page header (kicker + title + metadata) and production signatures — crop marks, edge ruler, colophon (visual-language §3.7); the colophon is never omitted.
- Inline `style=""` only for one-off micro-adjustments; a style appearing more than twice becomes a class.
- Avoid: Markdown-to-HTML conversion, half-finished fragments, pseudo-layout, flat articles without the visual language.

## Delivery Self-Check

Verify before delivery. Content items are blocking; visual items reduce to the Invariants plus semantic validity — not a numeric audit.

**Content (blocking)**

1. **Causal chain**: every major concept walks problem → pressure → mechanism → tradeoff; essence model present with later content tying back; analogies declare their breaking point.
2. **Coverage**: knowledge checklist fully covered or omissions declared; end-of-page takeaways map back to every item.
3. **Signal density**: ≥1 new operational insight per paragraph; every mechanism paired with a real-data worked example.
4. **Facts**: mechanism, history, and code verified; code runnable; tradeoffs bidirectional.
5. **Exam depth** (if applicable): each exam point taught (mechanism + derivation + trap), not listed.
6. **Delivery**: page header complete; `<title>` in the page language; kebab-case filename; colophon present; no typos.

**Visual (blocking — the Invariants)**

7. Every invariant in visual-language §2 holds: L0–L5 layer semantics and color values, dual-red division, stacking/contrast bans, red-surface threshold, 60% breathing rule, single 20° axis (never inside mechanism figures, body text never slanted), no forbidden materials (gradients / glow / soft shadows / rounded containers).

**Semantic validity**

8. Every mechanism form answers "what does this encode" — each Step 5 form rationale holds; failures go back for reselection, not deletion; no degenerate grid arrays. Every plate is cited from prose or self-concluding in its caption. Deviation from any default is stated with its semantic gain.
