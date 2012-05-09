==============================
Prerequisites for installation
==============================

You will need these for your installation:

- A Live CD or another installation of *the same version* of the distribution
  to install
- A working internet connection to your target machine or a local mirror of
  your distribution

.. note::

   If you plan to do a lot of sans-Anaconda installations with the same
   distribution, having a local mirror will prevent you from downloading the
   same data over and over again for each installation.


Why a Live CD?
==============

In order for this to work, you need to already be running the distribution of
your choice. The standard Anaconda installer image boots into a limited
environment with the sole purpose of starting Anaconda and providing a minimal
debug shell that doesn't provide all the tools needed.

Some distributions don't have a Live CD. The recommended way of handling this
is to install from a computer that already has your target distribution
installed. In general, you can get around this by finding a Live CD from a
distribution very similar to the one you plan to install.


Downloading and using a Live CD
===============================

Googling the distribution's name with "live" appended to it should make it
fairly clear where to find a Live CD image. This image should have an `.iso`
extension.


Using a Live USB
----------------

If your motherboard supports it and you have a USB drive, you can boot from
that drive. For modern Live CD images, you can use a command similar to the
following as root::

    dd if=path/to/Live-CD.iso of=/dev/sdX

.. warning::

   The above command will destroy information on a USB drive.

Check the documentation for your distribution for more information about using
a Live USB.
