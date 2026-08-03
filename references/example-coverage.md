# Example Coverage Matrix — 例文 × 组件覆盖矩阵 / Component × Example Coverage Matrix

六篇中文例文共同覆盖全部 core + extended 组件（SKILL.md 组件与装裱 → style-guide 全部 Specs）；`example-kmp.en.html` 为英文旗舰例文（同一系统、全考点、语言与实现双模板）。**新页面落组件时以此矩阵查例文实现**；矩阵中「—」= 该组件未在该页出现，属语义未命中，不是遗漏。

The six Chinese examples together cover every core + extended component; `example-kmp.en.html` is the English flagship example (same system, full exam points — the language & implementation template). Consult this matrix when placing a component on a new page; "—" means the component is semantically absent from that page, not an omission.

| 组件 / 形态 | 例文 |
|---|---|
| 标准式页头（kicker + hdr-bar + meta） | 全部六篇 |
| 海报式页头（poster-marks 色票条 + em 词眼） | maxwell |
| wedge-block（G2） | twos · tcp · kmp · maxwell · photoelectric |
| essence-hook（`.hook`） | 全部六篇（breather 节） |
| giant-num（breather 编号） | 全部六篇 |
| giant-verdict（巨字判词） | 全部六篇 |
| plate.full（全装裱） | 全部六篇 |
| plate.light（轻装裱） | tcp（状态图 图 2）· maxwell（图 5） |
| plate-row（图版横列） | twos（三码 punch card 图 2a/2b/2c） |
| rail-hang（G4 outset 左轨出血） | tcp（三次握手主图版 图 1） |
| 三角指针（`.tri` 三态：red 方向 / ink 静止 / paper L2 静止） | tcp（swimlane 交接箭头 图 1/4/7——red 方向、paper 延迟静止） |
| punch card | twos（三码对照 图 2a/2b/2c） |
| memory map | virtual（地址空间 图 1）· tcp / maxwell（借用 mmap-row 布局做对照条，非地址空间语义） |
| nested tree | virtual（两级页表 图 4） |
| exploded frame（爆炸框） | virtual（PTE 图 3） |
| trace（tr-grid + 列题 + 步叙 + 图例） | twos（进位 图 3 + 溢出 图 5）· virtual（翻译 图 5）· tcp（重传 图 5）· kmp（账本 图 8）· photoelectric（V₀–ν 图 5） |
| stepper / step-through（交互，渐进增强） | kmp（匹配走查 图 4）· virtual（缺页 图 7） |
| swimlane | tcp（三次握手 图 1 + 延迟重放 图 4 + 四次挥手 图 7） |
| state diagram | tcp（状态转移 图 2） |
| ascii diagram | tcp（报文段头 图 3） |
| dialogue | tcp（为何两次不够）· photoelectric（波动说 vs 光量子说） |
| warning box | 全部六篇 |
| archival panel（档案面板） | twos（补码定义）· kmp（next 定义 / nextval 优化规则）· maxwell（电磁波定义）· photoelectric（光电效应方程） |
| archive card + 戳记（rotate(-4deg)） | maxwell（史实引文） |
| timetable | maxwell（电磁学演进）· photoelectric（光子学说史） |
| gauge（仪表盘） | virtual（TLB 命中率 图 6）· photoelectric（红限频率 图 2） |
| ratio bar | kmp（省下的比较次数） |
| readout / instrument strip（仪器带） | twos · virtual · tcp · maxwell · photoelectric |
| G1 cut-corner block | photoelectric（截止电压读数面板） |
| G3 circle callout（红圆） | photoelectric（E = hν 焦点） |
| G5 color field（ochre 色场） | maxwell（演进带） |
| G6 nested panel（外层 olive 语境 + 内层 steel 结构面） | kmp（第 03 节双法手算嵌套面板） |
| G7 stair（阶梯组，层级色阶） | maxwell（从实验定律到方程组） |
| G8 collage（拼贴平面，red 硬投影） | maxwell（「光是电磁波」结论）· photoelectric（波粒二象性结论） |
| insight panel | maxwell（方程意义）· photoelectric（应试技巧）· kmp（速算口诀 / 一句话总结） |
| inset panel（G4 inset，olive 底） | twos · virtual · tcp · kmp · photoelectric（worked example / Q&A） |
| split（对称双栏） | photoelectric（装置读数 vs 史纲） |
| staggered（错位双栏） | photoelectric（经典预言 vs 实验事实） |
| asym（非对称网格） | maxwell（方程主栏 + 窄栏读数） |
| causal chain（因果链） | 全部六篇 |
| blueprint callout | twos（丢弃进位 = mod 256）· virtual（位宽拆分）· tcp（滑动窗口）· kmp（哨兵 j=0） |
| code block（ink 黑底 + 语法色） | twos · tcp · kmp · maxwell · photoelectric |
| compare table / data table | 全部六篇 |
| checklist（回顾索引） | 全部六篇 |
| hatching（剖面线） | virtual（未映射区） |
| 密度标注（density-breather / density-dense 类） | 全部六篇 |
| 图版数约定 | 按**图号**计（plate-row 分图 图 2a/2b/2c 计入同号 图 2）；colophon 与正文图号一致 |

## 六篇例文的主题分工 / Theme Division

| 例文 | 教学模式 | 谱系 | 重点覆盖 |
|---|---|---|---|
| `example-twos-complement.html` | 工程理解（R1 红楔） | 印刷族 | 图版制、punch card、plate-row、trace、blueprint callout、compare table |
| `example-virtual-memory.html` | 工程理解（R2 蓝图） | 图纸族 | memory map、nested tree、exploded frame、gauge、trace、stepper、剖面线 |
| `example-tcp.html` | 工程理解（R1 红楔） | 印刷族 + 图纸族 | swimlane、state diagram、ascii、dialogue、plate.light、warning、trace |
| `example-kmp.html` | 考点教学（408） | 图纸族 | archival panel、stepper/step-through、causal chain、ratio bar、warning box、code block |
| `example-maxwell-equations.html` | 工程理解（R3 档案） | 印刷族 | 海报式页头、timetable、archive card、G5 色场、G7 stair（层级色阶）、G8 collage、asym |
| `example-photoelectric-effect.html` | 工程理解（R1 + R3） | 印刷族 | G1、G3 红圆、gauge、dialogue、staggered、insight panel、split |
| `example-kmp.en.html` | 考点教学（EN） | 图纸族 | English flagship — same 10 figures & complete teaching coverage as example-kmp.html (no exam-oriented framing); language & implementation template |
