# OrangePiZero2ArmbianWirelessFix
How to make Armbian WiFi &amp; Bluetooth work on Orange Pi Zero 2

## Background
Armbian Bookworm hides images with legacy kernel, and the default image with mainline kernel does not support aw859a(uwe5622), so WiFi is gone

## Fix?
Just download legacy builds from https://archive.armbian.com/orangepizero2/archive

Or connect the wire and install `linux-image-legacy-sun50iw9` `linux-dtb-legacy-sun50iw9`

## Newer kernel
The legacy kernel is 4.9, here are some other versions:

### 5.16
I extracted stock kernel using dpkg-repack, you can download them from [Releases](https://github.com/iovxw/OrangePiZero2ArmbianWirelessFix/releases/latest)

```sh
dpkg -i linux-dtb-current-sun50iw9_3.0.0_arm64.deb linux-image-current-sun50iw9_3.0.0_arm64.deb
```

The `armbian-firmware` should work out of the box, or you can install `orangepi-firmware_3.0.0_b2809d6_all.deb` which is the latest [orangepi-xunlong/firmware](https://github.com/orangepi-xunlong/firmware)

load modules

```sh
printf "\nsprdwl_ng\nsprdbt_tty" >> /etc/modules
```

enable overlay

```sh
printf "\noverlay_prefix=sun50i-h616" >> /boot/armbianEnv.txt
```

restart

### 6.1

The kernel of Orange Pi Zero 3 works on Zero 2 too!

https://github.com/orangepi-xunlong/linux-orangepi/tree/orange-pi-6.1-sun50iw9

