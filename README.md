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
