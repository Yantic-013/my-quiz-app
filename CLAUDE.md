# CLAUDE.md - 刷题网站项目

## 项目概述
纯前端刷题网站，单 HTML 文件，浏览器直接运行。

## 标准文件路径

| 文件 | 路径 | 说明 |
|------|------|------|
| 主应用 | `quiz-app.html` | 唯一代码文件 |
| 需求文档 | `docs/requirements.md` | 功能需求规格 |
| 技术规范 | `docs/tech-spec.md` | 技术选型与数据设计 |
| UI 规范 | `docs/ui-design.md` | 配色、布局、组件规范 |
| 开发步骤 | `docs/dev-steps.md` | 分阶段执行步骤 |
| 开发日志 | `dev-log/` | 每日开发记录 |
| 题库模板 | `templates/题库模板.xlsx` | Excel 导入模板 |

## 工作约定
1. 分阶段推进，每阶段完成并能验证后再进入下一阶段
2. 每次开发结束后更新 `dev-log/YYYY-MM-DD.md`，记录完成事项和待办事项
3. 所有代码在 `quiz-app.html` 单文件中，不拆分为多个文件
4. 修改代码前先阅读 `docs/` 下的规范文档，确保实现符合设计
5. 功能完成后在浏览器中实际验证，不从代码层面假设"应该没问题"

## 技术约束
- 纯前端，无后端，无框架，无构建工具
- 数据存储：localStorage
- Excel 导入：SheetJS CDN (`https://cdn.sheetjs.com/xlsx-0.20.1/package/dist/xlsx.full.min.js`)  — 必须使用！不允许替代库
- CSS 不使用任何 UI 框架（Bootstrap 等），全部手写
- 不引入任何 npm 依赖
