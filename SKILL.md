---
name: noesis-tutorial
description: Use only when the user asks for a complete, no-build HTML learning page (technical tutorial, concept study page, learning notes, or exam-point review). Conversational "explain X" / Q&A / "tell me about X" requests do NOT trigger this skill; answer them directly. 仅当用户明确要求交付 HTML 学习页面（技术教程、概念精讲、学习笔记、考点精讲页面）时使用；聊天式的“讲讲 X / 解释一下 X”问答不触发本技能，直接回答即可。
---

# noesis-tutorial

## Purpose

Create complete, runnable HTML learning pages that explain why an idea is needed, how it works, where its model breaks, and what the learner can subsequently predict or do. **Write in the language of the user's request.** Produce a designed engineering knowledge product, not a textbook dump, Markdown-to-HTML conversion, or generic summary.

## When NOT to Use

**Default to chat; make the page the exception.** A direct answer must satisfy any request that does not positively authorize a learning page. When the medium is ambiguous, answer briefly and offer once: “需要我把这个整理成 HTML 学习页面吗？” Only an explicit yes starts this workflow. Explicit invocation counts as authorization unless another output format conflicts.

Groups **A / B / C / F veto** the skill. Groups **D / E** select chat by default, but an explicit HTML **Cheatsheet** request may override them. A positive page request must also fit this skill's technical-editorial teaching scope; HTML or styling words alone are insufficient.

### A. Chat-mode Q&A — no deliverable requested

- The user asks 讲讲 / 解释一下 / 介绍一下 X, “what is X”, “how does X work”, or “X 和 Y 有什么区别”.
- The user needs an immediate answer rather than an artifact to keep, reuse, print, or share.
- The message is a follow-up or one-off doubt, even when it concerns a page already built.
- The subject is not a technical or learning topic.

### B. Another output format is requested or implied

- The user names Markdown, plain text, slides, PDF, Word, notebook, mind map, Feishu, Notion, or another format.
- The request is an article, summary, or study note without web-page intent. Use Markdown in chat unless HTML is subsequently confirmed.
- The user requests an attractive or appropriate HTML style without requesting this constructivist technical-editorial language. Build directly in a suitable style unless the learning-page fit is genuine.
- The task is a marketing page, dashboard, portfolio, simple article, or other non-teaching artifact.

### C. Non-teaching work

- Coding, debugging, review, refactoring, tests, implementation, analysis, scaffolding, tooling, Git / DevOps, or architecture proposals do not activate the skill merely because explanation is involved.

### D. Topic too thin for a full teaching arc

- A term lookup, single fact, or definition comfortably answered in a few paragraphs.
- No mechanism, meaningful example, misconception, boundary, or design tension to develop.
- Use an explicitly requested Cheatsheet for compact reference material; do not inflate a thin topic into a full tutorial.

### E. Lightweight / quick intent

- Treat 简单说说 / 大概讲一下 / 不用太细 / keep it simple / short answer as chat intent.
- After explicit HTML confirmation, use Cheatsheet mode rather than performing the full workflow superficially.

### F. Work on existing artifacts

- Handle typo fixes, restyling, rephrasing, a local addition, or questions about an existing page or plan as direct edits or answers, not a full-workflow rerun.

## Teaching Architecture

### Build three levels of explanation

1. **Page arc:** why this topic matters and what understanding it closes.
2. **Concept map:** core concepts, prerequisite dependencies, symbols, and likely misconceptions.
3. **Local explanation:** the teaching beats each core concept actually needs.

Prefer this engineering sequence when applicable: **original problem → constraints / pressure → limited alternatives → working model → mechanism with a concrete worked input → tradeoff → formal definition → system consequence**. Do not force every beat onto every concept.

Adapt causality to the subject instead of inventing engineering history:

- **Engineering:** constraints, failed alternatives, tradeoffs, system effects.
- **Science:** observations, anomalies, consistency requirements, predictions, domains of validity.
- **Mathematics:** representational difficulty, invariants, formalization, counterexamples.
- **Procedures / mechanisms:** inputs, states, transitions, outputs, failure modes.

Use a minimal working definition early when later reasoning depends on it; refine it into a formal definition after intuition. Never delay indispensable terminology merely to obey “definition last.”

