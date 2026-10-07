# 常用命令速查

## 配置

```bash
git config --global user.name "你的名字"
git config --global user.email "你的邮箱"
git config --list
```

## 仓库操作

```bash
git init                          # 在当前文件夹初始化仓库
git clone <url>                   # 克隆远程仓库
git status                        # 查看仓库状态
git log --oneline                 # 查看简洁提交历史
```

## 提交 workflow

```bash
git add <文件>                     # 添加指定文件到暂存区
git add .                          # 添加所有改动
git commit -m "提交说明"            # 提交
git push origin main              # 推送到远程 main 分支
git pull origin main              # 从远程拉取最新代码
```

## 撤销与回退

```bash
git checkout -- <文件>             # 放弃工作区改动
git restore --staged <文件>        # 取消暂存
git commit --amend                # 修改最后一次提交
```

## 分支

```bash
git branch                        # 查看分支
git checkout -b <分支名>           # 创建并切换分支
git checkout <分支名>              # 切换分支
git merge <分支名>                 # 合并分支到当前分支
```

## 远程

```bash
git remote -v                     # 查看远程仓库地址
git remote add origin <url>       # 关联远程仓库
```


## 团队协作：同步协作者的最新修改

这是实际做团队项目时非常常用的一组操作。假设你的协作者已经把新修改合并到了远程 `main`，而你只是想把最新版本同步到自己的电脑：

### 1. 先确认当前状态

```bash
git status
```

如果你还有**未提交的本地修改**，不要直接 `pull`；先处理这些修改（commit 或 stash），避免覆盖或产生冲突。

### 2. 更新本地 main

```bash
git switch main
git pull origin main
```

现在你的本地 `main` 就与 GitHub 上的 `main` 同步了。

### 3. 如果你自己的开发分支也需要最新 main

例如你正在 `frank-development` 上继续工作：

```bash
git switch frank-development
git merge main
```

如果出现：

```text
Already up to date.
```

说明你的开发分支已经包含最新的 `main`，不需要额外操作。

### 推荐的日常同步流程

```bash
git status
git switch main
git pull origin main

# 如果要继续自己的功能开发
git switch <你的分支>
git merge main
```

> **注意：** `git pull` 更新的是你当前所在的分支。  
> 如果你想更新 `main`，应该先 `git switch main`，再执行 `git pull origin main`。

---

## 团队项目：更新后在本地运行

Git 负责同步代码，但很多项目还需要重新安装依赖并启动开发服务器。

以使用 Node.js + pnpm 的项目为例：

```bash
pnpm install
pnpm dev
```

通常流程是：

```bash
git switch main
git pull origin main
pnpm install
pnpm dev
```

然后打开终端中显示的 localhost 地址，例如：

```text
http://127.0.0.1:5173/
```

如果 5173 已被其他程序占用，Vite 可能会自动使用 5174、5175 等其他端口；**以终端实际显示的地址为准。**

### 如果是在自己的 feature branch 上运行

```bash
git switch <你的分支>
git merge main
pnpm install
pnpm dev
```

这样可以确保你是在包含协作者最新代码的基础上继续开发。

> `pnpm install` 是否需要每次执行取决于项目是否有新的依赖变化。  
> 如果只是普通的 Git 同步、没有依赖变化，通常不必重复安装。

---

## 一眼判断：我现在该输入什么？

| 你的目的 | 命令 |
|---|---|
| 查看当前状态 | `git status` |
| 看自己在哪个 branch | `git branch` |
| 更新远程 main | `git switch main` → `git pull origin main` |
| 回到自己的开发分支 | `git switch <你的分支>` |
| 把最新 main 合并进自己的分支 | `git merge main` |
| 安装项目依赖 | `pnpm install` |
| 启动本地开发服务器 | `pnpm dev` |
| 检查项目能否正常构建 | `pnpm build` |

### 一个完整的真实场景

假设你的协作者刚刚把修改合并进 `main`，你想把最新版本拉到电脑上看看：

```bash
cd D:\你的项目文件夹

git status
git switch main
git pull origin main

pnpm install
pnpm dev
```

如果之后你要继续自己的开发：

```bash
git switch <你的分支>
git merge main
pnpm dev
```

这套流程可以作为团队项目中最常用的「**同步 → 更新 → 本地运行 → 继续开发**」模板。
