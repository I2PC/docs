.. figure:: ../_static/images/xmipp_noBackground.png
   :alt: xmipp logo
   :width: 400

Welcome to Xmipp documentation!
========================================
Xmipp is a suite of image processing programs, primarily aimed at single-particle 3D electron microscopy, 
designed and managed by the `Biocomputing Unit <http://biocomputingunit.es/>`_ located in Madrid, Spain.

The Xmipp project is form by the xmipp programs, mainly written in C++, the scipion-em-xmipp plugin,
 where all the protocols of SPA  are located and the scipion-em-xmippTomo plugin, 
 where all the protocols of tomography are located . 

Getting started
----------------
The recommended way for users (not developers) to install and use Xmipp is via the `Scipion framework <https://scipion-em.github.io/docs/release-3.0.0/docs/scipion-modes/how-to-install.html>_`, where you can use Xmipp with other Cryo-EM-related software. Xmipp will be installed during Scipion installation (pay attemption on the -noXmipp flag). The Scipion installer should take care of all dependencies for you, however, you can make its life easier if you have your compiler, CUDA and HDF5 library ready and available in the standard paths. Read the installation page for more details about these softwares requirements. Follow the official installation guide of Scipion for more details.




.. _Installation-docs:

.. toctree::
    :maxdepth: 1
    :hidden:
    :caption: Installation

    Installation/Installation-with-Scipion/index
    Installation/Requirements/index
    Installation/Standlone-installation/index

.. _Utils-docs:

  .. toctree::
    :maxdepth: 1
    :hidden:
    :caption: Utils

    Utils/Deprecating-programs-and-protocols/index
    Utils/List-deprecated/index

.. _Developers-docs:

  .. toctree::
    :maxdepth: 1
    :hidden:
    :caption: Developers

    Developers/Checkout-specific-date/index
    Developers/How-to-release/index
    
.. _Releases-docs:

  .. toctree::
    :maxdepth: 1
    :hidden:
    :caption: Releases

    Releases/Releases-xmipp-program/index
    Releases/Releases-scipion-em-xmipp/index
    Releases/Releases-scipion-em-xmippTomo/index


  .. toctree::
    :maxdepth: 1
    :hidden:
    :caption: Others
    
    listOfPublications
    contact
    license
