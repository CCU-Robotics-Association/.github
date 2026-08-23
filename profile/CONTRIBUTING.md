<div align="center">

# CCU Robotics Association

## GitHub 提交与协作指南

![Git](https://img.shields.io/badge/Git-Workflow-F05032?style=flat-square\&logo=git\&logoColor=white)
![GitHub](https://img.shields.io/badge/GitHub-Collaboration-181717?style=flat-square\&logo=github\&logoColor=white)
![Standard](https://img.shields.io/badge/Code-Standard-2F81F7?style=flat-square)
![Association](https://img.shields.io/badge/AREA-ROBOTICS-E67E22?style=flat-square)

**Contribution · Collaboration · Maintenance**

</div>

> [!NOTE]
> 本文档用于规范 **CCU 机器人协会 GitHub Organization** 内的代码提交、分支管理、Commit、Pull Request 及 Issue 使用方式。

---

## 📌 导航

<table>
<tr>
<td width="50%" valign="top">

### 🚀 协作流程

* [基本原则](#-1-基本原则)
* [开始协作前](#-2-开始协作前)
* [Clone 项目](#-3-clone-项目)
* [分支规范](#-4-分支规范)
* [开发流程](#-5-开发流程)

</td>
<td width="50%" valign="top">

### 🛠 提交规范

* [Commit 规范](#-6-commit-提交规范)
* [Push 规范](#-7-push-规范)
* [Pull Request](#-8-pull-request-规范)
* [Issue](#-9-issue-使用规范)
* [最终检查](#-17-最终检查)

</td>
</tr>
</table>

# 📖 一、基本原则

关于协会 Github 中的 **协作项目**。

提交代码时，请遵循以下基本原则：

<div align="center">

|  #  | <div align="center"> 原则                       |
| :-: | :----------------------- |
|  01 | 请勿未经沟通直接修改不属于自己的内容           |
|  02 | 请勿未经沟通随意删除其他成员的代码            |
|  03 | 请勿将未经测试的代码直接提交到主分支       |
|  04 | 请每次提交只完成一个相对明确的任务         |
|  05 | 请 Commit 信息尽量说明本次修改内容    |
|  06 | 请提交前检查代码是否能够正常运行          |
|  07 | 请将重要修改优先通过 Pull Request 合并 |

</div>

> [!IMPORTANT]
> `main` 分支应尽量保持 **稳定、完整、可运行**。
> 若不确定自己的修改是否应该直接提交，请优先创建独立分支并提交 Pull Request。


# 🧑‍💻 二、Git 配置

首次使用 Git 时，需要配置用户名与邮箱。

```bash
git config --global user.name "你的GitHub用户名"
```

```bash
git config --global user.email "你的GitHub邮箱"
```

查看当前配置：

```bash
git config --global --list
```

# 📦 三、Clone 项目

选择 GitHub Repository。

点击：

```text
Code
```

复制仓库地址。

例如：

```bash
git clone https://github.com/CCU-Robotics-Association/项目名称.git
```

进入项目：

```bash
cd 项目名称
```

完整过程：

```text
GitHub Repository
        │
        ▼
      Code
        │
        ▼
 Copy Repository URL
        │
        ▼
    git clone
        │
        ▼
    Local Project
```

# 🌿 四、分支规范

## 4.1 主分支

项目默认主分支：

```text
main
```

`main` 应始终尽量保持：

> **稳定 · 完整 · 可运行**

因此一般情况下：

> [!WARNING]
> **请勿直接在 `main` 上进行较大的功能开发。**

## 4.2 开发分支

进行功能开发、Bug 修复或文档修改时，应建立新的分支。

推荐格式：

```text
类型/内容
```

## 4.3 分支类型

| Prefix      | 用途      | 示例                        |
| :---------- | :------ | :------------------------ |
| `feature/`  | 新功能开发   | `feature/opencv-camera`   |
| `fix/`      | Bug 修复  | `fix/image-read-error`    |
| `docs/`     | 文档修改    | `docs/update-readme`      |
| `refactor/` | 代码重构    | `refactor/pid-controller` |
| `test/`     | 测试相关    | `test/camera-module`      |
| `chore/`    | 配置、工程杂项 | `chore/update-config`     |

## 4.4 创建分支

```bash
git switch main
```

同步最新代码：

```bash
git pull
```

创建开发分支：

```bash
git switch -c feature/example
```

查看当前分支：

```bash
git branch
```

---

# 🔄 五、开发流程

流程：

```mermaid
flowchart LR
    A[同步 main] --> B[创建开发分支]
    B --> C[进行开发]
    C --> D[本地测试]
    D --> E[git add]
    E --> F[git commit]
    F --> G[git push]
    G --> H[Pull Request]
    H --> I[Review]
    I --> J[Merge]
```

# 📝 六、Commit 提交规范

Commit 是 Git 项目中重要的开发记录。

## ✅ 推荐格式

```text
type: description
```

##  Commit 类型

|    Type    | 含义     
| :--------: | :----- 
|   `feat`   | 新功能
|    `fix`   | 修复 Bug
|   `docs`   | 文档修改
|   `style`  | 格式调整
| `refactor` | 代码重构
|   `perf`   | 性能优化
|   `test`   | 测试
|   `build`  | 构建相关
|    `ci`    | CI 相关
|   `chore`  | 其他修改
|  `revert`  | 回退修改

> [!TIP]
> Commit 应包含：
>
> **有效信息**

# ⬆️ 七、Push 规范

开发分支首次 Push：

```bash
git push -u origin branch-name
```

例如：

```bash
git push -u origin feature/opencv-camera
```

后续提交：

```bash
git push
```

## ⚠️ Force Push

除特殊情况外，请避免：

```bash
git push --force
```

尤其禁止：

```text
main
```

执行 Force Push。

> [!CAUTION]
> Force Push 可能直接覆盖远程提交记录，导致代码丢失。

# 🔀 八、Pull Request 规范

### ❌ 严禁

```text
    开发
     │
     ▼
直接 Push main
```

### ✅ 推荐

```text
  开发分支
     │
     ▼
    Push
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

## 8.1 PR 标题

建议与 Commit 保持类似格式：

```text
type: description
```

## 8.2 PR 描述

Pull Request 至少需要说明：

```markdown
- 修改内容

- 修改原因

- 测试情况
```

# 💬 九、Issue 使用规范

Issue 可以用于：

- Bug 报告
- 功能建议
- 开发任务
- 文档问题
- 项目讨论

# 📚 十、README 与文档规范

协会项目原则上都应该具备：

```text
README.md
```

# 🗂 十一、文件与目录规范

保持清晰的目录结构。

例如 Python 项目：

```text
project/
│
├── README.md
├── LICENSE
├── requirements.txt
│
├── src/
│   ├── main.py
│   └── utils.py
│
├── docs/
│   └── images/
│
└── tests/
```

## 11.1 禁止的命名方式

```text
新建文件夹
新建文件夹2
test2
test3
最终
最终2
```

# 🔐 十二、禁止提交内容

> [!CAUTION]
> 以下内容原则上 **禁止上传 GitHub**。

## Password

```python
password = "xxxx"
```

## Token / API Key

```text
GitHub Token
OpenAI API Key
QQ 机器人Token
云服务Access Key

......
```

## 私钥

```text
id_rsa
*.pem
*.key

......
```

## 数据库账号

```text
DATABASE_PASSWORD
DATABASE_URL

......
```

> [!IMPORTANT]
> 敏感配置应通过环境变量、配置文件模板或其他安全方式进行管理，并将实际配置加入 `.gitignore`。

# 📦 十三、大文件处理

可以放网盘。

# ⚔️ 十四、冲突处理

如果 Push 时提示：

```text
rejected
```

请勿直接 Force Push。

首先尝试：

```bash
git pull
```

或者：

```bash
git pull --rebase
```

## 14.1 Conflict

发生冲突时可能看到：

```text
<<<<<<< HEAD

你的代码

=======

其他人的代码

>>>>>>> branch
```

需要确认最终保留内容。

处理完成：

```bash
git add .
```

普通 Merge 情况继续：

```bash
git commit
```

Rebase 情况继续：

```bash
git rebase --continue
```

> [!WARNING]
> 如果无法判断应该保留哪部分内容，**请勿随意删除冲突代码**。

# ⌨️ 十六、常用 Git 命令

<details>
<summary><strong>查看状态</strong></summary>

<br>

```bash
git status
```

</details>

<details>
<summary><strong>查看分支</strong></summary>

<br>

```bash
git branch
```

</details>

<details>
<summary><strong>创建分支</strong></summary>

<br>

```bash
git switch -c feature/example
```

</details>

<details>
<summary><strong>切换分支</strong></summary>

<br>

```bash
git switch main
```

</details>

<details>
<summary><strong>获取最新代码</strong></summary>

<br>

```bash
git pull
```

</details>

<details>
<summary><strong>添加修改</strong></summary>

<br>

单个文件：

```bash
git add filename
```

全部修改：

```bash
git add .
```

</details>

<details>
<summary><strong>提交 Commit</strong></summary>

<br>

```bash
git commit -m "feat: 添加新功能"
```

</details>

<details>
<summary><strong>Push</strong></summary>

<br>

```bash
git push
```

</details>

<details>
<summary><strong>查看提交记录</strong></summary>

<br>

```bash
git log --oneline
```

</details>

<details>
<summary><strong>查看远程仓库</strong></summary>

<br>

```bash
git remote -v
```

</details>


<div align="center">

# CCU Robotics Association

<br>

本仓库用于协会内部学习、培训与机器人项目开发。

</div>

---

<div align="center">

<br>

**CONTRIBUTING**

<br>

**CCU Robotics Association**

</div>
