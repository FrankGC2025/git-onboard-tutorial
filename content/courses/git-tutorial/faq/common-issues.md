# 常见问题

## Q1: `git` 命令找不到

**原因**：Git 没有正确安装，或者没有加入系统 PATH。

**解决**：

1. 重新运行 Git 安装程序。
2. 在安装过程中选择 **"Git from the command line and also from 3rd-party software"**。
3. 安装完成后重启终端。

## Q2: 每次 push 都要输入用户名密码

**原因**：使用的是 HTTPS 链接且没有配置凭据缓存。

**解决**：

```bash
git config --global credential.helper cache
```

或者在 GitHub 上设置 SSH key，改用 SSH 链接克隆仓库。

## Q3: `git push` 被拒绝

**错误信息**：

```text
! [rejected]        main -> main (fetch first)
```

**解决**：

```bash
git pull origin main --rebase
git push origin main
```

## Q4: GitHub Pages 没有更新

**排查步骤**：

1. 进入仓库 **Actions** 页面，看最新 workflow 是否成功。
2. 如果失败，点击查看日志，定位错误。
3. 如果成功，等 1–2 分钟后硬刷新网页（`Ctrl + F5`）。
4. 确认 Settings → Pages 的 Source 是 **GitHub Actions**。

## Q5: 误删了文件怎么办

如果文件已经提交过，可以用以下命令恢复：

```bash
git checkout -- <文件名>
```

如果已经 commit 后又删除了，可以用 `git log` 找到历史版本，再 `git checkout <commit-id> -- <文件名>`。

## Q6: 仓库里有很多不想提交的文件

在项目根目录创建 `.gitignore` 文件，列出要忽略的文件或目录：

```gitignore
node_modules/
dist/
*.log
```

如果文件已经被 Git 跟踪，需要先用 `git rm --cached <文件>` 取消跟踪。

## Q7: 如何修改已经 push 的提交信息

如果只是一次 push，可以：

```bash
git commit --amend -m "新的提交信息"
git push origin main --force-with-lease
```

⚠️ 注意：修改已经 push 的历史会改变 commit ID，团队协作时要谨慎使用。
