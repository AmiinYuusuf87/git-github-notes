Lesson 1 — Setup

git --version
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
git config --list

Lesson 2 — Git Basics

git init
git status
git diff
git diff --staged
git add <file>
git add .
git commit -m "message"
git log
git log --oneline

Lesson 3 — Branching


git switch -c <branch-name>
git checkout -b <branch-name>
git switch <branch-name>
git branch
git restore <file>
git restore --staged <file>
git stash
git stash pop
git stash list

Lesson 4 — Remote Repositories

git remote add origin <URL>
git remote -v
git remote set-url origin <new-URL>
git push -u origin main
git push
git pull
git fetch
gh auth login
gh auth status

Lesson 5 — Collaboration

git clone <URL>
git merge main
git rebase main

Lesson 6 — Pull Requests & Merging

git merge <branch-name>
git branch -d <branch-name>
git add <file>
git commit -m "message"
git push
git reset --soft HEAD~1
git reset HEAD~1
git reset --hard HEAD~1
git revert HEAD
git revert <commit-hash>

Lesson 7 — .gitignore & Organization

git rm <file>
git rm --cached <file>
git mv <old-name> <new-name>

Lesson 8 — Open Source Workflows

git switch main
git pull origin main
git switch -c <branch-name>
git clone <fork-URL>
git remote -v
git add .
git commit -m "message"
git push -u origin <branch-name>

Lesson 9 — GitHub Actions

mkdir -p .github/workflows
git add .github/workflows/<file>.yml
git commit -m "Add GitHub Actions workflow"
git push