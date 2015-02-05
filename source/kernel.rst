.. _linux-kernel:

Linux Kernel
============

The first step to compile the linux Kernel is to get the sources.
You can get them from the Internet by cloning the proper repository and checking out the proper hash commit:

.. host::

 | cd ~/Documents
 | git clone -b linux-3.8.y git://git.kernel.org/pub/scm/linux/kernel/git/stable/linux-stable.git
 | cd linux-stable
 | git checkout 531ec28f9f26f78797124b9efcf2138b89794a1e

The second step is to properly patching the sources:

.. host::

 | cd ~/Documents/linux-stable
 | patch -p1 -d linux-stable/ < ~/architech_sdk/architech/@board-alias@/yocto/meta-clanton_v1.0.1/meta-clanton-bsp/recipes-kernel/linux/files/0001-tty-don-t-deadlock-while-flushing-workqueue-quark.patch
 | patch -p1 -d linux-stable/ < ~/architech_sdk/architech/@board-alias@/yocto/meta-clanton_v1.0.1/meta-clanton-bsp/recipes-kernel/linux/files/0002-driver-core-constify-data-for-class_find_devic-quark.patch
 | patch -p1 -d linux-stable/ < ~/architech_sdk/architech/@board-alias@/yocto/meta-clanton_v1.0.1/meta-clanton-bsp/recipes-kernel/linux/files/0003-TTY-mark-tty_get_device-call-with-the-proper-c-quark.patch
 | patch -p1 -d linux-stable/ < ~/architech_sdk/architech/@board-alias@/yocto/meta-clanton_v1.0.1/meta-clanton-bsp/recipes-kernel/linux/files/0004-pwm-Add-sysfs-interface-quark.patch
 | patch -p1 -d linux-stable/ < ~/architech_sdk/architech/@board-alias@/yocto/meta-clanton_v1.0.1/meta-clanton-bsp/recipes-kernel/linux/files/0005-drivers-pwm-sysfs.c-add-export.h-RTC-50404-quark.patch
 | patch -p1 -d linux-stable/ < ~/architech_sdk/architech/@board-alias@/yocto/meta-clanton_v1.0.1/meta-clanton-bsp/recipes-kernel/linux/files/0006-core-Quark-patch-quark.patch
 | patch -p1 -d linux-stable/ < ~/architech_sdk/architech/@board-alias@/yocto/meta-clanton_v1.0.1/meta-clanton-bsp/recipes-kernel/linux/files/0007-Quark-Platform-Code-quark.patch
 | patch -p1 -d linux-stable/ < ~/architech_sdk/architech/@board-alias@/yocto/meta-clanton_v1.0.1/meta-clanton-bsp/recipes-kernel/linux/files/0008-Quark-UART-quark.patch
 | patch -p1 -d linux-stable/ < ~/architech_sdk/architech/@board-alias@/yocto/meta-clanton_v1.0.1/meta-clanton-bsp/recipes-kernel/linux/files/0009-EFI-capsule-update-quark.patch
 | patch -p1 -d linux-stable/ < ~/architech_sdk/architech/@board-alias@/yocto/meta-clanton_v1.0.1/meta-clanton-bsp/recipes-kernel/linux/files/0010-Quark-SDIO-host-controller-quark.patch
 | patch -p1 -d linux-stable/ < ~/architech_sdk/architech/@board-alias@/yocto/meta-clanton_v1.0.1/meta-clanton-bsp/recipes-kernel/linux/files/0011-Quark-USB-host-quark.patch
 | patch -p1 -d linux-stable/ < ~/architech_sdk/architech/@board-alias@/yocto/meta-clanton_v1.0.1/meta-clanton-bsp/recipes-kernel/linux/files/0012-USB-gadget-serial-quark.patch
 | patch -p1 -d linux-stable/ < ~/architech_sdk/architech/@board-alias@/yocto/meta-clanton_v1.0.1/meta-clanton-bsp/recipes-kernel/linux/files/0013-Quark-stmmac-Ethernet-quark.patch
 | patch -p1 -d linux-stable/ < ~/architech_sdk/architech/@board-alias@/yocto/meta-clanton_v1.0.1/meta-clanton-bsp/recipes-kernel/linux/files/0014-Quark-GPIO-2-2-quark.patch
 | patch -p1 -d linux-stable/ < ~/architech_sdk/architech/@board-alias@/yocto/meta-clanton_v1.0.1/meta-clanton-bsp/recipes-kernel/linux/files/0015-Quark-GPIO-1-2-quark.patch
 | patch -p1 -d linux-stable/ < ~/architech_sdk/architech/@board-alias@/yocto/meta-clanton_v1.0.1/meta-clanton-bsp/recipes-kernel/linux/files/0016-Quark-GIP-Cypress-I-O-expander-quark.patch
 | patch -p1 -d linux-stable/ < ~/architech_sdk/architech/@board-alias@/yocto/meta-clanton_v1.0.1/meta-clanton-bsp/recipes-kernel/linux/files/0017-Quark-I2C-quark.patch
 | patch -p1 -d linux-stable/ < ~/architech_sdk/architech/@board-alias@/yocto/meta-clanton_v1.0.1/meta-clanton-bsp/recipes-kernel/linux/files/0018-Quark-sensors-quark.patch
 | patch -p1 -d linux-stable/ < ~/architech_sdk/architech/@board-alias@/yocto/meta-clanton_v1.0.1/meta-clanton-bsp/recipes-kernel/linux/files/0019-Quark-SC-SPI-quark.patch
 | patch -p1 -d linux-stable/ < ~/architech_sdk/architech/@board-alias@/yocto/meta-clanton_v1.0.1/meta-clanton-bsp/recipes-kernel/linux/files/0020-Quark-IIO-quark.patch
 | patch -p1 -d linux-stable/ < ~/architech_sdk/architech/@board-alias@/yocto/meta-clanton_v1.0.1/meta-clanton-bsp/recipes-kernel/linux/files/0021-Quark-SPI-flash-quark.patch
 | patch -p1 -d linux-stable/ < ~/architech_sdk/architech/@board-alias@/yocto/meta-clanton_v1.0.1/meta-clanton-bsp/recipes-kernel/linux/files/uart-1.0.patch
 | patch -p1 -d linux-stable/ < ~/architech_sdk/architech/@board-alias@/yocto/meta-clanton_v1.0.1/meta-clanton-bsp/recipes-kernel/linux/files/GAL-118-USBDeviceResetOnSUSRES-2.patch

