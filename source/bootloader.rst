Bootloader
======

On power on the boot sequence steps of @board@ are:

- BIOS starts
- grub loads the kernel and ramdisk
- the kernel loads the ramdisk drivers
- the kernel loads the sdcard rootfs


The bootloader used by @board@ is **Quark EDKII**. 
If You need to build the open source EDKII firmware for the Intel® Quark™ SoC download the Intel® Build and Software User Guide:

 | http://downloadmirror.intel.com/23962/eng/Quark_BSP_BuildandSWUserGuide_329687_007.pdf

The building guide starts at chapter 4.

If You want only to download the latest firmware go to:

 | https://communities.intel.com/docs/DOC-22226

