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

## General

* **To background** in shell (f.e.: nano):
  * `CTRL+Z` - to background
  * `fg` - back to foreground
* write iso to sd/usb
  * `sudo dd bs=4M if=theIso.iso of=/dev/sda status=progress oflag=sync`
    * if: source
    * of: target
* Find **biggest files**
  * `sudo du -a /dir/ | sort -n -r | head -n 20
    * 20 ... show just the 20 biggest files
## ZSH

### fzf - Terminal file search
(Used via fzf)

* `CTRL-T` - show folder and subfolder content
* `CTRL-R` - show file/folder history
* `CTRL-C` - show subfolders

### other used plugins (Oh My Zsh)
https://ohmyz.sh/
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
In `~/.oh-my-zsh/custom/plugins`
* git clone https://github.com/agkozak/zsh-z
* git clone https://github.com/zsh-users/zsh-syntax-highlighting.git
* git clone https://github.com/zsh-users/zsh-autosuggestions

### Install powerlevel 10k

* `git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k`
* change theme in `~/.zshrc`
  * ZSH_THEME="powerlevel10k/powerlevel10k"
* update zsh: `source ~/.zshrc`
