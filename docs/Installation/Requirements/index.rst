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

CUDA is optional but highly recommended. By default, Xmipp will search for your CUDA installation.  

- Supported versions: **11.0 – 12.9**
- We recommend using the newest version available for your operating system.
- Installation guide: `CUDA Toolkit Archive <https://developer.nvidia.com/cuda-toolkit-archive>`_

.. warning::
   CUDA 11.5 is not compatible with GCC 9. Please change one of them if you encounter errors.

Dependencies
^^^^^^^^^^^^

The following packages must be installed before building Xmipp:

- ``gcc``, ``g++`` — C and C++ compilers
- ``cmake (>=3.18,<4)`` — cross-platform build system
- ``git`` — version control system
- ``zlib`` — compression library
- ``fftw (>=3)`` — FFT library
- ``hdf5 (>=1.18)`` — HDF5 library
- ``openmpi`` development libraries
- ``sqlite (>=3)`` — SQLite database
- ``libtiff`` — TIFF image support
- ``libjpeg`` — JPEG support (Ubuntu: ``libjpeg-dev`` / RHEL: ``libjpeg-turbo-devel``)
- ``openjdk (>=11)`` — Java Development Kit
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