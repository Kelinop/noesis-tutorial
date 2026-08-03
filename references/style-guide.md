# Style Guide — Tokens & Component Specs

**用法**：Tokens 是法（精确值，不可改）；Specs 是意图与约束——**据此自己写 CSS，不要寻找成品模板**。组件的完整实现范例见 `references/example-*.html` 六篇例文（组件覆盖矩阵见 `example-coverage.md`）。

色彩语义（色层模型）、轴线与几何语义见 `visual-system.md`，此处不重复。

## Tokens

```css
:root {
  /* Palette — 色层 L0–L5 */
  --paper: #f1ece2;      /* L0 空气/图底 */
  --ink: #1c1c1c;        /* L1 主结构 */
  --steel: #637880;      /* L1 次结构（只做线与字级注释） */
  --blue: #0f4c81;       /* L2 图纸底 */
  --blue-note: #9db8cc;  /* L2 注释 */
  --ochre: #b8863b;      /* L3 档案（永不做文字色） */
  --white: #ffffff;      /* L4 纸卡（仅 sidebar / 浮起 UI / punch 孔位，见白卡作用域） */
  --red: #e63946;        /* L5 事件（动词） */
  --deep-red: #cc2a26;   /* L5 焦点（名词） */

  /* Typography — 四字体系统 */
  --font-sans: "IBM Plex Sans", "Noto Sans SC", sans-serif;
  --font-mono: "Google Sans Code", "Noto Sans SC", monospace;
  --font-num:  "Urbanist", "IBM Plex Sans", sans-serif;

  /* Type scale */
  --text-xs: 0.75rem;
  --text-sm: 0.875rem;
  --text-base: 1rem;
  --text-lg: 1.25rem;
  --text-xl: 1.75rem;
  --text-2xl: 2.5rem;
  --text-3xl: 4rem;

  /* Spacing */
  --gap-xs: 0.5rem;
  --gap-sm: 1rem;
  --gap-md: 2rem;
  --gap-lg: 4rem;

  /* Board — 居中对称留白（默认态） */
  --board-max: 1240px;      /* 带 sidebar；两侧对称留白（1600 视口每侧 ≈180px） */
  --main-max: 980px;        /* 不带 sidebar 主栏（居中） */
  --rail: 3rem;             /* 页缘标尺左轨 */
  --text-rail: 46rem;       /* 文字轨 ≈68 字符 */
}
```

CDN（放 `<head>`；字重纪律见 `visual-system.md` → Typography Discipline）：

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=IBM+Plex+Sans:wght@300;400;500;600&family=Noto+Sans+SC:wght@300;400;500;600&family=Urbanist:wght@300;400;500;600&family=Google+Sans+Code:wght@400;500;600&display=swap" rel="stylesheet">
```

**轴线实现（数值源）**（贯穿所有斜切件）：切角深度与组件设计高度成比例（≈0.36 = tan20°），参考高度下精确 20°，内容高度差异 ±2° 内波动：

```text
kicker / 小切角件   → 8px  （参考高 ~24px）
标题带 / 大切角件   → 16px （参考高 ~44px，单行）
楔形块             → 56px （参考高 ~154px，内容 ≤2 行）
三角指针           → 5px  （参考高 14px）
分隔线 / 剖面线     → repeating-linear-gradient(110deg, …)（条纹与轴线平行）
```

**文字安全总规则**：斜切只发生在组件**底部呼吸区**（padding 区），禁止切入文本区。斜切件的底部 padding 必须 ≥ 文本区底边到组件底边的距离 + 切角深度；含轴线的组件遵守本规则，否则不用斜切。G1 切角是「棱角」豁免（固定 20–24px），不参与轴线判定。

Body base：font-sans / 1rem / line-height 1.7 / ink on paper / 必加 `-webkit-font-smoothing: antialiased`、`-moz-osx-font-smoothing: grayscale`、`text-rendering: optimizeLegibility`（Windows 防过粗）。

## Layout Specs

### Board（板面）

- 带 sidebar：`.board` = grid `220px 1fr`，`max-width: var(--board-max)`，`margin: 0 auto`——**居中，左右对称留白**；padding `gap-md`；≤768px 塌单栏。
- 不带 sidebar：主栏 `max-width: var(--main-max)`，`margin: 0 auto` 居中。
- **对称默认规则**：板面与组件排布默认对称；非对称（偏左板面、右侧留白、左轨出血、非对称网格、错位双栏）仅在能论证"带来了语义增益"时使用（主从层级、权重差异、强调/突破），论证不了就回到对称。
- **双轨**：`.text-rail`（正文段落、hook、dialogue、判词类组件）`max-width: 46rem`；图版轨 = 主栏全宽（居中板面内）。文字窄、图版宽。
- 左轨：≥1100px 时主栏 `padding-left: 3rem`（标尺轨）。

### Edge Ruler（页缘标尺，≥1100px 显示）

标尺 = **纯静态刻度**（tick），无竖线、无滚动进度条（进度条仅存在于 sidebar 底部，见 Sidebar 节）：

```css
.article { position: relative; }
.ruler-tick { display: none; }   /* <1100px 全部隐藏（含 768–1100px 区间） */
@media (min-width: 1100px) {
  .article { padding-left: var(--rail); }
}
```

- **禁止任何贯穿页面的竖线与滚动红线**——steel 只做字级注释，永不成线/面；red 不用于页面级装饰线。

- 每节锚点处一枚刻度（**编号单一权威**）：

```html
<span class="ruler-tick" aria-hidden="true">
  <span class="rt-num">04</span><span class="rt-word">MECH.</span>
</span>
```

```css
/* 定位上下文是 section（section 左缘 = rail 右缘）：left: 0 + translateX(-100%)
   使刻度完全落在标尺轨内，右边缘贴内容区左缘——不得再叠加 rail 偏移（会压进内容区） */
.ruler-tick { display: none; }
@media (min-width: 1100px) {
  .ruler-tick { display: block; position: absolute; left: 0; top: var(--gap-md);
                transform: translateX(-100%); text-align: right; padding-right: 9px; }
}
.ruler-tick::before { content: ""; position: absolute; right: -4px; top: 50%;
                      width: 14px; height: 2px; background: var(--ink); }
.rt-num { font-family: var(--font-num); font-weight: 600; font-size: var(--text-sm); display: block; }
.rt-word { font-family: var(--font-mono); font-size: 0.6rem; letter-spacing: .25em;
           color: var(--steel); display: block; }
