---
title: 07 用网页版 ChatGPT 修改 GitHub Repo
---

# 用网页版 ChatGPT 修改 GitHub Repo

如果你已经会基本的 Git workflow，那么还有一种非常方便的方式：

> **让网页版 ChatGPT 连接你的 GitHub repository，阅读代码、修改文件，并通过 branch + commit + Pull Request 提交修改。**

这并不意味着 ChatGPT 取代 Git。相反，ChatGPT 做的事情仍然应该遵循你熟悉的 Git workflow：

![ChatGPT + GitHub workflow](../../../chatgpt-github-workflow.svg)

```text
你的需求
   │
   ▼
ChatGPT 读取 Repository
   │
   ▼
ChatGPT 分析 / 修改文件
   │
   ▼
创建 Branch
   │
   ▼
Commit
   │
   ▼
Pull Request
   │
   ▼
你 Review
   │
   ▼
Merge → main
```

这种方式特别适合：

- 不熟悉代码的团队成员
- 想让 AI 帮忙修改 Markdown / HTML / CSS / JavaScript 的人
- 想快速定位 bug 或理解陌生项目的人
- 希望保留 Pull Request review 流程的团队

---

## 1. 先连接 GitHub

在 ChatGPT 中打开 **Settings → Apps / Connectors**，找到 GitHub 并完成授权。

授权过程中，你可能会看到类似下面的界面：

![GitHub authorization screen](../../../chatgpt-github-connection.svg)

这个示意图根据实际连接界面整理而成。具体按钮、权限描述和页面布局可能随 ChatGPT / GitHub 版本变化。

完成连接后，GitHub connector 会显示为已安装或已连接。此时 ChatGPT 才可以按照你授予的权限访问相应 repository。

> **重要：** 不要为了一个普通教程仓库就给任何工具不必要的权限。只连接你真正需要使用的 repository。

连接完成后，可以直接在 ChatGPT 对话中告诉它：

```text
Read my GitHub repository:
FrankGC2025/git-onboard-tutorial

Please review the current structure and README.
```

如果连接成功，ChatGPT 应该能够读取 repository 中的文件。

---

## 2. 不要一上来就让 AI “随便改”

第一次使用时，推荐先让 ChatGPT **Read / Review**，而不是直接修改：

```text
Read my repository and review:
1. the project structure
2. README.md
3. the current tutorial organization

Do not modify anything yet.
```

这样做有两个好处：

1. AI 会先理解项目，而不是根据一个文件片段猜测。
2. 你可以先判断 AI 对项目的理解是否正确。

这和找一个新队友加入项目很像：

> **先让它读代码，再让它动代码。**

---

## 3. 给 AI 一个明确的修改任务

当你确认 AI 已经理解项目后，再提出具体修改。

例如：

```text
Please add a new tutorial explaining how to use
the ChatGPT web interface to work with a GitHub repository.

Keep the existing writing style and folder structure.
Do not modify unrelated files.
Please create a new branch and open a Pull Request.
```

一个好的任务描述通常包含：

| 内容 | 示例 |
|---|---|
| 做什么 | Add a new GitHub + ChatGPT tutorial |
| 改哪里 | content/courses/git-tutorial/tutorials/ |
| 风格 | Keep the existing writing style |
| 范围 | Do not modify unrelated files |
| Git workflow | Create a branch and open a PR |

---

## 4. 为什么推荐让 AI 创建 Branch？

**不要让 AI 直接修改 `main`。**

推荐：

```text
main
 │
 ├── feature/chatgpt-github
 │
 │     └── 修改文件
 │
 ▼
Pull Request
 │
 ▼
Review
 │
 ▼
Merge
```

这样即使 AI 的修改不符合预期，也不会直接破坏正式版本。

你甚至可以明确告诉 ChatGPT：

```text
Do not modify main directly.
Create a new branch first, make the changes there,
commit them, and open a Pull Request against main.
```

---

## 5. ChatGPT 可以帮你完成哪些事情？

连接 GitHub 后，常见任务包括：

### 阅读项目

```text
Read this repository and explain how the build system works.
```

### 修改 Markdown

```text
Add a new tutorial about merge conflicts.
Keep the current Markdown style.
```

### 修改网页样式

