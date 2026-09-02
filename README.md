# taskfolders
## The Filesystem Productivity System (FPS)

A task management system that uses only your operating system's filesystem, your file manager, and plain text files. No apps, no subscriptions, no vendor lock-in.

---

## Quick Start

**1. Create the structure**
```text
~/Documents/Tasks/
├── 1_Inbox/
├── 2_Today/
├── 3_This_Week/
├── 4_Waiting/
├── 5_Done/
└── 6_Archive/
```

**2. Create a task**
```text
1_Inbox/
└── Call Dentist - schedule cleaning - need insurance info/
    └── description.txt
```

**3. Move it forward**
- Drag to `2_Today/` when you start working
- Drag to `5_Done/` when finished

That's it. The rest of this document explains the details.

---

## The Core Idea

### Folders as Tasks
Every task is a folder. Everything related to that task lives inside it:
- Task description
- Notes and updates
- Checklists
- Attachments (files, images, documents)
- Sub-tasks

### Movement as Status Change
Moving a folder between directories changes its status:
| Action | Meaning |
|--------|---------|
| `1_Inbox/` → `2_Today/` | Starting work on this |
| `2_Today/` → `5_Done/` | Completed |
| `2_Today/` → `4_Waiting/` | Blocked, waiting on something |
| `1_Inbox/` → `3_This_Week/` | Scheduled for later |

### Names as Descriptions
Linux filesystems allow up to 255 characters for a filename. This means you can put the entire task description in the folder name itself. 

Instead of:
```text
Task_001/
```
You can have:
```text
Call dentist - schedule cleaning - need insurance info - due Aug 30/
```
When you open your `2_Today/` folder, you see everything at a glance. No clicking required.

---

## Directory Structure

### The Six Main Folders
```text
~/Documents/Tasks/
├── 1_Inbox/          # New tasks, quick capture
├── 2_Today/          # Active work
├── 3_This_Week/      # Planned, not urgent
├── 4_Waiting/        # Blocked by something or someone
├── 5_Done/           # Completed tasks (short-term)
└── 6_Archive/        # Historical tasks (long-term)
```

### Optional: Projects Folder
For larger initiatives that need their own structure:
```text
~/Documents/Tasks/Projects/
└── Website Redesign 2026/
    ├── 1_Planning/
    ├── 2_Design/
    ├── 3_Development/
    └── 4_Launch/
```

### Task Folder Template
```text
Task Name/
├── description.txt      # What needs to be done
├── notes.txt            # Progress updates, decisions
├── checklist.txt        # Subtasks with checkboxes
├── files/               # Attachments (any type)
└── references/          # Reference material
```
The only required file is `description.txt`. Everything else is optional. Markdown (`.md`) files work equally well if you prefer formatting. The examples use `.txt` because they work on every system.

---

## Kanban View

The folder structure works as a visual kanban board:
- `1_Inbox/` = Backlog
- `2_Today/` = Doing
- `3_This_Week/` = Scheduled
- `4_Waiting/` = Blocked
- `5_Done/` = Done
- `6_Archive/` = Archived

**Example:**
```text
Tasks/
├── 1_Inbox/
│   ├── Call dentist - schedule cleaning/
│   └── Review Q3 report - need numbers/
├── 2_Today/
│   └── Server Migration - backup done - testing 80%/
├── 3_This_Week/
│   └── Q4 Presentation - gathering data/
├── 4_Waiting/
│   └── [@Sarah] Contract review - waiting for legal/
├── 5_Done/
│   ├── [DONE] Deploy API v3/
│   └── [DONE] Website update/
└── 6_Archive/
    └── 2026-08/
```

### Viewing the Full Board
In a file manager, you see one column at a time. This is fine for focused work but doesn't show the whole picture. 

**To see the full board:**
- **In the terminal with `tree`:** `tree ~/Documents/Tasks/`
- **In Thunar (Linux):** View → Side Pane → Tree
- **In Nautilus (Linux/GNOME):** View → Sidebar → Tree
- **In Finder (macOS):** View → Show Sidebar → Column View
- **In Windows Explorer:** View → Navigation Pane → Expand folders

**Terminal options:**
```bash
# Show only directories
tree -d ~/Documents/Tasks/
# Show with full paths
tree -f ~/Documents/Tasks/
# Limit depth
tree -L 2 ~/Documents/Tasks/
```

---

## Basic Usage (No Terminal Required)

### Creating a New Task
1. Navigate to `1_Inbox/`
2. Create a new folder with a descriptive name
3. Inside the folder, create `description.txt`
4. Write what needs to be done

**Example:**
```text
1_Inbox/
└── Server Migration - backup completed - testing phase 80% - due Aug 25/
    └── description.txt
```

### Processing Inbox
Open `1_Inbox/` and decide what to do with each task:
- Drag to `2_Today/` if you'll work on it now
- Drag to `3_This_Week/` if it's scheduled for later
- Drag to `4_Waiting/` if it's blocked
- Leave in `1_Inbox/` if you need more information

### Working on a Task
1. Open the task folder in `2_Today/`
2. Add notes to `notes.txt` as you make progress
3. Update `checklist.txt` to track subtasks
4. Drag files into the folder as needed

