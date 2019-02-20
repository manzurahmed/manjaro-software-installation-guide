# Install Skype for Manjaro

**System Requirement: Manjaro 18 Illyria Linux or later**

```
git clone https://aur.archlinux.org/skypeforlinux-stable-bin
cd skypeforlinux-stable-bin/
makepkg -s
ls *pkg.tar.xz
sudo pacman -U --noconfirm skypeforlinux-stable-bin-8.3*.*.**-*-x86_64.pkg.tar.xz
```