```

- **<1100px：全部刻度隐藏**，编号由 `.sec-num`（section 标题内 num 前缀）承担。

### Sidebar（canonical 导航）

- 左侧竖列 `position: sticky; top: gap-md`；ink 3px 边框、白底（L4）；头行 ink 底 paper 字「目录」；四角对版小直角（与图版对版十字呼应）。
- 条目：block 链接，steel 1px 下边框；条目编号 num 字体；`.active` = 左 4px red 边 + red 600 字；hover 变红。
- 底部轨（`.sb-track`）内左侧 4px 竖向 red 进度条（唯一进度条，`height = scroll%`；JS 渐进增强，无 JS 时隐藏，rAF + passive scroll listener）。
- ≤768px：`position: static` 置于顶部，全宽**竖排**列表——绝不折叠成横向 strip。
- 每个链接 `href="#id"` 与 `<section id="…">` 一一对应；scroll-spy（可选）：IntersectionObserver `rootMargin: '-20% 0px -70% 0px'`；无 JS 不影响跳转。

### Crop Marks（四角对版标记，≥1100px）

```html
<div class="crop-marks" aria-hidden="true"><i class="c1"></i><i class="c2"></i><i class="c3"></i><i class="c4"></i></div>
```

固定定位、pointer-events none、四角 2px ink L 形（14px 边长、8px 内距）。不选整页外框。

### Sections

- 容器：`border-top: 4px solid ink`；padding `gap-md 0`；标题 text-2xl / 600 / tracking -0.02em；标题前 `.sec-num`（num 字体 600 text-lg，仅 <1100px 显示——≥1100px 编号由标尺刻度承担，编号单一权威）。
- **breather 节编号例外**：breather 节可不放 `.sec-num` 与 ruler-tick——编号由 `.giant-num` 承担（例：essence 节），标尺/侧栏编号照常按节序。
- 密度标注（Step 4 决定，类名落进 section）：`.density-breather`（padding `gap-lg 0`，组件间距 gap-lg，giant-num 可用）、`.density-standard`（默认）、`.density-dense`（组件间距 gap-sm，图纸连片）。**dense ≠ 深色**：呼吸带规则始终有效。
- Accent 映射（border 与 section-tag 同色；类名以示例实现为准）：`problem`（原始问题）/ `misunderstanding` → red；`essence` → deep-red；`tradeoff` → steel；`evolution` → ochre（档案语义，tag 文字 ink）；`mechanism` / `system-impact` → 默认 ink。
- `.section-tag`：ink 底 paper 字，mono xs，+0.1em。
- `.giant-num`（仅 breather 节，编号回显）：num 字体 5rem（≤768px 3rem），paper 填充 + ink 2px 描边，@supports 回退 steel 35% 透明。

### Page Header（二选一）

- **标准式**：cut-corner kicker（ink 底 paper 字 mono xs，右下切角，切角 8px）+ text-3xl 标题 + 4rem×8px red bar（每页仅一处）+ steel 副题 text-lg 500 + meta 行。
- **海报式**：顶部 flex（cut-corner + `.poster-marks` 色票条——ink / red / deep-red / ochre 四个 12px 小方块，编码页面自身色板）+ `clamp(2.5rem, 7vw, 4rem)` 标题（`em` 词眼 6px red 下划线）+ meta 行。
- kicker 切角 8px（小切角件，轴线系）。

### Section Band（斜切标题带，机制重心声明，一页最多一节）

```css
.section-band {
  display: inline-block;
  background: var(--ink); color: var(--paper);
  padding: var(--gap-xs) calc(var(--gap-md) + 16px) var(--gap-xs) var(--gap-sm);
  clip-path: polygon(0 0, 100% 0, calc(100% - 16px) 100%, 0 100%); /* 大切角件：16px ≈ 20°（参考高 ~44px） */
  margin-bottom: var(--gap-sm);
}
```

- 单行标题带高度固定 → 斜切吃掉底部呼吸区，文本安全。带内不再放其他组件；正文从带下方开始。
- ≤768px 切角深度不变（16px 是轻量细节）。

### Giant Verdict（巨字判词，extended，一页最多一处）

```css
.giant-verdict {
  font-size: clamp(2.5rem, 6vw, 4.5rem);
  font-weight: 600; /* 展示巨字允许（字重纪律上限） */
  line-height: 1.2;
  letter-spacing: -0.02em;
  margin: var(--gap-lg) 0;
}
.giant-verdict em { font-style: normal; border-bottom: 6px solid var(--red); }
```

- 四条硬规则：机制段的结论句；≤2 行；位于机制→权衡转折点；**必须被回顾段 checklist 引用**（`<a href="#verdict-1">` 锚点闭环）。无编号无组件，L0 上 ink 字。

### 宽度参差（Width Rhythm）

- 全宽：机制图解（trace / swimlane / SVG / punch card）、表格、图纸层容器、图版——内容本体。
- 收窄 85%：判词类组件（wedge block、insight panel）；≤768px 回 100%。
- 连续同宽组件说明宽度层级没有编码内容权重——评审时让其中一个换宽度层级或几何形态（形态有效性核验，不是次数规则）。
- **散文容器文字轨**：essence-hook、`.dialogue .a`、warning-box 等散文容器 `max-width: var(--text-rail)`——散文收进文字轨，不随图版轨全宽。
- **超宽处理**：表格 / ASCII / 位格式超出文字轨时横向滚动（`overflow-x: auto`）或等比缩放，不得撑宽文字轨——桌面端与 ≤768px 同样适用。

### 白卡作用域

**规范（规范源）**：见 `visual-system.md` → 色层模型 L4 行与禁令·白卡作用域——`--white` 只允许三处：sidebar、页面级浮起 UI（按钮 hover、G8 拼贴浮动平面）、punch card 孔位。

**容器类名实现清单**（全量注册：以下内容容器禁白底，表面三选一）：

- **机制类** → L2 图纸底（blue + 4–6% paper 网格；注释用 blue-note，focus 用 red，deep-red 禁落蓝底）：trace（`.tr-grid` / `.st-grid`）、swimlane、stepper、ascii-diagram、code-block（`.code`）、punch-card、memory-map（`.mmap-row`）、nested-tree（`.nt-node`）；
- **陈述类** → L0 透明底，仅靠边框 / 硬阴影成型——不出现「卡片」轮廓：essence-hook（`.hook`）、insight-panel、inset-panel、warning-box、dialogue 答案（`.dialogue .a` / `.b`）、stair-item、collage-main、circle-callout、cause-node / state-box / msg-label、readout、ratio-bar、blueprint-callout（`.bp-callout`）、exploded-frame（`.x-frame`，无底）、tables（`.cmp` / `.data-table`）、checklist；
- **档案类** → L3 ochre 带：archive-card、archival-panel（`.archival-panel`）、timetable。

### 红面阈值

**阈值定义（数值源）**：见 `visual-system.md` → 色层模型 L5 行（红面阈值 · 数值源：块 / 面 / 每屏 ≤1% / 红圆例外的完整定义与豁免）。本节只列处置动作。

**处置动作（实现规格）**：

- ratio bar 红段高 ≤24px，或改 **2px red 边框 + paper 底 + red 数值字**（保留「事件」语义但不成面）；
- 表格表头禁止红底（改 deep-red 文字 + 红色左划线）；
- trace 失败格保持格级尺寸（≤32×32 参考），且格间保留 ink/paper 分隔（结构性间距）；
- **红圆唯一例外**：实心红圆直径 ≤128px、语义必须为压力/转折性结论（Rodchenko 红日）——其余红色一律遵守本节阈值。

### 横向构成

```css
/* 错位双栏：两栏并行但不同步，第二栏下移 gap-md */
.staggered { display: grid; grid-template-columns: 1fr 1fr; gap: var(--gap-md); align-items: start; }
.staggered > *:nth-child(2) { margin-top: var(--gap-md); }
/* ≤768px 塌单栏，错位归零 */

/* 图版横列：2–3 块同主题小图版并置，独立图号 图 3a/3b */
.plate-row { display: grid; grid-template-columns: repeat(auto-fit, minmax(0, 1fr)); gap: var(--gap-md); }
.plate-row .plate { margin: 0; }
/* ≤768px 塌纵列 */

