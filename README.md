# Workflow Studio Public Demo

IQ Buddy / Workflow Studio 的静态交互原型，用于演示「硅基实习生」工作台体验。项目主要覆盖 Agent 列表、权限开通、会话历史、自动化任务、任务详情和多种详情展示方式。

该项目不包含后端服务，页面数据来自本地静态 JSON 和前端脚本，适合用于产品评审、设计走查、交互验证和前端样式对齐。

## 在线访问

- GitHub Pages: https://monica137142.github.io/workflow-studio-public-demo/
- GitHub 仓库: https://github.com/monica137142/workflow-studio-public-demo

## 项目结构

| 文件 | 说明 |
| --- | --- |
| `index.html` | 项目入口页，会自动跳转到主原型页面。 |
| `agents-replica.html` | 主演示页面，包含侧边导航、Agent 卡片列表、权限详情、会话与任务交互。 |
| `public-agents.json` | 静态 Agent 数据源。 |
| `source-index.css` | 源页面样式参考文件。 |
| `source-index.js` | 源页面脚本参考文件。 |
| `vendor-antd.js` | 本地依赖脚本。 |
| `DESIGN.md` | IQ Buddy 设计规范，包括颜色、字体、间距、布局和组件规则。 |

## 核心功能

- 硅基实习生列表展示：支持不同 Agent 状态、版本、描述和工作组信息。
- 多种详情形态：支持分栏、抽屉、弹窗三种权限详情展示方式。
- 独立入口状态：不同硅基实习生入口拥有独立搜索、筛选、滚动和选中状态。
- 会话历史模拟：支持会话列表、任务列表、展开收起、hover 操作和删除确认。
- 自动化任务原型：保留任务页、自动化页、任务详情和执行记录等基础交互。
- 设计规范沉淀：通过 `DESIGN.md` 记录可复用的视觉和交互规则。

## 本地预览

这是一个纯静态项目，可以直接打开 `index.html`。

为了避免浏览器对本地 JSON 读取的限制，推荐使用静态服务器预览：

```bash
python3 -m http.server 3000
```

然后访问：

```text
http://localhost:3000/
```

入口页会自动跳转到：

```text
http://localhost:3000/agents-replica.html
```

## 数据配置

`public-agents.json` 是主页面使用的数据源。修改 Agent 名称、描述、状态、版本、工作组、训练态和可用态等展示信息时，优先调整该文件。

如果需要修改页面交互、筛选逻辑、弹窗行为或任务模拟逻辑，主要查看 `agents-replica.html` 中的脚本部分。

## 设计说明

设计规范位于 `DESIGN.md`，包含：

- 色彩与语义 token。
- 字体、字号和文本截断规则。
- 页面布局、侧边栏、卡片网格、右侧分栏、弹窗和抽屉规则。
- Agent 卡片、按钮、标签、表单、任务列表等组件规范。

后续调整页面时，建议同步维护 `DESIGN.md`，保证设计说明和实际页面一致。

## 部署

项目通过 GitHub Pages 托管。提交代码到 `main` 分支后，GitHub Pages 会自动更新线上页面。

常用流程：

```bash
git status
git add .
git commit -m "Update demo"
git push origin main
```

## 注意事项

- 本项目是静态演示原型，不包含真实登录、鉴权、接口请求或任务执行能力。
- 页面中的数据和交互主要用于评审，不代表完整生产逻辑。
- 发布前请检查 `public-agents.json`，避免提交敏感数据或内部不可公开信息。
