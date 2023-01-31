# Git Commands CheatSheet

## How to store github PAT's

1. Create them via: 'Settings/Developer Settings' on github
2. activate credential helper (locally): 
  * on windows: `git config --global credential.helper manager-core`
  * on linux: `git config --global credential.helper store`
4. make push or clone: enter Username + Generated PAT in step 1

## Update credentials

When using username/password instead of PAT's and credentials have changed
  * `git config --global credential.helper manager-core --replace-all` (followed by pull or clone)

## Show History 

```git log --oneline --abbrev-commit --all --graph --decorate --color```

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

`git checkout master; git remote update origin --prune; git branch -vv | Select-String -Pattern ": gone]" | % { $_.toString().Trim().Split(" ")[0]} | % {git branch -D $_}`