### Completing a Task
1. Verify all work is done
2. Drag the folder from `2_Today/` to `5_Done/`
3. Optionally rename to add `[DONE]` to the folder name

### Archiving
When `5_Done/` becomes full, move completed tasks to `6_Archive/`:
1. Create a dated folder: `6_Archive/2026-08/`
2. Drag old task folders into it

---

## Advanced Usage (Optional)

The following sections are entirely optional. The core system works with just a file manager.

### Version Control with Git
The folder structure works well with Git for version control and collaboration.
```bash
# Initialize
cd ~/Documents/Tasks/
git init
git add .
git commit -m "Initial task system setup"

# Daily workflow
git add .
git commit -m "EOD: Completed 3 tasks, moved 2 to Waiting"

# Remote repository
git remote add origin https://github.com/yourusername/taskfolders.git
git push -u origin main
```

### Git History as a Report
Git tracks every change. Here's a simple example:
```bash
# See what happened today
git log --since="today" --oneline
```
*Example output:*
```text
a4f2d1e Move "Call Dentist" from Inbox to Waiting
b3e9c2a Add notes to "Server Migration" task
c7d4f1b Create "Review Q3 Report" in Inbox
```
For more examples, see [Git Examples](docs/git-examples.md).

### Searching
**Using the file manager:**
- Use the search bar
- Sort by date modified
- Search within files (if supported)

**Using the command line:**
```bash
# Find all tasks containing "urgent"
grep -r "urgent" ~/Documents/Tasks/
# Find tasks in the Today folder
find ~/Documents/Tasks/2_Today/ -type d -maxdepth 1
# Find tasks with PDF attachments
find ~/Documents/Tasks/ -name "*.pdf"
```

### Optional Scripts
Scripts are provided for automation. They are entirely optional and not required for the system to work.

**Daily summary:**
```bash
#!/bin/bash
TASKS_DIR=~/Documents/Tasks
echo "Task Summary - $(date)"
echo "Inbox:    $(find $TASKS_DIR/1_Inbox/ -mindepth 1 -maxdepth 1 -type d | wc -l)"
echo "Today:    $(find $TASKS_DIR/2_Today/ -mindepth 1 -maxdepth 1 -type d | wc -l)"
echo "Waiting:  $(find $TASKS_DIR/4_Waiting/ -mindepth 1 -maxdepth 1 -type d | wc -l)"
echo "Done:     $(find $TASKS_DIR/5_Done/ -mindepth 1 -maxdepth 1 -type d | wc -l)"
```

**Auto-archive:**
```bash
#!/bin/bash
MONTH=$(date +%Y-%m)
mkdir -p ~/Documents/Tasks/6_Archive/$MONTH
find ~/Documents/Tasks/5_Done/ -type d -ctime +30 -exec mv {} ~/Documents/Tasks/6_Archive/$MONTH/ \;
```
More scripts are available in [docs/scripts/](docs/scripts/).

### File Manager Custom Actions
In Thunar, you can create custom actions for common operations:
- "Move to Today" — Move selected folder to `2_Today/`
- "Mark Complete" — Add `[DONE]` to folder name and move to `5_Done/`
- "Add Priority" — Add `[!]` to folder name

---

## Examples

For detailed examples of personal, team, project, and calendar boards, see [Examples](docs/examples.md).

---

## Reference

### Naming Conventions
**Priority markers** (add to folder name):
- `[!]` — High priority / urgent
- `[@]` — Waiting on someone
- `[?]` — Need more information
- `[DONE]` — Completed

**Tags** (add to folder name or description):
- `#project` — Project tag
- `#client` — Client tag
- `#urgent` — Urgency flag
- `#blocked` — Currently blocked
- `#waiting` — Waiting for response

### Template Files
Templates are provided in [docs/templates/](docs/templates/).

**description.txt**
```text
Task: [Task Name]
Priority: High / Medium / Low
Due Date: YYYY-MM-DD
Tags: #project #client

Description:
[Detailed description of what needs to be done]
```

**notes.txt**
```text
Notes: [Task Name]

2026-08-21:
- Progress update
- Decisions made
- Blockers identified
- Next steps
```

**checklist.txt**
```text
Checklist: [Task Name]

- [ ] Step 1
- [ ] Step 2
- [ ] Step 3
```

### Cloud Sync Compatibility
| Service | Path Limit | Notes |
|---------|------------|-------|
| Git (GitHub/GitLab) | ~4,096 chars | Best option |
| Google Drive | 32,768 chars | Good option |
| OneDrive | 400 chars | Limited |
| Dropbox | 260 chars (recommended) | Most restrictive |
| Windows (local) | 260 chars | Legacy limit |

**Recommendations:**
- Keep folder names under 250 characters
- Avoid special characters: `\`, `/`, `:`, `*`, `?`, `"`, `<`, `>`, `|`
- Use Git as the primary sync method

---

## FAQ

