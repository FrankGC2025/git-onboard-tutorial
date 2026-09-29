# 05 部署 GitHub Pages

GitHub Pages 是 GitHub 提供的免费静态网页托管服务。只要你的仓库里有 HTML 文件，就可以一键上线。

## 准备工作

确保你的仓库根目录有可以部署的内容。对于本教程的项目，构建后会生成 `dist/` 文件夹，里面就是静态网页。

## 启用 GitHub Pages

1. 打开 GitHub 仓库页面，点击 **Settings**。
2. 左侧菜单选择 **Pages**。
3. 在 **Build and deployment** 下，Source 选择 **GitHub Actions**。

![GitHub Pages 设置](figures/github-pages-configure.png)

## 添加部署工作流

在仓库中创建文件 `.github/workflows/deploy.yml`，内容如下：

```yaml
name: Deploy to GitHub Pages

on:
  push:
    branches: [main]
  workflow_dispatch:

permissions:
  contents: read
  pages: write
  id-token: write

concurrency:
  group: "pages"
  cancel-in-progress: false

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v4
      - name: Setup Node
        uses: actions/setup-node@v4
        with:
          node-version: "20"
          cache: npm
      - name: Install dependencies
        run: npm ci
      - name: Build site
        run: npm run build:gh
      - name: Upload artifact
        uses: actions/upload-pages-artifact@v3
        with:
          path: ./dist

  deploy:
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    runs-on: ubuntu-latest
    needs: build
    steps:
      - name: Deploy to GitHub Pages
        id: deployment
        uses: actions/deploy-pages@v4
```

## 提交并推送

```bash
git add .
git commit -m "ci: add GitHub Pages deployment workflow"
git push origin main
```

## 查看部署状态

推送后，进入仓库的 **Actions** 标签页，可以看到工作流正在运行。

![GitHub Actions 部署失败示例](figures/github-actions-error.png)

如果看到红色失败标志，点击进去查看具体错误。常见问题包括：

- `package.json` 里的依赖没写全
- 构建脚本路径错误
- 仓库 Settings → Pages 里没有选择 GitHub Actions

## 部署成功

工作流变成绿色后，回到 **Settings → Pages**，你会看到类似：

![GitHub Pages 已上线](figures/github-pages-live.png)

点击链接即可访问你的网站：

```text
https://你的用户名.github.io/仓库名/
```

## 更新网站

以后每次推送 `main` 分支，GitHub Actions 都会自动重新构建和部署。通常等 1–2 分钟即可生效。

## 下一步

网站上线了，但真正的运维才刚刚开始。下一节讲日常 workflow 和常见问题。
