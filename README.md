# Manjaro software installation guide

My own guide to install softwares on Manjaro Linux

### Switch to Fastest Mirror

```
sudo pacman-mirrors --fasttrack
```

### Update Manjaro
```
sudo pacman -Syyu
```

### Install AUR package manager
```
sudo pacman -S yaourt
```

### Enabling AUR in Manjaro

(Enable AUR)!https://www.fosslinux.com/4278/what-is-aur-and-how-to-enable-it-in-manjaro.htm

## Install Vim Editor
```
sudo pacman -S vim
```

In case if you get any error while installing the package, try the command below and repeat the previous commands:
```
sudo pacman -Rs vim
```

## Install XnView Multi Platform

Install from "Add/Remove Software" app using AUR.

## Archive Software (RAR, ZIP, etc)

Open "Add/Remove Software" app and search for "peazip-gtk2" from AUR repository. Build from the search result.

peazip-gtk2 (GTK2 archiver utility)
Repository: AUR
size: 20.7 MB