/* 仪器带：一组测量件共用一条基线与 steel 基线尺 */
.strip { display: flex; align-items: flex-end; gap: var(--gap-md);
         border-bottom: 2px solid var(--steel); padding-bottom: var(--gap-sm);
         margin: var(--gap-md) 0; }

/* 左轨出血：≥1100px 图版左缘挂进标尺轨 1.5rem */
@media (min-width: 1100px) {
  .rail-hang { margin-left: -1.5rem; }
}

/* 非对称网格：主 2/3 + 窄栏 1/3，窄栏永远在右——对称默认规则的合法例外（主从语义） */
.asym { display: grid; grid-template-columns: 2fr 1fr; gap: var(--gap-md); align-items: start; margin: var(--gap-md) 0; }
.asym > * { min-width: 0; margin-top: 0; margin-bottom: 0; }
/* 语义：主从 / 权重差异；等价内容用 split（对称）；窄栏只容纳垂直友好组件（readout / ratio bar 入窄栏改纵向堆叠）；≤768px 塌单栏 */
```

纪律：对称是默认态；非对称只用于语义需要表达主从/权重/强调的场合，且必须能论证语义增益，论证不了就用对称。横向元素共享基线或轴线，不允许各自为政的漂移。**split（对称双栏）**：等价内容并置（非主从）——与 asym 区分，两栏同基线、无错位；≤768px 塌单栏。

## Plate Specs（图版装裱三级）

```css
.plate { position: relative; margin: var(--gap-md) 0; }
.plate.full { border: 2px solid var(--ink); padding: var(--gap-sm); }
.plate.light { border: none; }

.plate-marks i { position: absolute; width: 8px; height: 8px; }
.plate-marks .m1 { top: -2px; left: -2px;  border-top: 2px solid var(--ink); border-left: 2px solid var(--ink); }
.plate-marks .m2 { top: -2px; right: -2px; border-top: 2px solid var(--ink); border-right: 2px solid var(--ink); }
.plate-marks .m3 { bottom: -2px; left: -2px;  border-bottom: 2px solid var(--ink); border-left: 2px solid var(--ink); }
.plate-marks .m4 { bottom: -2px; right: -2px; border-bottom: 2px solid var(--ink); border-right: 2px solid var(--ink); }

.fig-num { display: inline-block; background: var(--ink); color: var(--paper);
           font-family: var(--font-mono); font-size: var(--text-xs);
           padding: 2px 10px; letter-spacing: .1em; margin-bottom: var(--gap-xs); }
.plate-caption { font-family: var(--font-mono); font-size: var(--text-xs);
                 color: var(--steel); margin-top: var(--gap-xs); }
.plate-caption .cap-num { color: var(--deep-red); font-weight: 600; }
.fig-ref { color: var(--ink); font-weight: 600; border-bottom: 2px solid var(--red); text-decoration: none; }
```

- **全装裱**：2px ink 框 + 四角对版十字 + 图号 + 图题。机制类组件（图解/trace/swimlane/punch card/爆炸框）默认全装裱。
- **轻装裱**：无框，仅对版十字 + 图号 + 图题。独立成立但非主图的展件。
- **不装裱**：流式，随文。小 SVG、轻量示意。
- **图版必须被引用**：正文交叉引用 `图 N`（`.fig-ref`），或图题本身传达机制结论。无人引用的图版 = 装饰。
- 图版框保持正交矩形，框上不得加对角线动作。
- **图版内衬**：进入图版框的 L2 容器 padding ≥ gap-md，图纸内容不贴框线。
- **深色间距表**：数值与判定见 visual-system → 禁令·深色间距表（数值源）；深色贴边按间距表判定，不按「接触视口边缘」（滚动瞬态误报）。
- HTML 约定：`<figure class="plate full" id="fig-2">`；图号 `<span class="fig-num">图 2</span>`；图题 `<figcaption class="plate-caption">图 2：…</figcaption>`。
- 图版内禁用 L4 白卡（内容直接在 L0/L2 上）；机制节内组件进图版后转 L2 图纸底（trace / swimlane / stepper / ascii / punch-card 一律图纸底，无论是否进图版）。

### Colophon（印刷版权条）

```css
.colophon { border-top: 2px solid var(--ink); margin-top: var(--gap-lg);
            padding: var(--gap-xs) 0; font-family: var(--font-mono);
            font-size: var(--text-xs); color: var(--steel);
            letter-spacing: .05em; display: flex; gap: var(--gap-md); flex-wrap: wrap; }
