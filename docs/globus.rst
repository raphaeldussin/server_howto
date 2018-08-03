======
Globus
======

Install:
********

Reference : `globus for linux <https://docs.globus.org/how-to/globus-connect-personal-linux>`_

Install the globus client::

    wget https://downloads.globus.org/globus-connect-personal/linux/stable/globusconnectpersonal-latest.tgz
    tar xzf globusconnectpersonal-latest.tgz
    cd globusconnectpersonal-2.3.5/ 

Contrary to what the reference says, we could not create the endpoint in command line.
Instead log into the globus website. Go to "Endpoints", then "add Globus Connect Personal endpoint",
enter <server_name> in the 'Display name' box and press 'Generate Setup Key". Save the key to clipboard then
go back to terminal and run:: 

    ./globusconnectpersonal -setup <setup_key_from_clipboard>

And you're all set!

Usage:
******

Some useful globus commands::

    ./globusconnectpersonal -help
    ./globusconnectpersonal -start 
    ./globusconnectpersonal -stop
    ./globusconnectpersonal -status

By default, globus access only your home directory.
To allow globus to access your workspace::

./globusconnectpersonal -restrict-paths /local/data/<server_name>/workspace/$(whoami) -start
