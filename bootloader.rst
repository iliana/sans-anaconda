======================
Install the bootloader
======================

In order for the target system to boot, the bootloader must be installed on the
Master Boot Record of one of your hard drives.

This process differs based on the version of GRUB your distribution uses. To
determine which version you have, run :command:`rpm --root=/mnt/root -q grub`.
If there is output, you have GRUB 1; if there is no output you have GRUB 2.


------
GRUB 1
------

Write :file:`grub.conf`
-----------------------

You will need to write a :file:`grub.conf` to instruct GRUB where to boot from.

#. Determine the version of the ``kernel`` package you are running::

    rpm --root=/mnt/root -q kernel --qf '%{VERSION}-%{RELEASE}.%{ARCH}\n'

   This command will output something similar to ``2.6.32-220.4.1.el6.x86_64``.

#. Determine the UUID of the root partition (the partition mounted at
   :file:`/mnt/root`). Your :file:`fstab` should contain this.

Write this to :file:`/mnt/root/boot/grub/grub.conf`::

    default=0
    timeout=5
    title Scientific Linux (UNAME)
        root (hd0,0)
        kernel /vmlinuz-UNAME ro root=UUID=ROOT_UUID selinux=0
        initrd /initramfs-UNAME.img

replacing ``UNAME`` with the kernel version and ``ROOT_UUID`` with the UUID of
the root partition.

:command:`grub-install`
-----------------------

Determine the hard drive (*not* the partition) that will be booted from. (In
most cases, this is the only hard drive.) Run :command:`grub-install`::

    grub-install --root-directory=/mnt/root /dev/sdX


------
GRUB 2
------

#. Mount the special filesystems under :file:`/mnt/root`::

    mount -t devtmpfs devtmpfs /mnt/root/dev
    mount -t proc proc /mnt/root/proc
    mount -t sysfs sysfs /mnt/root/sys

#. Enter a chroot under :file:`/mnt/root`::

    chroot /mnt/root

#. Determine the hard drive (*not* the partition) that will be booted from. (In
   most cases, this is the only hard drive.)

#. Run these commands inside the chroot::

    grub2-install /dev/sdX
    grub2-mkconfig -o /boot/grub2/grub.cfg

#. Exit the chroot by typing :command:`exit` or pressing :kbd:`Control-D`.

#. Unmount the special filesystems under :file:`/mnt/root`::

    umount /mnt/root/dev
    umount /mnt/root/proc
    umount /mnt/root/sys
