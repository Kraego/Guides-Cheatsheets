<!-- omit in toc -->
# XServer Windows - WSL2 (Ubuntu):

- [Install X-Server Windows](#install-x-server-windows)
- [Set Display forward in WSL Distro](#set-display-forward-in-wsl-distro)
- [Start XLaunch on Windows](#start-xlaunch-on-windows)
- [Test it](#test-it)
- [Add it to autostart](#add-it-to-autostart)

## Install X-Server Windows

https://sourceforge.net/projects/vcxsrv/

## Set Display forward in WSL Distro

``` bash
export DISPLAY=$(awk '/nameserver / {print $2; exit}' /etc/resolv.conf 2>/dev/null):0
export LIBGL_ALWAYS_INDIRECT=1

sudo apt update
sudo apt install x11-apps
```

## Start XLaunch on Windows

* Multiple Windows
* Start no client
* disable Native opengl
* enable Disable access control

## Test it

In wsl: enter xcalc - Calculator should open in Windows10

## Add it to autostart

1. Run Dialog see [Start XLaunch on Windows](#start-xlaunch-on-windows)
2. Save configuration
3. Press Windows + R
4. Enter: shell:startup
5. Copy save configuration: *.launch (Generated in step 2) to this folder (step 4)

Now the XServer will be started with windows startup.