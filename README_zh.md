<div align="center">

# 🧠 Copilot Memory Bank

精心设计的自定义指令，通过结构化的 `Markdown` 文件为 `Copilot` 提供了一个与 VS Code 集成的持久化的项目上下文，帮助 GitHub Copilot 在不同会话间保持对项目的理解、记录决策和任务进度，并在需要时快速提供相关信息。

[![ENGLISH](https://img.shields.io/badge/EN-ENGLISH-blue)](README.md) [![简体中文](https://img.shields.io/badge/CN-简体中文-red)](README_zh.md)

</div>

## 💡 灵感来源

本项目受到以下项目的启发：
- [Kilo](https://kilo.ai/docs/zh-CN/advanced-usage/memory-bank) - 高级内存库使用文档
- [GitHub Awesome Copilot](https://github.com/github/awesome-copilot/blob/main/instructions/memory-bank.instructions.md) - Copilot的内存库指令

## ✨ 功能特性

- **持久记忆**：通过结构化的Markdown文件维护跨Copilot会话的项目知识
- **任务管理**：跟踪任务的详细进度日志和状态更新
- **项目智能**：捕获模式、偏好和见解，以改善协作
- **实时更新**：持续上下文同步，AGENT在适当的时机更新自己的记忆

---

## 🎯 概念与工作流

使用一组结构化的文档，将项目的详细信息进行持久化，使Copilot在多个会话之间获得之前的记忆，无需重复向Copilot提示已经获得的信息。

- 🗂️ 采集：扫描仓库中的高价值信息（架构笔记、决策、README、未完成的任务）。
- 🧾 结构化：将规范文件放入 `.memory-bank/`，分别用于项目简介、活动上下文、决策记录、进度与任务。
- 🔁 同步：在开发过程中保持文件更新（实时触发或手动 `update memory bank`）。
- 🧭 呈现：将这些内容用于提供给 Copilot 的上下文、提示与决策历史。

---

## 🚀 快速开始

1. 克隆或下载本仓库，确保自定义指令已存放在项目的 `.github` 目录中。
2. 选择性能强劲的模型，以内置的Agent模式，运行指令 `initialize memory bank` 要求初始化Memory Bank。
3. 检阅初始生成的记忆库文档，修改它们，使文档符合项目的现状。
4. 完成文档修改后，Copilot 获得对您项目的深度理解，并将这些知识用于后续的开发。

小贴士：如果你可以手动创建 `projectbrief.md` 并在其中，会显著提升 Copilot 的初始表现。

---

## 📁 Memory Bank 结构

```
.memory-bank/
├── projectbrief.md       # 项目摘要与目标
├── productContext.md     # 项目目标、用户与价值
├── activeContext.md      # 当前会话目标与下一步
├── decisionLog.md        # 技术/架构决策与理由
├── progress.md           # 已完成工作与待办项
└── tasks/
    ├── _index.md         # 任务总览
    └── TASKID-*.md       # 单个任务文件
```

---

## 🔁 记忆管理

- 自动：可选的自动更新触发器（基于模式事件），Copilot会自动在合适的时机进行记忆库更新。
- 手动：使用 `update memory bank` 指令，强制要求Copilot重新检阅项目并刷新记忆库。

---

## 🗂️ 任务管理

在 `.memory-bank` 中使用 `tasks/` 文件夹来管理任务和进度。每个任务为独立的 Markdown 文件（格式：`TASKID-任务名.md`），并在 `tasks/_index.md` 中维护任务总览，便于追踪状态与历史。你可以要求Copilot向你说明如何使用任务系统，像这样：

> 请告诉我 Memory Bank 的任务系统如何使用.

### 管理流程

创建任务 → 记录实现计划 → 在任务文件中写入进度日志 → 在 `tasks/_index.md` 同步状态。

### 可用指令

- `add task` / `create task`：创建新任务文件并将其加入 `tasks/_index.md`。
- `update task [ID]`：在指定任务文件中添加当天的进度条目并更新状态字段（`Status`、`Updated` 等）。
- `show tasks [filter]`：显示任务列表并支持过滤。

## 🤝 贡献

欢迎贡献：请遵循Copilot自定义指令的格式对本仓库进行完善。

---

## 📜 许可证(MTI)

允许您无限制地使用、复制、修改、合并、发布、分发、再许可本仓库的内容。