```

内容：版式 / 字体 / 色版（ink·red·blue·ochre）/ 图版数 N / 轴线 20°。与页头色票首尾呼应。

## Geometric Specs（几何容器 G1–G8）

> **贯穿技术前提**：`clip-path` 会裁切 `border` 与 `box-shadow`——G1/G2 容器一律不设 border 与 box-shadow，轮廓由剪影承担；任何组件不得组合 clip-path 与 border/box-shadow。G1 切角是「棱角」，不参与轴线判定，保持固定小切角；G2 楔形与标题带等斜切件参与轴线（tan 公式 + 文字安全总规则）。

### G1 Cut-Corner Block（切角容器）

- 语义：工业精度。固定切角 20–24px（右下切，默认方向；**切角一律在右侧**）。
- 防裁规则：切角方向 padding ≥ 切角深度 + 正常内边距。

### G2 Wedge Block（楔形块）

- 语义：力量方向——只用于全页最强的冲突/转折点；每处都用楔形，力量就均匀了。
- 默认 ink 底 paper 字反转；宽度收窄 85%（≤768px 回 100%）。

```css
.wedge-block {
  width: 85%;
  background: var(--ink); color: var(--paper);
  padding: var(--gap-sm) 3rem;
  padding-bottom: 5rem;   /* 文字安全：斜切只发生在底部呼吸区 */
  margin: var(--gap-md) 0;
  clip-path: polygon(0 0, 100% 0, calc(100% - 56px) 100%, 0 100%); /* 56px ≈ 20°（参考高 ~154px） */
}
```

- **内容限制 ≤2 行**（判词）；更长内容禁用楔形（改用 insight panel 或色场）。文字安全由「≤2 行 + padding-bottom 5rem + padding-right 3rem」共同保证。
- 反向楔形（指向左）用镜像 polygon（方向与轴线同系）。

### G3 Circle Callout（圆形标注）

- 语义：焦点声明。ink 圆框 = 普通焦点；**red 圆框 = 事件级焦点**（该焦点同时是压力/转折性结论，Rodchenko 红日）——语义成立才用，同屏不出现两个等重焦点互抢。机制径向圆（SVG 钟面、环）不受此约束。
- 规格：直径 8rem（≤768px 6rem）；`border-radius` 两处例外之一（另一处为 punch card 孔位）。

### G4 Offset Block（偏移块）

- 语义：位置偏移即关系声明——**inset（内嵌）** = 附属/批注（内容从属于正文流）；**outset（外挂）** = 强调/突破（组件被标尺「测量」）。
- 解剖：

```text
│ rail │ 内容区（主栏）
│      │ ┌─ inset：流内面板（ink 边框 / 硬阴影，L0 底，随文）
│  04  │ │
│   ┌──┼─ outset：左缘挂出 1.5rem 进标尺轨（图版 / giant-num / 判词类）
│   │  │
```

- 规则：
  - **inset**：陈述类表面（L0 透明底 + ink 边框或硬阴影，无圆角）、不装裱、散文收文字轨——即 inset-panel 的容器语义（见 Form Specs → 陈述类容器通则）；
  - **outset**：仅 ≥1100px 生效（`.rail-hang`，挂出 1.5rem——实现规格见 Layout Specs → 横向构成）；<1100px 与 ≤768px 偏移归零；
  - outset 属对称默认规则的**例外**（强调/突破语义）——须能论证「该组件是所在节的重心」，论证不了回对称。
- 形态理由（规则 B）：附属/突破 → offset → 编码「内容与正文流的从属关系」，位移方向即关系方向。

### G5 Color Field（色场）

- 语义：段落级材料归属声明——**ink 场** = 结构/判词区（标题带、判词的场化形态）；**ochre 场** = 档案区（L3 档案层的条带形态，史料/演进）。
- 解剖：通栏或收窄 85% 的纯色矩形容器；ink 场上 paper 反白字，ochre 场上 ink 字（ink/ochre ≈5.3:1 达标 AA）；内承组件随场换色板，不加新色相。
- 规则：
  - **只用 ink / ochre**——blue 只承载可测量内容（L2 图纸）、red 永不成面（红面阈值）、steel 永不成面，均不得作色场；
  - ochre 场面积 ≤ 所在 section 一半；不与 L2 相邻（≥gap-md，色层禁令）；永不做文字色；
  - ink 场之间由 L0 呼吸带分隔（骨架连成天际线而非墨点）；
  - 色场计入连续深色（60% 规则），dense 节同样受限；
  - ≤768px padding 缩为 `gap-md gap-sm`。
- 形态理由（规则 B）：氛围/归属 → color field → 编码「段落级材料归属」，场色即色层职能。

### G6 Nested Panel（嵌套面板）

- 语义：面板套面板 = 包含/从属——外层是语境，内层是内容（容器级嵌套；层级包含的完整图解形态用 Nested Tree，见 Form Specs）。
- 解剖：外层容器（ink 边框，L0 底）+ 内层面板；机制节内整体进图版时转 L2 图纸底，内层组件（stepper 等）随之图纸化；层级标签 mono 小字（次结构注释：L0 底 steel，图纸化后改 blue-note）。
- 规则：
  - 嵌套必须编码「包含」关系本身——退化为纯缩进列表时改用列表 / stair（规则 A，与 Nested Tree 同判据）；
  - 机制类 → 随所在图版装裱；陈述类 → 不装裱、保持流式；
  - 内层表面遵守白卡作用域三选一（机制 → L2 / 陈述 → L0 / 档案 → L3），禁白底；
  - 内衬 ≥gap-md（进图版框按图版内衬）。
- 形态理由（规则 B）：语境包含内容 → nested panel → 编码「外层语境 × 内层内容」的几何从属。

### G7 Stair Group（阶梯组）

- 语义：**递进构建**——每项建立在前项之上（推导链、复杂度递增、抽象升级）；扁平枚举禁用（递进是语义前提，不是造型）。
- 解剖：

```text
┌ 级 1 ──────────────
    └ 级 2 ──────────────
        └ 级 3 ──────────────   ← 级间错位方向与 20° 轴线同系
```

  2–4 级 stair-item（陈述类表面：L0 透明底 + ink 边框/硬阴影）；级号 num 字体；末级结论可用 deep-red 词眼（落 L0）。
- 规则：
  - **≤4 级**——超过拆分为两组或改用 causal chain（与 Nested Tree 层级上限同级数）；
  - 各项无先后依赖关系时禁用，改用列表；
  - 陈述类 → 不装裱、保持流式；散文收文字轨；
  - ≤768px 退化竖排，错位归零。
- 形态理由（规则 B）：递进构建 → stair → 编码「步骤的先后依赖与爬升方向」，级位即进度。

### G8 Overlapping Planes（重叠平面 / 拼贴）

- 语义：**结论从证据浮现**——浮动平面承载判词，压在下层证据平面之上（系统影响节的「高点」形态；collage 的容器语义）。
- 解剖：下层 = 证据平面（L0 上流式组件 / 图版残片）；上层 = 浮动平面（**L4 白底**——白卡三处豁免之「页面级浮起 UI / G8 拼贴浮动平面」）+ 硬投影 `8px 8px 0 red`（判词以事件方式落下，投影无模糊）。
- 规则：
  - 浮动平面是内容级容器中唯一合法白底（L4 豁免）；其余表面禁令照常；
  - 硬投影只用 red（事件色），禁渐变/柔化；
  - 与巨字判词**二选一**——同一「系统影响」高点不叠加两种高潮形态（教学映射「拼贴平面 或 巨字判词」）；
  - ≤768px 浮动平面转静态全宽，重叠归零。
- 形态理由（规则 B）：结论浮现于证据 → overlapping planes → 编码「层级压叠 = 结论高于证据」，红投影即事件落点。

## Instrument Specs（测量仪器）

### Triangle Pointer（三角指针）

```css
.tri { width: 14px; height: 14px; background: var(--red);
       clip-path: polygon(0 0, 100% 0, calc(100% - 5px) 100%); } /* 5px ≈ 20°（参考高 14px） */
```

- 斜边与轴线同系；红色做方向/起点，ink 做静止指示。禁用对称正三角。
- 场景：序列起点、仪表指针尖、消息箭头、图解指示点。

### Exploded Frame（爆炸框）

```css
.x-frame { position: relative; padding: var(--gap-sm) 0 var(--gap-sm) 5rem; }
.x-level { display: flex; gap: var(--gap-sm); align-items: baseline;
           margin: var(--gap-sm) 0; }
.x-level:nth-child(2) { margin-left: -1.5rem; }   /* 沿轴线逐级左移（错位方向与轴线同系） */
.x-level:nth-child(3) { margin-left: -3rem; }
.x-level:nth-child(n+4) { margin-left: -4.5rem; }
.x-tag { font-family: var(--font-mono); font-size: var(--text-xs);
         color: var(--paper); background: var(--ink); padding: 1px 8px;
         letter-spacing: .1em; flex-shrink: 0; }
.x-key .x-tag { background: var(--red); }
```

- 语义：机制分解为「零件陈列」——沿轴线方向逐级错位（无引线）；末级（结果/丢弃/终点）用 red tag（事件）。静态，无动画。
- 默认进图版框（全装裱）；错位方向与轴线同系（自右上向左下）。

### Gauge（仪表盘）

- SVG 径向：圆弧 + 刻度 + 指针（red 三角指针做指针尖）。只用于**阈值型读数**（负载因子、水位、利用率、开销逼近阈值）；线性读数用 readout / ratio bar。
- 指针角度 = 读数，不受轴线约束（轴线约束切角几何，不约束仪表读数）。刻度 blue-note（steel 禁落 L2；仪表整体落 L0 时可用 steel），结构 ink 3px。
- 禁动画；`role="img"` + `aria-label` 描述读数含义。

### Hatching（剖面线）

```css
.hatch { background-image: repeating-linear-gradient(110deg,
         var(--ink) 0 2px, transparent 2px 8px); }
.hatch.red { background-image: repeating-linear-gradient(110deg,
         var(--red) 0 2px, transparent 2px 8px); }
.hatch.paper { background-image: repeating-linear-gradient(110deg,
         var(--paper) 0 2px, transparent 2px 8px); }
