# Plasma-i3wm

## 1. 安装软件


* i3-gaps(obviously)
* feh to set up the background
* j4-dmenu-desktop-git (not required)
* morc_menu (not required)
* i3status for the status bar of i3
* compton Enable transparency (optional)
* wmctrl to add to the i3 config (if you're not on an English installation of Plasma)
* rofi: quickly start app
* zensu: run sudo command
* kdialog: input zensu password

sudo pacman -Syu && sudo pacman -S i3-gaps feh rofi i3status wmctrl compton zensu kdialog


## 2. 使用i3wm 作为window manager
   - KDE Version < 5.25
      添加XSession，向/usr/share/xsessions/plasma-i3.desktop写入：
   ```
   [Desktop Entry]
   Type=XSession
   Exec=env KDEWM=/usr/bin/i3 /usr/bin/startplasma-x11
   DesktopNames=KDE
   Name=Plasma with i3
   Comment=Plasma with i3
   ```
   - KDE Version >= 5.25
      kde 5.25 之后的版本，使用systemd启动wm。
      
      向~/.config/systemd/user/plasma-i3.service写入：
   ```
   [Install]
   WantedBy=plasma.workspace.target
   
   [Unit]
   Description=i3wm
   Before=plasma.workspace.target
   
   [Service]
   ExecStart=/usr/bin/i3
   Slice=session.slice
   Restart=on-failure
   ```
   执行以下命令：
   ```
   $ systemctl --user mask plasma-kwin_x11.service
   $ systemctl --user enable plasma-i3.service
   ```
