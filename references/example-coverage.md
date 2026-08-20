# Example Coverage & Index — 例文 × 组件索引 + 构图索引

> 本文件由两张索引 + 示例价值盘点 + 设计注解构成。七篇例文（六篇中文 + 英文旗舰 `example-kmp.en.html`）共同覆盖全部 core + extended 组件。**新页面落组件时以组件索引查规范例与变体例**；**规划整页骨架时以构图索引查已验证先例**。

## 1. 组件索引（Component Index）

组件 → 规范例 → 变体例 → 所在区段 → 对应规格。

> **规范例** = 最完整、最符合规则、最容易复用的实现。**变体例** = 提供不同材料层、不同教学角色、不同组合或响应式处理的实现，每例注明新增价值。

| 组件 | 规范例 | 变体例（新增价值） | 对应规格 |
|---|---|---|---|
| 标准式页头 | 全部六篇 | — | style-guide → Page Header |
| 海报式页头 | maxwell | — | style-guide → Page Header |
| wedge-block（G2） | twos（补码压力开场） | tcp（握手压力）/ kmp（匹配失败压力）/ maxwell（电磁学张力）/ photoelectric（经典预言冲突）——不同教学动作的楔形 | style-guide → G2 |
| essence-hook（`.hook`） | twos（钟面模型） | photoelectric（光子能量模型）/ maxwell（场论模型）——不同认知类型的 hook | style-guide → 陈述类容器通则 |
| giant-num | 全部六篇 | — | style-guide → Sections |
| giant-verdict | twos（mod 256 结论） | kmp（O(n+m) 结论）/ maxwell（光是电磁波结论）——不同主题的判词 | style-guide → Giant Verdict |
| plate.full（全装裱） | twos | — | style-guide → Plate Specs |
| plate.light（轻装裱） | tcp（状态图 图 2） | maxwell（图 5）/ photoelectric（图 6）——不同展件的轻装裱 | style-guide → Plate Specs |
| plate-row（图版横列） | twos（三码 punch card 2a/2b/2c） | — | style-guide → 横向构成 |
| rail-hang（G4 outset） | tcp（握手主图版 图 1） | — | style-guide → G4 |
| 三角指针（`.tri`） | tcp（swimlane 交接箭头 图 1/4/7） | — | style-guide → Triangle Pointer |
| punch card | twos（三码对照 图 2a/2b/2c） | — | style-guide → Punch Card |
| memory map | virtual（地址空间 图 1） | tcp / maxwell（借用 mmap-row 布局做对照条，非地址空间语义——变体价值=布局复用） | style-guide → Memory Map |
| nested tree | virtual（两级页表 图 4） | — | style-guide → Nested Tree |
| exploded frame | virtual（PTE 图 3） | — | style-guide → Exploded Frame |
| trace | twos（进位 图 3 + 溢出 图 5） | virtual（翻译 图 5——地址翻译变体）/ tcp（重传 图 5——时序变体）/ kmp（账本 图 8——bf-grid 格阵变体）/ photoelectric（V₀–ν 图 5——物理数据变体） | style-guide → Trace |
| stepper / step-through | kmp（匹配走查 图 4——含交互） | virtual（缺页 图 7——静态步进变体） | style-guide → Stepper |
| swimlane | tcp（握手 图 1 + 延迟重放 图 4 + 挥手 图 7） | — | style-guide → Swimlane |
| state diagram | tcp（状态转移 图 2） | — | style-guide → State Diagram |
| ascii diagram | tcp（报文段头 图 3） | — | style-guide → ASCII Diagram |
| dialogue | photoelectric（波动说 vs 光量子说） | tcp（为何两次不够——误解纠正变体） | style-guide → Dialogue |
| warning box | 全部六篇 | — | style-guide → 陈述类容器通则 |
| archival panel | kmp（next 定义 + nextval 优化规则） | twos（补码定义——单一定义变体）/ maxwell（电磁波定义——物理定义变体）/ photoelectric（光电效应方程——方程定义变体） | style-guide → Archival Panel |
| archive card + 戳记 | maxwell（史实引文） | — | style-guide → Archive Card |
| timetable | maxwell（电磁学演进） | photoelectric（光子学说史——较短时序变体） | style-guide → Timetable |
| gauge | photoelectric（红限频率 图 2） | virtual（TLB 命中率 图 6——利用率变体） | style-guide → Gauge |
| ratio bar | kmp（省下的比较次数） | — | style-guide → Ratio Bar |
| readout / instrument strip | twos | virtual / tcp / maxwell / photoelectric——不同读数场景 | style-guide → Readout |
| G1 cut-corner block | photoelectric（截止电压读数面板） | — | style-guide → G1 |
| G3 circle callout（红圆） | photoelectric（E = hν 焦点） | — | style-guide → G3 |
| G5 color field（ochre 色场） | maxwell（演进带） | — | style-guide → G5 |
| G6 nested panel | kmp（第 03 节双法手算嵌套面板） | — | style-guide → G6 |
| G7 stair（阶梯组） | maxwell（从实验定律到方程组） | — | style-guide → G7 |
| G8 collage（拼贴平面） | maxwell（「光是电磁波」结论） | photoelectric（波粒二象性结论——不同主题的拼贴变体） | style-guide → G8 |
| insight panel | photoelectric（应试技巧） | maxwell（方程意义——物理意义变体）/ kmp（速算口诀——考点技巧变体） | style-guide → 陈述类容器通则 |
| inset panel（G4 inset） | twos | virtual / tcp / kmp / photoelectric——worked example / Q&A 变体 | style-guide → G4 |
| split（对称双栏） | photoelectric（装置读数 vs 史纲） | — | style-guide → 对照类 |
| staggered（错位双栏） | photoelectric（经典预言 vs 实验事实） | — | style-guide → 横向构成 |
| asym（非对称网格） | maxwell（方程主栏 + 窄栏读数） | — | style-guide → 横向构成 |
| causal chain | twos（补码因果链——最简洁清晰） | 全部六篇（各自主题的因果序列） | style-guide → Causal Chain |
| blueprint callout | twos（丢弃进位 = mod 256） | virtual（位宽拆分）/ tcp（滑动窗口）/ kmp（哨兵 j=0）——不同机制的局部放大 | style-guide → Blueprint Callout |
| code block | twos | tcp / kmp / maxwell / photoelectric——不同语言的代码示例 | style-guide → Code Block |
| compare table / data table | 全部六篇 | — | style-guide → Tables |
| checklist（回顾索引） | 全部六篇 | — | style-guide → Checklist |
| hatching（剖面线） | virtual（未映射区） | — | style-guide → Hatching |
| 密度标注 | 全部六篇 | — | style-guide → Sections |
| section band（斜切标题带） | 多篇 | — | style-guide → Section Band |
| sidebar（侧栏导航） | 全部长篇例文 | — | style-guide → Sidebar |
| edge ruler（页缘标尺） | 全部六篇 | — | style-guide → Edge Ruler |
| crop marks（四角对版标记） | 全部六篇 | — | style-guide → Crop Marks |
| colophon（版权条） | 全部六篇 | — | style-guide → Colophon |
| 蓝图容器（`.blueprint`） | 多篇 | — | style-guide → 图解通则 |

