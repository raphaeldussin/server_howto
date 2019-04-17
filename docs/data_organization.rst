=================
Data Organization
=================

1. home: to keep your light weight & precious files (codes, scripts, figures,...)

2. workspace: for all personal data files (post-processing runs, diagnostics,...)
   It can be accessed at::
       /local/data/<server>/workspace/<username>

   Or by using the corresponding environment variable::

       cd $workspace

3. Observations: if you download, regrid, process,... observations into a dataset that
   can be useful to others. Please contact admin to move it to the shared space located at::

       /local/data/<server>/observations

   Quick access with::

       cd $observations

4. Simulations: model inputs/outputs from the group valuable (published, in prep.) experiments,
   as well as reference experiments from others group (NCAR, GFDL,...) that are of
   common interest should be moved to::

       /local/data/<server>/simulations

   Quick access with::

       cd $simulations

Discover data with intake:
**************************

You can explore the datasets available using intake catalogs available here::

   /local/data/<server>/catalogs

For example, exploring ASTE data inside python can be done with:

.. code-block:: python

    import intake
    catalog = intake.Catalog('/local/data/artemis/catalogs/ASTE_catalog.yml')
    list(catalog)

Once you have found the dataset you're interested in, you can load as follows:

.. code-block:: python

   ds_biomes = catalog.Biomes_FayMcKinley.to_dask()

   import matplotlib.pylab as plt
   ds_biomes.MeanBiomes.sel(face=4).plot()
   plt.show()

