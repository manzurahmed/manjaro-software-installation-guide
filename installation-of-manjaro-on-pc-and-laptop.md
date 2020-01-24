# Make bootable pendrive from ISO in Manjaro

Make a USB stick bootable using the following command:

```
sudo dd bs=4M if=/home/webtechriser/Downloads/manjaro-kde-18.1.5-191229-linux54.iso of=/dev/sdb status=progress oflag=sync
```

For details, read in full from the following link:

https://wiki.manjaro.org/index.php?title=Burn_an_ISO_File#Writing_to_a_USB_Stick_in_Linux


## Resolving errors

* https://forum.manjaro.org/t/hp-folio1040-boot-device-not-found/44038/5
* https://forum.manjaro.org/t/using-livecd-v17-0-1-and-above-as-grub-to-boot-os-with-broken-bootloader/24916
* https://forum.manjaro.org/t/solved-installation-check/86639/5
