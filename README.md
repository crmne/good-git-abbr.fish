# good-git-abbr

A Fish plugin containing focused, high-signal Git abbreviations.

## Install

With Fisher:

```fish
fisher install crmne/good-git-abbr.fish
```

## Usage

### Start here

| Abbreviation | Command | Why/When |
| --- | --- | --- |
| `gabbr` | show all `good-git-abbr` abbreviations | See the full abbreviation table quickly in your shell. |

### Sample workflows

```fish
# fast commit and push
gaa                            # git add --all
gss                            # git status -s
gcam "Improve sample workflow docs"  # git commit -a -m "Improve sample workflow docs"
gP                             # git push
```

```fish
# sync, branch, and start work
gcom                           # git checkout (__good_git_default_branch)
gp                             # git pull
gcb fix-login-bug              # git checkout -b fix-login-bug
```

### Core

| Abbreviation | Command | Why/When |
| --- | --- | --- |
| `g` | `git` | Base git command entrypoint. |
| `gcl` | `git clone` | Clone a repository locally. |

### Status

| Abbreviation | Command | Why/When |
| --- | --- | --- |
| `gst` | `git status` | Full status view with branch and hints. |
| `gss` | `git status -s` | Compact status for quick scans. |

### Branch

| Abbreviation | Command | Why/When |
| --- | --- | --- |
| `gb` | `git branch -vv` | Inspect local branches and upstream tracking. |
| `gba` | `git branch -a -v` | View local and remote branches together. |
| `gbd!` | `git branch -d` | Delete a branch only if already merged. |
| `gbD!` | `git branch -D` | Force-delete a branch (destructive). |
| `gbm` | `git branch --move` | Rename the current branch or a target branch. |

### Checkout

| Abbreviation | Command | Why/When |
| --- | --- | --- |
| `gco` | `git checkout` | Switch branches or restore paths. |
| `gcom` | `git checkout (__good_git_default_branch)` | Jump back to default branch (`main`/`master`). |
| `gcb` | `git checkout -b` | Create and switch to a new branch. |

### Commit

| Abbreviation | Command | Why/When |
| --- | --- | --- |
| `gc` | `git commit -v` | Commit with diff context in editor. |
| `gc!` | `git commit -v --amend` | Amend the previous commit. |
| `gcn!` | `git commit -v --no-edit --amend` | Amend without editing the message. |
| `gca` | `git commit -v -a` | Commit tracked-file changes without explicit `add`. |
| `gca!` | `git commit -v -a --amend` | Amend previous commit including tracked changes. |
| `gcan!` | `git commit -v -a --no-edit --amend` | Fast amend of tracked changes, keep message. |
| `gcv` | `git commit -v --no-verify` | Skip commit hooks when necessary. |
| `gcav` | `git commit -a -v --no-verify` | Commit tracked changes and skip hooks. |
| `gcav!` | `git commit -a -v --no-verify --amend` | Amend while skipping hooks. |
| `gcm` | `git commit -m` | Quick commit with inline message. |
| `gcam` | `git commit -a -m` | One-liner commit for tracked changes. |

### Diff and log

| Abbreviation | Command | Why/When |
| --- | --- | --- |
| `gd` | `git diff` | Review unstaged changes. |
| `gdc` | `git diff --cached` | Review staged changes before commit. |
| `gl` | `git log` | Browse commit history with full details. |
| `gls` | `git log --stat` | See commit history with file-change stats. |
| `glg` | `git log --oneline --decorate --color --graph` | Compact visual graph of branch history. |

### Pull and push

| Abbreviation | Command | Why/When |
| --- | --- | --- |
| `gp` | `git pull` | Pull latest changes from remote. |
| `gup` | `git pull --rebase` | Keep history linear while updating. |
| `gP` | `git push` | Push current branch to remote. |
| `gP!` | `git push --force-with-lease` | Safe-force push after rewrite (destructive). |
| `gPn` | `git push --no-verify` | Push while skipping push hooks. |
| `gPn!` | `git push --no-verify --force-with-lease` | Force-with-lease + no hooks (destructive). |
| `gpu` | `git push origin (__good_git_current_branch) --set-upstream` | First push of a new branch with upstream set. |
| `gpa` | `git push origin --all` | Push all local branches to origin. |
| `gpt` | `git push origin --tags` | Push tags to origin. |

### Rebase

| Abbreviation | Command | Why/When |
| --- | --- | --- |
| `gr` | `git rebase` | Reapply commits onto a new base. |
| `gra` | `git rebase --abort` | Exit and undo an in-progress rebase. |
| `grc` | `git rebase --continue` | Continue after resolving rebase conflicts. |
| `gri` | `git rebase --interactive` | Reorder/squash/edit commits before sharing. |

### Stash

| Abbreviation | Command | Why/When |
| --- | --- | --- |
| `gsta` | `git stash` | Temporarily shelve working changes. |
| `gstp` | `git stash pop` | Reapply the latest stash and remove it. |
| `gstl` | `git stash list` | View saved stash entries. |
| `gstd` | `git stash drop` | Remove a stash entry you no longer need. |

### Local file ops

| Abbreviation | Command | Why/When |
| --- | --- | --- |
| `ga` | `git add` | Stage selected files. |
| `gaa` | `git add --all` | Stage all tracked/untracked changes. |
| `grm` | `git rm` | Remove file from working tree and index. |
| `grmc` | `git rm --cached` | Untrack file but keep it locally. |

### Safety-sensitive

| Abbreviation | Command | Why/When |
| --- | --- | --- |
| `gclean` | `git clean -di` | Interactively remove untracked files/dirs. |
| `gclean!` | `git clean -dfx` | Remove all untracked + ignored files (destructive). |
| `gclean!!` | `git reset --hard; and git clean -dfx` | Full reset to pristine state (very destructive). |
| `gm` | `git merge` | Merge another branch into current branch. |
| `grf` | `git revert` | Undo a commit by creating a new inverse commit. |
| `grp!` | `git reset --hard HEAD` | Discard local tracked-file changes (destructive). |

## omafish compatibility

When both plugins are installed, `good-git-abbr` removes legacy [`omafish`](https://github.com/crmne/omafish) git wrapper functions (`g`, `gcm`, `gcam`, `gcad`) at load time so abbreviations win predictably.

To keep those wrappers, set:

```fish
set -gx GOOD_GIT_ABBR_KEEP_OMAFISH_WRAPPERS 1
```

## Plugin layout

- `functions/`: commands and helpers (`gabbr`, branch helpers, compatibility helpers)
- `conf.d/`: interactive startup setup (register abbreviations)
