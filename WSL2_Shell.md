# How to pimp your WSL2 Shell

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
Set-PoshPrompt -Theme Paradox
```

## In WSL

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

* https://www.nerdfonts.com/font-downloads
* https://github.com/microsoft/cascadia-code/releases

## Set required Font in all Shells

https://stackoverflow.com/questions/66042480/not-getting-cascadia-code-pl-in-powershell
