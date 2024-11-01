# LMDE 6 Install Notes
[Screenshots](screenshots/screenshots.md)
![title]("screenshots/Screenshot from 2024-10-12 17-25-03.png")

## Post Install Tasks

### Remove packages
```
sudo apt remove libreoffice* thunderbird celluloid
```
### Install Packages
```
sudo apt install tmux mosh htop eog audacious rsync git jq vnc lynx moc xfce4-terminal vim-gtk3 vlc
```
### Configuration Files
- [lynx](config/lynx_config)
- [moc](config/moc)
- [vnc](config/vnc)
- [vim](config/vim)

### Other 
 - [freetube(deb)](https://freetubeapp.io/#download)
 - [plexamp(flattub)](https://flathub.org/apps/details/com.plexamp.Plexamp)

## Macbook Pro 2011 Specific (Disable Faulty AMD dGPU)

### Update /etc/default/grub 
```
GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash radeon.modeset=0 i915.lvds_channel_mode=2 i915.modeset=1"
GRUB_CMDLINE_LINUX=""
```

### Update /etc/grub.d/10_linux
```
echo "        outb 0x728 1" | sed "s/^/$submenu_indentation/"
echo "          outb 0x710 2" | sed "s/^/$submenu_indentation/"
echo "          outb 0x740 2" | sed "s/^/$submenu_indentation/"
echo "          outb 0x750 0" | sed "s/^/$submenu_indentation/"
echo "        insmod gzio" | sed "s/^/$submenu_indentation/"
```
### Update Grub 
```
sudo update-grub
```
### Validate dGPU is disabled
```
lspci -vnnn | grep VGA
```

## Resources
[LMDE 6 Download link](https://linuxmint.com/download_lmde.php)