### 组件覆盖完整性声明

以上索引覆盖全部现有组件（core + extended + G1–G8 + 全部 Form Specs + Diagram Specs + Interaction Specs + Layout Specs 布局骨架）。无覆盖缺口。`example-kmp.en.html` 作为英文旗舰例文，与 `example-kmp.html` 共享同一 10 图版和完整教学覆盖（无考向框架），作为语言与实现双模板。

---

## 2. 构图索引（Composition Index）

主题类型 → 教学主线 → 主图/辅助组件 → 转场 → 高潮 → 密度曲线 → 有效原因。

| 主题类型 | 先例 | 教学主线 | 主图组件 | 辅助组件 | 转场 | 高潮 | 密度曲线 | 有效原因 |
|---|---|---|---|---|---|---|---|---|
| 机制驱动（单一因果） | R1 | 问题→本质→机制→权衡→回顾 | punch card + trace | wedge / blueprint callout / compare table | L5→L0→L2（事件→呼吸→图纸） | giant verdict | standard→breather→dense→standard | 红楔开场压力→图纸展开机制→冷静权衡 |
| 机制深潜（多子系统） | R2 | 本质→机制×N→推演→权衡→回顾 | memory map + nested tree + exploded frame | gauge / trace / stepper / hatching | L0→L2（呼吸→图纸连片） | giant verdict | breather→dense×N→standard | 蓝图集群即展墙，读者沿标尺逐图推进 |
| 多角色流程 | R1 变体 | 问题→角色→机制→状态→权衡 | swimlane + state diagram | ascii / dialogue / triangle pointer | L5→L2（事件→图纸） | giant verdict | standard→dense→standard | 泳道编码角色交接，状态图编码转移 |
| 史料演进 | R3 | 演进→问题→机制→系统影响→回顾 | timetable + archive card | G5 色场 / G7 stair / G8 collage / asym | L3→L0→L2→L0（档案→呼吸→图纸→呼吸） | G8 collage | standard→standard→dense→breather | 档案层与"历史"语义同构，结论从证据浮现 |
| 物理实验 | R1+R3 | 问题→历史→机制→对照→结论 | gauge + dialogue + SVG | G1 / G3 / staggered / split / insight panel | L3→L0→L2→L0（档案→呼吸→图纸→呼吸） | G8 collage / giant verdict | standard→standard→dense→standard→breather | 仪表测量阈值，对话纠正误解，拼贴浮现二象性 |
| 考点精讲（408） | R2 变体 | 本质→定义→机制→推演→陷阱→速算→回顾 | stepper + trace + archival panel | causal chain / ratio bar / warning box / code block / insight panel | L0→L3→L2→L0（呼吸→档案定义→图纸推演→呼吸） | giant verdict | breather→standard→dense×N→standard | 考点深度=机制+推导+陷阱，每步真实数据 |
| 短结论 | R4 | 页头→本质→机制→判词→回顾 | 单块主图 | G3 / essence hook | L0→L2→L0（呼吸→图纸→呼吸） | giant verdict | breather→standard→breather | 单点结论→海报→巨字与留白即构图 |

