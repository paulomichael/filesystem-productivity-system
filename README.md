# The Filesystem Productivity System (FPS)

## Also known as `taskfolders`

A task management system that uses only your operating system's filesystem, your file manager, and plain text files. No apps, no subscriptions, no vendor lock-in.

---

## Quick Start

**1. Create the structure**

```
~/Documents/Tasks/
├── Inbox/
├── Today/
├── This Week/
├── Waiting/
├── Done/
└── Archive/
```

**2. Create a task**

```
Inbox/
└── Call Dentist/
    └── description.txt
```

**3. Move it forward**

- Drag to `Today/` when you start working
- Drag to `Done/` when finished

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
| `Inbox/` → `Today/` | Starting work on this |
| `Today/` → `Done/` | Completed |
| `Today/` → `Waiting/` | Blocked, waiting on something |
| `Inbox/` → `This Week/` | Scheduled for later |

### Names as Descriptions

Linux filesystems allow up to 255 characters for a filename. This means you can put the entire task description in the folder name itself.

Instead of:

```
Task_001/
```

You can have:

```
Call dentist - schedule cleaning - need insurance info - due Aug 30/
```

When you open your `Today/` folder, you see everything at a glance. No clicking required.

---

## Directory Structure

### The Six Main Folders

```
~/Documents/Tasks/
├── Inbox/          # New tasks, quick capture
├── Today/          # Active work
├── This Week/      # Planned, not urgent
├── Waiting/        # Blocked by something or someone
├── Done/           # Completed tasks (short-term)
└── Archive/        # Historical tasks (long-term)
```

### Optional: Projects Folder

For larger initiatives that need their own structure:

```
~/Documents/Tasks/Projects/
└── Website Redesign 2026/
    ├── 01_Planning/
    ├── 02_Design/
    ├── 03_Development/
    └── 04_Launch/
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

The only required file is `description.txt`. Everything else is optional.

---

## Basic Usage (No Terminal Required)

### Creating a New Task

1. Navigate to `Inbox/`
2. Create a new folder with a descriptive name
3. Inside the folder, create `description.txt`
4. Write what needs to be done

Example:

```
Inbox/
└── Server Migration - backup completed - testing phase 80% - due Aug 25/
    └── description.txt
```

### Processing Inbox

Open `Inbox/` and decide what to do with each task:

- Drag to `Today/` if you'll work on it now
- Drag to `This Week/` if it's scheduled for later
- Drag to `Waiting/` if it's blocked
- Leave in `Inbox/` if you need more information

### Working on a Task

1. Open the task folder in `Today/`
2. Add notes to `notes.txt` as you make progress
3. Update `checklist.txt` to track subtasks
4. Drag files into the folder as needed

### Completing a Task

1. Verify all work is done
2. Drag the folder from `Today/` to `Done/`
3. Optionally rename to add `[DONE]` to the folder name

### Archiving

When `Done/` becomes full, move completed tasks to `Archive/`:

1. Create a dated folder: `Archive/2026-08/`
2. Drag old task folders into it

---

## Advanced Usage (Optional)

### Version Control with Git

The folder structure works well with Git for version control and collaboration.

**Initialize:**

```
cd ~/Documents/Tasks/
git init
git add .
git commit -m "Initial task system setup"
```

**Daily workflow:**

```
git add .
git commit -m "EOD: Completed 3 tasks, moved 2 to Waiting"
```

**Remote repository:**

```
git remote add origin https://github.com/yourusername/taskfolders.git
git push -u origin main
```

### Searching

**Using the file manager:**
- Use the search bar
- Sort by date modified
- Search within files (if supported)

**Using the command line:**

```
# Find all tasks containing "urgent"
grep -r "urgent" ~/Documents/Tasks/

# Find tasks in the Today folder
find ~/Documents/Tasks/Today/ -type d -maxdepth 1

# Find tasks with PDF attachments
find ~/Documents/Tasks/ -name "*.pdf"
```

### Automation Scripts

**Daily summary:**

```
#!/bin/bash
TASKS_DIR=~/Documents/Tasks

