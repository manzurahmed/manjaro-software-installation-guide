# Install Sublime Text 3

I have taken the instructions to install Sublime Text 3 editor in Manjaro from Sublime Text'3 official website (https://www.sublimetext.com/docs/3/linux_repositories.html).

###  Install the GPG key: 

```
curl -O https://download.sublimetext.com/sublimehq-pub.gpg && sudo pacman-key --add sublimehq-pub.gpg && sudo pacman-key --lsign-key 8A8F901A && rm sublimehq-pub.gpg
```

###  Select the channel to use: 

**Stable**

```
echo -e "\n[sublime-text]\nServer = https://download.sublimetext.com/arch/stable/x86_64" | sudo tee -a /etc/pacman.conf
```

###  Update pacman and install Sublime Text 

```
sudo pacman -Syu sublime-text
```
