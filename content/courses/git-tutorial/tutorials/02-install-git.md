# 02 安装 Git

## 下载 Git

打开官网下载页面：

> https://git-scm.com/download/win

Windows 用户通常会自动下载安装包。下载完成后双击运行。

## 安装步骤

### 1. 选择组件

保持默认勾选即可。建议保留：

- **Windows Explorer integration**：右键菜单中显示 "Git Bash Here" 和 "Git GUI Here"。
- **Git LFS**：如果你以后需要管理大文件（如视频、高清图片），会用到。

![Git 安装：选择组件](figures/git-setup-components.png)

### 2. 开始菜单文件夹

直接点 Next。

![Git 安装：开始菜单文件夹](figures/git-setup-start-menu.png)

### 3. 选择默认编辑器

如果你安装了 **Visual Studio Code**，推荐选它。否则可以先保留默认的 Vim，以后再用命令改。

![Git 安装：默认编辑器](figures/git-setup-editor.png)

### 4. 初始分支名称

现在大部分项目都用 `main` 作为默认分支名，建议在这里改成 `main`，省得以后每次新建仓库都手动改。

![Git 安装：初始分支名称](figures/git-setup-branch-name.png)

### 5. 调整 PATH

选择 **"Git from the command line and also from 3rd-party software"**。这样你可以在 Git Bash、PowerShell 和 VS Code 终端里直接使用 git 命令。

![Git 安装：PATH 设置](figures/git-setup-path.png)

### 6. HTTPS 传输后端

保持默认的 **"Use the native Windows Secure Channel library"**，它兼容性更好。

![Git 安装：HTTPS 传输后端](figures/git-setup-https.png)

### 7. 完成安装

点击 Finish，安装结束。

![Git 安装：完成](figures/git-setup-complete.png)

## 验证安装

打开 **Git Bash**（或 PowerShell / VS Code 终端），输入：

```bash
git --version
```

如果看到类似下面的输出，说明安装成功：

```text
git version 2.55.0.windows.1
```

## 配置用户名和邮箱

Git 需要知道你是谁，这样每次提交才会记录作者信息。输入：

```bash
git config --global user.name "你的名字"
git config --global user.email "你的邮箱@example.com"
```

验证配置：

```bash
git config --list
```

建议用 GitHub 注册时使用的邮箱，这样提交记录才能正确关联到你的 GitHub 账号。

## 下一步

安装完成并配置好身份后，我们就可以创建第一个仓库了。
