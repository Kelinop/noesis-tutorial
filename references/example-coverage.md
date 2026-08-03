# Example Coverage Matrix — 例文 × 组件覆盖矩阵

六篇例文共同覆盖全部 core + extended 组件（SKILL.md 组件与装裱 → style-guide 全部 Specs）。**新页面落组件时以此矩阵查例文实现**；矩阵中「—」= 该组件未在该页出现，属语义未命中，不是遗漏。

| 组件 / 形态 | 例文 |
|---|---|
| 标准式页头（kicker + hdr-bar + meta） | 全部六篇 |
| 海报式页头（poster-marks 色票条 + em 词眼） | maxwell |
| wedge-block（G2） | twos · tcp · kmp · maxwell · photoelectric |
| essence-hook（`.hook`） | 全部六篇（breather 节） |
| giant-num（breather 编号） | 全部六篇 |
| giant-verdict（巨字判词） | twos · virtual · tcp · kmp · photoelectric |
| plate.full（全装裱） | 全部六篇 |
| plate.light（轻装裱） | tcp（状态图 图 2） |
| plate-row（图版横列） | twos（三码 punch card 图 2a/2b/2c） |
| rail-hang（G4 outset 左轨出血） | virtual（PTE 图 4） |
| punch card | twos（三码对照）· virtual（VA 位划分） |
| memory map | virtual（地址空间 图 1） |
| nested tree | virtual（两级页表 图 3） |
| exploded frame（爆炸框） | virtual（PTE 图 4）· tcp（标志位 图 4）· maxwell（方程项 图 2） |
| trace（tr-grid + 列题 + 步叙 + 图例） | twos（进位 图 3）· kmp（前缀-后缀 图 1 + 真题） |
| step trace（st-grid） | virtual（翻译走查 图 5） |
| stepper / step-through（交互，渐进增强） | kmp（匹配过程手推） |
| swimlane | tcp（三次握手 图 1） |
| state diagram | tcp（状态转移 图 2） |
| ascii diagram | tcp（报文段头 图 3） |
| dialogue | tcp（为何两次不够）· photoelectric（波动说 vs 光量子说） |
| warning box | kmp（next 易错陷阱）· tcp（半连接 / SYN flood） |
| archival panel（档案面板） | kmp（next 定义 / nextval 优化规则） |
| archive card + 戳记（rotate(-4deg)） | maxwell（史实）· photoelectric（历史） |
| timetable | maxwell（电磁学演进）· photoelectric（光子学说史） |
| gauge（仪表盘） | virtual（TLB 命中率）· photoelectric（红限频率） |
| ratio bar | kmp（省下的比较次数）· photoelectric（光子能量分配） |
| readout / instrument strip（仪器带） | twos · virtual · tcp · photoelectric |
| G1 cut-corner block | photoelectric（截止电压读数面板） |
| G3 circle callout（红圆） | photoelectric（E = hν 焦点） |
| G5 color field（ochre 色场） | maxwell（演进带）· photoelectric（史纲条带） |
| G6 nested panel | kmp（手算 worked example 嵌套） |
| G7 stair（阶梯组） | maxwell（从实验定律到方程组） |
| G8 collage（拼贴平面，red 硬投影） | maxwell（「光是电磁波」结论） |
| insight panel | maxwell（方程意义）· photoelectric（应试技巧） |
| inset panel（G4 inset） | kmp（真题手算内嵌） |
| split（对称双栏） | tcp（两次 vs 三次）· photoelectric（波动 vs 粒子现象） |
| staggered（错位双栏） | photoelectric（经典预言 vs 实验事实） |
| asym（非对称网格） | maxwell（方程主栏 + 窄栏读数） |
| causal chain（因果链） | kmp（BF 失败 → KMP 设计） |
| blueprint callout | twos（丢弃进位 = mod 256） |
| code block | twos · kmp · maxwell（方程）· photoelectric（计算） |
| compare table / data table | twos（三码对照）· kmp（真题表）· maxwell（四方程表） |
| checklist（回顾索引） | 全部六篇 |
| hatching（剖面线） | virtual（未映射区）· photoelectric（史纲剖面） |
| 图版数约定 | 按**图号**计（plate-row 分图 图 2a/2b/2c 计入同号 图 2）；colophon 与正文图号一致 |

## 六篇例文的主题分工

| 例文 | 教学模式 | 谱系 | 重点覆盖 |
|---|---|---|---|
| `example-twos-complement.html` | 工程理解（R1 红楔） | 印刷族 | 图版制、punch card、plate-row、trace、blueprint callout、compare table |
| `example-virtual-memory.html` | 工程理解（R2 蓝图） | 图纸族 | memory map、nested tree、exploded frame、gauge、rail-hang、剖面线 |
| `example-tcp.html` | 工程理解（R1 红楔） | 印刷族 + 图纸族 | swimlane、state diagram、ascii、dialogue、split、plate.light |
| `example-kmp.html` | 考点教学（408） | 图纸族 | archival panel、stepper/step-through、causal chain、ratio bar、warning box、G6 |
| `example-maxwell-equations.html` | 工程理解（R3 档案） | 印刷族 | 海报式页头、timetable、archive card、G5 色场、G7 stair、G8 collage、asym |
| `example-photoelectric-effect.html` | 工程理解（R1 + R3） | 印刷族 | G1、G3 红圆、gauge、dialogue、staggered、insight panel、split |
