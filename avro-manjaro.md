# Install Avro on Manjaro Linux

Follow this Medium tutorial: https://medium.com/@sashraf94/installing-ibus-avro-on-arch-distros-arch-manjaro-for-newbies-6a73a2839f66

## First thing : Install Pamac
```
sudo pacman -Syu pamac
```

## Enabling AUR

```
sudo pacman -Syu yaourt
```

## Now to Avro

Search for **ibus-avro-git**, it’ll be displayed in AUR repos. Build it.

## Enabling ibus-avro

From Start menu, type "IBus Preferences" and hit Enter key. You will be prompt to start IBus Deamon. Start it.
A new icon "EN" will appear on the Taskbar.
Press Right click on that button and select "Preferences".
There are 4 tabs, General, Input Method, Emoji and Advanced.
Click on "Input Method".
From Right hand side, click on "+Add" button, input method select list will appear.
Click on Bangla and "Bengali - Avro Phonetic" will appear under "Bengali".
Add Avro as input method.