```

- 条纹与轴线平行（110deg 梯度方向 → 条纹走向 = 20° 自水平线，与轴线同向）。仅 ink/paper/red 单色系；非明显时必须带图例。剖面线 = 材料/角色身份，不加新色相。

## Form Specs（认知形态）

本节规格：Dialogue / Swimlane / Nested Tree / Readout / Timetable / Blueprint Callout / Punch Card / Ratio Bar（+ 竖排变体）。

### Punch Card（打孔卡）

> 认知映射：位模式 / 编码 / 指令格式（SKILL.md → Form Selection）。一张卡片 = **左轨字段名（L0）+ 右轨孔阵（L2）** 两种材料区，由 grid 分栏承载，不共享表面。

**解剖**：

```text
┌────────────────────────────────────────┐
│ sign  │ 7  6  5  4  3  2  1  0 │ 注释   │ ← 位号行（blue-note num 字，只落 L2）
│ bit   │ ○  ○  ●  ○  ○  ●  ○  ○ │ blue- │ ← 孔阵行（L2 图纸底 + paper 网格）
│       └───────────────────────┘ note   │
│ ↑ L0 轨（deep-red 字段名）  ↑ L2 图纸底 │
└────────────────────────────────────────┘
```

- **字段名轨 `pc-key`**：卡片左列，L0 纸底上的 deep-red mono 标签（字级）。deep-red = 名词/铆钉，**只落 L0 轨——禁落孔阵蓝底**（deep-red 对 blue ≈1.7:1，对比度不足；蓝底上的焦点改用 red）。字段名不属图纸内容。
- **孔阵 `pc-bits`**：右列 L2 图纸底（blue + 4–6% paper 坐标网格）；进入图版框后内衬 padding ≥ gap-md（图版内衬）。
- **位号行 `pc-idx`**：孔阵顶部，blue-note num 字体位号（7 6 5 … 0）——只落 L2。
- **格 `pc-bit`**：圆形位单元，直径 24px。两种状态：
  - `pc-hole`（孔 = 1）：**实心 white 圆**——white 三处豁免之一（punch 孔位）+ `border-radius: 0` 两处例外之一；
  - 无孔（0）：blue-note 1.5px 空心圆环（透明底，仅描边）——0 的可见性由描边承担，不新增表面。
- **行尾注释 `pc-note`**：blue-note 小字（字段语义、机制说明），只落 L2。

HTML 骨架：

```html
<figure class="plate full" id="fig-2">
  <span class="fig-num">图 2</span>
  <div class="punch-card" role="img" aria-label="原码 5 = 00000101 的位格式">
    <div class="pc-row">
      <span class="pc-key">符号位</span>
      <span class="pc-idx" aria-hidden="true">7 6 5 4 3 2 1 0</span>
      <span class="pc-bits" aria-hidden="true">
        <span class="pc-bit"></span><span class="pc-bit"></span><span class="pc-bit pc-hole"></span>
      </span>
      <span class="pc-note">主动路径：进位链</span>
    </div>
  </div>
  <figcaption class="plate-caption">图 2：符号位与数值位分离，取模自动完成</figcaption>
</figure>
```

CSS 骨架（据此自写，非成品模板）：

```css
.punch-card { background: var(--blue); padding: var(--gap-md);
              display: grid; gap: var(--gap-sm); }
.pc-row { display: grid; grid-template-columns: auto auto auto 1fr;
          align-items: center; gap: var(--gap-sm); }
.pc-key { color: var(--deep-red); font-family: var(--font-mono);
          font-size: var(--text-xs); font-weight: 600; letter-spacing: .1em; }
.pc-idx { font-family: var(--font-num); color: var(--blue-note);
          font-size: var(--text-xs); }
.pc-bits { display: flex; gap: 6px; }
.pc-bit { box-sizing: border-box; /* 孔与环同外径 24px——否则环 27px，多行孔阵位号列错位 */
          width: 24px; height: 24px; border: 1.5px solid var(--blue-note);
          border-radius: 50%; }