echo "Task Summary - $(date)"
echo "Inbox:    $(find $TASKS_DIR/Inbox/ -mindepth 1 -maxdepth 1 -type d | wc -l)"
echo "Today:    $(find $TASKS_DIR/Today/ -mindepth 1 -maxdepth 1 -type d | wc -l)"
echo "Waiting:  $(find $TASKS_DIR/Waiting/ -mindepth 1 -maxdepth 1 -type d | wc -l)"
echo "Done:     $(find $TASKS_DIR/Done/ -mindepth 1 -maxdepth 1 -type d | wc -l)"
```

**Auto-archive:**

```
#!/bin/bash
MONTH=$(date +%Y-%m)
mkdir -p ~/Documents/Tasks/Archive/$MONTH
find ~/Documents/Tasks/Done/ -type d -ctime +30 -exec mv {} ~/Documents/Tasks/Archive/$MONTH/ \;
```

### File Manager Custom Actions

**In Thunar**, you can create custom actions for common operations:

- "Move to Today" — Move selected folder to `Today/`
- "Mark Complete" — Add `[DONE]` to folder name and move to `Done/`
- "Add Priority" — Add `[!]` to folder name

---

## Examples

### Example: Daily Workflow

**Morning: Inbox**

```
Inbox/
├── Call Dentist/
├── Website Update/
└── Review Reports/
```

**Processing: Move to appropriate folders**

```
Today/
└── Website Update/

Waiting/
└── [@Sarah] Call Dentist/

This Week/
└── Review Reports/
```

**Working: Add content**

```
Today/Website Update/
├── description.txt       # "Fix broken contact form"
├── notes.txt            # "Found bug in JavaScript"
├── checklist.txt        # - [x] Find bug, [ ] Fix, [ ] Test
└── files/
    ├── bug_screenshot.png
    └── error_logs.txt
```

**Evening: Completed tasks**

```
Done/
├── Website Update/
└── Review Reports/
```

### Example: Long Descriptive Names

The 255-character filename limit allows for highly descriptive task names:

```
[!] Server Migration - backup completed 2026-08-21 - testing phase 80% - rollback plan ready - due Aug 25/
```

```
[@Sarah] Contract review - legal team needs approval - sent Aug 20 - follow up Aug 25/
```

```
[DONE] Deploy API v3 - completed Aug 21 - took 2 hours - no issues - post-mortem in folder/
```

This creates an at-a-glance view of all tasks, their status, and their context.

### Example: Project with Structure

```
Projects/Website Redesign 2026/
├── README.md
├── timeline.md
├── team.md
├── 01_Planning/
│   ├── Research/
│   │   ├── competitor_analysis.pdf
│   │   └── user_survey_results.csv
│   └── Requirements/
│       ├── requirements.md
│       └── wireframes.fig
├── 02_Design/
│   ├── mockups/
│   └── style_guide.pdf
├── 03_Development/
│   ├── code_reviews/
│   └── staging_deploy/
└── 04_Launch/
    ├── qa_test_results/
    └── deploy_scripts/
```

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

**description.txt**

```
Task: [Task Name]

Priority: High / Medium / Low
Due Date: YYYY-MM-DD
Tags: #project #client

Description:
[Detailed description of what needs to be done]
```

**notes.txt**

```
Notes: [Task Name]

2026-08-21:
- Progress update
- Decisions made
- Blockers identified
- Next steps
```

**checklist.txt**

```
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

**Q: What if I have a lot of files in a task folder?**
A: Create subfolders inside the task folder to organize:
```
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
```
Task Name/
├── 01_Research/
├── 02_Design/
├── 03_Development/
└── 04_Review/
```

**Q: What about recurring tasks?**
A: Add `[Daily]` or `[Weekly]` to the folder name. When completed, move to `Done/` and create a new one for the next occurrence.

**Q: Can I use this with a team?**
A: Yes. Options include:
- Sharing the folder on a network drive
- Using Git with a remote repository
- Syncing via Google Drive or Dropbox

**Q: What's the difference between Done and Archive?**
A: `Done/` holds recent completions (last few weeks). `Archive/` holds older tasks you want to keep for reference.

**Q: How do I search across all tasks?**
A: Most file managers have a search bar. For more advanced searching, use `grep` from the command line.

**Q: Is this compatible with Windows or macOS?**
A: Yes. The folder structure works on any operating system. Just be aware of path length limits on Windows (260 characters by default).

---

## Contributing

Contributions are welcome:

1. Improvements to documentation
2. Additional examples and use cases
3. Helper scripts
4. Suggestions for the system

Please open an issue or pull request.

---

## License

This project is in the public domain under the Unlicense. You can use, modify, and share it freely.

---

## Acknowledgments

- Inspired by the Unix philosophy: "Do one thing and do it well"
- Built on the simplicity of the filesystem
- Made possible by free and open source software

