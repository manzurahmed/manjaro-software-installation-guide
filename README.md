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

### Install Web Browser of Choice
```
yaourt -S brave
sudo pacman -S chromium
```

### Instal Dropbox 64-bit using yaourt

Go to Dropbox's official website (https://www.dropbox.com/install?os=lnx).
Run the two following commands and you are good to go.
```
cd ~ && wget -O - "https://www.dropbox.com/download?plat=lnx.x86_64" | tar xzf -
~/.dropbox-dist/dropboxd
```
