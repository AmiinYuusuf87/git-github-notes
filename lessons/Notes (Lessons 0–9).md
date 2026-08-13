Git & GitHub — Summary Notes (Lessons 0–9)

Lesson 0 — The Version Control Era

The problem before VCS: File copying chaos (file_final_v2.txt), lost history, people overwriting each other's work, no accountability.
VCS (Version Control System): A tool that records changes to files over time, so you can recall previous versions and see who changed what.
Centralized (SVN): One central server holds all the history → single point of failure (if the server dies, history can be lost).
Distributed (Git): Every developer has a full copy of the history → works offline, safe, fast.
Git: Created by Linus Torvalds in 2005 to manage the Linux kernel.
Why Git won: Free & open-source, distributed, fast/easy branching, scales from tiny to huge projects.

Lesson 1 — Introduction to Git & GitHub

Git = a tool/software that runs on your computer and tracks changes.
GitHub = a website/cloud platform that hosts Git projects, adding PRs, Issues, Actions.
Key point: Git ≠ GitHub. Git is the camera, GitHub is Instagram (where the snapshots get shared).
Alternatives to GitHub: GitLab, Bitbucket.
Install: Check with git --version; if missing, install from git-scm.com.
Configuration (one-time, critical):
bash
  git config --global user.name "Your Name"
  git config --global user.email "you@example.com"

→ Required before your first commit (Assignment 1 checks the name/email on your commits).

Lesson 2 — Git Basics

Repository (repo): A folder Git tracks, containing a hidden .git folder.
The three areas:
Working Directory — the files you edit
Staging Area — a "waiting room" before commit
Repository (.git) — the permanent saved history
Commit = a permanent snapshot with an ID, author, date, and message.
Core commands:
git init — start a repo
git status — check current state (use often)
git diff — see unstaged changes
git diff --staged — see staged changes
git add <file> — move to staging area
git commit -m "message" — save permanently
git log --oneline — view history
Daily cycle: edit → status → diff → add → commit → log.
Commit messages: must be clear (e.g. Add login button), never vague like stuff, fix, update.

Lesson 3 — Branching

Branch = an independent line of work that doesn't affect main.
Default branch: main.
Commands:
git switch -c <name> — create + switch to a new branch
git switch <name> — switch to an existing branch
git branch — list all branches (* = current one)
git restore <file> — discard uncommitted changes (cannot be undone — be careful).
git restore --staged <file> — unstage a file (changes are kept).
git stash — temporarily save uncommitted changes so you can switch branches.
git stash pop — restore the stashed changes.
Golden rule: Never try to switch branches with uncommitted changes — commit, stash, or restore first.

Lesson 4 — Remote Repositories

Remote repository = the version of your project hosted on a server (GitHub).
origin = the default nickname for your remote.
Connecting:
bash
  git remote add origin <URL>
  git remote -v   # confirm the connection
git push -u origin main — first push (links local main → remote main).
git push — subsequent pushes.
git pull — download + merge remote changes (pull = fetch + merge).
git fetch — only download (doesn't change your files, just a "preview").
Authentication: Use GitHub CLI (gh auth login) or browser login — a Personal Access Token is the last-resort fallback.

Lesson 5 — Collaboration with GitHub

Clone = a full local copy (origin remote is set up automatically).
bash
  git clone <URL>
Fork = your own personal copy on GitHub (server-side) that you can freely push to.
Init vs Clone: init = brand-new repo; clone = copy of an existing one.
Clone vs Fork: Clone is local, Fork happens on GitHub (browser); if you don't own the repo, fork it first, then clone your fork.
Team workflow: clone → create your branch → commit → push → open PR → review → merge → delete branch.
Golden rule: Never work directly on main — always use a branch.
Keeping your branch updated: git merge main or git rebase main to pull in the latest changes from main.

Lesson 6 — Pull Requests and Code Reviews

Pull Request (PR) = a request to merge changes from one branch into another, for review before merging.
Flow: branch → commit → push → open PR → review → merge → delete branch.
Review outcomes: Approve / Request changes / Comment.
git merge:
bash
  git switch main
  git merge feature-branch
Merge Conflict: Happens when two branches change the same lines of the same file. Resolve by:
Opening the file and removing <<<<<<<, =======, >>>>>>>
git add <file>
git commit
git reset — move the branch back to an earlier commit (local only, not yet pushed).
--soft (staged), --mixed (unstaged), --hard (fully discarded — be careful).
git revert — creates a new commit that undoes an earlier one (safe for shared/pushed history).
Best practices: small PRs, one purpose per PR, kind and constructive reviews.

Lesson 7 — .gitignore and Project Organization

.gitignore = a file listing what Git should ignore.
Examples: node_modules/, .env, *.log, .DS_Store, dist/
Important: Create .gitignore early — it won't stop tracking a file that's already committed. Use:
bash
  git rm --cached <file>
git rm — delete a file + stage the deletion.
git mv — rename/move a file (history stays connected).
README.md — the project's front door: what it is, how to use it, installation steps.
Organization: src/, assets/, docs/, a clean root folder.
Secrets: Never hard-code passwords/API keys in your code — use .env (listed in .gitignore). If a secret ever gets pushed, revoke it immediately.

Lesson 8 — Open Source Workflows

Open Source = software whose source code is public, so anyone can view/modify/contribute.
Issue = where bugs/features are reported (title, description, open/closed status).
Discussions = open-ended conversation (not a task) — Issues are "tasks," Discussions are "conversation."
Contribution etiquette:
Read CONTRIBUTING.md
Search before opening a new issue
Comment "I'd like to work on this" before starting
One PR = one problem
Contribution flow: find issue → comment → fork → clone your fork → branch → commit → push → PR → Fixes #N → review.
Linking PR to Issue: Fixes #42, Closes #42, Resolves #42 — automatically closes the issue when the PR merges.
Sync Fork: Your fork doesn't auto-update — use the Sync fork button on GitHub, then:
bash
  git switch main
  git pull origin main
Good First Issue = a label for beginner-friendly tasks.

Lesson 9 — GitHub Actions Introduction

CI/CD: Automatically tests and prepares code when it's pushed.
CI = automatic testing/checking
CD = automatic release/delivery
GitHub Actions = GitHub's built-in automation tool, running workflows (YAML files) stored in .github/workflows/.
Vocabulary: Workflow → Job → Step → Runner; an Event (e.g. push) triggers the workflow.
Simple example:
yaml
  name: My First Workflow
  on: push
  jobs:
    say-hello:
      runs-on: ubuntu-latest
      steps:
        - uses: actions/checkout@v4
        - run: echo "Hello World"
uses = run a shared action (e.g. actions/checkout@v4 — required when you need your repo's files).
run = execute a shell command.
Other events: pull_request, schedule (cron), workflow_dispatch, release.
Status Checks: When on: pull_request is used, the ✅/❌ result shows directly on the PR page before merge.
Common mistakes: wrong folder, broken YAML indentation, forgetting checkout.