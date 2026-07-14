# Workflow Studio Public Demo

IQ Buddy / Workflow Studio 的静态交互原型，用于演示硅基实习生、自动化任务、会话历史、权限申请等工作台体验。

## 在线访问

- GitHub Pages: https://monica137142.github.io/workflow-studio-public-demo/
- GitHub 仓库: https://github.com/monica137142/workflow-studio-public-demo

## 项目内容

- `index.html`: 入口页，自动跳转到主原型页面。
- `agents-replica.html`: 主演示页面，包含侧导航、硅基实习生列表、权限详情、抽屉/弹窗/分栏形态、会话历史和自动化任务等交互。
- `public-agents.json`: Agent 数据配置。
- `source-index.css`: 源页面样式参考。
- `source-index.js`: 源页面脚本参考。
- `vendor-antd.js`: 本地依赖脚本。
- `DESIGN.md`: 设计系统说明。

## 主要功能

- 侧导航包含三个硅基实习生入口：
  - `硅基实习生-分栏`
  - `硅基实习生-抽屉`
  - `硅基实习生-弹窗`
- 三个硅基实习生入口的筛选、搜索、详情打开状态和滚动位置相互独立。
- 支持开通权限详情的分栏、右侧抽屉和弹窗三种展示方式。
- 权限详情内提供固定头部、简介内容、支持平台地区表格和使用手册链接。
- 左侧会话/任务列表支持历史会话、更多折叠、展开收起、hover 新建和删除确认。
- 对话页、任务页和自动化页保留基础原型交互。

## 本地预览

这是一个静态页面项目，可以直接打开 `index.html`，也可以用任意静态服务器预览：

```bash
python3 -m http.server 3000
```

然后访问：

```text
http://localhost:3000/
```

## 部署方式

本项目通过 GitHub Pages 托管。提交到 `main` 后，GitHub Pages 会使用仓库中的静态文件生成访问页面。

## 备注

该仓库主要用于原型评审和交互验证，不包含后端服务。页面中的数据和交互多为本地静态模拟。
