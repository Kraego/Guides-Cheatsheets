# Git Commands CheatSheet

## How to store github PAT's

1. Create them via: 'Settings/Developer Settings' on github
2. activate credential helper (locally): 
  * on windows: `git config --global credential.helper manager-core`
  * on linux: `git config --global credential.helper store`
4. make push or clone: enter Username + Generated PAT in step 1

## Show History 

```git log --oneline --abbrev-commit --all --graph --decorate --color```

## Rebase

* To start
```bash
git fetch
git rebase origin/main #rebase to remote
```
or 
```bash
git fetch
git checkout main
git pull
git checkout [working branch]
git rebase main
```
* Then follow guiding
  * try pull: 'git pull' ... automerge should work otherwise merge manualy
  * push merge: 'git push'  
