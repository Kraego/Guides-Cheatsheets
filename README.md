# Guides-Cheatsheets
Useful notes, hints, howto's for development.

**Contents**
* How to open windows from wsl on hostOS (Windows 10): [XServerWSL2.md](https://github.com/Kraego/Guides-Cheatsheets/blob/master/XServerWSL2.md)
* Improve Terminal Prompt for wsl2 (Debian) + Powershell: [Pimp_WindowsTerminal.md](https://github.com/Kraego/Guides-Cheatsheets/blob/master/Pimp_WindowsTerminal.md)
* Openshift/OKD Hints: [Openshift.md](https://github.com/Kraego/Guides-Cheatsheets/blob/master/Openshift.md)
* WSL Common stuff and notes: [WSL_Common.md](https://github.com/Kraego/Guides-Cheatsheets/blob/master/WSL_Common.md)

## Common

When creating a zip with windows, linux won't be able to `unzip` it, to fix that, run

```bash
zip -FFv foo.zip --out fixed.zip
```