### Make the mental model falsifiable and portable

Build the model, use it to make a prediction, test an ordinary example, probe a boundary or counterexample, revise the model, then check transfer to a new case. Include at least one learner action per complete teaching arc: predict an output, choose a mechanism, diagnose an error, or solve a small transfer problem. Do not append mechanical exercises to every section.

Give every analogy its breaking point. Distinguish a concrete constructed input from measured empirical data and illustrative synthetic data.

### Exam-point overlay

Keep the teaching base and overlay exam requirements. For each relevant exam point, include as applicable:

1. **Positioning:** question type, skill demanded, and score weight only when supported by a reliable source. For interviews, describe the assessed skill rather than inventing a weight.
2. **Mechanism and derivation:** trace state changes with concrete input, including the steps on which credit depends.
3. **Misconceptions and traps:** explain why the error is attractive and how to detect it.
4. **Verification and technique:** show a check, efficient method, or mnemonic without replacing understanding.
5. **Connections:** show how the point combines with others.

The end-of-page list is an index, not the lesson. Avoid promises such as “guaranteed full marks” or “free points.”

## Visual Language

Read `references/visual-language.md` before writing CSS. It is the sole visual authority for the aesthetic identity, Invariants, layered form-selection logic, diagram construction, typography, composition, and aesthetic review.

Construct a visual thesis from the learning arc, then construct forms from information relations. Treat 20° geometry, production marks, mounting, breakpoints, and component vocabulary as guided defaults within that system, not quotas. Read only the example closest in **mode + content relation + temperament**:

- `references/example-kmp.html` — exam-dense, blueprint-led.
- `references/example-maxwell-equations.html` — historical arc, poster-led.
- `references/example-photoelectric-effect.html` — threshold mechanism, instrument-led.

Examples demonstrate possibilities; they never override written Invariants.

## Creation Workflow

### Step 0: Establish the learning contract

Infer and record in `plan-<topic>.md`:

```text
学习者 / 先修知识 / 可观察学习结果 / 语言 / 范围与省略 / 模式
核心概念与依赖 / 可能误解 / 普通例 / 边界或失败例 / 迁移任务
```

Ask only when an unresolved choice would materially change the deliverable. Otherwise state a reasonable assumption and proceed.

Select the mode contract:

| Requirement | Teaching | Exam overlay | Cheatsheet |
|---|---|---|---|
| Essence model and boundary | Required | Required | One-sentence model + boundary |
| Page arc and causal explanation | Required; select beats by topic | Required for tested concepts | Compress; declare omitted depth |
| Concrete worked input | Every core mechanism | Every tested derivation | Only high-risk or confusing items |
| Boundary / failure probe | Required per arc | Required per tested model | Include when it prevents misuse |
| Learner action / transfer | At least one per arc | At least one per arc | Optional self-check |
| Review index | Recommended | Required | May form the main body |

### Step 1: Research and build the evidence ledger

Verify before writing:

- Use specifications, official documentation, primary sources, or authoritative scholarship for mechanisms, history, quotations, and exam claims. Record versions when behavior is version-dependent.
- Keep an evidence ledger in the planning file: `claim / type / source or derivation / status / page treatment`.
- Distinguish **verified / derived / illustrative / contested / unverified**. Never present unverified material as fact or label illustrative data as measured.
- Run code with recorded commands, inputs, expected outputs, and relevant boundary cases. Do not equate syntactic plausibility with execution.
- Treat user material as scope evidence, not automatic factual authority. Reconcile differences against versioned sources; explain consequential corrections or version differences.
- Narrow an over-broad topic only with a stated reason. Ask first if narrowing would change the user's goal.

Build the scoped knowledge checklist and map every item to a section or declare its omission. Keep the planning file as the resumable record for the ledger, causal arc, models, annotations, form-selection records, and consequential deviations. Retain it through review; do not automatically delete the only audit trail.

### Step 2: Construct the arc and dependency map

Write a 3–5 sentence page arc: difficulty or question → pressure or evidence → limited prior understanding → working model → consequence and boundary. Order concepts by dependency, inserting just-in-time definitions or prerequisite bridges where needed.

For multi-concept topics, give each core concept a local model rather than stretching one metaphor across the whole page.

### Step 3: Design and test the essence model（本质模型）

