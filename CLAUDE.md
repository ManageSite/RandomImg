# RandomImg — 项目规范

## 项目概述
二次元随机图片加载器，静态网页应用，部署于 GitHub Pages。

## 目录结构

```
RandomImg/
├── index.html              # 入口页面
├── assets/
│   ├── css/
│   │   └── style.css       # 样式表
│   ├── js/
│   │   └── app.js          # 主逻辑（ImageLoader 类）
│   └── images/             # 图片资源（预留）
├── test/
│   └── test.html           # 测试页面
├── .github/workflows/      # CI/CD 配置
├── CNAME                   # 自定义域名配置
├── README.md               # 项目简介
├── CLAUDE.md               # 本文件：开发与协作规范
└── .gitignore              # Git 忽略规则
```

## Git 工作流

采用 **Dev → Main 合并流**：

```
main  ──────────────────●─────────  (生产/稳定分支，仅接受合并)
                         ↑
dev   ──●────●────●────●────●────  (日常开发分支，所有提交在此)
             ↑
feature ─────┘  (复杂功能可临时开子分支，完成后合并回 dev)
```

### 分支规则

| 分支 | 用途 | 提交方式 |
|------|------|----------|
| `main` | 生产环境，GitHub Pages 自动部署 | **禁止直接提交**，仅接受 `dev` 的 Merge/Pull Request |
| `dev` | 日常开发、功能集成 | 直接提交或 feature 分支合并 |
| `feature/*` | 复杂功能开发（可选） | 完成后合并回 `dev` 并删除 |

### 开发流程

1. 确保在 `dev` 分支上开发：
   ```bash
   git checkout dev
   git pull origin dev   # 同步远程更新
   ```

2. 开发完成后提交：
   ```bash
   git add .
   git commit -m "描述本次变更"
   git push origin dev
   ```

3. 准备发布时，将 `dev` 合并到 `main`：
   ```bash
   git checkout main
   git merge dev         # Fast-forward 合并
   git push origin main
   ```

### Commit 规范

- 使用中文或英文简明描述变更
- 格式：`<动作>: <描述>`，例如 `feat: 添加新的图片源`
- 常见动作：`feat`（新功能）、`fix`（修复）、`style`（样式）、`refactor`（重构）、`docs`（文档）

## 开发规范

### 代码风格
- JavaScript：使用 ES6+ Class 语法，保持现有 `ImageLoader` 类结构
- CSS：保持 BEM-like 命名风格
- HTML：语义化标签，中文界面

### API 与数据源
- 图片源配置集中管理于 `ImageLoader.imageSources`
- 所有外部请求通过 CORS 代理 `https://cors.mythlogos.top`
- 添加/修改图源时需同步更新 `index.html` 中的选择器 UI

### 安全注意
- `app.js` 为源码文件，**禁止**用混淆版本覆盖源码提交
- 混淆版仅在部署时作为可选优化，不纳入版本控制
