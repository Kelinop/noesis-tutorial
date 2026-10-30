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

<p>单文件、零构建的 HTML 学习页面，采用<strong>当代构成主义技术编辑语言</strong>。<br>
以因果解释、可检验的心智模型与有依据的视觉层级为核心——不是教材搬运，也不是 Markdown 转 HTML。</p>

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
| 01 | [KMP 全 408 考点](https://htmlpreview.github.io/?https://github.com/Kelinop/noesis-tutorial/blob/main/references/example-kmp.html) | KMP（408） | 高频考点 / 图纸族：构造输入 trace、交互 stepper、双条错位图、档案参照面板 |
| 02 | [麦克斯韦方程组](https://htmlpreview.github.io/?https://github.com/Kelinop/noesis-tutorial/blob/main/references/example-maxwell-equations.html) | 麦克斯韦方程组 | 历史海报 / 几何自由：时间线、递进推导、镜像对置构图、证据拼贴 |
| 03 | [光电效应](https://htmlpreview.github.io/?https://github.com/Kelinop/noesis-tutorial/blob/main/references/example-photoelectric-effect.html) | 光电效应 | 阈值焦点 / 阈值轴 / 模型对话：红限阈值轴、立场碰撞、SVG 装置 |

三篇例文侧重三种内容关系：考点密集的图纸、历史推演的海报、阈值判断的标尺。它们演示同一套生成语法，不是可直接照搬的模板。

## 产出

| 特性 | 说明 |
|:---|:---|
| **单文件 HTML** | 零构建步骤。浏览器直接打开；Google Fonts 是可选 CDN 依赖，并保留可读回退。 |
| **学习架构** | 学习者与先修知识 → 概念依赖图 → 因果弧 → 经普通例、边界例和迁移任务检验的心智模型 |
| **视觉语言** | 当代构成主义技术编辑：材料职能（L0–L5）、字体层级、响应式构图、分层选型，以及从命题与视觉通道到尺度、标注、边界和无 JS/窄屏变体的图解施工流程；美学效果与表达新颖性是硬性约束之后的正面标准 |
| **考点深度** | 考点定位、逐状态推导、陷阱、验证技巧与关联考点；分值主张仅在可靠来源支持时出现 |
| **四道质量门** | 学习与范围、证据与正确性、产物的实际行为、视觉与语义有效性 |

<a name="安装"></a>
## 安装

这是一个 **Agent Skill**（`SKILL.md` + `references/`）。把仓库复制进你的 agent 的 skills 目录：

```bash
# CodeBuddy（用户级）
cp -r noesis-tutorial ~/.codebuddy/skills/

# Claude Code / Claude Desktop
cp -r noesis-tutorial ~/.claude/skills/

# Cursor、Windsurf 等读取 .claude/skills 的 agent
cp -r noesis-tutorial .claude/skills/
```

任何支持 `SKILL.md` 与可选参考文件的 agent 都能使用。`visual-language.md` 按需加载，示例按内容关系选择性阅读。

## 激活规则

请求命中 frontmatter description 时自动激活：

```yaml
name: noesis-tutorial
description: Use only when the user asks for a complete, no-build HTML learning
  page (technical tutorial, concept study page, learning notes, or exam-point
  review). Conversational "explain X" / Q&A requests do NOT trigger this skill.
  仅当用户明确要求交付 HTML 学习页面时使用；聊天式问答不触发本技能。
```

也可按名字显式调用。

<a name="使用"></a>
## 使用

以学习页面的形式提出技术主题：

> **「写一份 KMP 的完整 408 考点笔记，要 HTML 页面」**
>
> **"Write a complete HTML study note on KMP with full exam points"**
>
> **「解释虚拟内存，做成 HTML 学习页面」**

agent 按 `SKILL.md` 的**创建流程**执行：

```
学习契约 → 证据台账 → 依赖图 → 受检验的心智模型
→ 语义与审美编排 → 形式选择与图解施工 → 增量生成 HTML → 四道质量门
```

交付前依次检查学习与范围、证据与正确性、产物行为、视觉与语义有效性。产物是单文件、零构建页面，浏览器直接打开。

## 目录结构

```
noesis-tutorial/
├── SKILL.md                        # 激活规则、教学架构、工作流、输出契约、四道质量门
├── references/
│   ├── visual-language.md          # 审美界定、不变量、形式选择、图解施工、字体排版、审美复核
│   ├── example-kmp.html            # 考点密集 / 图纸主导
│   ├── example-maxwell-equations.html  # 历史弧 / 海报主导
│   └── example-photoelectric-effect.html  # 阈值机制 / 阈值轴主导
├── assets/                         # README 预览图
├── README.md                       # English version
├── README.zh-CN.md                 # 本文件
└── LICENSE                         # MIT License
```

**执行输入**：`SKILL.md` 始终参与；写 CSS 前加载 `visual-language.md`，示例只读与当前内容关系最接近的相关部分。

---

## 许可

[MIT](LICENSE) © Kelinop
