Requirements
------------

Supported OS
^^^^^^^^^^^^

Xmipp has been tested on the following operating systems:

- **Ubuntu**: 18.04, 20.04, 22.04, 24.04
- **CentOS**: 7

Other Linux systems may work but are not officially supported. Compilation and execution might not be straightforward.

Hardware requirements
^^^^^^^^^^^^^^^^^^^^^

- At least **2 CPU cores** are required.  
- On some virtual machine tools only one is assigned by default. Please check and ensure at least two processors are assigned.

Software dependencies
^^^^^^^^^^^^^^^^^^^^^

Compiler
^^^^^^^^

Xmipp requires a **C++17 compatible compiler**. We only officially support GCC and we require **GCC >= 9**

Some users have reported successfully compiling xmipp with Clang >= 5.0 but is not officialy supported

.. note::
   If compiling with CUDA, a `compatible compiler <https://gist.github.com/ax3l/9489132>`_ must be available.

CMake
^^^^^

Xmipp requires **CMake >= 3.18 and < 4**.

CUDA (optional)
^^^^^^^^^^^^^^^

By default, Xmipp attempts to automatically detect a CUDA installation. Manual configuration is possible if needed. 

To activate/deactivate CUDA compilation:
- XMIPP_USE_CUDA (xmipp.conf)
- XMIPP3_XMIPP_USE_CUDA (environment)

To specify the CUDA compiler (nvcc):
- CMAKE_CUDA_COMPILER (xmipp.conf)
- XMIPP_CUDA_BIN (`Scipion configuration file <https://scipion-em.github.io/docs/release-3.0.0/docs/scipion-modes/scipion-configuration.html>`_)
- XMIPP3_CMAKE_CUDA_COMPILER (environment)

To define a specific host compiler:
- CMAKE_CUDA_HOST_COMPILER (xmipp.conf)
- XMIPP3_CMAKE_CUDA_HOST_COMPILER (environment)

To manually set CUDA libraries path:
- XMIPP_CUDA_LIB (`Scipion configuration file <https://scipion-em.github.io/docs/release-3.0.0/docs/scipion-modes/scipion-configuration.html>`_)

Refer to the `configuration page <https://i2pc.github.io/docs/Utils/ConfigurationF/index.html#configuration-file>`_ for additional details.


- Supported versions: **11.0 – 12.9**
- We recommend using the newest version available for your operating system.
- Installation guide: `CUDA Toolkit Archive <https://developer.nvidia.com/cuda-toolkit-archive>`_
- CUDA - compiler compatibility (`reference <https://stackoverflow.com/questions/6622454/cuda-incompatible-with-gcc-version>`_)

.. list-table:: 
   :header-rows: 0
   :widths: 50 50

   * - CUDA version
     - Max supported GCC version
   * - 12.8, 12.9
     - 14
   * - 12.4, 12.5, 12.6
     - 13.2
   * - 12.1, 12.2, 12.3
     - 12.2
   * - 12
     - 12.1
   * - 11.4.1+, 11.5, 11.6, 11.7, 11.8
     - 11
   * - 11.1, 11.2, 11.3, 11.4.0
     - 10
   * - 11
     - 9


.. warning::

   CUDA 11.5 is not compatible with GCC 9. Please change one of them if you encounter errors.


HDF5 
^^^^^^^^^^^^^^^
Scipion requires the HDF5 library. When using the default **Scipion Conda environment**, HDF5 is installed automatically from *conda-forge*. By default, this pulls the **latest available version** of HDF5. Versions **newer than 1.12** require **GCC 13 or newer** to be available on the system. If the system compiler is older, this may lead to compilation or runtime errors.

For this reason, it is **recommended to explicitly install a compatible HDF5 version** inside the Scipion Conda environment:

.. code-block:: bash

   scipion3 run conda install conda-forge::hdf5==1.12.2

This version is known to be compatible with older GCC compilers commonly found on supported Linux distributions.

Dependencies
^^^^^^^^^^^^

The following packages must be installed before building Xmipp:

- ``gcc``, ``g++`` — C and C++ compilers
- ``cmake (>=3.18,<4)`` — cross-platform build system
- ``git`` — version control system
- ``zlib`` — compression library
- ``fftw (>=3)`` — FFT library
- ``hdf5 (1.8 <= version <=1.12.2)`` — HDF5 library
- ``openmpi`` development libraries
- ``sqlite (>=3)`` — SQLite database
- ``libtiff`` — TIFF image support
- ``libjpeg`` — JPEG support (Ubuntu: ``libjpeg-dev`` / RHEL: ``libjpeg-turbo-devel``)
- ``openjdk (<=11)`` — Java Development Kit
- ``python3-dev`` and ``python3-numpy`` — Python 3 development headers and NumPy

Installing dependencies
^^^^^^^^^^^^^^^^^^^^^^^

Ubuntu/Debian
"""""""""""""

.. code-block:: bash

   sudo apt install -y gcc g++ cmake git libfftw3-dev libopenmpi-dev libhdf5-dev libtiff5-dev libsqlite3-dev libjpeg-dev python3-dev python3-numpy default-jdk zlib1g-dev

CentOS/RHEL
"""""""""""

.. note::
   On CentOS 7, the default GCC version is not compatible with Xmipp.  
   You can enable a newer GCC version with:

   .. code-block:: bash

      yum install centos-release-scl
      yum install devtoolset-10
      scl enable devtoolset-10 bash

.. note::
   On some RHEL-based systems, HDF5 may require enabling the **EPEL** repository:

   .. code-block:: bash

      yum install epel-release

Install dependencies with:

.. code-block:: bash

   yum install -y gcc gcc-c++ cmake git fftw-devel openmpi-devel hdf5-devel libtiff-devel sqlite-devel libjpeg-turbo-devel python3-devel python3-numpy java-11-openjdk-devel zlib-devel

Final notes
^^^^^^^^^^^

These requirements will ensure your system is ready to build and run Xmipp.  
If you encounter problems, please check known `issues <https://github.com/I2PC/xmipp/issues?q=is%3Aissue>`_ or report a new one.