---

## 3. 示例价值盘点（Example Value Inventory）

### 3.1 主题分工

| 例文 | 教学模式 | 先例 | 谱系 | 重点覆盖 |
|---|---|---|---|---|
| `example-twos-complement.html` | 工程理解（R1 红楔） | 机制驱动 | 印刷族 | 图版制、punch card、plate-row、trace、blueprint callout、compare table |
| `example-virtual-memory.html` | 工程理解（R2 蓝图） | 机制深潜 | 图纸族 | memory map、nested tree、exploded frame、gauge、trace、stepper、剖面线 |
| `example-tcp.html` | 工程理解（R1 变体） | 多角色流程 | 印刷族 + 图纸族 | swimlane、state diagram、ascii、dialogue、plate.light、warning、trace |
| `example-kmp.html` | 考点教学（408） | R2 变体 | 图纸族 | archival panel、stepper/step-through、causal chain、ratio bar、warning box、code block |
| `example-maxwell-equations.html` | 工程理解（R3 档案） | 史料演进 | 印刷族 | 海报式页头、timetable、archive card、G5 色场、G7 stair、G8 collage、asym |
| `example-photoelectric-effect.html` | 工程理解（R1+R3） | 物理实验 | 印刷族 | G1、G3 红圆、gauge、dialogue、staggered、insight panel、split |
| `example-kmp.en.html` | 考点教学（EN） | R2 变体 | 图纸族 | English flagship — same 10 figures & complete teaching coverage as example-kmp.html (no exam-oriented framing); language & implementation template |

