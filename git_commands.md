# Git Commands CheatSheet

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
