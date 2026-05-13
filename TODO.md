# 项目待办 (Todolist)

说明：按照「先能运行→代码质量→功能完善→优化/文档」的顺序排列。优先级说明：必做 = Must，应该 = Should，额外 = Nice-to-have。估时为粗略小时数（单人）。

## 0. 快速可运行（必须）
- [ ] 初始化 README（Must, 0.5h）
  - 简短说明项目用途、运行方式（本地打开 index.html 或 npm start）、依赖、demo 地址（http://demo.game.io/）。
- [ ] 提供运行脚本 / 指引（Must, 0.5h）
  - 若使用构建工具则写 `package.json` scripts（start/build/serve）。
- [ ] 检查并补齐 `index.html`（Must, 1h）
  - 确保引用的 JS/CSS 路径正确，页面能在本地预览。

## 1. 项目结构与开发环境（Must/Should）
- [ ] 规范目录结构（Should, 1h）
  - 建议： `src/`（模块化 JS）、`assets/`（图片/音频）、`dist/`（构建产物）、`docs/`。
- [ ] 添加 package.json 与依赖管理（Should, 0.5h）
  - node + npm 或 pnpm，列出 devDependencies（eslint、prettier、http-server）。
- [ ] 配置 ESLint + Prettier（Should, 1.5h）
  - 保持 JS 风格一致，添加 `.eslintrc` 与 `.prettierrc`。
- [ ] 添加 .gitignore（Must, 0.2h）
  - 忽略 node_modules、dist、.DS_Store 等。

## 2. 核心功能实现（Must）
- [ ] 抽离主逻辑到模块（Must, 2-4h）
  - 将游戏初始化、游戏循环、渲染与输入分别模块化（eg. `src/init.js`, `src/loop.js`, `src/render.js`, `src/input.js`）。
- [ ] 游戏循环与渲染的稳定性（Must, 2h）
  - 使用 requestAnimationFrame，分离 update 与 render。
- [ ] 资源加载管理（Should, 2h）
  - 统一加载图片/音频并显示加载进度/错误处理。
- [ ] 基本错误处理与日志（Should, 1h）
  - 在控制台输出清晰的错误信息，必要时友好提示用户。

## 3. 质量保障（Should）
- [ ] 单元测试（逻辑层）（Should, 3h）
  - 用 Jest 或其它测试框架测试关键算法（碰撞检测、分数计算等）。
- [ ] 简单的集成/端到端测试（Nice-to-have, 4h）
  - 使用 Playwright/Chromium 做场景测试（可选）。
- [ ] 性能检查（Should, 2h）
  - FPS 监控、内存泄露检查、Canvas 绘制优化。

## 4. 可访问性与响应式（Should）
- [ ] 响应式布局（Should, 2h）
  - 在不同分辨率下适配画布与UI（移动/桌面）。
- [ ] 键盘/触摸输入支持（Should, 2h）
  - 触摸事件适配及按键映射说明。
- [ ] 基本无障碍支持（Nice-to-have, 2h）
  - 可通过键盘操作、为重要元素添加 aria-label。

## 5. 部署与 CI（Should）
- [ ] GitHub Pages 部署（Should, 0.5h）
  - 配置 `gh-pages` 或 Actions 自动部署 `dist/`。
- [ ] 添加 GitHub Actions（CI）（Should, 1.5h）
  - 流程：checkout → install → lint → test → build → deploy（可选）。
- [ ] 版本发布/变更日志（Nice-to-have, 1h）
  - 使用 `CHANGELOG.md` 或 Releases。

## 6. 文档与贡献（Should/Nice）
- [ ] CONTRIBUTING.md（Nice-to-have, 1h）
  - 分支/PR 规范、提交信息格式、代码风格。
- [ ] PR 模板与 Issue 模板（Nice-to-have, 0.5h）
  - 提高协作效率。
- [ ] API / 模块文档（Should, 2h）
  - 简要说明各模块职责与导出接口。

## 7. 额外优化（Nice-to-have）
- [ ] 自动化格式化 (pre-commit hooks)（Nice-to-have, 1h）
  - husky + lint-staged。
- [ ] 性能上进一步优化（Nice-to-have, 4h）
  - 精灵图、资源合并、减少重绘。
- [ ] 添加遥测/错误收集（Sentry 等）（Nice-to-have, 2h）
- [ ] 国际化支持（Nice-to-have, 3h）

---

## 开发习惯建议（推荐遵循）
- 分支命名：`feat/<描述>`、`fix/<描述>`、`chore/<desc>`。
- 提交信息：遵循 Conventional Commits（`feat: ...`, `fix: ...`, `chore: ...`）。
- PR 流程：小而频繁的 PR + 描述要包含目的与如何测试。
- 代码审查重点：可读性、错误处理、性能（热路径）、资源释放。
