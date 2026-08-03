# noesis-tutorial


A skill that turns technical topics into **designed engineering knowledge pages** — HTML learning notes in a constructivist technical-editorial style , not textbook dumps.

Pages are written in the language you ask for on request.

## What it produces

- HTML pages, zero build tools, one external dependency (Google Fonts CDN)
- Causal-chain teaching: problem → pressure → failed approach → essence hook → mechanism (real-data worked examples) → tradeoff → definition → system impact
- A complete visual system: layer-based color model (L0–L5), 20° axis, plate mounting, gauges, punch cards, swimlanes, trace grids, dialogues, stair groups — 40+ encoded components
- Exam-point deep teaching (e.g. 408 postgrad entrance exams): positioning, derivations, traps, speed tricks, related topics
- 13-item quality checklist enforced before delivery

## Install

This is an Agent Skill (SKILL.md + references). Copy the repository into your agent's skills directory:

```bash
cp -r noesis-tutorial ~/.claude/skills/
# or keep it in the project: .claude/skills/noesis-tutorial/
```

The skill activates when the request matches the frontmatter description (technical tutorials / concept explanations / learning notes / exam-point study material, in English or Chinese). You can also invoke it explicitly by name.

## Usage

Ask for a technical topic as a learning page:

- "Write a complete study note on KMP with full exam points"
- "Explain how TCP's three-way handshake works, as an HTML page"

The agent follows the 7-step workflow in `SKILL.md`, then verifies against the 13-item quality checklist. Pages are standalone — open the HTML directly in a browser.

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

## Examples

Open any `references/example-*.html` in a browser. The six Chinese examples together cover every component in the system; the English example demonstrates the same system in English.

## License

MIT — see [LICENSE](LICENSE).