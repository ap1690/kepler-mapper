.. note::
    :class: sphx-glr-download-link-note

    Click :ref:`here <sphx_glr_download_generated_gallery_plot_cat.py>` to download the full example code
.. rst-class:: sphx-glr-example-title

.. _sphx_glr_generated_gallery_plot_cat.py:

3D Cat Data
============


This example generates a Mapper built from a point-cloud sampled from a 3D model of a cat.

`Visualization of the cat mapper <../../_static/cat.html>`_


.. image:: /generated/gallery/images/sphx_glr_plot_cat_001.png
    :class: sphx-glr-single-img


.. rst-class:: sphx-glr-script-out

 Out:

 .. code-block:: none

    KeplerMapper(verbose=2)
    ..Composing projection pipeline of length 1:
            Projections: sum
            Distance matrices: False
            Scalers: MinMaxScaler(copy=True, feature_range=(0, 1))
    ..Projecting on data shaped (7207, 3)

    ..Projecting data using: sum

    ..Scaling with: MinMaxScaler(copy=True, feature_range=(0, 1))

    Mapping on data shaped (7207, 3) using lens shaped (7207, 1)

    Minimal points in hypercube before clustering: 5
    Creating 15 hypercubes.
       > Found 2 clusters in hypercube 0.
       > Found 2 clusters in hypercube 1.
       > Found 2 clusters in hypercube 2.
       > Found 1 clusters in hypercube 3.
       > Found 2 clusters in hypercube 4.
       > Found 2 clusters in hypercube 5.
       > Found 1 clusters in hypercube 6.
       > Found 1 clusters in hypercube 7.
       > Found 1 clusters in hypercube 8.
       > Found 1 clusters in hypercube 9.
       > Found 1 clusters in hypercube 10.
       > Found 1 clusters in hypercube 11.
       > Found 1 clusters in hypercube 12.
       > Found 1 clusters in hypercube 13.
       > Found 1 clusters in hypercube 14.

    Created 19 edges and 20 nodes in 0:00:00.125082.
    Wrote visualization to: output/cat.html




|


.. code-block:: default



    import numpy as np
    import sklearn
    import kmapper as km

    data = np.genfromtxt('data/cat-reference.csv', delimiter=',')

    mapper = km.KeplerMapper(verbose=2)

    lens = mapper.fit_transform(data)

    graph = mapper.map(lens,
                       data,
                       clusterer=sklearn.cluster.DBSCAN(eps=0.1, min_samples=5),
                       cover=km.Cover(n_cubes=15, perc_overlap=0.2))

    mapper.visualize(graph,
                     path_html="output/cat.html")

    km.draw_matplotlib(graph)

    import matplotlib.pyplot as plt
    plt.show()


.. rst-class:: sphx-glr-timing

   **Total running time of the script:** ( 0 minutes  0.530 seconds)


.. _sphx_glr_download_generated_gallery_plot_cat.py:


.. only :: html

 .. container:: sphx-glr-footer
    :class: sphx-glr-footer-example



  .. container:: sphx-glr-download

     :download:`Download Python source code: plot_cat.py <plot_cat.py>`



  .. container:: sphx-glr-download

     :download:`Download Jupyter notebook: plot_cat.ipynb <plot_cat.ipynb>`


.. only:: html

 .. rst-class:: sphx-glr-signature

    `Gallery generated by Sphinx-Gallery <https://sphinx-gallery.readthedocs.io>`_
