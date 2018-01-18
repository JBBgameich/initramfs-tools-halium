# initramfs-tools-halium

Hooks and configuration to build a Halium initramfs

## Build an initramfs image

Building your own initramfs image wtih the tools in this repository is simple.

Requirements:

* Any OS with `debootstrap`
* `sudo` rights on the machine, to create the chroot

1. Clone this repository into your home folder
1. `cd` into the repository
1. Run `sudo ./build-initrd.sh -a [ARCH]`

The initrd will be saved as `./out/initrd.img-touch-$ARCH` by default.

## Command-line / Environment options

`-a|--arch / ARCH=` The architecture to build an initrd for. Can be any architecture supported by Debian. Default `armhf`.

`-m|--mirror / MIRROR=` Mirror to pass to debootstrap. Default `http://deb.debian.org/debian`.

`RELEASE=` Debian release to use for building this initrd. Default `stable`.

`ROOT=` Location to place build chroot. Default `./build/$ARCH`.

`OUT=` Location to copy finished initrd to. Default `./out`.

`INCHROOTPACKAGES=` Packages to install in the chroot. These are installed in addition to the `minbase` packages specified by debootstrap. Default `initramfs-tools dctrl-tools e2fsprogs libc6-dev zlib1g-dev libssl-dev busybox-static`

## FAQ

*I'm getting a strange error when I try to build*

Try deleting your chroots (normally in the `build/` directory) and building again.

*I can't delete my chroots! They say that something is busy!*

Just run `umount build/*/*` to unmount anything that's mounted. If that doesn't work, reboot your computer. The mounts should be gone after that. Then you can delete the chroots.
