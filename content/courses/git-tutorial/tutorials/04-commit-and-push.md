# 04 提交与推送

Git 的核心工作流程可以总结为三个命令：

```bash
git add .
git commit -m "提交说明"
git push origin main
```

## 工作区、暂存区、仓库

理解这三个区域，是学会 Git 的关键：

| 区域 | 说明 | 对应命令 |
|------|------|----------|
| 工作区（Working Directory） | 你实际看到的文件 | 直接编辑文件 |
| 暂存区（Staging Area） | 准备提交的改动 | `git add` |
| 本地仓库（Repository） | 提交后的历史记录 | `git commit` |
| 远程仓库（Remote） | GitHub 上的仓库 | `git push` / `git pull` |

## 第一次提交

假设你修改了 `README.md`，现在想保存这次改动：

### 1. 查看状态

```bash
git status
```

你会看到 `README.md` 显示为红色（modified）。

### 2. 加入暂存区

```bash
git add README.md
```

或者一次性添加所有改动：

```bash
git add .
```

### 3. 提交到本地仓库

```bash
git commit -m "docs: update README with project intro"
```

提交说明的第一行要简洁，告诉别人这次改动做了什么。

### 4. 推送到 GitHub

```bash
git push origin main
```

- `origin` 是远程仓库的默认别名。
- `main` 是当前分支名。

## 常见提交信息格式

| 前缀 | 含义 |
|------|------|
| `feat:` | 新功能 |
| `fix:` | 修复 bug |
| `docs:` | 文档改动 |
| `style:` | 格式调整（不影响功能） |
| `refactor:` | 重构 |
| `chore:` | 杂项（如依赖更新） |

示例：

```bash
git commit -m "feat: add dark mode toggle"
git commit -m "fix: correct navigation link on mobile"
git commit -m "docs: update install instructions"
```

## 查看提交历史

```bash
git log
```

简化输出：

```bash
git log --oneline
```

## 推送前被拒绝了怎么办

如果 GitHub 上的仓库比本地新，会出现类似错误：

```text
! [rejected]        main -> main (fetch first)
```

这时需要先拉取远程改动，再推送：

```bash
git pull origin main --rebase
git push origin main
```

## 下一步

提交和推送掌握了，我们就可以把网站部署到 GitHub Pages，让全世界都能访问。
