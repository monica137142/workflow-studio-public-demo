# IQ Buddy Design Specification

## 设计概述

IQ Buddy 是一个面向内部运营与自动化任务的工作台界面。整体设计语言应保持克制、清晰、偏工具化，强调信息扫描效率、任务状态识别、重复操作稳定性和多模块之间的一致体验。

核心视觉关键词：

- 工作台：高密度信息、稳定导航、低干扰装饰。
- 智能助手：绿色主色传达可用、成功、权限开通和执行能力。
- 运营工具：卡片、表单、任务列表、日志列表以扫描和编辑效率优先。
- 渐进复杂度：默认展示关键内容，详情、权限、执行历史通过右侧分栏或弹窗承载。

界面不采用营销页式大幅视觉，不使用大面积渐变、装饰光斑或过重插画。主要画面由侧边栏、顶部 sticky 标题区、二级筛选导航、内容卡片网格、任务表单和右侧详情区组成。

## Design Tokens

### Color

| Token | Value | 用途 |
| --- | --- | --- |
| `--color-bg` | `#ffffff` | 主应用背景 |
| `--color-primary` | `#22b573` | 主行动、成功状态、选中强调、品牌绿 |
| `--color-primary-light` | `#e6fff4` | 主色浅底、头像底、状态浅底 |
| `--color-highlight-yellow` | `#fff9e6` | 轻提示或黄色高亮 |
| `--color-text-main` | `#222222` | 一级正文、页面标题 |
| `--color-text-sub` | `#666666` | 二级说明文字 |
| `--color-text-placeholder` | `#999999` | 输入提示、弱信息 |
| `--color-border` | `#e5e5e5` | 默认边框 |

补充色板：

| Color | Value | 用途 |
| --- | --- | --- |
| Surface gray | `#f5f6f8` | 页面底色、hover 背景 |
| Sidebar bg | `#fbfcfd` | 左侧导航底色 |
| Divider | `#e8ebee` | 分割线、卡片边框 |
| Light divider | `#eef1f3` | 顶部栏底边、表单区块边框 |
| Text strong | `#1a1d1f` | 重要标题、激活状态 |
| Text muted | `#969ba1` | 版本号、辅助说明 |
| Green hover | `#1b9c61` | 主按钮 hover |
| Green dark | `#12824c` | 权限按钮 hover 文本 |
| Blue accent | `#3b82f6` | 上传图标、个别信息强调 |
| Blue tag text | `#4f72d8` | 第二类特长标签 |
| Amber bg | `#fff7e8` | 训练态、第三类标签 |
| Amber text | `#b66b18`, `#c8842a` | 训练态与标签文字 |
| Danger | `#f04438` | 删除、危险操作 |
| Danger hover | `#d92d20` | 危险主按钮 hover |
| Danger soft | `#fff5f5` | 危险描边按钮 hover |

### Semantic Tokens

| Semantic | Token / Value | 用途 |
| --- | --- | --- |
| Primary action | `#22b573` background, white text | 进入对话、保存修改、开通权限强化按钮 |
| Secondary action | `#fff` background, `#dde1e5` border | 取消、普通次级按钮 |
| Danger action | `#f04438` background, white text | 确认删除 |
| Danger outline | white background, `#f04438` border, `#d92d20` text | 编辑弹窗中的删除按钮 |
| Disabled / pending | `#f5f6f8` background, `#8a9199` text | 申请中、不可用状态 |
| Selected card | white background, green border and outer ring | 右侧分栏打开时的选中 card |
| Focus ring | `rgba(34, 181, 115, .24)` | 键盘 focus 可见态 |

## 字体

### Font Family

主字体使用系统字体栈：

```css
--font-main: -apple-system, BlinkMacSystemFont, "Microsoft YaHei", "Segoe UI", sans-serif;
```

### Type Scale

| 场景 | 字号 | 字重 | 行高 / 说明 |
| --- | --- | --- | --- |
| 顶部主导航标题 tab | `21px` | `700` | 页面一级入口，如「全体实习生」 |
| 页面普通标题 | `24px` 或 `21px` | `700` | 连接中心、自动化等页头 |
| 卡片标题 | `14.5px` | `600` | 单行省略 |
| 卡片版本号 | `11.5px` | normal | 弱化辅助信息 |
| 卡片描述 | `12px` | normal | 2 行截断 |
| 分组标题 | `14px` | `600` | 如可用实习生分组 |
| 正文/表单文字 | `13px` 至 `14px` | normal / `500` | 工作台常规信息 |
| 按钮文字 | `12px` 至 `13px` | `500` 或 `600` | 主按钮与任务按钮 |
| 标签文字 | `10.5px` 至 `12px` | `600` | 状态、特长、分类 |
| 说明文字 | `12px` 至 `13px` | normal | 副标题、提示、hint |

