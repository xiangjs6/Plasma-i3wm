# Plasma-i3wm

## 1. 安装软件


* i3-gaps(obviously)
* feh to set up the background
* dmenu (not required)
* morc_menu (not required)
* i3status for the status bar of i3
* compton Enable transparency (optional)
* wmctrl to add to the i3 config (if you're not on an English installation of Plasma)


sudo pacman -Syu && sudo pacman -S i3-gaps feh j4-dmenu-desktop-git morc_menu i3status wmctrl compton



## 2. 添加XSession

向/usr/share/xsessions/plasma-i3.desktop写入：

```
[Desktop Entry]
Type=XSession
Exec=env KDEWM=/usr/bin/i3 /usr/bin/startplasma-x11
DesktopNames=KDE
Name=Plasma with i3
Comment=Plasma with i3
```
