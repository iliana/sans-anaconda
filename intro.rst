============
Introduction
============

A friend and I started developing this procedure when we were attempting to
install CentOS on a machine. Our requirements were:

- Minimal package set to fit the / partition in about 2 GB and still have room
  to grow
- A single XFS filesystem on a hybrid RAID 0/RAID 5 layout of 8 disks (don't
  ask)
- Ability to do all of this with a graphics card that the installer didn't
  support

Recently before this the Anaconda team decided (correctly) that it was
extremely difficult to maintain the partition manager for both the graphical
and text installers, so the text installer lost quite a bit of functionality.
Additionally, Anaconda had zero support for XFS.

After about 15 hours of messing around, we finally ended up with a working
installation that did what we wanted and a sparse set of documentation on how
to do it again. About a year later, we had a fairly complete document on how to
do the installation for RHEL 6 or similar systems.

This document is an attempt to flesh out the above into something more than a
sparse how-to that provides a reference for years of different versions of RHEL
and Fedora.


Who this manual is for
======================

While this manual was written to be very straightforward and provide everything
necessary to do a sans-Anaconda install, it's not for the faint of heart. Users
of this manual should have some pretty solid experience with RPM_ and Yum_,
command-line partitioning systems, creating and using filesystems, and the
`GRUB bootloader`_.

.. _RPM: http://en.wikipedia.org/wiki/RPM_Package_Manager
.. _Yum: http://en.wikipedia.org/wiki/Yellowdog_Updater,_Modified
.. _GRUB bootloader: http://www.gnu.org/software/grub/


.. _not-included-here:

What this manual won't tell you
===============================

To make this guide simpler, we decided against including some tasks in the
installation process. Some of these may be added later (possibly by you --- see
:ref:`halp`).

Installing Red Hat Enterprise Linux
-----------------------------------

We don't recommend installing Red Hat Enterprise Linux (RHEL) using this
process for a few reasons:

- RHEL makes it relatively difficult to get copies of their binary packages
  without configuring your system properly.
- Anaconda is the only supported installer for RHEL.

Please don't try to call Red Hat for support for a system you installed without
using Anaconda. It will be a bad situation for everybody involved.

.. note::

   This section talks about RHEL --- the version Red Hat releases. RHEL
   rebuilds such as CentOS and Scientific Linux work well with this process.

Installing SELinux
------------------

We have had quite a bit of trouble getting this process to behave with
`SELinux`_. Our manual instructs you to disable SELinux when installing and not
install SELinux on the target system.

Running SELinux is *highly* recommended on production systems. If you are
building a system for `serious business`_, please don't use this installation
method. Something will probably break, and it won't be our fault.

.. _SELinux: http://selinuxproject.org/
.. _serious business: http://knowyourmeme.com/memes/the-internet-is-serious-business

Installing a graphical environment
----------------------------------

After trying for quite a bit and spending countless nights reading
documentation and reinstalling an operating system, we haven't been able to get
a solid list of packages that provides a basic graphical environment. If you
know the answer, :ref:`please let us know <halp>`!


.. _halp:

We want your help!
==================

If you know additional information that you think would be a great addition to this manual, please let us know.

This manual is `hosted on GitHub`_. For those with experience in writing
reStructuredText_ and who can provide a patch for this manual, feel free to
send a pull request. For the rest, you can open an issue and provide content
there.

.. _hosted on GitHub: https://github.com/ianweller/sans-anaconda
.. _reStructuredText: http://docutils.sourceforge.net/rst.html
