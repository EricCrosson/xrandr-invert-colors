XRandR Invert Colors
====================

Simple utility that inverts colors on all screens, using XrandR.

Ansible installation
--------------------

Run the ansible playbook to install::

    ansible-playbook site.yml -e 'target=localhost'

Note that this method of installation provides a quick way to invoke
:code:`xrandr-invert-colors`::

    inv

If :code:`xbindkeys` is running, :code:`Alt + F11` will invoke this utility.

Manual installation
-------------------

Dependencies
~~~~~~~~~~~~

-  XrandR development files (``apt-get install libxcb-randr0-dev``)
-  Type ``sudo make deps-apt`` on Debian / Ubuntu

Build
~~~~~

-  From a terminal, type ``make``

Install
~~~~~~~

Execute ``sudo make install`` after build to put the binary in the
following location: + ``/usr/local/bin/xrandr-invert-colors``

Use
---

Run ``xrandr-invert-colors.bin`` for inverting colors on all screens.
The follwing program option is implemented:

-  ``-s <crtc_number>`` : Instead of inverting all screens, invert only
   the colors of the screen identified by ``<crtc_number>``.
-  ``--help`` and ``-h`` : Print a short help for the program.
-  ``--version`` : Print a (dummy) version information.
-  ``-d`` : Enables debug log on standard output. Prints diagonstic
   messages.

Hint: put the executable in the a directory listed in $PATH, and bind
the execution of ``xrandr-invert-colors.bin`` to a shortcut key.

Achknowledgements
-----------------

Redshift developers, for creating the XRandR gamma setting code. Their
code is reused in this application. http://jonls.dk/redshift/
https://launchpad.net/redshift

Zoltanp for the original xrandr-invert-colors_ repo.

.. _xrandr-invert-colors: https://github.com/zoltanp/xrandr-invert-colors

Alternatives
------------

-  ``xcalib -i -a`` : Inverts the colors of the current screen.
-  Note that as of date of last testing (2014, xcalib version 0.8)
   xcalib has not been able to invert the colors on all monitors in a
   multi-monitor setup, because all monitors are presented by the X11
   server as a single screen. Thus this limitation is coming from the
   X11 server. ``xrandr-invert-colors`` does not have this limitation,
   because it uses XRandR API, which correctly handles all attached
   monitors.

License
-------

GNU GPL v3