Use one or two low-jargon sentences that let the learner reason, not merely remember. Useful strategies include:

- **Physical intuition:** fixed-width two's complement as arithmetic on a finite clock, with overflow as wraparound within that model.
- **Constraint derivation:** show how a mechanism follows from explicit assumptions rather than calling it inevitable.
- **Appearance versus operation:** distinguish what a system appears to do from the state transition it actually performs.
- **Predictive compression:** choose the model that correctly predicts several cases with the fewest necessary ideas.

Write the model's domain and breaking point beside it. Test it against the planned ordinary, boundary, and transfer cases. A memorable statement that predicts incorrectly fails.

### Step 4: Orchestrate semantics and aesthetics

Decide which sections the learning arc needs. For each section and consequential figure, record the form-selection triple from visual-language §3.2:

```text
读者问题 / 主要学习操作 / 信息关系与证据状态
```

Add narrative state, intensity, and reading role only where they change material or composition. Then write the one-sentence visual thesis from §3.1 and determine the reading route, page roles, material transitions, and density rhythm before choosing components.

Ensure that substantive prose advances a mechanism, relation, constraint, prediction, boundary, or consequence. Exempt captions, transitions, scope notes, and genuine synthesis from mechanical “one insight per paragraph” accounting; remove repetition wherever it occurs.

Choose navigation from page length, structure, and lookup needs, not a section-count threshold. Decide splitting from learning goals and delivery intent, not line or figure counts.

### Step 5: Select forms and construct diagrams

Follow visual-language §3.3. Select by layer, not by component name: **reader operation → information relation and evidence → encoding family → container and rhetorical overlay**. Do not begin with a name from the form vocabulary.

For each consequential figure, declare one primary operation and at most one supporting operation. If a figure is asked to perform more than two distinct operations, split it or narrow its purpose. A secondary overlay must add a different interpretive move, not restate the encoding.

Compare materially different candidates only when the relation admits more than one encoding family, a candidate adds interaction or substantial visual mass, or the narrow/no-JS variant changes the learning operation. Candidates must differ in information geometry, not merely styling. Otherwise use the canonical family and keep the decision lightweight.

Eliminate candidates that fail truth or evidence requirements, accessibility or legibility, complete no-JS reading, or viable narrow-screen recomposition. Among survivors, prefer exact operation match, then lower cognitive and interaction cost, then aesthetic and compositional effect, then expressive novelty.

Treat aesthetic effect as a positive criterion: clarity of the visual thesis, hierarchy, material contrast, rhythm, and fit with the page. Reuse is a fallback only when it matches the current aesthetic effect, not an automatic priority. Novelty may decide among operationally comparable forms and may justify a new or differentiated form when it materially strengthens the visual argument without avoidable cognitive cost.

Apply the form budget from visual-language §3.3: one primary form per learning turn and one primary encoding per relation. A new or differentiated form may replace an operationally adequate one when it preserves the operation and materially improves the aesthetic argument. For each primary form, record the reader question, operation, relation and evidence, chosen and rejected candidates, aesthetic or novelty gain, container and overlay, no-JS/narrow variant, and validation question. Minor forms need one sentence.

For diagrammatic forms, convert the selected form into the diagram brief in visual-language §3.4 before markup: inference, entities/states/quantities, relations and direction, evidence provenance, boundary/failure/comparison case, omitted detail, channel and scale mapping, units, labels, no-JS/narrow variant, and read-off question. Verify spatial semantics before styling; no aesthetic gesture may alter scale, order, overlap, or direction.

After rendering, test each primary form by removal, by reading the figure without its explanatory prose, and against a simpler alternative. If the operation survives its removal, retain the figure only when it performs necessary compositional or rhetorical work. If the figure cannot support the operation alone, it does not encode the relation. If a simpler form preserves both the operation and the intended aesthetic effect, prefer it. Never add diagrams or colored grids merely to satisfy a variety quota.

### Step 6: Generate and revise incrementally

Write the scaffold, then complete and re-read one section at a time. Before cross-section edits, inspect the affected concept, figure, and anchor dependencies. Resume from the planning file and the first incomplete section after interruption. Rebuild only when corruption or a foundational model error makes repair less reliable.

## Editorial Standards

