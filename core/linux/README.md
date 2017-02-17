## Linux-4.9.9 BFQ, AUFS, Corsair

This is a custom version of the current package for the Linux kernel 4.9.9 with additional support for:

    * BFQ IO Scheduler
    * AUFS useful with docker
    * Corsair K65 and K70 RGB Rapidfire support
    * Corsair Scimitar PRO RGB driver

### How to compile it

Install [abs](https://www.archlinux.org/packages/?name=abs) and the [base-devel](https://www.archlinux.org/groups/x86_64/base-devel/)
package group.

Clone this repo:

```
git clone https://github.com/DamnWidget/archlinux-packages
```

**note**: this repository follows the same directories structure than the [abs](https://www.archlinux.org/packages/?name=abs) tool
generates.

Cd into your new cloned repo and run `makepkg`

```
cd archlinux-packages/core/linux
makepkg -s
```

The `-s` parameter will download any additional dependencies that the package needs.

### Installation

Then install it using pacman as usual, install the headers first and then the kernel

```
pacman -U linux-damnwidget-headers-4.9.9-2-x86_64.pkg.tar.gz
pacman -U linux-damnwidget-4.9.9-2-x86_86.pkg.tar.gz
```

### Considerations

This `PKGBUILD` makes use of multiple computer cores to speed up the compilation process, if the compilation process fails
or you experience erratic behavior when you boot into your custom compiled kernel change the `PKGBUILD` line 5 into:

`MAKEFLAGS="-j1"`

Then recompile (note that this time the compilation will take much longer).


### PGP Keys

To successfully compile the Kernel you need to import Linus Torvals and Greg Kroah-Hartman GPG keys if you did not yet

```
gpg --recv-keys 79BE3E4300411886
gpg --recv-keys 38DBBDC86092693E
```
