---
name: noesis-skill-constructive-refactor
overview: 将 noesis-tutorial skill 从声明式规范重构为构造式规则：全面重写 SKILL.md 并大幅精简 references 下的视觉/样式文档，删除逐组件规格，保留视觉身份与可读性底线两类不变量，示例精简到 2-3 个代表例，让模型按语义需要自行构造布局与组件。
todos:
  - id: rewrite-skill-md
    content: 使用 [skill:skill-creator] 重写 SKILL.md 为构造式精简骨架（≤200 行），保留触发判定与教学范式
    status: completed
  - id: create-visual-language
    content: 合并 visual-system.md 与 style-guide.md，新建 references/visual-language.md（不变量+生成语法+形式词汇表）
    status: completed
  - id: prune-examples
    content: 精简示例：保留 kmp/maxwell/photoelectric 三个代表例，删除其余 4 个 HTML、两个旧参考文档与 example-coverage.md
    status: completed
    dependencies:
      - create-visual-language
  - id: update-readmes
    content: 同步更新 README.md 与 README.zh-CN.md：示例表、仓库结构、卖点措辞、frontmatter 引用
    status: completed
    dependencies:
      - prune-examples
  - id: verify-consistency
    content: 全局校验：无悬空引用、不变量清单与用户选定一致、文档间无自相矛盾
    status: completed
    dependencies:
      - rewrite-skill-md
      - create-visual-language
      - update-readmes
---

## 用户需求

用户自研的 Agent Skill（noesis-tutorial，生成构成主义风格 HTML 学习页面）在使用中暴露出"规则太重、过分详细"的问题：声明式规范限制了模型根据具体场景的发挥。用户希望把它从**声明式规范**提炼为**构造式规则**——保留核心思维范式（因果链教学架构、本质模型、研究核查义务）和艺术风格（构成主义三原则、L0–L5 色层、20° 轴），同时放宽对内容布局、组件设计的限制，允许更多场景泛化与创造。

## 产品概述

对整个 skill 仓库做全面重构：重写 SKILL.md 为精简的生成式骨架，将 visual-system.md（32KB）与 style-guide.md（85KB）合并提炼为单个视觉语言参考文档（约 10–20KB），示例 HTML 从 7 个精简到 3 个差异最大的代表例，同步更新两份 README。

## 核心特性

- **构造式规则体系**：给模型"生成语法"（语义标注 → 叙事状态 → 形式构造）而非组件目录；组件由模型按语义需要自行构造，示例与先例仅作启发
- **不变量白名单**：仅保留两类不可协商项——视觉身份类（L0–L5 色层语义、双红分工、20° 轴、禁渐变/辉光）与可读性底线（对比度禁令、红面阈值、连续深色 ≤60%）
- **核心思维范式保留**：教学因果链、本质模型设计、研究核查义务、考点教学模式、语义标注生成入口
- **降级为可偏离默认**：单文件、字体栈、768px 断点、装裱三级、页缘标尺/版权条等工程约束从"必须"变为"默认起点，可论证偏离"
- **质量自查转型**：从 13 项逐屏数值审查转为少量不变量校验 + 语义有效性自查（"每个形式必须能回答它编码了什么"）
- **示例即事实标准**：保留 KMP（考点密集/图纸族）、Maxwell（海报式/几何自由）、光电效应（短判词/对话/仪表）三个代表例

## 技术方案

### 实现策略

这是一次**文档架构重构**（非代码任务）：把"规则目录"改写为"生成语法 + 不变量 + 启发示例"三层结构。核心方法论是 skill 最佳实践中的渐进式披露（progressive disclosure）：SKILL.md 保持精简主干，细节按需查阅参考文档，风格具体做法由示例 HTML 承载。

关键决策与取舍：

