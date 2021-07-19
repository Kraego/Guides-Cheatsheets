# How to pimp your WSL2 Shell

In order to run **ZSH** in *Windows Terminal* you have to do both parts below.

## Debian

* install zsh ```sudo apt-get install zsh```
* install powerline for "agnostic": ```sudo apt-get install fonts-powerline``` 
* Change theme of zsh: ``` sudo nano ~/.zshrc```
   * go to *ZSH_THEME* and set it to "agnoster"
* Save the file
* Make ZSH your default shell: ```chsh -s $(which zsh)```
* Enter "normal" shell with ```bash```

## On Windows:

* Install *Oh my posh* to get the fonts etc.
* see: https://ohmyposh.dev/docs/windows
