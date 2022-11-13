# Arch Linux Helpers

## AUR packages

* Stuff thats not available as `pacman` package 
  * update everything: `sudo pacman -Syu`
  * install package: `sudo pacman -S [package name]`
  * remove package: `sudo pacman -R [package name]`
    * also remove dependencies `sudo pacman -Rs [package name]`
* Using yay
  * install: `yay -S <aur package name>`
  * upgrade (guided): `yay -Sua`
  * remove: `yay -R <aur package name>`

## ZSH

### fzf - Terminal file search
(Used via fzf)

* `CTRL-T` - show folder and subfolder content
* `CTRL-R` - show file/folder history
* `CTRL-C` - show subfolders

### other used plugins

```
plugins=(
    fzf
    git
    history-substring-search
    colored-man-pages
    zsh-autosuggestions
    zsh-syntax-highlighting
    zsh-z
    vscode
)
```
* git clone https://github.com/agkozak/zsh-z
* git clone https://github.com/zsh-users/zsh-syntax-highlighting.git
* git clone https://github.com/zsh-users/zsh-autosuggestions