The third step is to copy the configuration:

.. host::

 | cp ~/architech_sdk/architech/galileo/yocto/meta-clanton_v1.0.1/meta-clanton-bsp/recipes-kernel/linux/files/quark.cfg linux-stable/.config
 | source ~/architech_sdk/architech/galileo/toolchain/environment-nofs
 | cd ~/Documents/linux-2.6-imx
 | make menuconfig

and the next step is to compile them:

.. host::

 | mkdir ../modules
 | KMACHINE=clanton KTYPE=standard KARCH=i386 make -j X
 | make modules_install INSTALL_MOD_PATH=../modules
 
.. warning::

 | X isn't a parameter. It's the number of processor's threads

By the end of the build process you will get **bzImage** under *arch/i386/boot*.

.. host::

 | ~/Documents/linux-stable/arch/i386/boot/bzImage


Now you need to download and unzip the RAMdisk rootfs from the Internet:

.. host::

 | cd ~
 | wget http://downloads.architechboards.com/galileo/download/dylan/initramfs-rootfs.tgz
 | tar -zxvf initramfs-rootfs.tgz 

Then you have to copy the compiled modules to RAMdisk rootfs:

.. host::

 | cp -r ~/Documents/modules/lib/modules/3.8.7+/ ~/rootfs/lib/modules/
 | cd rootfs
 | find . | cpio -o -H newc > ~/core-image-minimal-initramfs-clanton.cpio
 | cd ..
 | gzip -f -9 -c ~/core-image-minimal-initramfs-clanton.cpio > ~/core-image-minimal-initramfs-clanton.cpio.gz



