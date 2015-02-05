*******
Add-ons
*******

Huawei MU609
============

MU609 is high-quality designed HSPA module in small size and Huawei standard
LGA form factor which is specially designed for industrial-grade M2M applications such
as vehicle telematics, tracking, mobile payment, industrial router, safety
monitor and industrial PDAs.
@board@ sources can be easily updated to support MU609.

Download the `kernel patch <_static/0002-tibidabo-huawei.patch>`_ and 
`the configuration fragment <_static/huawei-mu609.cfg>`_ to *~/Documents*.
Be sure you followed the guide on @board@ :ref:`linux kernel <linux-kernel>`, 
and once you have prepared the kernel sources to be compiled by hand you can
apply the patches:

.. host::

 | patch -p1 -d ~/Documents/linux-2.6-imx/ < ~/Documents/0002-tibidabo-huawei.patch

To make the device work properly, make sure the Linux kernel is configured according
to the configuration fragment file (~/Documents/huawei-mu609.cfg) you just downloaded.

.. note::

 The patches have been tested with module MU609 programmed with firmware version 12.105.29.00.00
