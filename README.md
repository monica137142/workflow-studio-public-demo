# Workflow Studio Public Demo

IQ Buddy / Workflow Studio 的静态交互原型，用于演示「硅基实习生」工作台的导航、Agent 列表、权限开通、会话历史、自动化任务和多种详情承载方式。

该仓库面向产品评审、设计走查和前端交互验证。项目不依赖后端服务，核心页面通过本地静态数据和浏览器端脚本模拟真实工作流。

## 在线地址

- GitHub Pages: https://monica137142.github.io/workflow-studio-public-demo/
- GitHub 仓库: https://github.com/monica137142/workflow-studio-public-demo

## 功能概览

- 硅基实习生工作台：展示可用、训练中、待开通等不同状态的 Agent 卡片。
- 多入口状态隔离：分栏、抽屉、弹窗三个硅基实习生入口拥有独立筛选、搜索、滚动和选中状态。
- 权限开通详情：支持右侧分栏、右侧抽屉和居中弹窗三种展示形态。
- 会话与任务列表：模拟历史会话、任务记录、展开收起、hover 操作、新建入口和删除确认。
- 对话工作区：保留 Agent 对话、任务页、自动化页等基础交互框架。
- 设计系统参考：在 `DESIGN.md` 中沉淀颜色、字体、间距、组件和布局规则。

## 页面结构

| 文件 | 说明 |
| --- | --- |
| `index.html` | 入口页，自动跳转到 `agents-replica.html`。 |
| `agents-replica.html` | 主演示页面，包含侧导航、Agent 列表、权限详情、会话历史和任务交互。 |
| `public-agents.json` | 静态 Agent 数据配置，用于渲染列表、状态和详情信息。 |
| `source-index.css` | 源页面样式参考。 |
| `source-index.js` | 源页面脚本参考。 |
| `vendor-antd.js` | 本地依赖脚本。 |
| `DESIGN.md` | IQ Buddy 设计规范与组件说明。 |

## 本地运行

这是一个纯静态项目，可以直接用浏览器打开 `index.html`。

更推荐使用本地静态服务器预览，避免部分浏览器对本地 JSON 请求的限制：

```bash
python3 -m http.server 3000
```

启动后访问：

```text
http://localhost:3000/
```

入口页会自动跳转到主页面：

```text
http://localhost:3000/agents-replica.html
```

## 典型评审路径

1. 打开首页，进入硅基实习生工作台。
2. 切换左侧导航中的三个入口：
   - 硅基实习生-分栏
   - 硅基实习生-抽屉
   - 硅基实习生-弹窗
3. 在 Agent 列表中尝试搜索、筛选、打开权限详情。
4. 对比分栏、抽屉、弹窗三种详情体验。
5. 查看左侧会话/任务列表的展开、折叠、hover 和删除确认交互。

## 数据说明

`public-agents.json` 是当前演示页面的数据源，主要包含：

- Agent 名称、描述、状态、版本和工作组信息。
- training / serving 等不同视图类型。
- 权限、运行态、远端映射和展示所需的元信息。

如需调整演示内容，优先修改 `public-agents.json` 中的展示字段；如需调整交互逻辑，再修改 `agents-replica.html` 中的脚本。

## 设计说明

`DESIGN.md` 记录了该原型的主要设计规则，包括：

- 品牌色、语义色和状态色。
- 字号、字重、行高和文本截断规则。
- 页面布局、侧边栏、卡片网格、右侧分栏、弹窗和抽屉规范。
- Agent 卡片、导航项、按钮、标签、表格等组件细节。

后续改版时建议先同步更新 `DESIGN.md`，再调整页面代码，避免设计规则和页面实现脱节。

## 部署

项目通过 GitHub Pages 托管。将静态文件提交到 `main` 分支后，GitHub Pages 会自动发布最新版本。

常用提交流程：

```bash
git status
git add .
git commit -m "Update demo"
git push origin main
```

## 注意事项

- 该项目是静态原型，不包含登录、鉴权、后端接口或真实任务执行能力。
- 页面中的交互主要用于评审和体验验证，不代表完整生产逻辑。
- `public-agents.json` 中可能包含从内部环境导出的字段；发布前请确认不包含敏感信息。
