
# 📁 Filesystem Productivity System (FPS)

**Organize your life with folders and files. No apps. No subscriptions. Just your computer.**

---

## ✨ What Is This?

The Filesystem Productivity System (FPS) is a complete task management system that uses nothing but your operating system's filesystem, your file manager, and plain text files.

**The core idea is simple:** Every task is a folder. Moving folders between directories changes their status. Everything else—notes, files, checklists—lives inside the task folder.

No special apps. No cloud subscriptions. No vendor lock-in. Just your computer, working the way it was designed to.

---

## 🚀 Quick Start

### 1. Create the structure
```
~/Documents/Tasks/
├── Inbox/          # New tasks go here
├── Today/          # Working on now
├── This Week/      # Planned for later
├── Waiting/        # Blocked by something
├── Done/           # Completed
└── Archive/        # Long-term storage
```

### 2. Create a task
```
Inbox/
└── Call Dentist/
    └── description.txt   # "Schedule cleaning for next month"
```

### 3. Move it forward
- Drag to `Today/` when you start working on it
- Add notes, files, and checklists
- Drag to `Done/` when finished

### 4. That's it.
No terminal. No scripts. Just folders and files.

---

## 📖 Documentation

This repository contains complete guides in two formats:

### 🔰 Simple Version
- **For everyone** — No terminal, no scripts, no GitHub required
- Just your file manager and basic computer skills
- [Read the Simple Guide](docs/simple/README.md)
- [Português](docs/simple/README.pt.md)

### 🚀 Advanced Version
- **For power users** — Adds Git for version control, scripts for automation
- Full history, collaboration, searching, and more
- [Read the Advanced Guide](docs/advanced/README.md)
- [Português](docs/advanced/README.pt.md)

---

## 🎯 Why This Works

| Problem | Solution |
|---------|----------|
| Too many apps | Uses tools you already have |
| Expensive subscriptions | Completely free |
| Vendor lock-in | Plain files, open formats |
| Learning curve | Uses what you already know |
| Attachments limited | Unlimited files per task |
| Offline dependency | Works without internet |
| Future-proof | Files will always be readable |

---

## 🗂️ System Structure

### Directory Layout
```
Tasks/
├── Inbox/           # Capture new ideas quickly
├── Today/           # Current work in progress
├── This Week/       # Scheduled but not urgent
├── Waiting/         # Blocked by someone/something
├── Done/            # Completed tasks (short-term)
└── Archive/         # Historical tasks (long-term)

Projects/            # Optional: Large initiatives
└── Project Name/
    ├── 01_Planning/
    ├── 02_Execution/
    └── 03_Complete/
```

### Task Folder Template
```
Task Name/
├── description.txt      # What needs to be done
├── notes.txt            # Progress updates, decisions
├── checklist.txt        # Subtasks with checkboxes
├── files/               # Attachments (any type)
└── references/          # Reference material
```

---

## 💡 Key Concepts

### Tasks as Folders
Every task is a folder containing everything related to it: descriptions, notes, checklists, and attachments. This means you can store *anything* with your task—not just text.

### Movement as Status Change
Moving a folder between directories changes its status:
- `Inbox/` → `Today/` = "I'm starting this"
- `Today/` → `Done/` = "I finished this"
- `Today/` → `Waiting/` = "I'm blocked"

### Descriptive Names
Name tasks clearly, using markers for quick scanning:
- `[!]` — High priority / urgent
- `[@]` — Waiting on someone
- `[?]` — Need more information
- `[DONE]` — Completed

---

## 🎬 Examples

### Simple Example: Daily Workflow

**Morning:** Create tasks in `Inbox/`
```
Inbox/
├── Call Dentist/
├── Update Website/
└── Review Reports/
```

**Process:** Move to appropriate folders
```
Today/
└── Update Website/       # Working on now

Waiting/
└── [@Sarah] Call Dentist/  # Waiting for office to open

This Week/
└── Review Reports/       # Scheduled for later
```

**Work:** Add progress to `Today/` task
```
Update Website/
├── description.txt       # "Fix broken contact form"
├── notes.txt            # "Found bug in JavaScript"
├── checklist.txt        # - [x] Find bug, [ ] Fix, [ ] Test
└── files/
    ├── bug_screenshot.png
    └── error_logs.txt
```

**Evening:** Move completed task to `Done/`
```
Done/
└── Update Website/       # Complete!
```

---

## 🔍 Searching

### File Manager
- Use the search bar
- Sort by date modified
- Search within folders for specific files

### Command Line (Advanced)
```bash
# Find all tasks with "urgent"
grep -r "urgent" ~/Documents/Tasks/

# Find all tasks in Today folder
find ~/Documents/Tasks/Today/ -type d -maxdepth 1

# Find tasks with PDF attachments
find ~/Documents/Tasks/ -name "*.pdf"
```

---

## 🌍 Translations

- [Português](docs/README.pt.md)
- More coming soon...

---

## 📄 License

This project is in the public domain under the [Unlicense](LICENSE). You can use, modify, and share it freely.

---

## 🤝 Contributing

Contributions are welcome! Here's how you can help:

1. **Improve documentation** — Fix typos, clarify explanations
2. **Add translations** — Make it accessible to more people
3. **Share your workflow** — Show how you've adapted the system
4. **Suggest improvements** — Open an issue with your ideas

Please see [CONTRIBUTING.md](CONTRIBUTING.md) for details.

---

## 📬 Questions?

- **Simple version:** See the [Simple Guide](docs/simple/README.md)
- **Advanced version:** See the [Advanced Guide](docs/advanced/README.md)
- **Something else?** Open an issue

---

## 🌟 Why You'll Love This

> *"The best tool is the one you already have."*

This system works because it uses **what you already know** and **what you already have**. No new apps to learn, no subscriptions to pay, no data locked away in proprietary formats.

It's just folders and files, working the way they've always worked.

---

## 📸 Screenshots

*(Add screenshots of Thunar/Nautilus showing the folder structure, task folders, and workflow)*

---

## 📂 Repository Structure

```
filesystem-productivity-system/
├── README.md                   # This file
├── docs/
│   ├── simple/
│   │   ├── README.md          # Simple guide (English)
│   │   └── README.pt.md       # Simple guide (Portuguese)
│   ├── advanced/
│   │   ├── README.md          # Advanced guide (English)
│   │   └── README.pt.md       # Advanced guide (Portuguese)
│   ├── templates/              # Ready-to-use templates
│   │   ├── task_template/
│   │   └── project_template/
│   ├── scripts/                # Helper scripts (advanced version)
│   │   ├── daily-summary.sh
│   │   └── auto-archive.sh
│   └── images/                 # Screenshots and diagrams
└── examples/                   # Real-world examples
    ├── simple/
    └── advanced/
```

---

## 🎓 Learning Path

1. **Start simple** — Read the [Simple Guide](docs/simple/README.md)
2. **Try it for a week** — Use only the basic structure
3. **Add your own touches** — Create your own naming conventions
4. **Graduate to advanced** — Add Git when you're ready
5. **Automate** — Add scripts for repetitive tasks

---

## 📊 Status

This project is **stable and complete**. The core concepts are proven and have been used for years. The documentation is ready for real-world use.

**Current version:** 1.0.0

---

## 🙏 Acknowledgments

- Inspired by the Unix philosophy: *Do one thing and do it well*
- Built on the simplicity of the filesystem
- Made possible by free and open source software

---

*"Files and folders. The most powerful productivity tool you already have."*

---
