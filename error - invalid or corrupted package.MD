
# Issues with “signature is marginal trust” or “invalid or corrupted package” 

https://archived.forum.manjaro.org/t/issues-with-signature-is-marginal-trust-or-invalid-or-corrupted-package/33268/5

If --refresh-keys doesn't work (for whatever reason) try:

```
sudo pacman-key --refresh-keys --keyserver pgp.mit.edu
```
This uses a different keyserver than the default so might work better depending on your internet connection.

***************************************

If you still can't update, try updating your package mirrors too, before finally updating all packages:

sudo pacman-mirrors -f0
sudo pacman -Sy archlinux-keyring manjaro-keyring
sudo pacman-key --populate archlinux manjaro
sudo pacman-key --refresh-keys
sudo pacman -Syyu

***************************************

If you have any other errors, there's the "nuclear option":

sudo rm -fr /etc/pacman.d/gnupg
sudo pacman-key --init
sudo pacman-key --populate archlinux manjaro
sudo pacman-key --refresh-keys
sudo pacman -Syyu

And if this still doesn't work, and you trust that the packages are actually correct and not corrupt and haven't been interfered with, then you can force (re)installation of the keyring packages:

```
sudo pacman -U /var/cache/pacman/pkg/{archlinux,manjaro}-keyring*.pkg.tar.xz 
```

then try again.

***************************************

If you're installing an AUR package a PGP key can be used to verify the source files. You will need to import this into your personal keyring before it can be verified. If you don't you'll get an error similar to:

```
[...]
llvm-5.0.0.src.tar.xz ... FAILED (unknown public key 0FC3042E345AD05D)
libcxx-5.0.0.src.tar.xz ... FAILED (unknown public key 0FC3042E345AD05D)
libcxxabi-5.0.0.src.tar.xz ... FAILED (unknown public key 0FC3042E345AD05D)
[...]
```

To "fix" this, simply import the key:

gpg --recv-key 0FC3042E345AD05D

***************************************