.pc-bit.pc-hole { background: var(--white); border: none; }
.pc-note { color: var(--blue-note); font-size: var(--text-xs); }
```

**规则**：

- **位置即语义**：列位置 = 位号（权重/偏移），孔 = 1、无孔 = 0——位置本身携带语义，颜色只做状态确认。因此 punch card **免疫退化形式禁令**（它编码的是位置与值，不是「仅靠颜色区分的同构格阵」）；反之，位置不携带语义的纯列表/纯计数格阵应选 trace / 表格。
- **red 用法（L2 约束）**：L2 上的 red 仅限 ≥2px 线与 ≥sm 粗体标签——主动路径（进位链、比较路径）用 red 2px 线连接关键孔，压力位号可用 red ≥sm 粗体；**deep-red 禁落蓝底**，字段名与结果对照一律走 L0 轨。
- **装裱**：机制类默认全装裱（`figure.plate.full` + 图号 + 图题）；图版须被正文引用（见图 N）或图题传达机制结论。**白卡作用域适用于卡片本体**：仅孔位（`pc-hole`）豁免 white，其余表面禁止。
- **展开形态**：零件级分解（字段拆分、栈帧、进位接力）用**爆炸框**——爆炸框是 punch card 的展开形态，二者不混用：整卡读值用 punch card，拆零件用爆炸框。
- **多卡对照**：同主题多卡（原码/反码/补码）用**图版横列** plate-row 并置，独立图号（图 3a/3b）。
- **响应式**：≤768px 格径 24px → 20px（与 trace 缩比一致）；位号行可隐藏（孔阵语义仍在）；位宽 >12 时孔阵允许横向滚动（超宽条款），不撑宽文字轨。

**形态理由（规则 B）**：位格式内容 → punch card → 编码「位置（位号）× 状态（孔）」，孔的存在/缺失即位的 1/0——「位置即语义」使它在格阵家族中免疫退化形式禁令。

### Dialogue（对话）

- 语义：对比 / 争论 / 误解纠正——两个立场交锋，正解从交锋中浮现。
- 解剖：L0 透明底双声部（`.dialogue .a` / `.dialogue .b`），**无卡片轮廓**，仅靠边框与错位成型；说话人标签 mono 小字；正解句 deep-red 词眼（落 L0）；散文收文字轨（`max-width: var(--text-rail)`）。
- 规则：
  - 陈述类 → **不装裱**、保持流式（装裱判定）；
  - 误解方与正解方用 G4 错位或楔形标记区分（见 visual-system → 教学类型 × 系统映射）；楔形指向正解（轴线系）；
  - 答案行属「陈述类」表面——禁白底（白卡作用域）。
- 形态理由：观点交锋 → dialogue → 编码「立场对立 + 正解浮现」，错位与楔形编码纠错方向。

### Swimlane（泳道）

- 语义：多角色 / 多阶段流程交接（Multi-role / multi-stage process handoff）。
- 解剖：

```text
│ 角色A │ ●──────→ ○ ←── 三角指针（交接/消息箭头）
│ 角色B │          ●────→ ○
│ 角色C │               ●─→ ○
└ 阶段轴（时间/顺序，左→右，blue-note 刻度）
```

  水平泳道 = 角色（左侧角色标签轨 + 右侧事件序列）；垂直阶段轴 = 时间；交接箭头 = 三角指针（轴线系）；角色 ≥3 时用剖面线或 blue-note 区分身份（剖面线条款：多角色身份通道），**不加新色相**。
- 规则：机制类 → **默认全装裱**（`figure.plate.full` + 图号 + 图题）；L2 图纸底 + paper 网格；red 只标主动路径（关键交接）；轴线不进入泳道内部。
- 形态理由：多角色交接 → swimlane → 编码「角色 × 时序」二维归属与交接方向。

### Nested Tree（嵌套树）

- 语义：层级包含（地址空间、作用域、缓存层次）——Hierarchical containment。
- 解剖：嵌套矩形（外层包含内层，父子边框层级即包含关系）+ 每层左侧 mono 层级标签；最内层承载实际内容（基址 / 页号 / 对象）。
- 规则：机制类 → **默认全装裱**；L2 图纸底（地址/作用域 = 可测量内容）；层级 ≤4（与 G7 阶梯同级数上限一致）；退化为纯缩进列表时改用列表 / stair——嵌套矩形必须编码「包含」关系本身，否则形态失效（规则 A）。
- 形态理由：层级包含 → nested tree → 编码「包含 / 被包含」的几何从属。

### Readout（读数）

- 语义：关键读数 / 状态 / 判定数字（Key readings / state / verdict figures）。
- 解剖：大数字（num 字体，4–6rem ↔ 0.75rem mono 标签并置——尺度对比是构图）+ 单位/标签 + 可选状态标记（red = 动态，deep-red = 判定词眼，字级）。
- 规则：陈述类 → **不装裱**，L0 上 ink 数字；窄栏友好（readout 入窄栏改纵向堆叠）；**阈值型读数用仪表盘（径向），线性读数用 readout / ratio bar**——readout 不做仪表。
- 形态理由：关键读数 → readout → 编码「数值的权重」，尺度对比即构图语言。

### Timetable（时间表）

- 语义：精确时间序列（Precise time series）——演进史、版本沿革。
- 解剖：竖排时间轴（num 字体时间戳 + ink 刻度线——steel 禁落 L3，≈1.3:1 不可读）+ 事件行（事件名 + 一句话因果）；档案类语义 → **L3 ochre 带表面，不进图版**。
- 规则：ochre 永不做文字色——事件文字落 L0，ochre 只做背景带；时间戳必须经 Research Mandate 历史核查，不虚构日期；不与 L2 组件相邻（≥gap-md）。
- 形态理由：时间演进 → timetable → 编码「先后序与历时」，ochre 档案层与「历史」语义同构。

### Blueprint Callout（蓝图标注）

- 语义：机制图的局部放大 / 批注（Close-up annotation of a mechanism diagram）。
- 解剖：主图（L2 图版内）+ 引线（steel 1–2px，方向与轴线同系）+ 标注框（L0 纸底、ink 边框、直角）；标注框内容 = 机制结论句 + deep-red 词眼。
- 规则：引线不进入主图内部（轴线不进图解）；**与爆炸框分工**：局部批注用 blueprint callout，零件拆解陈列用爆炸框；标注框禁白底（白卡作用域）。
- 形态理由：局部机制 → blueprint callout → 编码「视点聚焦 + 批注归属」。

### Ratio Bar（比例条，含竖排变体）

- 语义：比例 / 频度 / 分布（Proportion / frequency / distribution）——苏联统计图形传统。
- 解剖：横轨 + 分段（ink / blue / ochre，遵守深色间距表）+ 数值标签（num 字体）；竖排变体 = 纵向轨道（窄栏友好，入窄栏改纵向堆叠）；「事件」语义段用 `ratio-seg-alt`（红段处置见红面阈值：高 ≤24px，或 2px red 边框 + paper 底 + red 数值字）。
- 规则：陈述类 → **不装裱**；红段遵守红面阈值；ochre 段遵守「不与 L2 相邻」。
- 形态理由：比例分布 → ratio bar → 编码「份额的相对量」，段长即数值。

### Archive Card（档案卡）

- 语义：证据 / 史实 / 引文（Evidence / historical fact / quotation）。
- 解剖：L3 ochre 左竖带（或顶带）+ 引文主体（ink 字，**可直接落在 ochre 带上**——ink/ochre ≈5.3:1 达标 AA；或落 L0）+ 出处行（mono ink 小字——steel 禁落 L3）；档案签戳记（rotate(-4deg) 例外）可选。
- 规则：档案类 → **不装裱**、流式；ochre 永不做文字色；不与 L2 相邻（≥gap-md）；史实必须经 Research Mandate 核查。
- 形态理由：历史证据 → archive card → 编码「档案归属」，ochre 即档案层。

### Archival Panel（档案面板 / 定义面板）

- 语义：**严格的学术定义与固定规则陈述**——Teaching Architecture 第 7 步「Formal definition」（直觉建立后引入精确术语）、考点教学的「定义 · 约定」声明（如「next[j] 定义」「严蔚敏约定 1-indexed」「优化规则」）。
- 解剖：L3 ochre 全带表面 + ink 3px 边框 + 顶置档案签（`.archival-tag`：ink 底 paper 字、mono xs、+0.1em——文字即声明类型：「定义」「定义 · 约定」「优化规则」）；内容 ink 字直接落 ochre 带（ink/ochre ≈5.3:1 达标 AA）；多段用 gap-xs 分隔；散文收文字轨。

```css
.archival-panel {
  background: var(--ochre);
  color: var(--ink);
  border: 3px solid var(--ink);
  padding: var(--gap-sm) var(--gap-md);
  margin: var(--gap-md) 0;
}
.archival-panel p { font-size: var(--text-sm); line-height: 1.6; margin-bottom: 0; }
.archival-panel p + p { margin-top: var(--gap-xs); }
.archival-tag {
  display: inline-block;
  font-family: var(--font-mono);
  font-size: var(--text-xs);
  color: var(--paper);
  background: var(--ink);
  padding: 2px 8px;
  margin-bottom: var(--gap-xs);
  letter-spacing: .1em;
}
```

```html
<aside class="archival-panel">
  <span class="archival-tag">定义</span>
  <p><strong>…物理含义</strong>：…（精确语句）。</p>
