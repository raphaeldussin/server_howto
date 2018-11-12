=================================
Setting up your conda environment
=================================

To install your custom packages, you need to create a personal conda environment on the server.
In this example, I show how I created my development environment.

Log into the server with ssh and load anaconda::

    module load anaconda3

Create your personal conda environment, here I choose to name it dev (how original!)
and clone the packages already installed in the default environment::

    conda create --name dev --clone root

Activate your newly created environment::

    source activate dev

Install the packages you want (for example Ryan's excellent `xgcm <https://xgcm.readthedocs.io>`_)
into your environment. (NB: you can't install new packages in the default environment)::

    conda install -c conda-forge xgcm

To use your conda environment in the server's jupyterhub,
install the ipython kernel for your conda environment::

    conda install ipykernel
    python -m ipykernel install --user --name dev --display-name "Python3 (dev,raf)"

The argument for ``--name`` must correspond to the environment name (e.g. dev).
Display-name is how the environment will be shown in jupyterhub.
You only need to do this once for this environment and it will become visible in jupyterhub,
in the rolling list under **New**. If you create a new environment, just repeat the entire process.

