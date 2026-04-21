# Git

Most researchers use Git as a slightly better way to back up files. That's not what it is. Git is a directed acyclic graph of content-addressable snapshots — once you understand the data structure, every command makes sense and you stop being afraid of it.

---

## Goal

- Understand Git's object model well enough that no command surprises you
- Use Git as an actual research tool: reproducible experiments, clean history, safe collaboration
- Recover confidently from the mistakes that currently feel unrecoverable
- Never lose work again

---

## Prerequisites

- Basic Git usage: `init`, `add`, `commit`, `push`, `pull`, `clone`

---

## Learning Path

### 1. The Object Model
Everything else follows from this. Git stores four object types — understand them and the rest is obvious.

- [ ] **Blobs:** file contents, content-addressed by SHA-1 hash
- [ ] **Trees:** directory snapshots — map filenames to blob/tree SHAs
- [ ] **Commits:** pointer to a tree + parent commit(s) + metadata
- [ ] **Tags:** named pointer to a commit
- [ ] `git cat-file -p <sha>`: inspect any object — do this for a real commit and follow the chain
- [ ] `git hash-object` and `git write-tree`: creating objects manually to understand the process
- [ ] The `.git/` directory: `objects/`, `refs/`, `HEAD`, `index` — know what each contains
- [ ] **Implementation:** Create a repo, make two commits, then manually traverse the object graph with `git cat-file` from `HEAD` down to individual blobs. Draw the DAG on paper.

### 2. Branching and Merging
- [ ] A branch is just a file containing a SHA — not a copy of the code
- [ ] `HEAD`: what it points to, detached HEAD state — when it happens and what to do
- [ ] Fast-forward merge: when it happens and what the history looks like
- [ ] Three-way merge: what Git does, what a merge commit is
- [ ] `git merge --no-ff`: forcing a merge commit when you want a clear feature boundary in history
- [ ] Merge conflicts: reading the conflict markers, resolving, completing the merge
- [ ] `git log --graph --oneline`: reading a branching history

### 3. Rebase
- [ ] What rebase does: replays commits onto a new base — rewrites SHAs
- [ ] `git rebase <branch>`: keeping a feature branch up to date with main
- [ ] Interactive rebase `git rebase -i`: squash, reword, reorder, drop commits
- [ ] The golden rule: never rebase commits that exist on a remote others are using
- [ ] `git rebase` vs `git merge`: when to prefer each — rebase for clean linear history, merge for preserving context
- [ ] **Implementation:** Take a branch with 4 messy commits ("fix", "fix again", "typo", "actually works"), interactively rebase into a single clean commit with a proper message

### 4. Undoing Things
The commands that matter when you've made a mistake.

- [ ] `git restore <file>`: discard unstaged changes in working tree
- [ ] `git restore --staged <file>`: unstage without losing changes
- [ ] `git reset HEAD~1 --soft`: undo last commit, keep changes staged
- [ ] `git reset HEAD~1 --mixed`: undo last commit, keep changes unstaged
- [ ] `git reset HEAD~1 --hard`: undo last commit, discard changes — destructive
- [ ] `git revert <sha>`: create a new commit that undoes a previous one — safe for shared branches
- [ ] `git reflog`: the safety net — every HEAD movement is logged here, nothing is permanently lost
- [ ] `git stash` / `git stash pop` / `git stash list`: shelving work in progress
- [ ] `git cherry-pick <sha>`: apply a specific commit to the current branch

### 5. Inspection and Debugging
- [ ] `git log`: `--oneline`, `--graph`, `--author`, `--since`, `--grep`, `-S` (pickaxe search)
- [ ] `git diff`: working tree vs index, index vs HEAD, between commits, between branches
- [ ] `git blame`: who changed each line, when — `git blame -L 10,20 file.py`
- [ ] `git bisect`: binary search through history to find the commit that introduced a bug — run it once on a real regression
- [ ] `git show <sha>`: inspect a specific commit's diff and metadata
- [ ] `git log -S "function_name"`: find every commit that added or removed a string

### 6. Working with Remotes
- [ ] `origin` is just a name: `git remote -v`, adding and removing remotes
- [ ] `git fetch` vs `git pull`: fetch retrieves, pull fetches + merges — prefer fetch + explicit merge
- [ ] `git push --force-with-lease`: safer than `--force` — fails if someone else pushed since you last fetched
- [ ] Tracking branches: `@{upstream}`, `git branch -vv`
- [ ] `git submodule`: what they are and why they're painful — know before you use one

### 7. Git for Research
Patterns specific to running experiments with Git.

- [ ] One commit per logical change: not one commit per day, not one commit per experiment
- [ ] Tagging submissions: `git tag v1.0-miccai-2025` before a paper submission freeze
- [ ] Branching per experiment: `exp/loss-boundary-weight-0.5` — keeps main clean, history is explicit
- [ ] Storing configs not outputs: commit Hydra configs and results summaries, not checkpoints (use DVC for those)
- [ ] `.gitignore` for ML repos: checkpoints, caches, `__pycache__`, `.wandb/`, large data files
- [ ] Commit messages for research: include the hypothesis and result, not just "update training script"
- [ ] **Implementation:** Set up a `.gitignore` for an ML project. Write 5 commit messages for past experiment changes — retroactively, using `git rebase -i` to reword them properly.

---

## Projects

| Project | Key concepts |
|---|---|
| Object graph traversal | `git cat-file`, object model, DAG |
| Interactive rebase cleanup | `rebase -i`, squash, reword |
| Bisect a regression | `git bisect`, debugging with history |
| ML repo `.gitignore` + commit hygiene | Research workflow, tagging, branching |

---

## Resources

**Books**
- *Pro Git* — Chacon & Straub (free at git-scm.com — chapters 1–3 and 7 are essential)
- *Think Like Git* — if you struggle with mental models, this bridges the gap

**Reference**
- `git help <command>` — the man pages are good; use them
- gitvisualizing.com / learngitbranching.js.org — interactive visualisations for branching and rebasing

---

## Progress

- [ ] The object model
- [ ] Branching and merging
- [ ] Rebase
- [ ] Undoing things
- [ ] Inspection and debugging
- [ ] Working with remotes
- [ ] Git for research
- [ ] Project: Object graph traversal
- [ ] Project: Interactive rebase cleanup
- [ ] Project: Bisect a regression
- [ ] Project: ML repo `.gitignore` + commit hygiene
