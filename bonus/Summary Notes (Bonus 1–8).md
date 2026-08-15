Bonus 1 — Conventional Commits

Format: type: short description in lowercase
Most important types: feat (new feature), fix (bug fix), docs (documentation), style, refactor, test, chore.
Three valid styles: Numbered (42 - Updated README), Descriptive, or Conventional (feat: add bio paragraph).
Tip: README-only changes → docs:, not feat:. Avoid vague messages like fix: stuff.

Bonus 2 — Team Repository Setup

Collaborators: When you own the repo, invite teammates (Read / Write / Admin roles) — don't use a fork for your own project.
Branch protection: Settings → Branches → Add rule (main) → Require a pull request before merging — blocks direct pushes to main.
PR template: .github/pull_request_template.md — auto-fills the description for new PRs.
CODEOWNERS: .github/CODEOWNERS — assigns reviewers to specific files/folders (e.g. *.js @frontend-team).
Common mistake: Using a fork instead of inviting a collaborator to your own project.

Bonus 3 — Open Source Contributing

Labels: bug, good first issue, documentation — help you find work to do.
Auto-close: Fixes #12 must go in the PR description, not just the commit message.
Sync fork (required before a PR):
GitHub → your fork → Sync fork → Update branch
Locally: git switch main && git pull origin main
git switch -c fix/docs-typo
Star vs Fork: Star = bookmark, Fork = ready to contribute and open a PR.
Check before contributing: Clear README, recent commits, maintainers responding to issues, LICENSE + CONTRIBUTING.md present.

Bonus 4 — Discussions, Projects & Notifications

Issues vs Discussions: Issues = actionable task with a "done" state; Discussions = open-ended conversation (ideas, Q&A). Maintainers can convert one to the other.
Projects board: Kanban-style (Todo → In progress → Done) — Repo → Projects → New project.
Notifications: Watch level — "Participating and @mentions" is a good default; "All Activity" only if you maintain the repo.
Community tab: Shows whether README/LICENSE/CONTRIBUTING/CODE_OF_CONDUCT are present.

Bonus 5 — Gists and Wiki

Gist: A small snippet you can share without a full repo. Public = anyone can see it; Secret = only people with the URL (not encrypted — never put passwords/tokens in a gist).
Wiki: Extra documentation pages on a repo (installation, FAQ) — enabled via Settings → Features → Wikis.
When to use which: README = first impression; Wiki = longer docs; Gist = standalone snippet not tied to one repo.

Bonus 6 — Open Source Licenses

Important: A public repo with no LICENSE is not automatically free to reuse — copyright applies by default.
MIT: Use for almost anything, even commercially, just keep the credit.
Apache 2.0: Like MIT + explicit patent protection — common in corporate open source.
GPL v3 (copyleft): If you distribute a modified version, you must share the source under the same license.
Creative Commons: Used for content (writing, courses) — not code. Example: CC BY-NC-SA (this bootcamp) = credit + non-commercial + share-alike.
Tip: Pick a license before your first release.

Bonus 7 — Tags and Releases

Tag: A fixed name marking a specific commit as a version (v1.0.0) — unlike a branch, it doesn't move.
Semantic Versioning (vMAJOR.MINOR.PATCH):
PATCH = bug fix (v1.0.0 → v1.0.1)
MINOR = new, compatible feature (v1.0.0 → v1.1.0)
MAJOR = breaking change (v1.0.0 → v2.0.0)
Commands:
bash
  git tag -a v1.0.0 -m "First public version"
  git push origin v1.0.0
Prefer annotated tags (-a -m) over lightweight tags — they store author and date.
GitHub Release: Releases → Create a new release → select the tag → write title/description → Publish.

Bonus 8 — GitHub Profile

Username: Use the same handle across GitHub, LinkedIn, and your portfolio — one consistent brand.
Edit profile: Photo, name, short bio, location. Pin up to 6 finished repos.
Contribution graph: Counts Commits, Issues, Pull Requests, and Code Review — not just commits. Enable Activity overview to show your orgs/repos.
Profile README: Create a public repo named exactly your username (username/username) — the README renders above your pins. Keep it shorter than the profile sidebar.
Skills: Only list what you actually use now — e.g. TypeScript · Next.js · PostgreSQL · Git, not every tool from every bootcamp.