排版规则：

- 不使用负字距，`letter-spacing` 默认 `0`。
- 卡片、导航、标签中的长文本必须单行省略。
- 描述类文本允许 2 行截断，避免卡片高度被撑开。
- 中文界面优先保证信息密度，避免过大的展示型字号。

## 间距

### Base Spacing

当前页面使用 2px 至 28px 的实用间距体系，以 4px、6px、8px、10px、12px、14px、16px、20px、24px、28px 为主要步进。

| 场景 | 间距 |
| --- | --- |
| 页面外边距 | `28px`，小屏降为 `20px` |
| sticky header 高度 | `108px` |
| header 内边距 | `16px 28px` |
| toolbar 与内容间距 | `20px 0` |
| card grid gap | `13px` |
| agent card padding | `15px` |
| card 内头像与文字 gap | `11px` |
| card 描述到底部间距 | `12px` |
| 标签间距 | `6px` 至 `8px` |
| 表单字段间距 | `12px` 至 `14px` |
| 弹窗 body padding | `20px` 级别 |
| 弹窗 footer padding | `14px 22px 20px` |

### Spacing Rules

- 页面级区域之间使用 20px 以上间距。
- 卡片内部控制在 6px 至 15px，保持紧凑。
- 表单关联字段可使用浅底容器，内部 gap 为 12px。
- 右侧分栏与主内容区域直接并排，不额外使用浮动卡片包裹。

## 圆角与阴影

### Radius

| Token / Value | 用途 |
| --- | --- |
| `--radius-card: 12px` | 通用卡片基准 |
| `14px` | agent card 主卡片 |
| `12px` | 头像方块、抽屉头像 |
| `10px` | 搜索框、上传框、表单区块 |
| `8px` | segmented active、弹窗按钮、任务按钮 |
| `7px` | 侧边导航项、普通小按钮 |
| `999px` | badge、pill、tag、圆角胶囊 |

圆角规则：

- 工具型按钮优先使用 `7px` 至 `8px`。
- 卡片使用 `12px` 至 `14px`，不要过度圆润。
- 状态、标签、badge 使用胶囊圆角。

### Shadow

| Shadow | 用途 |
| --- | --- |
| `--shadow-light: 0 4px 16px rgba(0, 0, 0, .04)` | 应用容器轻阴影 |
| `0 1px 2px rgba(20, 30, 40, .04), 0 1px 3px rgba(20, 30, 40, .03)` | 默认 card |
| `0 2px 8px rgba(20, 30, 40, .05)` | card hover |
| `0 8px 22px rgba(34, 181, 115, .14), 0 0 0 3px rgba(34, 181, 115, .2)` | 选中权限 card |
| `0 0 0 3px rgba(34, 181, 115, .12)` | 输入 focus |
| `0 24px 64px rgba(20, 30, 40, .18)` | 弹窗/抽屉浮层 |

阴影规则：

- 默认阴影要轻，不制造强烈层级噪音。
- hover 阴影只能轻微增强。
- 选中态可以使用 outer ring，但颜色必须统一为品牌绿。
- 弹窗和抽屉可以使用更强阴影以表达覆盖层级。

## 布局系统 Layout

### App Shell

- `.app-container` 使用横向 flex，固定高度 `100vh`。
- `.sidebar` 固定宽度 `288px`，收窄断点下为 `248px`。
- `.main-content-area` 横向 flex，用于主内容和右侧 inline panel 并排。
- `.portal-center-route-shell` 为主要滚动容器，背景 `#f5f6f8`，页面 padding 为 `0 28px 28px`。

### Header

- 页面 header 使用 sticky，固定高度 `108px`。
- header 背景为白色，底部分割线 `#eef1f3`。
- 顶部主标题 tab 使用 21px 粗体，选中时只改变文字色，不使用绿色短线。
- 副标题使用 13px 灰色，用于当前页面说明或统计。

### Secondary Navigation

- `.toolbar` 横向 flex，包含分类 segmented 控件和搜索框。
- 二级导航优先保持一行，按钮文本超长时省略。
- 搜索框响应式优先缩短，然后隐藏：
  - `<=1180px`：搜索框缩到 `220px`。
  - `<=1040px`：搜索框缩到 `168px`。
  - `<=900px`：隐藏搜索框。
- 中间 spacer 不抢占空间，使用 `flex: 0 1 0`。

### Card Grid

- `.grid` 使用 CSS grid：`repeat(auto-fill, minmax(296px, 1fr))`。
- card gap 为 `13px`。
- 卡片宽度由 grid 均分，内容长文本省略，避免卡片高度不一致。