- Prefer precise verbs, explicit state changes, earned causal connectives, and qualifications tied to actual assumptions.
- Separate fact, derivation, interpretation, analogy, and speculation. Use “always,” “inevitable,” “optimal,” “essence,” and “proven” only when their scope is demonstrated.
- Make parallel ideas grammatically parallel. Vary sentence length for emphasis without turning explanation into slogans.
- Introduce terminology once, reuse it consistently, and use bilingual labels only when they aid understanding.
- Make headings promise a defensible idea and captions reveal a relation. Remove hollow motivation, false profundity, tautology, and decorative rhetoric.
- Explain why code exists, why a simpler alternative is insufficient, and how its state changes. Keep examples compatible with the declared version.

## Large Document Strategy

Split at Step 4 only when at least two independently useful learning goals, complete arcs, or delivery contexts justify separate files. Honor an explicit single-file request unless it prevents a usable result; discuss that conflict before changing scope.

Keep each file self-contained in teaching logic, with its own model, closure, header, figure numbering, and production note. Use a `<kebab-case-topic>/` folder and descriptive kebab-case English filenames. Maintain series-level coverage and prerequisite order in the planning file. In the delivery response, list the recommended reading order, each file's scope, and declared omissions; do not force an index page or cross-file navigation.

## Output Contract

- Deliver single-file, no-build HTML beginning with `<!DOCTYPE html>`, with inline CSS and minimal inline JS only when interaction aids learning. Use `<kebab-case-topic>.html`, or the topic folder for a split series, and report the path(s).
- Use semantic HTML, the correct `lang`, a `<title>` in the page language, descriptive filenames, and a header that states title, discipline, and scope without inventing metadata.
- Preserve complete no-JS reading, keyboard operation, visible focus, responsive recomposition, and readable font fallbacks. Honor an offline request with local or bundled resources.
- Avoid runtime dependencies. Google Fonts is the default optional exception; do not describe a network-dependent page as offline-self-contained.
- Use visual-language defaults for breakpoints, mounting, production marks, and colophon. Complete the delivery checks rather than satisfying a component inventory.

## Delivery Self-Check

Use four gates. Fix failures at their source instead of adding compensating decoration or repeating the same checklist.

### Gate A — Learning and scope

Confirm the mode contract, learner assumptions, dependency order, checklist-to-section mapping, declared omissions, model boundary, and planned learner action. Verify that the page teaches rather than merely indexes its content.

### Gate B — Evidence and correctness

Confirm that consequential claims have an appropriate evidence status, historical and exam claims are traceable, constructed and measured data are distinguished, and code was actually run with expected outputs and relevant boundaries. Resolve contradictions between prose, figures, and interaction. For diagrams and charts, verify spatial semantics, units, baselines, scale transformations, uncertainty, data status, and provenance. No position, length, overlap, arrow, or color may imply a relation or precision unsupported by the evidence.

### Gate C — Artifact smoke test

Open the rendered HTML and check parsing, console errors, IDs, anchors, figure references, controls, and production-note values. Test no-JS reading, keyboard focus, font fallback, 200% zoom, 320px reflow, and any necessary two-dimensional scrolling. For complex diagrams, provide a short identifier plus a visible long description or caption that conveys the essential structure, values, and conclusion; do not hide the description from sighted readers or rely on color alone. Proofread and fix known language errors.

### Gate D — Visual and semantic validity

Verify every visual-language Invariant. Confirm the selection chain for primary forms: reader question, primary operation, relation and evidence, triggered candidate comparison, and no-JS/narrow variant. Check that one primary form owns each learning turn and no second form repeats the same relation. Apply removal, prose-removal, and simpler-alternative tests; retain a figure with no remaining learning operation only when it performs specific compositional or rhetorical work. Confirm that aesthetic effect and novelty were weighed as positive criteria after hard gates, not used as decorative excuses. For diagrammatic forms, run the read-off, false-inference, boundary, label-recovery, scientific-integrity, and accessibility checks from visual-language §3.4; the strongest gesture must land on the primary inference. Then inspect the rendered page using its three-distance aesthetic review: the visual thesis is visible, the main learning turn owns the strongest gesture, each consequential form reveals its relation, and narrow screens preserve the reading route. Record consequential deviations and their semantic or compositional gain.
