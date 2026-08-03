<div align="center">

<pre style="font-family: 'IBM Plex Mono', monospace; line-height: 1.2;">
╔══════════════════════════════════════════════════════════════╗
║                                                              ║
║   ███╗   ██╗ ██████╗ ███████╗███████╗██╗███████╗            ║
║   ████╗  ██║██╔═══██╗██╔════╝██╔════╝██║██╔════╝            ║
║   ██╔██╗ ██║██║   ██║█████╗  ███████╗██║███████╗            ║
║   ██║╚██╗██║██║   ██║██╔══╝  ╚════██║██║╚════██║            ║
║   ██║ ╚████║╚██████╔╝███████╗███████║██║███████║            ║
║   ╚═╝  ╚═══╝ ╚═════╝ ╚══════╝╚══════╝╚═╝╚══════╝            ║
║                                                              ║
║           T U T O R I A L   ·   S K I L L                    ║
║                                                              ║
╚══════════════════════════════════════════════════════════════╝
</pre>

<h3>Turn technical topics into designed engineering knowledge pages</h3>

<p>Complete, runnable HTML learning notes in a <strong>constructivist technical-editorial style</strong>.<br>
Not a textbook dump. Not a Markdown-to-HTML conversion.</p>

<p>
  <a href="LICENSE"><img src="https://img.shields.io/badge/license-MIT-0f4c81?style=flat-square" alt="License: MIT"></a>
  <img src="https://img.shields.io/badge/style-constructivist-1c1c1c?style=flat-square" alt="Style: Constructivist">
  <img src="https://img.shields.io/badge/output-standalone_HTML-e63946?style=flat-square" alt="Output: Standalone HTML">
  <img src="https://img.shields.io/badge/build-zero-b8863b?style=flat-square" alt="Build: Zero">
</p>

<p><a href="README.zh-CN.md">简体中文</a> · <a href="#live-preview">Live Preview</a> · <a href="#install">Install</a> · <a href="#usage">Usage</a></p>

<br>

<a href="https://htmlpreview.github.io/?https://github.com/Kelinop/noesis-tutorial/blob/main/references/example-kmp.en.html">
  <img src="assets/preview-kmp.png" alt="KMP Algorithm — noesis-tutorial preview" width="720">
</a>

<p><em>KMP Algorithm: The Main-String Pointer Never Backtracks — <a href="https://htmlpreview.github.io/?https://github.com/Kelinop/noesis-tutorial/blob/main/references/example-kmp.en.html">open in browser →</a></em></p>

</div>

---

## Live preview

This is what the skill produces. Every example is a standalone HTML file — click to open it in your browser (rendered via [htmlpreview](https://htmlpreview.github.io/)):

| # | Example | Topic | Highlights |
|:---:|:---|:---|:---|
| 01 | [KMP (English) — flagship](https://htmlpreview.github.io/?https://github.com/Kelinop/noesis-tutorial/blob/main/references/example-kmp.en.html) | Complete KMP teaching | English language & implementation template, all components |
| 02 | [Two's complement](https://htmlpreview.github.io/?https://github.com/Kelinop/noesis-tutorial/blob/main/references/example-twos-complement.html) | 补码 | Punch cards, carry trace, clock-face hook |
| 03 | [Virtual memory](https://htmlpreview.github.io/?https://github.com/Kelinop/noesis-tutorial/blob/main/references/example-virtual-memory.html) | 虚拟内存 | Memory map, nested tree, exploded frame, TLB gauge |
| 04 | [TCP handshake](https://htmlpreview.github.io/?https://github.com/Kelinop/noesis-tutorial/blob/main/references/example-tcp.html) | TCP 握手 | Swimlanes, state diagram, ASCII header, dialogue |
| 05 | [KMP — 408 exam points](https://htmlpreview.github.io/?https://github.com/Kelinop/noesis-tutorial/blob/main/references/example-kmp.html) | KMP 全 408 考点 | Interactive stepper, causal chain, ratio bar |
| 06 | [Maxwell's equations](https://htmlpreview.github.io/?https://github.com/Kelinop/noesis-tutorial/blob/main/references/example-maxwell-equations.html) | 麦克斯韦方程组 | Poster header, timetable, archive cards, stair groups |
| 07 | [Photoelectric effect](https://htmlpreview.github.io/?https://github.com/Kelinop/noesis-tutorial/blob/main/references/example-photoelectric-effect.html) | 光电效应 | Gauge, red circle, dialogue, SVG apparatus |

The six Chinese examples together cover every component in the visual system; the English example demonstrates the same system in English.

## What it produces

| Feature | Description |
|:---|:---|
| **Standalone HTML** | Zero build tools. One external dependency: Google Fonts CDN. Open in any browser. |
| **Causal-chain teaching** | Problem → Pressure → Failed approach → Essence hook → Mechanism (real-data worked examples) → Tradeoff → Definition → System impact |
| **Visual system** | Layer-based color model (L0–L5), 20° axis, plate mounting, gauges, punch cards, swimlanes, trace grids, dialogues, stair groups — **40+ encoded components** |
| **Exam-point depth** | 408 postgrad entrance exams: positioning, derivations, traps, speed tricks, related topics |
| **Quality gate** | 13-item checklist enforced before every delivery |

<a name="install"></a>
## Install

This is an **Agent Skill** (`SKILL.md` + `references/`). Copy the repository into your agent's skills directory:

```bash
# Claude Code / Claude Desktop
cp -r noesis-tutorial ~/.claude/skills/

# Cursor, Windsurf, or other agents that read .claude/skills
cp -r noesis-tutorial .claude/skills/
```

Any agent that reads `SKILL.md` can use it — the skill is just rules and examples.

## Activation

The skill auto-activates when a request matches the frontmatter description:

```yaml
name: noesis-tutorial
description: Use when the user asks for technical tutorials, concept explanations,
  learning notes, or exam-point study material, to be delivered as HTML learning pages.
  当用户请求技术教程、概念讲解、学习笔记或考点精讲，需交付 HTML 学习页面时使用。
```

Or invoke it explicitly by name.

<a name="usage"></a>
## Usage

Ask for a technical topic as a learning page:

> **"Write a complete study note on KMP with full exam points"**
>
> **"Explain how TCP's three-way handshake works, as an HTML page"**
>
> **「写一份虚拟内存的学习笔记，要 HTML 页面」**

The agent runs the **7-step workflow** in `SKILL.md`:

```
Research → Causal chain → Essence hook → Structure → Diagrams → HTML → Quality checklist
```

Then verifies against the **13-item checklist**. Pages are standalone — open the HTML directly in a browser.

## Repository layout

```
noesis-tutorial/
├── SKILL.md                        # Workflow: when to use, 7-step creation, teaching architecture, 13-item checklist
├── references/
│   ├── visual-system.md            # Design philosophy: layer model, axis, geometry semantics, composition
│   ├── style-guide.md              # Tokens + component specs — the rule source for every class name
│   ├── example-*.html × 6          # Chinese example pages — component coverage & teaching samples
│   ├── example-kmp.en.html         # English flagship example (component-heavy, complete teaching notes)
│   └── example-coverage.md         # Component × example coverage matrix
├── README.md                       # This file
├── README.zh-CN.md                 # 简体中文版本
└── LICENSE                         # MIT License
```

**Execution inputs**: `SKILL.md` + `visual-system.md` + `style-guide.md` + examples + coverage matrix.

---

## License

[MIT](LICENSE) © Kelinop