### Right Inline Panel

- 开通权限详情使用右侧 inline panel，而不是覆盖式 drawer。
- 右侧 panel 宽度 `420px`，最小宽度 `380px`。
- 打开时主内容区域应可收缩，选中 card 自动滚动到可视区域中间。
- 点击同一权限 card 再次收起，点击其他权限 card 切换内容。

### Modal

- modal 使用固定遮罩，`z-index: 240`。
- modal 居中，遮罩背景 `rgba(20, 30, 40, .24)`。
- footer 使用左右分组：危险/删除操作在左，取消与确认在右。

## 组件规范

### Sidebar Navigation

- 宽度：默认 `288px`，小屏 `248px`。
- 背景：`#fbfcfd`。
- nav item 高度至少 `34px`，圆角 `7px`。
- hover 背景 `#f5f6f8`。
- active 背景 `#eef1f4`，左侧使用 3px 绿色竖条。
- 文本超出必须省略。

### Agent Card

结构：

- 顶部：头像、名称、版本。
- 中部：2 行描述。
- 底部：2 至 3 个特长彩色标签，右侧为行动按钮。

尺寸与样式：

- padding `15px`。
- min-height `143px`。
- border `#e8ebee`。
- radius `14px`。
- hover 上移 `-1px`，轻微阴影增强。
- focus-visible 使用绿色 3px outline。

选中态：

- 普通选中：绿色边框和轻微绿色阴影。
- 开通权限右侧分栏选中：白底，品牌绿边框，3px 绿色外圈。
- 禁止使用蓝色默认 focus 线，必须统一绿色。

### Specialty Tag

card 与详情「我擅长」区域共用同一套特长标签。

| Class | Background | Text |
| --- | --- | --- |
| `.st-specialty-0` | `#e9faf1` | `#168655` |
| `.st-specialty-1` | `#eef2fb` | `#4f72d8` |
| `.st-specialty-2` | `#fff7e8` | `#b66b18` |

规则：

- 最多展示 2 至 3 个。
- 单个标签最大宽度 `88px`，超出省略。
- 详情页标签也必须有底色，不能退化为白底。

### Buttons

#### Compact Button `.cbtn`

- 默认：白底、灰边、深灰字。
- hover：边框与文字变为绿色。
- primary：绿底白字。
- permission：透明底、浅绿边、绿色文字。
- pending：灰底灰字，不强调。

#### Confirm Button `.confirm-btn`

- 默认：白底灰边。
- danger：红底白字，用于确认删除等强危险确认。
- danger-outline：白底红边红字，用于编辑弹窗中的删除。
- success：绿底白字，用于保存修改。

编辑任务弹窗：

- 左侧「删除」使用 `danger-outline`。
- 右侧「保存修改」使用 `success`。
- 新建态「创建任务」保留 danger 主按钮样式。

### Search

- 宽度默认 `280px`。
- 高度由 padding `8px 13px` 决定。
- focus 使用绿色边框和浅绿色 ring。
- 响应式时优先缩短和隐藏，不挤压二级导航。

### Upload Field

结构：

- 上传框 `.task-upload`。
- 图标 `.task-upload-icon`。
- 文件名 `.task-upload-text`。
- 删除按钮 `.task-upload-remove`。
- 说明 `.task-upload-hint`。
- 已上传后显示「继续上传」按钮 `.task-upload-continue`。

规则：

- 上传框为虚线边框，浅灰底。
- 文件名单行省略。
- 删除按钮在文件名右侧，点击后恢复「选择文件」。
- 继续上传按钮位于附件下方，仅已有附件时展示。
- 继续上传触发文件选择器。
- 内嵌 Tiktok 上传、编辑任务弹窗、侧边栏 Tiktok 上传新建页需保持一致。

### Agent Detail Panel

- 标题区：实习生详情。
- 头像使用 46px 方形圆角。
- 「支持技能」统一命名为「我擅长」。
- 「我擅长」标签与 card 特长标签内容和颜色一致。
- 「试试这样问」最多展示 3 条建议。
- 开通权限按钮位于建议下方，绿底白字。
- 右上角按钮在 inline panel 状态下为收起侧边栏图标。

### Automation Task List

- 自动化列表是密集表格化信息区。
- 任务标题和浏览器账号上下两行展示。
- 运行状态列使用开关样式。
- 新创建任务置顶，并与顶导航保持 36px 间距高亮。
- 编辑按钮打开编辑弹窗，不跳转对话。

### Schedule Task Card

- 卡片包含任务名、agent、调度信息、状态、动作按钮。
- 动作按钮使用图标优先，包含执行历史、编辑、删除。
- 二级切换「任务列表 / 执行历史」位于 card 上方左侧，圆角矩形样式。

