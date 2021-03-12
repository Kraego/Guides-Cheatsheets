XServer Windows - WSL2 Ubuntu:

## Install X-Server Windows:

https://sourceforge.net/projects/vcxsrv/

## Set Display forward in Linux:

export DISPLAY=$(awk '/nameserver / {print $2; exit}' /etc/resolv.conf 2>/dev/null):0
export LIBGL_ALWAYS_INDIRECT=1

sudo apt update
sudo apt install x11-apps

Testit: xcalc - Calculator should open on Windows