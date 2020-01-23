# Make bootable pendrive from ISO in Manjaro

Make a USB stick bootable using the following command:

```
sudo dd bs=4M if=/home/webtechriser/Downloads/manjaro-kde-18.1.5-191229-linux54.iso of=/dev/sdb status=progress oflag=sync
```

For details, read in full from the following link:

https://wiki.manjaro.org/index.php?title=Burn_an_ISO_File#Writing_to_a_USB_Stick_in_Linux
