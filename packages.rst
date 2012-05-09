===================
Installing packages
===================

This section explains the bulk of the installation: downloading and installing
software packages from your distribution's repository.


---------------------------
Initialize the RPM database
---------------------------

To use RPM on the target system, run this command to initialize the RPM database::

    rpm --root=/mnt/root --initdb


----------------------------------------
Download and install the release package
----------------------------------------

The :dfn:`release package`, a package named like ``fedora-release`` or
``centos-release``, contains files that provide information about available
software repositories, and needs to be installed manually.

.. note::

   In the examples below, replace ``fedora-release`` with the correct release
   package name for your distribution, if necessary.

#. Download the release package::

    yumdownloader fedora-release

#. Install the release package::

    rpm --root=/mnt/root --nodeps -ivh fedora-release-*.rpm

Release package names for common distributions
----------------------------------------------

================  ====================
Distribution      Release package name
================  ====================
Fedora            fedora-release
CentOS            centos-release
Scientific Linux  sl-release
================  ====================


---------------------
Install core packages
---------------------

Install a minimal set of packages::

    yum --installroot=/mnt/root install -y rpm yum bash grub passwd initscripts chkconfig

This will install everything necessary to *boot* your system, but it will be
mostly useless. You will probably want to install some of these packages:

- Your text editor of choice, such as ``vim-enhanced``
- ``openssh-server`` and ``openssh-clients``
- ``rsyslog``, to allow programs to write to :file:`/var/log/messages`
- Packages to manage filesystems, such as ``e2fsprogs`` for the ext filesystem series
- ``dhclient``, for getting a DHCP lease on a network
- ``mdadm``, if you are using a RAID
- ``lvm2``, if you are using LVM

.. note::

   The ``kernel`` package is missing from the above list. This is intentional.
   It will be installed after some configuration files are created that the
   package needs to build the initrd.
