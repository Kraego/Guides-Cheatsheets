# How to pimp your WSL2 Shell

This is mainly a summary of [scott hanselmans guide](https://www.hanselman.com/blog/how-to-make-a-pretty-prompt-in-windows-terminal-with-powerline-nerd-fonts-cascadia-code-wsl-and-ohmyposh) plus some googeling to make *Oh my posh* run on my machine.

## On Windows:

* Install *Oh my posh* to get the fonts etc.
* see: https://ohmyposh.dev/docs/windows
```powershell
Install-Module posh-git -Scope CurrentUser
Install-Module oh-my-posh -Scope CurrentUser
Install-Module -Name PSReadLine -Scope CurrentUser -Force -SkipPublisherCheck
code $PROFILE
```
add the following lines at the end of your profile
```
Import-Module posh-git
Import-Module oh-my-posh
Set-PoshPrompt -Theme jandedobbeleer
```

## In WSL

Install powerline
``` bash
sudo apt install golang-go
go get -u github.com/justjanne/powerline-go
```

Try it out with: ```eval "$(oh-my-posh --init --shell bash --config ~/.poshthemes/jandedobbeleer.omp.json)"```
if it's working copy this file to your ```~/.bashrc```.

In your ```~/.bashrc``` add the following lines

``` bash
GOPATH=$HOME/go
function _update_ps1() {
    PS1="$($GOPATH/bin/powerline-go -error $?)"
}
if [ "$TERM" != "linux" ] && [ -f "$GOPATH/bin/powerline-go" ]; then
    PROMPT_COMMAND="_update_ps1; $PROMPT_COMMAND"
fi
```

## Download & Install Fonts on Windows

* https://www.nerdfonts.com/font-downloads f.e.: Meslo NerdFont

## Set required Font in all Shells

https://stackoverflow.com/questions/66042480/not-getting-cascadia-code-pl-in-powershell

### In Terminal - settings.json

``` 
 "profiles":
    {
        "defaults":
        {
            // Put settings here that you want to apply to all profiles.
            "fontFace": "MesloLGM NF"  //"Cascadia Code PL"
        },
   ....
```
