<div align="center">

# 🧠 Copilot Memory Bank

A carefully designed set of custom instructions that provide Copilot with a persistent project context integrated with VS Code via structured `Markdown` files. It helps GitHub Copilot maintain understanding of the project across sessions, record decisions and task progress, and quickly provide relevant information when needed.

[![ENGLISH](https://img.shields.io/badge/EN-ENGLISH-blue)](README.md) [![简体中文](https://img.shields.io/badge/CN-简体中文-red)](README_zh.md)

</div>

## 💡 Inspiration

This project was inspired by:
- [Kilo](https://kilo.ai/docs/zh-CN/advanced-usage/memory-bank) - Advanced memory bank usage documentation
- [GitHub Awesome Copilot](https://github.com/github/awesome-copilot/blob/main/instructions/memory-bank.instructions.md) - Copilot memory bank instructions

## ✨ Features

- **Persistent Memory**: Maintain project knowledge across Copilot sessions using structured Markdown files
- **Task Management**: Track tasks with detailed progress logs and status updates
- **Project Intelligence**: Capture patterns, preferences, and insights to improve collaboration
- **Real-time Updates**: Continuously sync context; the AGENT updates its memory at appropriate times

---

## 🎯 Concept & Workflow

Persist project details using a set of structured documents so Copilot can retain previous session knowledge across multiple conversations without re-prompting for the same information.

- 🗂️ Collect: Scan the repository for high-value information (architecture notes, decisions, READMEs, unfinished tasks).
- 🧾 Structure: Place canonical files under `.memory-bank/` for project brief, active context, decision logs, progress, and tasks.
- 🔁 Sync: Keep files updated during development (automatic triggers or manual `update memory bank`).
- 🧭 Surface: Use these files as context, prompts, and decision history for Copilot.

---

## 🚀 Quick Start

1. Clone or download this repository and ensure the custom instructions are placed in the project's `.github` directory.
2. Choose a high-performance model and use the built-in Agent mode to run the `initialize memory bank` command to initialize the Memory Bank.
3. Review the initially generated memory bank documents and edit them to match the current project state.
4. After updating the documents, Copilot will gain a deeper understanding of your project and use that knowledge in subsequent development.

Tip: Manually creating a `projectbrief.md` with key project information will significantly improve Copilot's initial performance.

---

## 📁 Memory Bank Structure

```
.memory-bank/
├── projectbrief.md       # Project summary and goals
├── productContext.md     # Project goals, users, and value
├── activeContext.md      # Current session focus and next steps
├── systemPatterns.md     # System architecture and technical decisions
├── techContext.md        # Technologies used and technical constraints
├── progress.md           # Completed work and pending items
└── tasks/
    ├── _index.md         # Tasks overview
    └── TASKID-*.md       # Individual task files
```

---

## 🔁 Memory Management

- Automatic: Optional automatic update triggers (pattern-based) let Copilot update the memory bank at appropriate times.
- Manual: Use the `update memory bank` command to force Copilot to re-scan the project and refresh the memory bank.

---

## 🗂️ Task Management

Manage tasks and progress under the `.memory-bank/tasks/` folder. Each task is an individual Markdown file (format: `TASKID-taskname.md`) and is listed in `tasks/_index.md` for easy tracking and history. You can ask Copilot to explain how the task system works, for example:

> Please tell me how the Memory Bank task system works.

### Management Flow

Create a task → Document implementation plan → Write progress logs in the task file → Sync status in `tasks/_index.md`.

### Available Commands

- `add task` / `create task`: Create a new task file and add it to `tasks/_index.md`.
- `update task [ID]`: Add a progress entry for today in the specified task file and update status fields (`Status`, `Updated`, etc.).
- `show tasks [filter]`: Display task lists with filters.

## 🤝 Contributing

Contributions are welcome: please follow the Copilot custom instruction format when improving this repository.

---

## 📜 License (MIT)

You are permitted to use, copy, modify, merge, publish, distribute, and sublicense the contents of this repository without restriction.
