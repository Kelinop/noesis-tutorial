# noesis-tutorial


一个把技术和知识概念转化为美观的html笔记的 skill，产出构成主义技术编辑风格 HTML 学习笔记，而不是教材搬运。

页面语言跟随你的请求：默认中文，也可指定英文或其他语言。

## 产出

- 独立文件 HTML，零构建工具，唯一外部依赖 Google Fonts CDN
- 因果链教学：问题 → 压力 → 旧方案失败 → 本质解释 → 机制（真实数据推演）→ 权衡 → 定义 → 系统影响
- 完整视觉系统：分层色板（L0–L5）、20° 轴线、图版装裱、仪表盘、打孔卡、泳道、走查格阵、对话、阶梯组——40+ 编码组件
- 考点深度教学（如 408 考研）：考点定位、推导、陷阱、速算、关联考点
- 交付前强制 13 项质检清单

## 安装

这是一个 Agent Skill（SKILL.md + references）。把仓库复制进你的 agent 的 skills 目录：

```bash
cp -r noesis-tutorial ~/.claude/skills/
# 或放在项目内：.claude/skills/noesis-tutorial/
```

请求命中 frontmatter description（技术教程 / 概念讲解 / 学习笔记 / 考点精讲，中英文均可）时自动激活，也可按名字显式调用。

## 使用

以学习页面的形式提出技术主题：

- 「写一份 KMP 的完整 408 考点笔记」
- "Write a complete study note on KMP with full exam points"
- 「解释虚拟内存，要 HTML 页面」

agent 按 `SKILL.md` 的 7 步流程执行，交付前过 13 项质检。页面独立自包含，浏览器直接打开。

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

## 例文

浏览器直接打开 `references/example-*.html`。六篇中文例文合覆盖全部组件；英文例文用同一系统演示英文页面：

| 例文 | 语言 | 主题 | 重点组件 |
|---|---|---|---|
| example-twos-complement.html | 中文 | 补码（R1） | punch card 图版横列、进位 trace、钟面钩子 |
| example-virtual-memory.html | 中文 | 虚拟内存（R2） | memory map、nested tree、爆炸框、TLB 仪表、缺页 stepper |
| example-tcp.html | 中文 | TCP 握手（R1） | swimlane ×3、状态图、ASCII 头、dialogue、三角指针 |
| example-kmp.html | 中文 | KMP 全 408 考点 | 走查格阵、交互 stepper、继承链图解、10 图版 |
| example-maxwell-equations.html | 中文 | 麦克斯韦方程组（R3） | 海报页头、timetable、档案卡、G7 层级色阶、G8 拼贴 |
| example-photoelectric-effect.html | 中文 | 光电效应（R1+R3） | G1 切角、G3 红圆、红限仪表、SVG 装置、dialogue |
| example-kmp.en.html | English | KMP 完整教学 | 英文语言与实现双模板 |

## 许可

MIT——见 [LICENSE](LICENSE)。
