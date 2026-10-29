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

<h3>把技术概念转化为「设计过的工程知识页面」</h3>

<p>构成主义技术编辑风格的 HTML 学习笔记。<br>
不是教材搬运，也不是 Markdown 转 HTML。</p>

<p>
  <a href="LICENSE"><img src="https://img.shields.io/badge/license-MIT-0f4c81?style=flat-square" alt="License: MIT"></a>
  <img src="https://img.shields.io/badge/style-构成主义-1c1c1c?style=flat-square" alt="Style: Constructivist">
  <img src="https://img.shields.io/badge/output-独立_HTML-e63946?style=flat-square" alt="Output: Standalone HTML">
  <img src="https://img.shields.io/badge/build-零构建-b8863b?style=flat-square" alt="Build: Zero">
</p>

<p><a href="README.md">English</a> · <a href="#在线预览">在线预览</a> · <a href="#安装">安装</a> · <a href="#使用">使用</a></p>

<br>

<a href="https://htmlpreview.github.io/?https://github.com/Kelinop/noesis-tutorial/blob/main/references/example-maxwell-equations.html">
  <img src="assets/preview-mac.png" alt="麦克斯韦方程组 — noesis-tutorial 预览" width="720">
</a>

<p><em>麦克斯韦方程组 — <a href="https://htmlpreview.github.io/?https://github.com/Kelinop/noesis-tutorial/blob/main/references/example-maxwell-equations.html">在浏览器中打开 →</a></em></p>

</div>

---

## 在线预览

这就是 skill 的产出。每篇例文都是独立 HTML 文件，点击即可在浏览器中打开（经 <a href="https://htmlpreview.github.io/">htmlpreview</a> 渲染）：

| # | 例文 | 主题 | 页面气质 |
|:---:|:---|:---|:---|
| 01 | [KMP 全 408 考点](https://htmlpreview.github.io/?https://github.com/Kelinop/noesis-tutorial/blob/main/references/example-kmp.html) | KMP（408） | 考点密集 / 图纸族：真实数据 trace、交互 stepper、双条错位图、档案面板 |
| 02 | [麦克斯韦方程组](https://htmlpreview.github.io/?https://github.com/Kelinop/noesis-tutorial/blob/main/references/example-maxwell-equations.html) | 麦克斯韦方程组 | 海报式 / 几何自由：ochre 时间线、G7 层级色阶、镜像对置构图、G8 拼贴 |
| 03 | [光电效应](https://htmlpreview.github.io/?https://github.com/Kelinop/noesis-tutorial/blob/main/references/example-photoelectric-effect.html) | 光电效应 | 短判词 / 对话 / 仪表：红日、红限仪表、立场对话、SVG 装置 |

三篇例文覆盖差异最大化的三种页面气质；它们演示的是同一套由生成语法构造出的视觉语言，而非一份组件目录。

## 产出

| 特性 | 说明 |
|:---|:---|
| **独立 HTML** | 零构建工具。唯一外部依赖：Google Fonts CDN。浏览器直接打开。 |
| **因果链教学** | 问题 → 压力 → 旧方案失败 → 本质解释 → 机制（真实数据推演）→ 权衡 → 定义 → 系统影响 |
| **视觉语言** | 分层色板（L0–L5）、20° 轴线、图版装裱——一套**生成语法**：少量不变量 + 形式词汇表，形式按内容语义自行构造 |
| **考点深度** | 408 考研：考点定位、推导、陷阱、速算、关联考点 |
| **质检关卡** | 交付前执行不变量校验 + 语义有效性自查 |

<a name="安装"></a>
## 安装

这是一个 **Agent Skill**（`SKILL.md` + `references/`）。把仓库复制进你的 agent 的 skills 目录：

```bash
# Claude Code / Claude Desktop
cp -r noesis-tutorial ~/.claude/skills/

# Cursor、Windsurf 等读取 .claude/skills 的 agent
cp -r noesis-tutorial .claude/skills/
```

任何会读取 `SKILL.md` 的 agent 都能使用——skill 的本质就是规则与样例。

## 激活规则

请求命中 frontmatter description 时自动激活：

```yaml
name: noesis-tutorial
description: Use only when the user asks for a learning artifact — a complete,
  self-contained HTML learning page (technical tutorial, concept study page,
  learning notes, exam-point review material). Conversational "explain X" / Q&A
  requests do NOT trigger this skill; answer them directly.
  仅当用户明确要求交付 HTML 学习页面时使用；聊天式问答不触发本技能。
```

也可按名字显式调用。

<a name="使用"></a>
## 使用

以学习页面的形式提出技术主题：

> **「写一份 KMP 的完整 408 考点笔记」**
>
> **"Write a complete study note on KMP with full exam points"**
>
> **「解释虚拟内存，要 HTML 页面」**

agent 按 `SKILL.md` 的**创建流程**执行：

```
调研 → 因果链 → 本质模型 → 语义编排 → 形式构造 → HTML → 交付自查
```

交付前过**交付自查**（不变量校验 + 语义有效性）。页面独立自包含，浏览器直接打开。

## 目录结构

```
noesis-tutorial/
├── SKILL.md                        # 工作流：使用时机、创建流程、教学架构、交付自查（中英双语）
├── references/
│   ├── visual-language.md          # 单一视觉参考：不变量、生成语法、形式词汇表（中英混排）
│   ├── example-kmp.html            # 考点密集 / 图纸族
│   ├── example-maxwell-equations.html  # 海报式 / 几何自由
│   └── example-photoelectric-effect.html  # 短判词 / 对话 / 仪表
├── README.md                       # English version
├── README.zh-CN.md                 # 本文件
└── LICENSE                         # MIT License
```

**执行输入**：`SKILL.md` + `visual-language.md` + 三篇例文。

---

## 许可

[MIT](LICENSE) © Kelinop
