==========================
Mount Google Drive from CU
==========================

Install:
********

Reference : `globus for linux <https://docs.globus.org/how-to/globus-connect-personal-linux>`_

Install the google drive app from opam::

   opam init
   # Answer y to question then
   eval `opam config env`
   opam install google-drive-ocamlfuse

   mkdir /home/$(whoami)/google_drive

The last step, requires X11 forwarding available (use ssh -Y server) within
the campus. It will open firefox remotely on the server (painfully slow). 
Don't try this at home, connection behind vpn is even slower...::

   google-drive-ocamlfuse /home/$(whoami)/google_drive


log in with your university email/password, authorize,...
and you're all set!

Usage:
******

Your linux system will interact with your google drive like a local disk.

Troubleshooting:
****************

If your command line freezes on ls $HOME or similar. You need to ask admin
to unmount::

   sudo umount -f /home/$(whoami)/google_drive

then you can remount the drive::

   google-drive-ocamlfuse /home/$(whoami)/google_drive
