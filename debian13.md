# Debian 13 Install Notes

## Post Install Tasks

### Remove packages
```
sudo apt remove libreoffice* thunderbird celluloid gnome-software
```
### Install Packages
```
sudo apt install tmux mosh htop btop eog audacious rsync git jq lynx moc xfce4-terminal vim-gtk3 vlc openssh-server wget
```
### Configuration Files
- [lynx](config/lynx_config)
- [moc](config/moc)
- [vnc](config/vnc)
- [vim](config/vim)

### Other Packages
 - [freetube(deb)](https://freetubeapp.io/#download)
 - [plexamp(flattub)](https://flathub.org/apps/details/com.plexamp.Plexamp)


## VNC
```
sudo apt install tigervnc-standalone-server
```
```
vncpasswd
```
```
vi ~/.vnc/xstartup
```
paste the following
```#!/bin/bash
[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
vncconfig -iconic &
dbus-launch --exit-with-session  cinnamon-session

```
then
```
chmod u+x ~/.vnc/xstartup
```
add alias to .bashrc
```
alias vnc='env -u SESSION_MANAGER -u DBUS_SESSION_BUS_ADDRESS  tigervncserver -xstartup .vnc/xstartup -localhost no'
```
Other commands
```
vncserver -list
```
```
vncserver -kill :1
```
### Update /etc/default/grub 
```
GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash radeon.modeset=0 i915.lvds_channel_mode=2 i915.modeset=1"
GRUB_CMDLINE_LINUX=""
```
### Update Grub 
```
sudo update-grub
```
