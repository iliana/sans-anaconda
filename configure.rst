======================
Configuring the system
======================

.. note::

   Remember to prepend each filename with where you mounted your target system,
   such as :file:`/mnt/root`.

-------------------------------------
Filesystem table (:file:`/etc/fstab`)
-------------------------------------

:file:`fstab`, the filesystem table, lists the filesystems to be mounted at
boot time.

The most sane way to list filesystems is by UUID. Run :command:`blkid` to get a
list of block devices and the type of filesystem they have on them. The output
will look similar to this::

    /dev/sda2: UUID="fc5e44f4-84c1-4304-9a48-2ad1a7eadba7" TYPE="swap" 
    /dev/sda1: UUID="c843b959-6fbd-499c-8167-6171192f10f1" TYPE="ext4" 
    /dev/sda3: UUID="7946c131-b7e9-4fba-922f-de99e460542f" TYPE="ext4" 

Given output like the above, write this to :file:`/mnt/root/etc/fstab`::

    UUID=c843b959-6fbd-499c-8167-6171192f10f1       /boot   ext4    defaults        1 1
    UUID=fc5e44f4-84c1-4304-9a48-2ad1a7eadba7       swap    swap    defaults        1 2
    UUID=7946c131-b7e9-4fba-922f-de99e460542f       /       ext4    defaults        0 0

If your distribution's init daemon is not systemd (any distribution that is not
Fedora 15 or later), you will need to add these lines to
:file:`/mnt/root/etc/fstab`::

    tmpfs           /dev/shm        tmpfs   defaults        0 0
    devpts          /dev/pts        devpts  gid=5,mode=620  0 0
    sysfs           /sys            sysfs   defaults        0 0
    proc            /proc           proc    defaults        0 0

For more information, see the `fstab(5)`_ man page.

.. _fstab(5): http://linux.die.net/man/5/fstab


--------------------------------------------
RAID configuration (:file:`/etc/mdadm.conf`)
--------------------------------------------

If you are using RAID, you will need to write :file:`/mnt/root/etc/mdadm.conf`.

Here is a general-purpose :file:`mdadm.conf` written by some releases of
Anaconda::

    MAILADDR root
    AUTO +imsm +1.x -all

For more information, see the `mdadm.conf(5)`_ man page.

.. _mdadm.conf(5): http://linux.die.net/man/5/mdadm.conf


---------------------------------------------
LVM configuration (:file:`/etc/lvm/lvm.conf`)
---------------------------------------------

If you are using LVM, you will need to write
:file:`/mnt/root/etc/lvm/lvm.conf`.

For more information, see the `lvm.conf(5)`_ man page.

.. _lvm.conf(5): http://linux.die.net/man/5/lvm.conf


-----------------------------------------------
Timezone configuration (:file:`/etc/localtime`)
-----------------------------------------------

To set the system timezone, copy a zoneinfo file from
:file:`/usr/share/zoneinfo` to :file:`/etc/localtime`. For example, someone in
the US/Central timezone would run::

    cp /mnt/root/usr/share/zoneinfo/US/Central /mnt/root/etc/localtime


----------------------------------------------
Copy standard files to the root home directory
----------------------------------------------

:file:`/etc/skel` contains standard files to be placed in home directories for
users that are able to log in. Because the root user is not created with the
:command:`useradd` command, these files are not placed in root's home
directory.

To do so, run::

    rsync -avp /mnt/root/etc/skel/ /mnt/root/root/

For more information on :file:`/etc/skel`, see http://www.linfo.org/etc_skel.html.


---------------------
Set the root password
---------------------

.. note::

   If the root password is not set, you will not be able to log in to the
   target system.

#. Enter a chroot under :file:`/mnt/root`::

    chroot /mnt/root

#. Run :command:`passwd`::

    passwd root

#. Set the root password. You will be asked to confirm it after typing it once
   to make sure you didn't make any mistakes in typing it.

#. Exit the chroot by typing :command:`exit` or pressing :kbd:`Control-D`.


------------------------------
Install the ``kernel`` package
------------------------------

After the above is complete, install the ``kernel`` package::

    yum --installroot=/mnt/root install -y kernel
