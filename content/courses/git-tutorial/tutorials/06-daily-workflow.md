# 06 日常运维

网站上线后，你每天都会和 Git 打交道。下面是新手最常遇到的几个场景。

## 每日基础流程

```bash
# 1. 开始工作前，拉取远程最新代码
git pull origin main

# 2. 修改文件……

# 3. 查看改动
git status

# 4. 加入暂存区
git add .

# 5. 提交
git commit -m "feat: xxx"

# 6. 推送
git push origin main
```

## .gitignore：让 Git 忽略某些文件

不是所有文件都需要提交。例如 `node_modules/`、`dist/`、`tmp-test-*.js` 这些文件通常不应该进入仓库。

在项目根目录创建 `.gitignore`：

```gitignore
# 依赖目录
node_modules/

# 构建输出（如果 Pages 是从 Actions 自动构建）
dist/

# 日志
*.log

# 临时文件
.DS_Store
Thumbs.db
```

## 分支简介

分支让你可以在不影响主分支的情况下做实验。

```bash
# 创建并切换到新分支
git checkout -b feature/new-page

# 查看所有分支
git branch

# 切换回 main
git checkout main

# 合并分支（先切换到 main）
git merge feature/new-page
```

作为新手，先在 `main` 分支上练习；等熟悉后再尝试分支开发。

## 撤销改动的几种情况

| 场景 | 命令 |
|------|------|
| 工作区改错了，想放弃 | `git checkout -- 文件名` |
| 已经 add 了，想取消暂存 | `git restore --staged 文件名` |
| 已经 commit 了，想修改最后一次提交 | `git commit --amend` |

## 冲突怎么办

当两个人修改了同一文件的同一位置，Git 无法自动合并，就会报冲突。

冲突文件里会出现类似：

```text
<<<<<<< HEAD
本地内容
=======
远程内容
>>>>>>> branch-name
```

手动编辑文件，保留你想要的内容，然后：

```bash
git add .
git commit -m "resolve merge conflict"
```

## 好习惯清单

- **小步提交**：一次 commit 只做一件事。
- **写好提交信息**：让未来的自己看得懂。
- **先 pull 再 push**：减少冲突。
- **不要提交敏感信息**：密码、API key、大文件。
- **经常 push**：本地硬盘不是备份。

## 你现在已经会了

- 安装和配置 Git
- 创建本地和远程仓库
- add / commit / push
- 部署 GitHub Pages
- 日常运维与排错

Git 的学习曲线在前几天最陡，但只要坚持用起来，很快就会变成肌肉记忆。祝你上船顺利！
