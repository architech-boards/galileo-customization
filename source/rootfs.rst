Root FS
=======

By default, @board@'s Yocto/OpenEmbedded SDK will generate this files when you build an image:

* image-full-galileo-clanton.ext3*,

* core-image-minimal-initramfs-clanton.cpio.gz*


To open .ext3 file use: 

.. host::

 | mount -o loop image-full-galileo-clanton.ext3 /path/to/folder

now you can read and edit the files. At the end of your changes you must umount the folder

.. host::

 | umount /path/to/folder

This files and the bootloader are to be copied in your final medium partition (on SD card or USB stick) on your host development system and used for build
purposes with the Yocto Project.

The SD card ( or USB stick) must meet the following requirements:
 | - SD card must be formatted as FAT or FAT32.
 | - SD card size must be 32GB (or smaller) and SDHC format. SDXC format is not supported.

Now you are rady to copy the files to the final device: 

.. host::

 | cp -r ~/architech_sdk/architech/galileo/yocto/meta-clanton_v1.0.1/yocto_build/tmp/deploy/images/boot /path/to/your/sd/card/device
 | cp ~/architech_sdk/architech/galileo/yocto/meta-clanton_v1.0.1/yocto_build/tmp/deploy/images/bzImage /path/to/your/sd/card/device
 | cp ~/architech_sdk/architech/galileo/yocto/meta-clanton_v1.0.1/yocto_build/tmp/deploy/images/core-image-minimal-initramfs-clanton.cpio.gz /path/to/your/sd/card/device
 | cp ~/architech_sdk/architech/galileo/yocto/meta-clanton_v1.0.1/yocto_build/tmp/deploy/images/image-full-galileo-clanton.ext3 /path/to/your/sd/card/device

.. warning::
 
 | The content of the media will be lost forever!

After the copy completes, run:

.. host::

 | sync


