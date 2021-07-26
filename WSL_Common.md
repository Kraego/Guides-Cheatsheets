# Common WSL2 Stuff

* Avoid Git Newline Windows - Linux mashup (this results in dumm commits and polutes your repo), so run command below on windows and in wsl:
```
git config --global core.autocrlf input
git config --global core.eol lf
```
