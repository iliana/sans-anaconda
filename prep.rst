======================================
Preparing your system for installation
======================================

Back up your data
=================

This ought to be a no-brainer, but it doesn't hurt to have a reminder. If you
have any data on the system you wish to keep, move it to external storage (such
as DVD backup, external hard drive, or network server).

Do not trust that you or the tools you will be using will keep important data
intact.


Start the machine
=================

With a Live CD
--------------

#. If you are using a Live CD, insert the media into the system and, if
   necessary, configure your BIOS to boot from it.

#. A screen should appear which displays a message similar to
   :guilabel:`Automatic boot in 10 seconds...`. At this screen, press :kbd:`Tab`.

#. Use the arrow keys to select :guilabel:`Boot`, then press :kbd:`Tab` to edit
   options. A list of `kernel parameters`_ should appear.

#. Add :kbd:`3 selinux=0` to this list of parameters. This instructs the
   operating system to not start a graphical user interface and to disable
   SELinux.

   .. note::

      If you are having trouble with your installation, remove ``quiet`` from
      the kernel parameters, or check :file:`/var/log/messages` and
      :command:`dmesg`.

   .. note::

      It is generally not recommended to disable SELinux on a system. This
      guide cannot, however, assume that installing with SELinux turned on will
      work on all platforms with all package sets. For more information, see
      :ref:`not-included-here`.

#. Press :kbd:`Enter` to start the system. When the system is done starting, a
   message similar to the following will display::

    Distribution Name version 1.0 (Release name)
    Kernel 2.6.32-123.4.5.el6.x86_64 on an x86_64

#. Log in with the username :kbd:`root`. You should not be prompted for a
   password. If you are, check your distribution's documentation for details.

.. _kernel parameters: http://www.kernel.org/doc/Documentation/kernel-parameters.txt

With another installation
-------------------------

Boot your system and log in. You will need root privileges to install the
operating system on another device.