### 3.2 独立 HTML 重复说明

每个例文为可独立打开的成品，`head`、tokens、响应式 CSS、导航和必要的基础样式允许重复；清理对象是参考层面的重复讲解、重复规则入口和无新增价值的相似展示，**不是**破坏页面自包含性。具体到 CSS：

- **骨架 CSS 是必要重复，保留内联**：七篇例文 `<style>` 内的骨架区（tokens / reset / crop marks / board+sidebar / ruler / sec / 标准页头）是自包含成品的固有约束，不用 `<link>` 外链；骨架改动以 `example-kmp.html` 为基准同步其余六篇（maxwell 在海报式页头处分叉，分叉点之后不属骨架区）。
- **多次出现的基础组件每篇至多保留 1 处教学必需实例**（如 warning box / inset-panel / data-table）；无登记变体价值的重复实例是清理对象，被删内容由保留形态（dialogue / inset / 词眼 / 散文）承接，不丢教学要点。

### 3.3 图版数约定

按**图号**计（plate-row 分图 图 2a/2b/2c 计入同号 图 2）；colophon 与正文图号一致。

---

## 4. 设计注解（Design Annotations）

选取三个差异最大的示例，补充其"从教学递进链与语义标注到版式"的设计注解。

### 4.1 example-twos-complement.html — 机制驱动（R1 红楔先例）

**教学递进链**：
- 本质：256 个数排在钟面上，加减是顺/逆时针走动 → 钟面心智模型
- 问题：原码/反码有双零，加减法需要不同电路 → 工程压力
- 旧方法缺陷：符号位是外加标签，不参与运算 → 失败原因
- 机制：取模运算自动处理符号 → 补码 = mod 256
- Tradeoff：牺牲负数的直观可读性，换取加减法统一和单一零

**语义标注 → 版式映射**：

| 单元 | 语义标注 | 版式选择 | 选择理由 |
|---|---|---|---|
| 开场 | 建立直觉 / 钟面模型 / 解释 / breather / 原理 / 定锚 | essence-hook + giant-num（breather 节） | 钟面模型是最小心智模型，breather 密度给读者消化空间 |
| 问题 | 提问 / 双零缺陷 / 事件 / standard / 原理 / 定位 | wedge-block（G2，red 事件） | 双零是全页最强冲突点——楔形编码力量方向 |
| 机制-位格式 | 拆解 / 位置×二值 / 测量 / dense / 真实数据 / 展示 | punch card × 3（plate-row，三码对照） | 位置即语义（位号），孔=1/无孔=0；三码并置让差异可见 |
| 机制-进位 | 推演 / 状态变化 / 测量 / dense / 真实数据 / 展示 | trace（进位接力） + blueprint callout | trace 编码"行=时间步×列=状态维"；blueprint callout 放大"丢弃进位=mod 256" |
| 结论 | 定义 / 取模运算 / 归档 / standard / 规范定义 / 闭环 | archival panel（补码定义）+ giant verdict | 定义用档案面板（声明"应当如此"）；判词固定结论 |
| 权衡 | 比较 / 增益×代价 / 冷静 / standard / 综合判断 / 对照 | compare table + readout | 二维查找（增益×代价）用表；读数展示关键数值 |

**密度曲线**：standard（问题）→ breather（本质）→ dense（机制×2）→ standard（定义+权衡）→ breather（回顾）。图纸族主导，ochre 仅在档案面板出现，与 L2 之间有 L0 间隔。

### 4.2 example-virtual-memory.html — 机制深潜（R2 蓝图先例）

**教学递进链**：
- 本质：每个程序拥有独占的连续地址空间，物理内存是共享的碎片化资源 → 间接层心智模型
- 问题：程序需要连续内存，物理内存不够 → 工程压力
- 旧方法缺陷：交换整个进程代价太高 → 失败原因
- 机制：页表映射 + TLB 加速 + 按需分页 → 多子系统协同
- Tradeoff：牺牲地址翻译开销，换取内存利用率和隔离性

