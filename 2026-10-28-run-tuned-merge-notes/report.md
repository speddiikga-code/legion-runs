# Write a beginner cheat sheet with two parts: five essential git commands, and five essential PowerSh

- Mode: run
- Date: 2026-10-28
- Limits: maxAgents 16, maxDepth 2, minDepth 2, branching 2, effort medium, mergeEffort medium
- Stats: agents 11, splits 3, leaves 4, deepest 2, failed 0
- Tokens: 589,751

## Goal

Write a beginner cheat sheet with two parts: five essential git commands, and five essential PowerShell commands, each with a one-line explanation and an example.

## Outline

```
1 Root [split 2]
  1.1 Five essential git commands [split 2]
    1.1.1 Git setup and inspection commands [leaf]
    1.1.2 Git save and share commands [leaf]
  1.2 Five essential PowerShell commands [split 2]
    1.2.1 PowerShell navigation and reading cmdlets [leaf]
    1.2.2 PowerShell file-copy and help cmdlets [leaf]
```

## Result

# Beginner Cheat Sheet: Git and PowerShell

## Git

### git clone
Copies an existing remote repository, including its full history, into a new folder on your computer.
```bash
git clone https://github.com/user/project.git
```

### git status
Shows which files are modified, which are staged for the next commit, and which are untracked.
```bash
git status
```

### git add
Stages changes so they are included in your next commit.
```bash
git add README.md
```

### git commit
Saves the staged changes as a snapshot in your local history, with a message saying what changed.
```bash
git commit -m "Fix typo in README"
```

### git push
Uploads your local commits to a remote repository so others can see them.
```bash
git push origin main
```

## PowerShell

### Get-ChildItem (aliases `ls`, `dir`)
Lists the files and folders in the current directory, or in a path you give it.
```powershell
Get-ChildItem C:\Projects -Filter *.txt
```

### Set-Location (alias `cd`)
Moves you into a different directory so that later commands run there.
```powershell
Set-Location C:\Projects\my-app
```

### Get-Content (alias `cat`)
Prints the contents of a text file in the terminal.
```powershell
Get-Content .\README.md -TotalCount 20
```

### Copy-Item (aliases `cp`, `copy`)
Copies a file or folder from one location to another.
```powershell
Copy-Item .\report.txt -Destination .\backup\report.txt
```

### Get-Help (alias `help`)
Shows documentation and usage examples for any cmdlet.
```powershell
Get-Help Copy-Item -Examples
```

## Review

Complete: yes

- Copy-Item says it copies 'a file or folder', but copying a folder without -Recurse copies only the empty folder, not what is inside it. A beginner who follows this line will lose the contents.
- The Copy-Item example fails with a 'Could not find a part of the path' error if the .\backup folder does not exist yet. The cheat sheet should say the folder must exist first, or show New-Item -ItemType Directory .\backup.
- The Get-Help -Examples example may show only partial, auto-generated help with no examples on a new install, because full help files are not installed by default. It needs a short note about running Update-Help once, or using -Online.
- The aliases ls and cat (and cp) only exist in Windows PowerShell and PowerShell on Windows. In PowerShell 7 on macOS or Linux they run the system's own commands instead. This deserves a short note if the audience is not only on Windows.
- git push origin main assumes the branch is called main. Older repos often use master, and the first push of a new branch usually needs -u. A short note would help beginners.
- Missing for beginners, though the goal does not require it: git pull is not listed, so the git list covers sending changes but never getting other people's changes. git config user.name/user.email setup before the first commit is also not mentioned. Swapping pull in for clone or status is a matter of opinion, not an error.
- Small point: the git blocks are marked bash even though the reader is clearly using PowerShell. The commands work the same there, but labeling them powershell or leaving the fence unlabeled would be more consistent.

## Every node

### 1 Root (split, depth 0)

**Task:** Write a beginner cheat sheet with two parts: five essential git commands, and five essential PowerShell commands, each with a one-line explanation and an example.

**Why:** The cheat sheet has two independent parts, git and PowerShell, so each subtask covers exactly one of them.

# Beginner Cheat Sheet: Git and PowerShell

## Git

### git clone
Copies an existing remote repository, including its full history, into a new folder on your computer.
```bash
git clone https://github.com/user/project.git
```