</aside>
```

- 规则：
  - 档案类 → **不装裱**、流式；ochre 永不做文字色（内容一律 ink）；不与 L2 相邻（≥gap-md）；不与 L3 色场叠加（面板自身即带，内部不再加带）；
  - 与 archive card 分工：archive card = 证据 / 引文 / 史实（带出处行），archival panel = 定义 / 规则语句（教学精确声明）——前者证明「发生过」，后者声明「应当如此」；
  - `.archival-tag` 不是 `.section-tag`：后者是节级结构标签（ink 底 paper 字 mono），前者是档案签（同族同形，语义是内容类型声明）。
- 形态理由：严格定义 → 档案面板 → ochre 档案层编码「精确性来自约定（档案）」，签 = 声明类型。

### 对照类：Compare Table / Split

- **compare table**：对照表——二维查找表格的对照变体（考点关联、利弊对照）；表头禁红底（deep-red 文字 + 红左划线）；超宽横向滚动；规格同 Tables。
- **split**：对称双栏（**等价内容并置，非主从**）——与 asym（主 2/3 + 窄 1/3）区分；两栏同基线、无错位；≤768px 塌单栏。

### 陈述类容器通则（essence-hook / insight-panel / inset-panel / warning-box / stair / collage）

共性：陈述类 → **L0 透明底、禁白底**、仅靠边框 / 硬阴影成型（白卡作用域三选一之「陈述类」）；散文收文字轨（`max-width: var(--text-rail)`）。

- **essence-hook**（类名 `.hook`）：本质钩容器——hook 句 + deep-red 词眼（落 L0）；对应 Essence Hook 教学节，一页一个为主。
- **insight-panel**：洞察面板——判词类容器（宽收窄 85%，≤768px 回 100%），L0 透明底 + ink 边框或硬投影 + deep-red 词眼；与楔形块分工：楔形承载 ≤2 行强冲突判词（ink 底反转），insight panel 承载更长的分析性结论（考点教学「应试技巧」形态）。
- **inset-panel**：内嵌面板——随文小面板（G4 内嵌语义），ink 边框或硬阴影成型，无圆角。
- **warning-box**：警示框——易错陷阱容器（考点教学「易错陷阱」形态）；左 4px red 边（事件）+ ink 边框；词眼 deep-red。
- **stair**：阶梯组（G7 阶梯）——递进构建语义；≤4 级；扁平枚举禁用；级间错位沿轴线方向。
- **collage**：拼贴平面（G8 重叠）——结论从证据浮现；浮动平面投影 `8px 8px 0 red`（判词以事件方式落下）。

补充映射：

| 认知类型 | 形态 |
|---|---|
| 阈值型读数（负载因子、水位、利用率） | **gauge（仪表盘）** |
| 格式/机制的零件级分解（字段、栈帧、进位接力） | **exploded frame（爆炸框）**，进图版框 |
| 比例 / 频度 / 分布（测量件横排） | instrument strip（仪器带） |

**Ratio Bar 红段**：比例条里需要「事件」语义的分段（如「KMP 省下的比较次数」）用 `ratio-seg-alt`——红段高 ≤24px，或改 2px red 边框 + paper 底 + red 数值字；禁大面积纯红填充段（红面阈值）。

**形态理由（规则 B）**：Step 5 为每个机制组件写一行「认知类型 → 形态 → 该形态编码了什么语义操作」，质检 #13-9 逐条核验；形态退化为同构格阵（>16 个单元仅靠颜色区分、编码不了移动/方向/转移/连接）即失效，必须重选既有形态（见 visual-system → 形式有效性）。

### 字级微件（Inline Patterns）

进不了容器的字级语义，inline 实现：

- **词眼 `.kw`**：正文中的 deep-red 600 词眼（判词词眼、关键数字）——deep-red 落 L0 的默认形态（例：example-twos-complement.html 全文）。
- **`.red-b`**：L2 图纸底上的焦点标签——red ≥sm 粗体（deep-red 禁落蓝底，蓝底焦点改用 red）；语义用 `<b>` 承载。
- **`.dim`**：同构单元中的非激活态——`opacity: .4`（次状态用透明度，不新增色相）。
- **图例 `.legend`**：非明显角色/状态必须带图例——swatch（色块 / 剖面线样例，14–28px）+ mono 小字；落 L2 用 blue-note，落 L0 用 steel（例：`.mm-legend`「剖面线 = 未映射区」）。

### 类名注册表（canonical class names）

组件名 ↔ 示例实现类名速查（**示例为准，防止命名漂移**——新页面照此落名，禁止同名异形）：

| 组件 | 类名 |
|---|---|
| 本质钩 essence-hook | `.hook` |
| 词眼 / 蓝底焦点标签 / 次状态 | `.kw` / `.red-b` / `.dim` |
| 节标签 / 斜切标题带 / 巨字判词 / 巨字编号 | `.section-tag` / `.section-band` / `.giant-verdict`（`em` 词眼）/ `.giant-num` |
| 图版 | `.plate.full` / `.plate.light` + `.plate-marks` + `.fig-num` + `.plate-caption`；引用 `.fig-ref` |
| 蓝图容器（L2 底 + paper 网格） | `.blueprint` |
| 走查 trace | `.trace` + `.tr-grid` / `.tr-h` / `.tr-lab` / `.tr-c` / `.tr-foot`；步叙 `.trace-action`；列题 `.trace-header`；图例 `.legend` |
| 步进 trace | `.st-grid` / `.st-n` / `.st-c` / `.st-foot` |
| 代码块 | `.code`（`.cm` 注释 / `.hl` 关键行） |
| punch card | `.punch-card` / `.pc-row` / `.pc-key` / `.pc-body` / `.pc-idx` / `.pc-bits` / `.pc-bit` / `.pc-hole` / `.pc-note` |
| memory map | `.mmap-row` / `.mm-addr` / `.mm-seg` / `.mm-hatch` / `.mm-legend` |
| nested tree | `.nt-node` / `.nt-lab` / `.nt-cells` / `.nt-cell` |
| 爆炸框 | `.x-frame` / `.x-level` / `.x-tag` / `.x-key` |
| 档案面板 | `.archival-panel` + `.archival-tag` |
| 读数 / 仪器带 / 对照表 | `.readout`（`.ro-num` / `.ro-lab`）/ `.strip` / `.cmp`（`.cmp-wrap`）+ `.data-table` |
| 清单 / 版权条 / 页头 / sidebar / 标尺 | `.checklist` + `.ck` / `.colophon` / `.page-header`（`.kicker` / `.hdr-bar` / `.subtitle` / `.meta`）/ `.sidebar`（`.sb-head` / `.sb-track` / `.sidebar-progress`）/ `.ruler-tick`（`.rt-num` / `.rt-word`）+ `.sec-num` |

## Diagram Specs（机制图解）

### 图解通则（所有机制图解共性）

- 默认图纸化：L2 底 + 4–6% paper 网格 + blue-note 注释 + red 主动路径；**轴线不进入图解内部**（图解内一律正交）；多角色身份用剖面线或 blue-note 区分，不加新色相。
- **蓝图容器 `.blueprint`**：L2 底 + paper 网格（24px 参考）的标准容器——SVG 与 HTML 机制图解直接落其上；图版内衬 ≥gap-md；无图版（不装裱）时同样可用（图纸语义与装裱无关）。
- SVG 为一等公民：stroke ink 3–4px 结构 / red 6–7px 主动路径 / 辅助线 1–2px（**随表面换色**：L2 图纸底用 blue-note，L0 底用 steel——steel 禁落 L2）；直线直角、矩形节点、显式连接点、硬边框；`role="img"` + `aria-label`；`<figcaption>` 一句话说清机制结论。
- 机制类默认全装裱（`figure.plate.full` + 图号 + 图题），正文须引用（见图 N）或图题传达结论。
- **图解零件**：cause-node（因果节点）、state-box（状态盒）、msg-label（消息标签）——一律正交矩形 + ink 边框，内部身份用剖面线 / blue-note 区分；msg-label 用 mono + blue-note。

### Memory Map（内存图）

- 语义：地址空间布局。
- 解剖：地址纵轴（num 字体地址列，blue-note）+ 区块矩形（栈 / 堆 / 代码段 / 共享区）+ 区块标注（blue-note）+ 关键边界地址（red ≥sm 粗体，压力位）。
- 规则：机制类 → 全装裱；区块身份 >4 时用剖面线（负半区 / 共享区 / 未映射区）；地址 = 可测量内容，只落 L2。
- 形态理由：地址布局 → memory map → 编码「地址区间 × 归属」。

### ASCII Diagram（字符图）

- 语义：精确字符排布（位图 / 协议帧 / 网格）——**等宽对齐即信息**。
- 解剖：mono 预排版文本；机制类用 L2 图纸底 + paper 字符（陈述类可 L0 ink）；允许横向滚动（超宽条款）；关键区标记 red（≥sm 粗体或 2px 线）。
- 规则：**位置即语义**——纯字符格阵若不编码位置语义（如 166 个 char 格仅靠颜色/字符区分）即退化（规则 A），改用 punch card / trace；字符图免疫退化的前提与 punch card 相同。
- 形态理由：位图排布 → ASCII → 编码「等宽位置语义」。

### Trace（走查）

- 语义：真实数据逐步状态——**手工推演核心形态**（考点教学「手工推演」映射）。
- 解剖：行 = 步骤（步号 num 字体），列 = 变量 / 寄存器 / 指针；每格一个状态值；关键格（压力点 / 失败格）red 格级标记（≤32×32 参考，格间 ink/paper 分隔）；末行结论 deep-red 词眼落 L0 轨。
- 微件：列题行（`.tr-h` / `.trace-header`，blue-note mono 列名）；步叙行（`.trace-action`，逐轮叙述「第 N 轮：… 次比较」——落 L2 用 blue-note、落 L0 用 ink）；状态图例（`.legend`，swatch + 文字，见字级微件）。
- 规则：机制类 → 全装裱；L2 图纸底 + 纸网格；**必须用真实数据走完每一步**（SKILL.md 手工推演要求，不能只给最终结果）；与 stepper 区分：trace = 全表并置对比，stepper = 单步递进。
- 形态理由：逐步状态 → trace → 编码「行 = 时间步 × 列 = 状态维」的转移轨迹。

### State Diagram（状态图）

- 语义：状态转移。
- 解剖：状态节点（**矩形**，ink 边框）+ 转移箭头（三角指针 / red 主动路径）+ 起止标记（三角指针，轴线系）+ 守卫条件标签（blue-note）。
- 规则：机制类 → 全装裱；red 只标主动路径（关键转移）；圆只做焦点声明（G3），状态节点用矩形。
- 形态理由：状态转移 → state diagram → 编码「转移方向与条件」。

### Causal Chain（因果链）

- 语义：问题 → 压力 → 方案 → 权衡的因果序列（Teaching Architecture 的图解版）。
- 解剖：节点序列（矩形）+ 连接线（ink 2px）；压力节点 red（事件）；权衡节点 blue-note 标注（steel 禁落 L2）；词眼 deep-red 落 L0。
- 规则：机制类 → 全装裱或轻装裱（按主次）；链必须闭合到权衡（不悬空）；词眼 deep-red 落 L0 轨（**蓝底上的焦点改用 red**）；节点 >16 且仅靠颜色区分 → 退化（规则 A），重选既有形态。
- 形态理由：因果序列 → causal chain → 编码「压力传递方向」。

### Code Block（代码块）

- 语义：可运行代码示例。
- 解剖：L2 图纸底 + paper 字（代码 = 精确内容）+ 行号（blue-note num 字，可选）+ 关键行 red 2px 左竖条（事件）+ 注释行 blue-note；**禁用语法高亮**——色层语义替代：red = 事件行、blue-note = 注释。
- 规则：机制类 → 默认全装裱（代码即图版）；**必须可运行**（Research Mandate，禁混用不兼容版本 API）；超宽横向滚动；无 JS 高亮（渐进增强）。
- 形态理由：代码 → code block → 编码「执行路径的行级事件」，图纸底与「精确」同构。

### Checklist（清单）

- 语义：索引 / 回顾（知识清单、文末考点清单）——**零动作、克制**（教学映射「回顾 | 索引 | checklist」）。
- 解剖：L0 上 ink 列表 + check 编号（deep-red num 字——「check 编号」是 deep-red 分工的既有成员）；无图版、无几何动作。
- 规则：清单是索引不是内容（SKILL.md：文末复习清单可 bullet，正文必须已完成完整教学）；每条目须能映射回正文或考点（知识清单覆盖率闭环）。
- 形态理由：索引 → checklist → 编码「条目存在性」，编号 = 锚点。

### Tables（表格）

- 语义：**仅真正的二维查找**（Form Selection 质检 #8：防 table-stuffing）。
- 解剖：表头 deep-red 文字 + 红左划线（**禁红底**——红面阈值处置）；行列分隔 ink 1px；数值列 num 字体；超宽横向滚动（超宽条款）。
- 规则：单维数据用列表 / readout，不用表格；主从语义用 asym / split，不用表格；对照 / 权衡 / 考点联动用 compare table 变体。
- 形态理由：二维查找 → table → 编码「行 × 列交叉定位」。

### Stepper（步进器）

- 语义：真实数据单步演示——考点教学「手工推演」形态；Step-Through 的静态基座。
- 解剖：垂直步进行：步号（num 字）+ 状态描述 + 数据快照；当前步 red 标记（事件）；L2 图纸底（数据 = 可测量）。
- 规则：机制类 → 默认全装裱；步骤 3–7 步（与 Step-Through 一致）；每步必须有数据变化（禁空转）；与 trace 区分：stepper = 单步递进，trace = 全表并置。
- 形态理由：逐步演示 → stepper → 编码「步进顺序与当前焦点」。

## Interaction Specs

### Step-Through（步进演示）

- 语义：3–7 步的交互式演示——复用 Stepper 的静态结构加交互层；**渐进增强**。
- 解剖：控件（上一 / 下一 + 步号 num 字）+ 内容区（Stepper 结构）；按钮为 L4 UI（active/hover 落红合法——red 落 L4 仅限 UI 交互态）；无 JS 时渲染全部步骤，页面完整可读。
- 规则：键盘可达（Tab / 方向键）；JS 预算内（sidebar 进度条 + scroll-spy + stepper = 上限）；禁动画；每步内容与 Step 5 形态理由对应。
- **Scroll progress**：sidebar 底部唯一进度条（rAF + passive scroll）；无 JS 时进度条隐藏，页面完整可用。**标尺无进度条**。

```js
const bars = document.querySelectorAll('.sidebar-progress');
if (bars.length) {
  const update = () => {
    const d = document.documentElement;
    const max = d.scrollHeight - d.clientHeight;
    const p = max > 0 ? (d.scrollTop / max) * 100 : 0;
    bars.forEach(b => { b.style.height = p + '%'; });
  };
  addEventListener('scroll', () => requestAnimationFrame(update), { passive: true });
  update();
}
```

## Responsive Spec

768px 单断点，不为中间宽度新增断点：

- 板面塌单栏；双轨合一（图版轨与文字轨同宽）；标尺轨隐藏，编号由 `.sec-num` 承担；crop marks 隐藏。
- 标题：text-3xl → text-2xl；section 标题 text-2xl → text-xl；giant-num 5rem → 3rem；giant-verdict 收小；statement → text-xl。
- trace 格 2.2rem → 1.8rem；ascii / memory-map 字号降 xs 并允许横向滚动。
- 多栏塌单栏（staggered / plate-row / strip 变纵列；错位归零）；sidebar → 顶部全宽竖排列表。
- 几何容器：楔形 padding-bottom 收小（5rem → 3rem，斜切按公式自然收浅）；圆形 8rem → 6rem；偏移归零；阶梯退化竖排；色场 padding 缩为 `gap-md gap-sm`；浮动平面转静态全宽。
