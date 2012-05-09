.. TODO: Flesh out this section quite a bit more with:
           - brief command-line examples
           - information on different partition table types (MSDOS, GPT, ...)

================
Setting up disks
================

-----------------
Disk partitioning
-----------------

.. note::

   This manual assumes you are proficient with disk partitions and either the
   :command:`parted`, :command:`fdisk`, or :command:`cfdisk` utility. If not,
   you may wish to read the `Linux Partition How-To`_ and the
   :manpage:`cfdisk(8)` man page.

In general, Red Hat-based systems contain at least three partitions:

- A bootloader partition, approximately 500 MB, marked as bootable, mounted at
  :file:`/boot`
- A virtual memory partition (called :dfn:`swap`), approximately the size of
  the memory you have installed
- A root data partition, which fills the rest of your available disk space,
  mounted at :file:`/`

Partition your disks appropriately. 

.. _Linux Partition How-To: http://www.faqs.org/docs/Linux-mini/Partition.html


------------
RAID and LVM
------------

If you wish to set up RAID or LVM, this is the point where you should set those
up.


--------------------
Partition formatting
--------------------

Format the partitions you have created. A few notes:

- The bootloader partition should be ext3 or ext4. More recent versions of GRUB
  (especially GRUB 2) may support additional partitions --- check the
  documentation for your version of GRUB for a list of supported partitions.
- Use the :command:`mkswap` command to format a swap partition.


--------------------
Mount the partitions
--------------------

Mount each partition under a specific directory given its mount point. For
example, given the above standard partition layout of a root data partition and
a bootloader partition::

    mkdir /mnt/root
    mount $ROOT_PARTITION /mnt/root
    mkdir /mnt/root/boot
    mount $BOOT_PARTITION /mnt/root/boot

.. note::

   In this manual we use :file:`/mnt/root` as the root directory. You can use
   any directory you like, but you will need to replace :file:`/mnt/root` with
   your directory of choice throughout this manual.