**Q: What happens if the company behind my task app goes out of business?**  
A: Your data is stored in their servers, in their format, accessible through their interface. If they shut down, change their pricing, or change their terms, your data is at risk. With this system, your data is just files and folders on your computer. It's yours. Always. No company can take it away or hold it hostage.

**Q: Is my data really mine?**  
A: Yes. There is no proprietary format, no cloud dependency, no vendor lock-in. Everything is stored as plain text files and standard folders. You can open, read, and move them with any tool on any operating system. You don't need this system to access your data. You just need a file manager.

**Q: Is this really free?**  
A: Yes. The system uses only tools that come with your operating system. There are no subscriptions, no premium tiers, no paid upgrades. The code is in the public domain. You can use, modify, and share it freely.

**Q: Do I need to use Git?**  
A: No. Git is entirely optional. The basic system works with just a file manager. Git is an add-on for people who want version history, collaboration, or remote backup.

**Q: What if I have 500 tasks?**  
A: The limit is human, not technical. A person cannot meaningfully hold 500 active tasks. Most of those belong in Archive, not in active directories. The structure encourages pruning. If you have 500 tasks in Inbox, the problem isn't the system. The problem is that you're not processing your Inbox. Archive regularly and keep your active directories focused on what's actually relevant.

**Q: What if I have a lot of files in a task folder?**  
A: Create subfolders inside the task folder to organize:
```text
Task Name/
├── files/
│   ├── images/
│   ├── documents/
│   └── data/
├── notes/
└── description.txt
```

**Q: Can I have sub-tasks?**  
A: Yes. Create subfolders inside the task folder:
```text
Task Name/
├── 1_Research/
├── 2_Design/
├── 3_Development/
└── 4_Review/
```

**Q: What about recurring tasks?**  
A: Add `[Daily]` or `[Weekly]` to the folder name. When completed, move to `5_Done/` and create a new one for the next occurrence.

**Q: What if I want to use both .txt and .md files in the same task?**  
A: That's fine. The system doesn't enforce a single format. You can mix and match based on what you need. Some files might be `.txt` for simplicity, others `.md` for formatting. The system works with any text-based file.

**Q: What if I accidentally move a task to the wrong folder?**  
A: Just move it back. There's no penalty or undo limit. The system is forgiving.

**Q: Can I use this with a team?**  
A: Yes. Options include sharing the folder on a network drive, using Git with a remote repository, or syncing via Google Drive or Dropbox.

**Q: What's the difference between Done and Archive?**  
A: `5_Done/` holds recent completions (last few weeks). `6_Archive/` holds older tasks you want to keep for reference.

**Q: How do I search across all tasks?**  
A: Most file managers have a search bar. For more advanced searching, use `grep` from the command line.

**Q: Is this compatible with Windows or macOS?**  
A: Yes. The folder structure works on any operating system. Just be aware of path length limits on Windows (260 characters by default).

**Q: Is this available on mobile?**  
A: Yes, in the sense that any file manager on any platform can access the folder structure. There is no dedicated app, but the system works wherever you can access and move folders.

**Q: Can I use this with my existing folder structure?**  
A: Yes. You don't have to start from scratch. You can integrate the system into your existing setup by creating the six main folders and moving your current tasks into them.

**Q: What if I want to use this for things other than tasks?**  
A: The structure can be adapted for projects, documentation, research, or any other organizational need. The principles are general.

---

## Context

The filesystem is so common it's invisible. Folders and files are the first thing people learn, and often the last thing they think about.

We're conditioned to look for dedicated apps and specialized tools. But that assumption skips over a question worth asking: how much of what these tools offer is genuinely necessary? How much is just interface design, marketing, or features added to justify a subscription?

The filesystem has been stable, reliable, and free for decades. It doesn't add features to stay relevant. It doesn't need to be new to be useful. It simply works.

This system is built on that foundation. It uses what's already there, in ways you might not have considered. No new app. No subscription. No features you don't need.

The trade-off is explicit: you give up real-time collaboration, mobile apps, and automated reminders in exchange for simplicity, durability, and no subscription. That trade-off is intentional. It may or may not fit your needs.

---

## Prior Art

The idea of using the filesystem for task management has surfaced before. Projects like `gtd-on-fs` (2010), `hamster-system`, and `jobdone` each explored similar territory, approaching it from different angles—files instead of folders, CLI-driven interfaces, or automation-focused workflows.

That this idea keeps appearing independently suggests a recurring need that existing tools haven't fully addressed.

What makes this version distinct is partly a matter of timing. In the 80s and 90s, filenames were limited to 8 characters in DOS and 14 in early Unix. File managers were text-based. The conditions weren't right. Now they are.

This system is a recognition that the machinery was already there. It's not new. It's just noticed.

---

## Contributing

This project is in the public domain. Fork it, modify it, use it, share it. If you make improvements, consider sharing them back. Open an issue or pull request if you'd like.

---

## License

This project is in the public domain under the Unlicense. You can use, modify, and share it freely.

---

## Acknowledgments

- Inspired by the Unix philosophy: "Do one thing and do it well"
- Built on the simplicity of the filesystem
- Made possible by free and open source software

---

*Files and folders. The most powerful productivity tool you already have.*