### git status
Shows which files are modified, which are staged for the next commit, and which are untracked.
```bash
git status
```

### git add
Stages changes so they are included in your next commit.
```bash
git add README.md
```

### git commit
Saves the staged changes as a snapshot in your local history, with a message saying what changed.
```bash
git commit -m "Fix typo in README"
```

### git push
Uploads your local commits to a remote repository so others can see them.
```bash
git push origin main
```

## PowerShell

### Get-ChildItem (aliases `ls`, `dir`)
Lists the files and folders in the current directory, or in a path you give it.
```powershell
Get-ChildItem C:\Projects -Filter *.txt
```

### Set-Location (alias `cd`)
Moves you into a different directory so that later commands run there.
```powershell
Set-Location C:\Projects\my-app
```

### Get-Content (alias `cat`)
Prints the contents of a text file in the terminal.
```powershell
Get-Content .\README.md -TotalCount 20
```

### Copy-Item (aliases `cp`, `copy`)
Copies a file or folder from one location to another.
```powershell
Copy-Item .\report.txt -Destination .\backup\report.txt
```

### Get-Help (alias `help`)
Shows documentation and usage examples for any cmdlet.
```powershell
Get-Help Copy-Item -Examples
```

**Merge notes:** Content from both subtasks was kept unchanged. The only change is formatting: the PowerShell entries now use ### headings like the git entries instead of bold labels, and I added a top-level title. Neither subtask repeated or contradicted the other.

### 1.1 Five essential git commands (split, depth 1)

**Task:** Write the git part of a beginner cheat sheet: a Markdown section headed '## Git' that lists exactly five essential git commands for beginners (for example git clone, git status, git add, git commit, git push). For each command give the command name, a one-line plain-English explanation, and one realistic example in a code block. Cover git only, not PowerShell. Deliverable: that Markdown section alone, with no preamble.

**Why:** I split the git section into two parts: setting up and checking a local repository, and saving and sharing changes.

## Git

### git clone
Copies an existing remote repository, including its full history, into a new folder on your computer.

```bash
git clone https://github.com/user/project.git
```

### git status
Shows which files are modified, which are staged for the next commit, and which are untracked.

```bash
git status
```

### git add
Stages changes so they are included in your next commit.

```bash
git add README.md
```

### git commit
Saves the staged changes as a snapshot in your local history, with a message saying what changed.

```bash
git commit -m "Fix typo in README"
```

### git push
Uploads your local commits to a remote repository so others can see them.

```bash
git push origin main
```

**Merge notes:** Combined the two subtasks in workflow order: clone, status, add, commit, push. Added the required '## Git' heading. Made the blank lines after the subheadings match across all five entries. Nothing was repeated or contradictory, so none of the content changed.

### 1.1.1 Git setup and inspection commands (leaf, depth 2)

**Task:** Write Markdown entries for exactly two essential beginner git commands: git clone and git status. These go inside a cheat-sheet section headed '## Git'. Do not write that heading. For each command, give a '### ' subheading with the command name, a one-line plain-English explanation, and one realistic example in a ```bash code block, for example git clone https://github.com/user/project.git. Cover only these two commands, not PowerShell. Deliverable: the two Markdown entries alone, with no preamble.

**Why:** This is a small leaf task, so it was written directly.

### git clone
Copies an existing remote repository, including its full history, into a new folder on your computer.

```bash
git clone https://github.com/user/project.git
```

### git status
Shows which files are modified, which are staged for the next commit, and which are untracked.

```bash
git status
```

### 1.1.2 Git save and share commands (leaf, depth 2)

**Task:** Write Markdown entries for exactly three essential beginner git commands: git add, git commit and git push. These go inside a cheat-sheet section headed '## Git'. Do not write that heading. For each command, give a '### ' subheading with the command name, a one-line plain-English explanation, and one realistic example in a ```bash code block, for example git add README.md, git commit -m "Fix typo in README" and git push origin main. Cover only these three commands, not PowerShell. Deliverable: the three Markdown entries alone, with no preamble.

**Why:** This is a small leaf task, so writing it directly is the quickest way to finish it.

### git add

Stages changes so they are included in your next commit.

```bash
git add README.md
```

### git commit

Saves the staged changes as a snapshot in your local history, with a message saying what changed.

```bash
git commit -m "Fix typo in README"
```

