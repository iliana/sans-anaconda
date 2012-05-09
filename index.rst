The Sans-Anaconda Install
=========================

Anaconda_ is the installer for Fedora_ and `Red Hat Enterprise Linux`_ (and
their derivatives_). For a normal installation, it works well. But sometimes
you need to do something a little more insane.

For power users, doing a manual installation can sometimes be the right answer
if Anaconda doesn't support your disk layout or if you want an excessively
minimal installation.

This document contains the process for installing many Red Hat-like
distributions manually, as well as some discussion on whether or not to install
Linux like this.

.. _Anaconda: https://fedoraproject.org/wiki/Anaconda
.. _Fedora: http://fedoraproject.org/
.. _Red Hat Enterprise Linux: http://www.redhat.com/products/enterprise-linux/
.. _derivatives: http://en.wikipedia.org/wiki/Fedora_(operating_system)#Derivatives

Contents
--------

.. toctree::
   :maxdepth: 2

   intro
   prereq
   prep
   partformat
   packages
   configure
   bootloader
   reboot
   gfdl

Copyright and license
---------------------

Copyright 2012 Ian Weller and others. All rights reserved.

This document is licensed under both of the following licenses:

    Permission is granted to copy, distribute and/or modify this document under
    the terms of the GNU Free Documentation License, Version 1.3 or any later
    version published by the Free Software Foundation; with no Invariant
    Sections, no Front-Cover Texts, and no Back-Cover Texts. A copy of the
    license is included in the section entitled ":ref:`gfdl`".

    This work is licensed under the Creative Commons Attribution-ShareAlike 3.0
    Unported License. To view a copy of this license, visit
    http://creativecommons.org/licenses/by-sa/3.0/.

You may select the license of your choice.

Document history
----------------

Version 0.1, May 8, 2012
  First manual-like version, written for ENGL 362 at the University of Kansas.

Version 0.0, date unknown
  Two plain-text files containing slightly-annotated instructions for
  installing Scientific Linux 6.0 and Fedora 16.
