# Git CheatSheet

**Contents:**
- [Git Commands CheatSheet](#git-commands-cheatsheet)
  - [Undo Stuff](#undo-stuff)
  - [Better log alias](#better-log-alias)
  - [Search in the log](#search-in-the-log)
  - [Config diff to Delta](#config-diff-to-delta)
  - [Rerere](#rerere)
  - [Alias new and missing with dot Notation](#alias-new-and-missing-with-dot-notation)
  - [Enable Autostash](#enable-autostash)
  - [How to store github PAT's](#how-to-store-github-pats)
  - [Update credentials](#update-credentials)
  - [Show History with branches](#show-history-with-branches)
  - [Rebase (local)](#rebase-local)
    - [If you have many commits to rebase](#if-you-have-many-commits-to-rebase)
    - [Rebase](#rebase)
  - [Prune local branches (Windows)](#prune-local-branches-windows)

## Undo Stuff

**reflog** for Undoing stuff (rebase, merge, ...) stored in rr_cache, reflog keeptime is 90 days as default. The reflog stuff is stored in `.git\logs\refs`.

```bash
git reflog [branchname]
```

Example: Undo one wrong git action (`[branchname]@{[number of actions to undo]}`), `HEAD` can also be
used in branchname

```bash
git reset --hard main@{1}
```

## Better log alias

Create an alias `lg` for nicer logs

```bash
git log --pretty='%C(bold red)%h%Creset%C(bold yellow)%d%Creset %s %C(cyan)(%ar)%Creset'
```

**add as alias:**

```bash
git config --global alias.lg "log --pretty='%C(bold red)%h%Creset%C(bold yellow)%d%Creset %s %C(cyan)(%ar)%Creset'" 
```

## Search in the log

S ... pickaxe

```bash
git log -S `[Searchstring]`
```

Search by Changed - Function/Method

```bash
git log -L:[Functionname]:[FileFilter]
```

f.e.:
```bash
git log -L:add:FooFunction
```

## Config diff to Delta

nicer than `less` -> https://github.com/dandavison/delta (install with scoop: `scoop install delta`)

```bash
git config --global core.pager delta
```

## Rerere

Reuse Recorder Resolution: for example when working on a long living feature branch to integrate changes from main iterative (in other words record the resolve of merge conflicts to apply them when creating the PR).

```bash
git config --global rerere.enabled true
```

## Alias new and missing with dot Notation

Dotdot notation, stuff in main and not in foo: `git log main..foo` (for stuff in foo and not in main change places of branch)

```bash
git config --global alias.new 'log --oneline main..HEAD'
git config --global alias.missing 'log --oneline HEAD..main'
```

## Enable Autostash

Enable automatic stashing, so you don't have to commit before merging/rebase

```bash
git config --global rebase.autostash
```

## How to store github PAT's

1. Create them via: 'Settings/Developer Settings' on github
2. activate credential helper (locally): 
  * on windows: `git config --global credential.helper manager-core`
  * on linux: `git config --global credential.helper store`
4. make push or clone: enter Username + Generated PAT in step 1

## Update credentials

When using username/password instead of PAT's and credentials have changed
  * `git config --global credential.helper manager-core --replace-all` (followed by pull or clone)

## Show History with branches

```git log --oneline --abbrev-commit --all --graph --decorate --color```

save it as alias - `lgp`:

from: https://stackoverflow.com/a/9074343/11473934 

```bash
git config --global alias.lgp "log --graph --abbrev-commit --decorate --format=format:'%C(bold blue)%h%C(reset) - %C(bold green)(%ar)%C(reset) %C(white)%s%C(reset) %C(dim white)- %an%C(reset)%C(auto)%d%C(reset)' --all"
```

## Rebase (local)

### If you have many commits to rebase 

You can melt the commits to one single commit (interactive rebase),
select **f (for fixup)** for all commits except **p** for the first (oldest), or **r** if you want to rewrite the commit message.

```bash
git rebase -i HEAD~[Number of Commits] #double check the count
# Rebase file opens (Vi -> ESC i)
# select `f` for all -> to squash instead of pick
# rename commit with `r` 
```
exit with :x
**!IF something failes exit with :q!** (don't save interactive rebase)

### Rebase

From [working branch] to main

```bash
git fetch
git checkout main
git pull
git checkout [working branch]
git pull
git rebase main
```
* Then follow guiding from git
  * resolve marked parts from rebase manualy in editor
```
<<<<<<< HEAD
              CustomerPassword = GenerateCustomerPassword(command.CustomerPasswordLength),
=======
              CustomerPassword = HashCustomerPassword(GenerateCustomerPassword(command.CustomerPasswordLength)),
>>>>>>> dev
``` 
to
```            
CustomerPassword = HashCustomerPassword(GenerateCustomerPassword(command.CustomerPasswordLength)),
```
* Check and add the changes:
   *   `git add [file with changes]`
   *   `git -m commit rebase merge`
   *   `git push` (push the merge to working branch)

Now Conflicts should be resolved!!

## Prune local branches (Windows)

Prune local branches that don't have a remote anymore on windows:

`git checkout main; git remote update origin --prune; git branch -vv | Select-String -Pattern ": gone]" | % { $_.toString().Trim().Split(" ")[0]} | % {git branch -D $_}`
