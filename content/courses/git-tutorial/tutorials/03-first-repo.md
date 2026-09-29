# 03 创建第一个仓库

仓库（repository，简称 repo）就是 Git 用来存放项目历史的地方。一个仓库可以理解成一个被 Git 管理的文件夹。

## 方式一：从本地创建（git init）

1. 新建一个项目文件夹，比如 `my-first-repo`。
2. 在文件夹内右键，选择 **Git Bash Here**。
3. 输入：

```bash
git init
```

你会看到类似输出：

```text
Initialized empty Git repository in D:/Frank/my-first-repo/.git/
```

这表示 Git 已经在这个文件夹里建立了一个空的仓库。此时文件夹里会多出一个隐藏的 `.git` 目录，里面存储了所有的版本历史。

## 方式二：从 GitHub 创建（推荐）

1. 登录 GitHub，点击右上角 **+** → **New repository**。
2. 填写仓库名，例如 `my-first-repo`。
3. 选择 **Public**（公开）或 **Private**（私有）。
4. 勾选 **Add a README file**。
5. 点击 **Create repository**。

## 把远程仓库克隆到本地

在 GitHub 仓库页面点击绿色的 **Code** 按钮，复制 HTTPS 链接，然后运行：

```bash
git clone https://github.com/你的用户名/my-first-repo.git
```

这会在当前目录下创建一个 `my-first-repo` 文件夹，里面就是仓库的完整内容。

## 项目文件夹结构

一个典型的静态网页项目长这样：

![项目文件夹结构](figures/project-folder-structure.png)

```text
my-first-repo/
├── .github/          # GitHub 配置（如 Actions 工作流）
├── content/          # Markdown 内容
├── public/           # 静态资源（图片、字体等）
├── scripts/          # 构建脚本
├── src/              # 源码（CSS、JS）
├── .gitignore        # 告诉 Git 忽略哪些文件
├── package.json      # Node.js 项目配置
└── README.md         # 项目说明
```

## 查看仓库状态

进入仓库目录后，随时可以用：

```bash
git status
```

它会告诉你：

- 当前在哪个分支
- 有哪些文件被修改了
- 有哪些新文件还没被 Git 跟踪

## 下一步

仓库创建好了，接下来学习如何提交和推送你的第一次改动。