## 页面结构

### 1. 硅基实习生页

页面组成：

- sticky header：范围 tab「全体实习生 / 我的实习生」与副标题。
- toolbar：业务分类筛选与搜索。
- agent grid：可用 agent 卡片。
- 权限详情 inline panel：点击待开通权限 card 后展开。

关键行为：

- 点击已开通权限 card 进入对应对话或任务。
- 点击待开通权限 card 展开右侧详情。
- 再次点击同一 card 收起右侧详情。
- 展开详情时，选中 card 自动位于 view 中间。

### 2. 会话 / 任务页

页面组成：

- 左侧 sidebar agent 列表。
- 对话页标题区。
- 聊天内容区。
- 任务类 agent 的内嵌表单与执行日志分栏。

关键行为：

- 「进入对话」创建新会话。
- 任务类 agent 使用「新建任务」表单。
- Tiktok 上传任务支持附件删除与继续上传。

### 3. 自动化页

页面组成：

- sticky header：自动化任务范围与统计副标题。
- 顶部页面切换：自动化任务 / 定时任务。
- 定时任务内二级切换：任务列表 / 执行历史。
- 自动化任务列表与编辑弹窗。

关键行为：

- 新建任务后，新增任务出现在列表首位。
- 编辑任务打开弹窗。
- 编辑弹窗可保存修改或删除任务。
- 执行记录打开右侧抽屉。

### 4. 连接中心页

页面组成：

- sticky header。
- 连接 card 列表。
- card 内标题、副标题、标签单行省略。

响应式规则：

- card 宽度尽量一致。
- 可展示时尽量不折行。
- 容器不足时 card 折行排列。
- card 内字段优先省略，不撑高卡片。

## 交互与动效

### Interaction Timing

| 场景 | 时长 | easing |
| --- | --- | --- |
| hover color / background | `.13s` 至 `.15s` | ease |
| scope 内容切换 | `.26s` | ease |
| drawer 进入 | `.3s` | cubic-bezier(.18, .78, .22, 1) |
| overlay fade | `.22s` | ease |

### Hover

- card hover：上移 `-1px`，阴影轻微增强。
- nav hover：浅灰底。
- 按钮 hover：颜色加深，不改变尺寸。
- 上传框 hover：虚线边框加深，背景略变灰。

### Selected

- 顶部主 tab：只改变文字颜色，不加绿色短线。
- 二级 segmented：灰底无描边。
- card 选中：绿色边框与外圈。
- 权限 card 选中：必须明显，但保持白底。

### Loading

- 创建任务按钮 loading 约 1.5s 后显示 toast。
- loading 状态禁用按钮 pointer events，显示小 spinner。

### Toast

- 用于非阻断反馈，如申请提交、保存成功、删除任务、创建任务。
- 文案短句，不打断当前工作流。

## 可访问性

### Keyboard

- 可点击 card 设置 `tabIndex=0`。
- focus-visible 必须可见，统一绿色 outline。
- 不依赖浏览器默认蓝色 focus。
- 弹窗关闭按钮、删除按钮、继续上传按钮需要 `aria-label` 或明确文本。

### Text Overflow

- 导航项、card 标题、版本、标签、连接中心字段必须支持省略。
- 不允许长文本撑开按钮、卡片、侧边栏。
- 标签需要 `title` 承载完整内容。

### Color Contrast

- 主按钮绿底白字用于关键操作。
- 弱文本不承载关键状态。
- 危险操作必须红色区分。
- pending / disabled 状态必须降低对比并禁用 hover 强反馈。

### Modal / Drawer

- modal 使用 `role="dialog"` 与 `aria-modal="true"`。
- drawer 和侧栏按钮使用清晰 `aria-label`。
- 点击遮罩关闭弹窗时，弹窗内部点击需阻止冒泡。

### Reduced Motion

- 已有 `prefers-reduced-motion: reduce` 规则应禁用 overlay 和 drawer 动画。
- 新增动画必须纳入 reduced motion 控制。
- 工作台场景不使用大幅入场动画。

## Implementation Notes

- 所有新增 UI 应优先复用现有 class：`.cbtn`、`.confirm-btn`、`.task-upload`、`.st-specialty-*`、`.agent-title-tab`。
- 新增颜色优先从当前 token 和补充色板中选择。
- 新增页面布局优先遵循 app shell、sticky header、toolbar、grid、inline panel 的既有结构。
- 新增表单控件必须具备清晰 label、focus、hover、disabled 状态。
- 新增功能上线时同步更新 `index.html` 的版本参数，避免 GitHub Pages 缓存。
