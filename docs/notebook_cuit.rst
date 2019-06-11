=========================================
Running jupyter notebook on CUIT machines
=========================================

Foreword: this is best run in a "screen" (virtual terminal) session.
See https://linuxize.com/post/how-to-use-linux-screen/ for details.

First, we need to get a compute node allocated for our notebook, either from the global pool::

  salloc -N 1 -A ocpbgc --exclusive

or from our own::

  salloc -N 1 -A ocpbgc -p ocpbgc --exclusive

You can ask for more than one node (-N 2 for 2 nodes,...). Once our node is allocated we can
activate our conda environment::

  source activate myenv
  
We also need to disable this environment variable::

  unset XDG_RUNTIME_DIR
  
And find the ip of the node::

  export ip=$( srun hostname -i )

Note the ip address, will be refered to <nodeip> below.

Now we can start the notebook (here I start it in my workspace, not home directory)::

  srun jupyter notebook --no-browser --ip=$ip --notebook-dir=/rigel/ocpbgc/users/$whoami

The notebook should be running on port 8888. If not adapt the next items to the current port.
Leave this terminal alone, or detach the screen session. In a new terminal, we're gonna create
a tunnel to the 8888 port of the compute node to the 8010 port of our workstation/laptop, bouncing off
the login node (e.g. habanero)::

  ssh -L 8010:<nodeip>:8888 <name_of_login_node>
  
In your web browser, type::
 
  localhost:8010
  
And you should be connected to your notebook.
