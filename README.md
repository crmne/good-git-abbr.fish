# good-git-abbr

A Fish plugin containing focused, high-signal Git abbreviations.

## Install

With Fisher:

```fish
fisher install crmne/good-git-abbr.fish
```

## Usage

### Start here

| Abbreviation | Command |
| --- | --- |
| `gabbr` | show all `good-git-abbr` abbreviations |

### Core

| Abbreviation | Command |
| --- | --- |
| `g` | `git` |
| `gcl` | `git clone` |

### Status

| Abbreviation | Command |
| --- | --- |
| `gst` | `git status` |
| `gss` | `git status -s` |

### Branch

| Abbreviation | Command |
| --- | --- |
| `gb` | `git branch -vv` |
| `gba` | `git branch -a -v` |
| `gbd!` | `git branch -d` |
| `gbD!` | `git branch -D` |
| `gbm` | `git branch --move` |

### Checkout

| Abbreviation | Command |
| --- | --- |
| `gco` | `git checkout` |
| `gcom` | `git checkout (__good_git_default_branch)` |
| `gcb` | `git checkout -b` |

### Commit

| Abbreviation | Command |
| --- | --- |
| `gc` | `git commit -v` |
| `gc!` | `git commit -v --amend` |
| `gcn!` | `git commit -v --no-edit --amend` |
| `gca` | `git commit -v -a` |
| `gca!` | `git commit -v -a --amend` |
| `gcan!` | `git commit -v -a --no-edit --amend` |
| `gcv` | `git commit -v --no-verify` |
| `gcav` | `git commit -a -v --no-verify` |
| `gcav!` | `git commit -a -v --no-verify --amend` |
| `gcm` | `git commit -m` |
| `gcam` | `git commit -a -m` |

### Diff and log

| Abbreviation | Command |
| --- | --- |
| `gd` | `git diff` |
| `gdc` | `git diff --cached` |
| `gls` | `git log --stat` |
| `glg` | `git log --oneline --decorate --color --graph` |

### Pull and push

| Abbreviation | Command |
| --- | --- |
| `gp` | `git pull` |
| `gup` | `git pull --rebase` |
| `gP` | `git push` |
| `gP!` | `git push --force-with-lease` |
| `gPn` | `git push --no-verify` |
| `gPn!` | `git push --no-verify --force-with-lease` |
| `gpu` | `git push origin (__good_git_current_branch) --set-upstream` |
| `gpa` | `git push origin --all` |
| `gpt` | `git push origin --tags` |

### Rebase

| Abbreviation | Command |
| --- | --- |
| `gr` | `git rebase` |
| `gra` | `git rebase --abort` |
| `grc` | `git rebase --continue` |
| `gri` | `git rebase --interactive` |

### Stash

| Abbreviation | Command |
| --- | --- |
| `gsta` | `git stash` |
| `gstp` | `git stash pop` |
| `gstl` | `git stash list` |
| `gstd` | `git stash drop` |

### Local file ops

| Abbreviation | Command |
| --- | --- |
| `ga` | `git add` |
| `gaa` | `git add --all` |
| `grm` | `git rm` |
| `grmc` | `git rm --cached` |

### Safety-sensitive

| Abbreviation | Command |
| --- | --- |
| `gclean` | `git clean -di` |
| `gclean!` | `git clean -dfx` |
| `gclean!!` | `git reset --hard; and git clean -dfx` |
| `gm` | `git merge` |
| `grf` | `git revert` |
| `grp!` | `git reset --hard HEAD` |

## Sample workflows

```fish
cd my-repo
gst

# throw away everything and return pristine
gclean!!
gcom
gp
gcb fix-login-bug

# ... edit files ...

gaa
gc
gP

# ... edit more files ...

gcan!
gP!

# rebase on latest default branch
gp
gr
```

```fish
# dogfooding this plugin repo
gaa
gss
gcam "Use abbreviations in sample workflows"
gP
```

## omafish compatibility

When both plugins are installed, `good-git-abbr` removes legacy omafish git wrapper functions (`g`, `gcm`, `gcam`, `gcad`) at load time so abbreviations win predictably.

To keep those wrappers, set:

```fish
set -gx GOOD_GIT_ABBR_KEEP_OMAFISH_WRAPPERS 1
```

## Plugin layout

- `functions/`: commands and helpers (`gabbr`, branch helpers, compatibility helpers)
- `conf.d/`: interactive startup setup (register abbreviations)