```text
Make the navigation bar more compact on mobile.
Do not change the color palette.
```

### 修复 Bug

```text
The search box does not work on GitHub Pages.
Please inspect the relevant files and identify the problem.
```

### Code Review

```text
Review the current implementation for unnecessary complexity
and potential bugs. Do not modify anything yet.
```

### Pull Request

```text
Create a branch for this change, commit the changes,
and open a Pull Request against main.
```

---

## 6. 让 AI 修改 Repo 时，最好遵循这个模板

以后你可以直接复制下面这个模板：

```text
Repository:
FrankGC2025/your-repository

Task:
[describe exactly what you want]

Please:
1. Read the relevant existing files first.
2. Follow the existing project structure and style.
3. Modify only the files necessary for this task.
4. Do not modify main directly.
5. Create a new branch.
6. Commit the changes with a clear commit message.
7. Open a Pull Request against main.
8. In the Pull Request description, briefly explain what was changed.
9. Clearly indicate that the change was AI-assisted by ChatGPT.
```

---

## 7. Review the Pull Request yourself

**不要因为 AI 写出来了，就直接 Merge。**

Pull Request 的意义仍然存在。

你应该检查：

- 修改了哪些文件？
- 有没有修改不相关的文件？
- 内容是否符合项目要求？
- 有没有引入新的 bug？
- Commit message 是否清楚？
- 页面是否仍然可以正常 build？
- 是否需要继续让 ChatGPT 修改？

如果不满意，可以直接告诉 ChatGPT：

```text
I reviewed the Pull Request.
Please change the following:

1. ...
2. ...
3. ...

Keep the same branch and update the existing Pull Request.
Do not create a new PR.
```

这样就形成了一个很自然的循环：

```text
ChatGPT 修改
      ↓
Pull Request
      ↓
你 Review
      ↓
提出修改意见
      ↓
ChatGPT 更新 Branch
      ↓
再次 Review
      ↓
Merge
```

---

## 8. ChatGPT 和 Claude / Cursor 等工具有什么不同？

不同 AI 工具的具体 GitHub 集成方式会变化，但核心思想是一样的：

> **AI 是协作者，Git 是版本控制系统。**

不要把 AI 当成一个“直接替你覆盖整个项目”的黑盒。

更好的方式是：

```text
Human
  │
  │ requirements / review
  ▼
AI
  │
  │ code / documentation changes
  ▼
Git Branch
  │
  │ Pull Request
  ▼
Human Review
  │
  ▼
main
```

这样即使以后你换成其他 AI 工具，工作方式也不需要改变。

---

## 9. 关于 “ChatGPT 署名”

如果你希望团队成员知道某个 Pull Request 是由 ChatGPT 协助完成的，可以在 PR 描述中明确写：

```text
AI-assisted by ChatGPT.
```

例如：

```text
## Summary

AI-assisted by ChatGPT.

### Changes
- ...
- ...
- ...

### Review
The changes should be reviewed by a human before merging.
```

需要注意的是：通过 GitHub connector 执行的操作仍然使用你授权的 GitHub 账号完成。因此，**不要伪造一个名为 “ChatGPT” 的 GitHub 用户作为 commit author**。

更透明的做法是：

- GitHub commit / PR 保留真实执行账号
- PR description 标注 **AI-assisted by ChatGPT**
- 人类负责最终 Review 和 Merge

如果项目团队有自己的 AI attribution convention，优先遵循团队约定。

---

## 10. 最后记住

使用网页版 ChatGPT 修改 GitHub Repo，并不意味着你不需要学习 Git。

恰恰相反，你至少应该理解：

```text
Repository
   ↓
Branch
   ↓
Commit
   ↓
Pull Request
   ↓
Review
   ↓
Merge
```

因为 AI 可以帮你执行很多操作，但**你仍然需要知道这些操作意味着什么**。

### 最推荐的工作方式

```text
先让 ChatGPT 阅读
        ↓
确认它理解项目
        ↓
明确提出修改要求
        ↓
让它创建 Branch
        ↓
检查 Commit
        ↓
Review Pull Request
        ↓
满意后 Merge
```

> **AI 可以帮你写代码，但 Git workflow 仍然应该由你掌握。**
