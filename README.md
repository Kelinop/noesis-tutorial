# noesis-tutorial

[![License: MIT](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)

An **agent skill** that turns technical topics into designed engineering knowledge pages — complete, runnable HTML learning notes in a constructivist technical-editorial style. Not a textbook dump, not a Markdown-to-HTML conversion.

Pages are written in the language of the request — English, Chinese, or any other.

## Live preview

This is what the skill produces. Every example is a standalone HTML file — click to open it in your browser (rendered via [htmlpreview](https://htmlpreview.github.io/)):

| Example | Topic | Highlights |
|---|---|---|
| [KMP (English) — flagship](https://htmlpreview.github.io/?https://github.com/Kelinop/noesis-tutorial/blob/main/references/example-kmp.en.html) | Complete KMP teaching | English language & implementation template, all components |
| [Two's complement](https://htmlpreview.github.io/?https://github.com/Kelinop/noesis-tutorial/blob/main/references/example-twos-complement.html) | 补码 | Punch cards, carry trace, clock-face hook |
| [Virtual memory](https://htmlpreview.github.io/?https://github.com/Kelinop/noesis-tutorial/blob/main/references/example-virtual-memory.html) | 虚拟内存 | Memory map, nested tree, exploded frame, TLB gauge |
| [TCP handshake](https://htmlpreview.github.io/?https://github.com/Kelinop/noesis-tutorial/blob/main/references/example-tcp.html) | TCP 握手 | Swimlanes, state diagram, ASCII header, dialogue |
| [KMP — 408 exam points](https://htmlpreview.github.io/?https://github.com/Kelinop/noesis-tutorial/blob/main/references/example-kmp.html) | KMP 全 408 考点 | Interactive stepper, causal chain, ratio bar |
| [Maxwell's equations](https://htmlpreview.github.io/?https://github.com/Kelinop/noesis-tutorial/blob/main/references/example-maxwell-equations.html) | 麦克斯韦方程组 | Poster header, timetable, archive cards, stair groups |
| [Photoelectric effect](https://htmlpreview.github.io/?https://github.com/Kelinop/noesis-tutorial/blob/main/references/example-photoelectric-effect.html) | 光电效应 | Gauge, red circle, dialogue, SVG apparatus |

The six Chinese examples together cover every component in the visual system; the English example demonstrates the same system in English.

## What it produces

- Standalone HTML pages, zero build tools, one external dependency (Google Fonts CDN)
- Causal-chain teaching: problem → pressure → failed approach → essence hook → mechanism (real-data worked examples) → tradeoff → definition → system impact
- A complete visual system: layer-based color model (L0–L5), 20° axis, plate mounting, gauges, punch cards, swimlanes, trace grids, dialogues, stair groups — 40+ encoded components
- Exam-point deep teaching (e.g. 408 postgrad entrance exams): positioning, derivations, traps, speed tricks, related topics
- 13-item quality checklist enforced before delivery

## Install

This is an Agent Skill (`SKILL.md` + `references/`). Copy the repository into your agent's skills directory:

```bash
# Claude Code / Claude Desktop
cp -r noesis-tutorial ~/.claude/skills/
# Cursor, Windsurf, or other agents that read .claude/skills
# or keep it project-local:
cp -r noesis-tutorial .claude/skills/
```

Any agent that reads `SKILL.md` can use it — the skill is just rules and examples.

## Activation

The skill activates when a request matches the frontmatter description:

```yaml
name: noesis-tutorial
description: Use when the user asks for technical tutorials, concept explanations,
  learning notes, or exam-point study material, to be delivered as HTML learning pages.
  当用户请求技术教程、概念讲解、学习笔记或考点精讲，需交付 HTML 学习页面时使用。
```

You can also invoke it explicitly by name.

## Usage

Ask for a technical topic as a learning page:

- "Write a complete study note on KMP with full exam points"
- "Explain how TCP's three-way handshake works, as an HTML page"
- 「写一份虚拟内存的学习笔记，要 HTML 页面」

The agent runs the 7-step workflow in `SKILL.md` (research → causal chain → essence hook → structure → diagrams → HTML → quality checklist), then verifies against the 13-item checklist. Pages are standalone — open the HTML directly in a browser.

## Repository layout

```
SKILL.md                        # Workflow: when to use, 7-step creation, teaching architecture, 13-item checklist
references/
  visual-system.md              # Design philosophy: layer model, axis, geometry semantics, composition
  style-guide.md                # Tokens + component specs — the rule source for every class name
  example-*.html ×6             # Six Chinese example pages — component coverage & teaching samples
  example-kmp.en.html           # English flagship example (component-heavy, complete teaching notes)
  example-coverage.md           # Component × example coverage matrix
```

- **Execution inputs**: SKILL.md + visual-system.md + style-guide.md + examples + coverage matrix.

## License

MIT — see [LICENSE](LICENSE).