### git push

Uploads your local commits to a remote repository so others can see them.

```bash
git push origin main
```

### 1.2 Five essential PowerShell commands (split, depth 1)

**Task:** Write the PowerShell part of a beginner cheat sheet: a Markdown section headed '## PowerShell' that lists exactly five essential PowerShell cmdlets for beginners (for example Get-ChildItem, Set-Location, Get-Content, Copy-Item, Get-Help). For each cmdlet give the full cmdlet name (common alias in parentheses is fine), a one-line plain-English explanation, and one realistic example in a code block. Cover PowerShell only, not git. Deliverable: that Markdown section alone, with no preamble.

**Why:** I split the five cmdlets by kind: three for moving around and reading files, two for changing files and getting help. The two parts don't overlap and can be written separately, then joined under one heading.

## PowerShell

**Get-ChildItem** (alias `ls`, `dir`)
Lists the files and folders in the current directory, or in a path you give it.
```powershell
Get-ChildItem C:\Projects -Filter *.txt
```

**Set-Location** (alias `cd`)
Moves you into a different directory so that later commands run there.
```powershell
Set-Location C:\Projects\my-app
```

**Get-Content** (alias `cat`)
Prints the contents of a text file in the terminal.
```powershell
Get-Content .\README.md -TotalCount 20
```

**Copy-Item** (alias `cp`, `copy`)
Copies a file or folder from one location to another.
```powershell
Copy-Item .\report.txt -Destination .\backup\report.txt
```

**Get-Help** (alias `help`)
Shows documentation and usage examples for any cmdlet.
```powershell
Get-Help Copy-Item -Examples
```

**Merge notes:** The two subtasks did not overlap or contradict each other. I unified the alias format: 1.2.2 wrote "(alias: `cp`, `copy`)" and 1.2.1 wrote "(alias `ls` / `dir`)", so all five now use "(alias `x`, `y`)". I also removed the blank lines 1.2.2 left between the explanation and the code block, so every entry has the same layout. The content is unchanged. The aliases ls, cat and cp exist only on Windows. On PowerShell 7 for Linux/macOS, those names run the native Unix commands instead. dir, cd, copy and help work on every platform. The cheat sheet is meant for Windows users, so I did not add a note about this.

### 1.2.1 PowerShell navigation and reading cmdlets (leaf, depth 2)

**Task:** Write Markdown entries for exactly three PowerShell cmdlets that beginners use to move around and read files: Get-ChildItem (alias ls/dir), Set-Location (alias cd) and Get-Content (alias cat). For each one, give the full cmdlet name as a bold line with its common alias in parentheses, then a one-line plain-English explanation, then one realistic example in a ```powershell code block. Do not add a section heading. Cover PowerShell only, not git and not any other cmdlets. Deliverable: only those three entries in Markdown, with no preamble.

**Why:** This is a small, self-contained writing task at the depth limit, so I wrote it directly.

**Get-ChildItem** (alias `ls` / `dir`)
Lists the files and folders in the current directory, or in a path you give it.
```powershell
Get-ChildItem C:\Projects -Filter *.txt
```

**Set-Location** (alias `cd`)
Moves you into a different directory so that later commands run there.
```powershell
Set-Location C:\Projects\my-app
```

**Get-Content** (alias `cat`)
Prints the contents of a text file in the terminal.
```powershell
Get-Content .\README.md -TotalCount 20
```

### 1.2.2 PowerShell file-copy and help cmdlets (leaf, depth 2)

**Task:** Write Markdown entries for exactly two PowerShell cmdlets for beginners: Copy-Item (alias cp/copy) and Get-Help (alias help). For each one, give the full cmdlet name as a bold line with its common alias in parentheses, then a one-line plain-English explanation, then one realistic example in a ```powershell code block. Do not add a section heading. Cover PowerShell only, not git and not any other cmdlets. Deliverable: only those two entries in Markdown, with no preamble.

**Why:** This is a small leaf task, so I wrote both entries directly.

**Copy-Item** (alias: `cp`, `copy`)
Copies a file or folder from one location to another.

```powershell
Copy-Item .\report.txt -Destination .\backup\report.txt
```

**Get-Help** (alias: `help`)
Shows documentation and usage examples for any cmdlet.

```powershell
Get-Help Copy-Item -Examples
```
