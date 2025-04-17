## Welcome to Ubuntu Ready

Ubuntu Ready is a minimal version of Ubuntu rootfs for an ARM embedded system(ARMhf and ARM64). I hope it can help people start embedded Linux development quickly.


## Support devices:
Xilinx Zynq-7000, Zynq UltraScale+ MPSoC, Raspberry Pi 2/3, etc.

## Audience: 
embedded linux engineers/developers, hobbies, hacker who already familiar with Linux distributions.

## Download & Installation: 
Rootfs contains all the user program and more. There're several distribution. If you want a minimal version of Ubuntu, you can use debootstrap to create one.  

`debootstrap --arch $ARCH $RELEASE  $DIR $MIRROR`

example below is Ubuntu20.04 focal for arm64.

`sudo debootstrap --arch=arm64 focal rootfs_path`

once it's done, use chroot to add user and install software. Root password is not set by default, add a user, or set rootpassword. Linux kernel modules is not include. 
[chroot_rootfs](https://github.com/xuminready/chroot_rootfs)

```
adduser mx // or use useradd
adduser mx sudo // add mx to sudo group
```

# create initrd.img using initramfs-tools
initrd.img is a small temporary rootfs used when Linux kernel is bootup. It's only requires when the Linux kernel doesn't have storage driver build-in, and rootfs is on that storage driver. 
1. copy Linux modules to **/lib/modules/**
2. install initramfs-tools `apt install initramfs-tools`
3. `update-initramfs -cv -k all`

[update-initramfs](http://manpages.ubuntu.com/manpages/focal/man8/live-update-initramfs.8.html)
the initrd.img file will be generate in /boot/
### ARMhf
#### Xilinx Zynq-7000

### ARM64
#### Xilinx UltraScale+ MPSoC

### Raspberry Pi
#### [Raspberry Pi 2, 3 and 4 are fully supported by Canonical](https://ubuntu.com/download/raspberry-pi)


#### [Ubuntu releases](https://wiki.ubuntu.com/Releases)

| Version | Code name | Release date | End of Life date |
| ------ | ------ | ------ | ------ |
| Ubuntu 20.04 LTS | Focal Fossa | April 23, 2020| April 2025 |

## Custom Embedded Linux

* [Buildroot](https://buildroot.org/)

## Support or Contact

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.

## Contributing
Contributions to this repository are welcomed.
* [Understanding the GitHub Flow](https://guides.github.com/introduction/flow/)
* [How to Contribute to an Open Source Project on GitHub](https://egghead.io/courses/how-to-contribute-to-an-open-source-project-on-github)
