Boot related globalvars are reverted after booting
--------------------------------------------------

``global.bootm.*``, ``global.linux.*``, ``global.of.*`` and
``global.boot.watchdog_timeout`` are now snapshotted before each boot
entry and each bootm and restored afterwards, so changes made while
booting no longer leak into subsequent boot attempts.

Boot entries therefore no longer need to put Kernel command line options
into ``global.linux.bootargs.dyn.*``. The boot entries shipped with
barebox have dropped the ``.dyn`` infix. As the bootargs variables are
concatenated in lexicographical order, the order of the Kernel command
line options may change.
