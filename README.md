# RandomImg

二次元随机图片加载器 —— 一个简洁优雅的静态网页应用，支持多图源选择和批量加载。

## 在线访问

通过 GitHub Pages 部署：
- 主站：https://managesite.github.io/RandomImg/
- 自定义域名：（如已配置 CNAME）

## 功能特性

- 支持多个二次元图片 API 源（栗次元、樱花二次元、Jitsu 等）
- 批量加载（1–20 张），带进度条和加载状态统计
- 响应式布局，适配移动端
- 图片悬停缩放效果
- 右键复制图片地址

## 技术栈

- HTML5 + CSS3（Grid / Flexbox）
- Vanilla JavaScript（ES6 Class）
- Font Awesome 图标
- GitHub Pages 部署

## 本地开发

```bash
git clone git@github.com:ManageSite/RandomImg.git
cd RandomImg
git checkout dev        # 所有开发在 dev 分支进行
# 直接用浏览器打开 index.html 即可预览
```

## 项目结构

```
├── index.html              # 入口页面
├── assets/
│   ├── css/style.css       # 样式表
│   └── js/app.js           # 主逻辑
├── test/
│   └── test.html           # 测试页
└── .github/workflows/      # CI 配置
```

## 开发工作流

本项目采用 `dev` → `main` 分支模型：
- **`dev`**：日常开发分支，所有新功能在此开发
- **`main`**：生产分支，仅接受 `dev` 的合并，自动触发 GitHub Pages 部署

详见 [CLAUDE.md](./CLAUDE.md)。

## License

MIT
