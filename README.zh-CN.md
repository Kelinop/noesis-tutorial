# noesis-tutorial

[![License: MIT](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)

一个把技术概念转化为「设计过的工程知识页面」的 agent skill：构成主义技术编辑风格的 HTML 学习笔记，而不是教材搬运，也不是 Markdown 转 HTML。

页面语言跟随你的请求：中文、英文或其他语言均可。

## 在线预览

这就是 skill 的产出。每篇例文都是独立 HTML 文件，点击即可在浏览器中打开（经 [htmlpreview](https://htmlpreview.github.io/) 渲染）：

| 例文 | 主题 | 重点组件 |
|---|---|---|
| [KMP 完整教学（英文旗舰）](https://htmlpreview.github.io/?https://github.com/Kelinop/noesis-tutorial/blob/main/references/example-kmp.en.html) | KMP 全考点（EN） | 英文语言与实现双模板、全部组件 |
| [补码](https://htmlpreview.github.io/?https://github.com/Kelinop/noesis-tutorial/blob/main/references/example-twos-complement.html) | 补码（R1） | punch card 图版横列、进位 trace、钟面钩子 |
| [虚拟内存](https://htmlpreview.github.io/?https://github.com/Kelinop/noesis-tutorial/blob/main/references/example-virtual-memory.html) | 虚拟内存（R2） | memory map、nested tree、爆炸框、TLB 仪表、缺页 stepper |
| [TCP 握手](https://htmlpreview.github.io/?https://github.com/Kelinop/noesis-tutorial/blob/main/references/example-tcp.html) | TCP 握手（R1） | swimlane ×3、状态图、ASCII 头、dialogue、三角指针 |
| [KMP 全 408 考点](https://htmlpreview.github.io/?https://github.com/Kelinop/noesis-tutorial/blob/main/references/example-kmp.html) | KMP（408） | 走查格阵、交互 stepper、继承链图解、10 图版 |
| [麦克斯韦方程组](https://htmlpreview.github.io/?https://github.com/Kelinop/noesis-tutorial/blob/main/references/example-maxwell-equations.html) | 麦克斯韦方程组（R3） | 海报页头、timetable、档案卡、G7 层级色阶、G8 拼贴 |
| [光电效应](https://htmlpreview.github.io/?https://github.com/Kelinop/noesis-tutorial/blob/main/references/example-photoelectric-effect.html) | 光电效应（R1+R3） | G1 切角、G3 红圆、红限仪表、SVG 装置、dialogue |

六篇中文例文共同覆盖视觉系统的全部组件；英文例文演示同一系统在英文下的实现。

## 产出

- 独立文件 HTML，零构建工具，唯一外部依赖 Google Fonts CDN
- 因果链教学：问题 → 压力 → 旧方案失败 → 本质解释 → 机制（真实数据推演）→ 权衡 → 定义 → 系统影响
- 完整视觉系统：分层色板（L0–L5）、20° 轴线、图版装裱、仪表盘、打孔卡、泳道、走查格阵、对话、阶梯组——40+ 编码组件
- 考点深度教学（如 408 考研）：考点定位、推导、陷阱、速算、关联考点
- 交付前强制 13 项质检清单

## 安装

这是一个 Agent Skill（`SKILL.md` + `references/`）。把仓库复制进你的 agent 的 skills 目录：

```bash
# Claude Code / Claude Desktop
cp -r noesis-tutorial ~/.claude/skills/
# Cursor、Windsurf 等读取 .claude/skills 的 agent
# 或放在项目内：
cp -r noesis-tutorial .claude/skills/
```

任何会读取 `SKILL.md` 的 agent 都能使用——skill 的本质就是规则与样例。

## 激活规则

请求命中 frontmatter description 时自动激活：

```yaml
name: noesis-tutorial
description: Use when the user asks for technical tutorials, concept explanations,
  learning notes, or exam-point study material, to be delivered as HTML learning pages.
  当用户请求技术教程、概念讲解、学习笔记或考点精讲，需交付 HTML 学习页面时使用。
```

也可按名字显式调用。

## 使用

以学习页面的形式提出技术主题：

- 「写一份 KMP 的完整 408 考点笔记」
- "Write a complete study note on KMP with full exam points"
- 「解释虚拟内存，要 HTML 页面」

agent 按 `SKILL.md` 的 7 步流程执行（调研 → 因果链 → 本质钩 → 结构 → 图解 → HTML → 质检），交付前过 13 项质检。页面独立自包含，浏览器直接打开。

## 目录结构

```
SKILL.md                        # 工作流：使用时机、7 步创建、教学架构、13 项质检（中英双语）
references/
  visual-system.md              # 设计哲学：色层模型、轴线、几何语义、构图（中英双语）
  style-guide.md                # Tokens + 组件规格——每个类名的规则源（中文）
  example-*.html ×6             # 六篇中文例文——组件覆盖与教学样例
  example-kmp.en.html           # 英文旗舰例文（组件密集、完整教学）
  example-coverage.md           # 组件 × 例文覆盖矩阵
```

- **执行输入**：SKILL.md + visual-system.md + style-guide.md + 例文 + 覆盖矩阵。

## 许可

MIT——见 [LICENSE](LICENSE)。