**语义标注 → 版式映射**：

| 单元 | 语义标注 | 版式选择 | 选择理由 |
|---|---|---|---|
| 本质 | 建立直觉 / 间接层 / 解释 / breather / 原理 / 定锚 | essence-hook（breather 节） | 间接层模型是深潜前的心智锚点 |
| 地址空间 | 拆解 / 包含关系 / 测量 / dense / 真实数据 / 展示 | memory map（图 1） | 地址区间×归属 = 可测量内容，落 L2 |
| 页表层级 | 拆解 / 层级包含 / 测量 / dense / 真实数据 / 展示 | nested tree（图 4，两级页表） | 嵌套矩形编码"包含/被包含"的几何从属 |
| PTE 字段 | 拆解 / 零件分解 / 测量 / dense / 真实数据 / 展示 | exploded frame（图 3） | 沿轴线逐级错位分解 PTE 各字段 |
| 翻译过程 | 推演 / 状态变化 / 测量 / dense / 真实数据 / 展示 | trace（翻译 图 5） | 逐步状态并置，行=步骤×列=寄存器 |
| TLB 命中率 | 测量 / 阈值 / 测量 / standard / 真实数据 / 旁证 | gauge（图 6） | 阈值型读数——径向仪表 |
| 缺页处理 | 推演 / 单步递进 / 测量 / dense / 真实数据 / 展示 | stepper（图 7） | 单步演示缺页中断流程 |

**密度曲线**：breather（本质）→ dense（机制×4）→ standard（权衡）→ dense（推演）→ standard（回顾）。图纸族主导，dense≠深色——60% 呼吸带始终有效。剖面线标记未映射区（第二身份通道）。

### 4.3 example-maxwell-equations.html — 史料演进（R3 档案先例）

**教学递进链**：
- 演进：从库仑到法拉第的实验定律积累 → 历史背景
- 问题：电与磁的统一缺乏数学框架 → 工程压力
- 旧方法缺陷：实验定律是经验性的，无法预测新现象 → 失败原因
- 机制：位移电流 + 方程组统一 → 数学框架
- Tradeoff：牺牲直觉可读性，换取预测能力和统一性

**语义标注 → 版式映射**：

| 单元 | 语义标注 | 版式选择 | 选择理由 |
|---|---|---|---|
| 页头 | 定位 / 学科范围 / 事件 / breather / 可信来源 / 开场 | 海报式页头（poster-marks 色票条） | 物理学科海报式开场，色票编码页面色板 |
| 演进 | 回顾 / 时间序列 / 归档 / standard / 历史来源 / 转场 | timetable + archive card + G5 ochre 色场 | ochre 档案层与"历史"语义同构；时间表编码精确时序 |
| 递进构建 | 推演 / 因果递进 / 解释 / standard / 原理 / 展示 | G7 stair（层级色阶，从实验定律到方程组） | 每项建立在前项之上——递进构建语义 |
| 方程组 | 展示 / 数学框架 / 测量 / dense / 规范定义 / 主图 | asym（方程主栏 + 窄栏读数） | 主从权重——方程为主，读数为辅 |
| 结论 | 结论抽取 / 证据—结论 / 焦点 / breather / 综合判断 / 高潮 | G8 collage（「光是电磁波」结论，red 硬投影） | 结论从证据浮现——浮动平面承载判词 |
| 定义 | 定义 / 电磁波 / 归档 / standard / 规范定义 / 闭环 | archival panel（电磁波定义） | 严格定义用档案面板 |

**密度曲线**：standard（演进）→ standard（问题）→ dense（机制）→ breather（系统影响/G8）→ standard（回顾）。材料转场：L3（档案）→ L0（呼吸）→ L2（图纸）→ L0（呼吸/G8 浮起）。ochre 色场不与 L2 相邻（≥gap-md）。
