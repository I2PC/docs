Requirements
-----------------------
Supported OS
^^^^^^^^^^^^^^^^^^^^

We have tested Xmipp compilation on the following operating systems: Ubuntu 20.04, 22.04 and 24.04 and Centos 7. While compilation and execution might be possible on other systems, it might not be straightforward. 

Hardware requirements
^^^^^^^^^^^^^^^^^^^^

At least 2 processors are required to run Xmipp. In some virtual machine tools only one is assigned, please check that at least two processors are assigned to the virtual machine.

Software dependencies
^^^^^^^^^^^^^^^^^^^^^

Compiler
^^^^^^^^

Xmipp requires C++17 compatible compiler (see table below for minimum versions). We have had good experience with using GCC. Clang is mostly untested. Mind that when compiling with CUDA, a  `compatible compiler <https://gist.github.com/ax3l/9489132>`__ must be installed and findable (although it may not be used for non-CUDA sources) for Xmipp.

.. list-table:: 
   :header-rows: 1
   :widths: 50 50

   * - Compiler
     - Minimum Version
   * - GCC
     - 8.4
   * - Clang
     - 5.0

Cmake
^^^^^

Xmipp requires CMake 3.17 or above.

.. warning::
   Ubuntu 20.04 only supports CMake 3.16.3.  
   If you experience any issues, please install CMake using Conda in the Scipion3 environment:

   .. code-block:: bash

      scipion3 run conda install cmake

Cuda
^^^^

CUDA is optional but highly recommended. By default Xmippp will search your CUDA installation. Xmipp supports Cuda **11.0** through **12.6**. We recommend you to use the newest version available for your operating system. Pay attention to the `compiler - CUDA compatibility <https://gist.github.com/ax3l/9489132>`_.

.. Note::
  As of may 2025, we have officially dropped support for CUDA 10.2. Please make sure to upgrade to a supported CUDA version (11.0 or higher) to ensure compatibility.


To install CUDA for your operating system, follow the `official install guide <https://developer.nvidia.com/cuda-toolkit-archive>`_.

.. warning::
   `CUDA 11.5 is not compatible with GCC - 9 <https://forums.developer.nvidia.com/t/cuda-11-5-samples-throw-multiple-error-attribute-malloc-does-not-take-arguments/192750/12>`_, please change one of these.

Full list of dependencies
^^^^^^^^^^^^^^^^^^^^^^^^^

Before installing Xmipp, you need to ensure your system meets certain requirements. Below is a list of required packages and dependencies.

.. note::
  The next explanations are available on devel and from `Xmipp 3.25.06.0 - Rhea <https://i2pc.github.io/docs/Releases/Releases-scipion-em-xmipp/index.html#rhea>`_


Dependencies Automatically Installed via Scipion
"""""""""""""""""""""""""""""""""""""""""""""""""""

If Xmipp is installed **through Scipion** `with the plugin manager or with the terminal <https://i2pc.github.io/docs/Installation/Installations/index.html#installation-with-scipion>`_ , the following packages will be automatically installed in the Scipion environment by default:

- ``cmake>=3.18,<4``
- ``hdf5>=1.18``
- ``sqlite>=3``
- ``fftw>=3``
- ``make``
- ``zlib``
- ``openjdk``
- ``libtiff``
- ``libstdcxx-ng``
- ``libjpeg-turbo``

.. note::
   This automatic installation is enabled by default. To disable it, set ``default=False`` in `this file <https://github.com/I2PC/scipion-em-xmipp/blob/206832bff698a8eb40ac6b7d7cf5fbb1286d31ef/xmipp3/__init__.py#L177>`_

Manually Required Dependencies
""""""""""""""""""""""""""""""""""""

The following system-level packages **must be installed manually**, as they are not handled by Scipion:

- ``GCC``: C compiler
- ``G++``: C++ compiler
- ``OpenMPI`` development libraries

On **Ubuntu-based** systems, you can install them using:

.. code-block:: bash

   sudo apt install -y gcc g++ libopenmpi-dev

On **YUM-based** systems (e.g., CentOS, RHEL), use:

.. note::
   On CentOS 7, the default GCC version is not compatible with Xmipp. You can enable a newer GCC version using:

.. code-block:: bash

   yum install centos-release-scl
   yum install devtoolset-10
   scl enable devtoolset-10 bash

Then, install the dependencies:

.. code-block:: bash

   yum install gcc gcc-c++ openmpi-devel


These requirements will ensure that your system is ready for installing and using Xmipp. If you encounter a problem, please refer to known and fixed `issues <https://github.com/I2PC/xmipp/issues?q=is%3Aissue>`_. Let us know if something is not working.

