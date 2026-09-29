# Git Onboard Tutorial

一份给纯新手的 Git & GitHub 上船指南，用静态网页方式一步步讲解：

- 为什么要用 Git
- 在 Windows 上安装 Git
- 配置 Git 用户名和邮箱
- 创建第一个仓库
- 提交、推送、拉取
- 在 GitHub 上部署静态网页
- 日常运维与常见问题

## 本地开发

```bash
npm install
npm run serve
```

## 部署到 GitHub Pages

1. 在 GitHub 上创建仓库 `git-onboard-tutorial`。
2. 把本地仓库推送到 `origin main`。
3. 进入仓库 Settings → Pages → Source 选择 **GitHub Actions**。
4. 推送后 GitHub Actions 会自动构建并部署。

## 目录结构

```
content/          # Markdown 教程内容
public/           # 图片等静态资源
scripts/build.js  # 构建脚本
src/assets/       # CSS / JS
```