- **保留用户未提交的 When NOT to Use 改写成果**（触发判定 A–F 节），仅微调措辞融入新结构，不回退
- **合并而非并列**：visual-system.md 与 style-guide.md 合并为单一 `references/visual-language.md`，消除现有的"规则权威索引/数值门控表/单一权威"等跨文件同步机制——这些机制本身就是规则过重的症状
- **不变量集中声明**：新参考文档开头设"Invariants（不可协商项）"一节，显式列出用户选定的两类底线；其余全部标注为"默认/启发"，让模型明确知道自由边界在哪里——自由度来自边界清晰，而非规则消失
- **组件规格转为生成语法**：删除 G1–G8/仪器/形态/图解的逐个能力卡、像素规格、类名注册表；保留一份紧凑的"形式词汇表"（每个形式一句话语义，如 trace=多变量状态变化的全局并置），作为构造起点而非选用目录
- **R1–R4 构图先例**压缩为四行启发式描述，明确标注"先例而非模板"

### 新体系三层结构

```text
SKILL.md（≤200 行，生成式骨架）
  ├─ 触发判定（保留用户成果）
  ├─ 教学思维范式（因果链 / 本质模型 / 研究核查 / 考点模式）
  ├─ 生成入口（语义标注 → 形式构造的工作流，Step 合并精简）
  ├─ 交付基线（独立 HTML、页面语言、多文件拆分一段式说明）
  └─ 交付自查（不变量校验 + 语义有效性自查，替代 13 项清单）
references/visual-language.md（10–20KB，单一视觉语言参考）
  ├─ 三原则与哲学（构造可见 / 色彩即职能 / 几何即仪器）
  ├─ Invariants：色层 L0–L5 语义+色值、双红分工、叠加禁令、
  │   20° 轴、红面阈值、60% 呼吸、对比度禁令、禁渐变/辉光
  ├─ 生成语法：语义标注 → 叙事状态 → 形式构造；形式有效性
  │   （退化格阵禁令、"编码了什么"自查）
  ├─ 形式词汇表（一句话语义 × 约 20 个形式，启发用）
  ├─ 构图启发：板面/双轨/天际线/页面角色/R1–R4 先例（压缩版）
  ├─ 可偏离默认：字体栈+CDN、token 建议值、768px 断点、
  │   装裱惯例、页缘标尺/角标/版权条（签名元素，默认开启）
  └─ 示例索引（3 个示例各自示范什么）
references/example-{kmp,maxwell-equations,photoelectric-effect}.html
```

### 实施注意事项

- **爆炸半径控制**：重构只动文档与示例，不涉及可执行代码；删除文件前确认无残留引用（README、SKILL.md、示例索引中所有 `example-*.html`、`visual-system.md`、`style-guide.md`、`example-coverage.md` 的引用点需逐一更新或移除）
- **示例取舍标准**：覆盖差异最大化——kmp=考点模式+全装裱图纸族，maxwell=海报页头+G5/G7/G8 几何自由+档案族，photoelectric=短判词+对话+仪表+物理学科；kmp.en 与 kmp 内容重复，删英文版（README 旗舰链接改指保留示例）
- **README 同步点**：示例表格（7→3）、"40+ components / 13-item checklist"等过时卖点措辞、仓库结构图、工作流描述、frontmatter 引用块
- **语言一致性**：新文档沿用现有中英混排风格（原则与教学内容为英文主干、设计术语保留中文标注），与现有文档气质一致
- **验证方式**：完成后通读三份核心文档，检查无悬空引用、无自相矛盾（如 SKILL.md 不再说 "Read first, in full"）、不变量清单与用户选定范围一致

## Agent Extensions

### Skill

- **skill-creator**
- Purpose: 本任务是更新一个现有 Agent Skill，使用该 skill 的最佳实践指南（渐进式披露、SKILL.md 精简度、参考文档组织）来校验重构方案与新文档结构
- Expected outcome: 新的 SKILL.md 与 references/ 结构符合 skill 编写规范，主文件精简、细节按需披露，无规则冗余