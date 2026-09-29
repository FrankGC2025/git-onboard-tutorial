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
