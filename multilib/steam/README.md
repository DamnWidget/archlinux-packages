## Steam with common Patches

This is a custom version of the steam-native archlinux package, it is pretty much the same than Manjaro has

### How to compile it

Install the [base-devel](https://www.archlinux.org/groups/x86_64/base-devel/) package group.

Clone this repo:

```
git clone https://github.com/DamnWidget/archlinux-packages
```

**note**: this repository follows the same directories structure than the [abs](https://www.archlinux.org/packages/?name=abs) tool
generates.

Cd into your new cloned repo and run `makepkg`

```
cd archlinux-packages/multilib/steam
makepkg -sc
```

The `-s` parameter will download any additional dependencies that the package needs. The `-c` parameter
instructs `makepkg` to clean up the directory after the build is done.

**note**: you can also run `makepkg -sci` to install the package as soon as the build process finish.

### Installation

Then install it using pacman as usual, install the headers first and then the kernel

```
pacman -U steam-1.0.0.54-5-x86_64.pkg.tar.gz
```

### Considerations

You need to uncoment the `multilib` section in your `pacman.conf` file

```
[multilib]
Include = /etc/pacman.d/mirrorlist
```
