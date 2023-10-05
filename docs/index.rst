.. figure:: ../_static/images/xmipp_noBackground.png
   :alt: xmipp logo
   :width: 400

Welcome to Xmipp documentation!
========================================
Xmipp is a suite of image processing programs, primarily aimed at single-particle 3D electron microscopy, 
designed and managed by the `Biocomputing Unit <http://biocomputingunit.es/>`_ located in Madrid, Spain.

The Xmipp project is divided into four repositories: `xmipp <https://github.com/I2PC/xmipp>`_, `xmippCore <https://github.com/I2PC/xmipp>`_, `scipion-em-xmipp <https://github.com/I2PC/scipion-em-xmipp>`_ and `xmippVix <https://github.com/I2PC/xmippViz>`_,  are automatically downloaded during the installation process.

Getting started
----------------
The recommended way for users (not developers) to install and use Xmipp is via the Scipion framework, where you can use Xmipp with other Cryo-EM-related software. Xmipp will be installed during Scipion installation (pay attemption on the -noXmipp flag). The Scipion installer should take care of all dependencies for you, however, you can make its life easier if you have your compiler, CUDA and HDF5 library ready and available in the standard paths. Read the installation page for more details about these softwares requirements. Follow the official installation guide of Scipion for more details.

.. _XmippField:
      :maxdepth: 1
    :hidden:
    :caption: _XmippField

    XmippField/Releases-scipion-em-xmipp/index
    XmippField/Releases-xmipp-program/index


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
    

  .. toctree::
    :maxdepth: 1
    :hidden:
    :caption: Others
    
    contact
    license
    listOfPublications
