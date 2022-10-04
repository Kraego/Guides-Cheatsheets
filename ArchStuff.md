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
