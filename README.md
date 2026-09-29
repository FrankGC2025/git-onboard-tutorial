# Git Onboard Tutorial

一个面向 Git & GitHub 新手的实战上手指南。

这个项目不是一本完整的 Git 教科书，而是帮助第一次参与团队 GitHub 项目的同学，快速掌握**实际工作中最常用的 Git / GitHub 工作流**。

> **Start Here →** [在线教程](https://frankgc2025.github.io/git-onboard-tutorial/index.html)

## 你会学到什么

教程围绕真实的团队协作场景展开，主要包括：

- Git 和 GitHub 分别是什么，以及为什么需要它们
- Windows 上安装和配置 Git
- Clone 一个已有的 GitHub repository
- 修改文件、查看状态和差异
- Commit、Pull、Push
- 使用 Branch 开发新内容
- 通过 Pull Request 提交修改
- Pull Before You Work 的基本协作习惯
- Merge Conflict 的基本处理思路
- GitHub Pages 静态网站部署
- 常见 Git / GitHub 问题与排查方法

重点不是记住很多命令，而是建立一套清晰的工作流程：

```text
Working Directory
      │
      │ git add
      ▼
Staging Area
      │
      │ git commit
      ▼
Local Repository
      │
      │ git push
      ▼
GitHub Repository
```

## 推荐学习方式

如果你是第一次接触 Git，建议按照网站中的教程顺序完成，而不是只看命令列表。

最推荐的练习路径：

1. 安装 Git 并完成基本配置
2. Clone 一个 repository
3. 修改一个 Markdown 文件
4. `git status` → `git add` → `git commit` → `git push`
5. 创建自己的 branch
6. Push branch 到 GitHub
7. 创建 Pull Request
8. 练习一次 Merge Conflict
9. 再进入真正的团队项目

这样你学到的是一套可以直接迁移到其他 GitHub 项目的工作流。

## 本地运行

这是一个 Node.js 静态网站项目。

### 1. 安装依赖

```bash
npm install
```

### 2. 本地构建并预览

```bash
npm run serve
```

默认会先执行 build，然后使用 `serve` 启动生成后的 `dist/` 目录。

如果需要使用 GitHub Pages 的路径前缀：

```bash
npm run serve:gh
```

### 3. 只构建网站

```bash
npm run build
```

GitHub Pages 使用：

```bash
npm run build:gh
```

## 项目结构

```text
git-onboard-tutorial/
├── content/              # 教程正文，以 Markdown 为主要内容格式
│   └── courses/          # 各教程/课程内容
├── public/               # 原始静态资源，例如图片
├── scripts/
│   └── build.js          # Markdown → HTML、搜索索引等构建逻辑
├── src/
│   └── assets/           # CSS / JavaScript 等网站资源
├── package.json           # Node.js 项目配置与依赖
└── README.md              # 项目说明
```

构建完成后，网站会生成到：

```text
dist/
```

## 技术栈

项目采用比较轻量的静态网站方案：

- **Node.js** — 构建工具链
- **Markdown** — 教程内容
- **Markdown-it** — Markdown 渲染
- **KaTeX** — 数学公式
- **highlight.js** — 代码高亮
- **MiniSearch** — 前端全文搜索
- **GitHub Pages** — 网站部署

项目不依赖数据库或后端服务，因此教程内容可以直接通过 Git 管理和发布。

## GitHub Pages 部署

网站部署在 GitHub Pages：

**https://frankgc2025.github.io/git-onboard-tutorial/**

基本部署流程：

1. 修改 `content/`、`src/` 或其他项目文件
2. Commit 修改
3. Push 到 GitHub
4. GitHub Actions 执行构建与部署
5. GitHub Pages 发布最新版本

如果以后把这个项目作为团队协作练习，可以把整个过程本身作为 Git 教程的一部分。

## 内容与网站代码分离

这个项目有意把**教程内容**和**网站实现**分开：

- 想增加教程 → 主要修改 `content/`
- 想修改网站样式 → 修改 `src/assets/`
- 想修改 Markdown → HTML 的构建逻辑 → 修改 `scripts/build.js`
- 想修改图片等静态资源 → 放入 `public/`

因此，完全不会写 JavaScript 的同学，也可以主要通过编辑 Markdown 来参与内容贡献。

## 给贡献者

如果你要参与这个项目，推荐遵循：

```bash
git switch main
git pull

git switch -c feature/your-change

# 修改文件后
git status
git add .
git commit -m "docs: add xxx"
git push -u origin feature/your-change
```

然后在 GitHub 上创建 Pull Request，经过检查后再合并到 `main`。

### Golden Rules

- **不要直接在 `main` 上开发。**
- **开始工作前先 `git pull`。**
- **一次 commit 尽量只完成一个清晰的修改。**
- **Commit message 要说明“改了什么”。**
- **Push branch，然后通过 Pull Request 合并。**
- 如果看到 `CONFLICT`、`rejected`、`fatal:` 等错误，先运行 `git status`，不要盲目复制网上的命令。

## 为什么这个项目存在

Git 对第一次接触团队开发的人来说，真正困难的通常不是某一个命令，而是不知道：

> **“我现在应该在哪个 branch？什么时候 pull？什么时候 commit？什么时候 push？什么时候开 Pull Request？”**

所以这个项目更关注**实际工作流**，而不是试图覆盖 Git 的所有高级功能。

---

## License

This project is intended as an educational Git & GitHub onboarding resource.
