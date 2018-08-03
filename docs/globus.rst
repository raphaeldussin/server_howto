======
GLOBUS
======

start with instructions from : https://docs.globus.org/how-to/globus-connect-personal-linux/

wget https://downloads.globus.org/globus-connect-personal/linux/stable/globusconnectpersonal-latest.tgz
tar xzf globusconnectpersonal-latest.tgz
cd globusconnectpersonal-2.3.5/ # or ulterior (time dependent)

# this section of the doc doesn't work
# ./globus endpoint create --personal artemis_ldeo

# insteead log into the globus website, go to "Endpoints", then "add Globus Connect Personal endpoint",
# enter artmis_ldeo in 'Display name' box and press 'Generate Setup Key", save the key to clipboard then
# go back to terminal and run : 

./globusconnectpersonal -setup <setup_key_from_clipboard>

# and that's it!

# Useful globus commands :

./globusconnectpersonal -start 
./globusconnectpersonal -help
./globusconnectpersonal -stop
./globusconnectpersonal -status

# To allow globus to access your workspace :

./globusconnectpersonal -restrict-paths /local/data/artemis/workspace/$(whoami) -start
