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

Before installing Xmipp, you need to ensure that your system meets certain requirements. Here are the necessary packages and dependencies:

- `GCC`: `compiler <https://i2pc.github.io/docs/Installation/Requirements/index.html#compiler>`_ for C
- `GXX`: `Compiler <https://i2pc.github.io/docs/Installation/Requirements/index.html#compiler>`_ for C++
- `libfftw3-dev`: FFTW3 library development files.
- `libopenmpi-dev`: OpenMPI development files.
- `libhdf5-dev`: HDF5 library development files.
- `python3-numpy`: NumPy library for Python 3.
- `python3-dev`: Python 3 development headers.
- `libtiff5-dev`: LibTIFF development files.
- `libsqlite3-dev`: SQLite3 development files.
- `default-jdk`: Default Java Development Kit.
- `git`: Version control system for source code management.
- `cmake`: Cross-platform build system.
- `libjpeg-dev`: Compress, decompress, transform JPEG images.


You can install these packages on **Ubuntu-based** systems using the following command:

.. Note::
    The the installation of the compiler is not included in the next command

.. code-block:: bash

   sudo apt install -y libfftw3-dev libopenmpi-dev libhdf5-dev python3-numpy python3-dev libtiff5-dev libsqlite3-dev default-jdk git cmake libjpeg-dev



Installing dependencies via **yum**

.. Note::
    Note: For HDF5 to be available Extra Packages for Enterprise Linux (EPEL) repository needs to be activated in certain distros with yum install epel-release

.. Note::
    Note: On CentOS-7 the gcc available by default is not compatible with Xmipp. You can enable newer gcc releases using:

.. code-block:: bash
    
    yum install centos-release-scl

    yum install devtoolset-10

    scl enable devtoolset-10 bash

.. code-block:: bash

  yum install python3-devel python3-numpy fftw-devel openmpi-devel hdf5-devel sqlite-devel libtiff-devel libjpeg-turbo-devel java-17-openjdk-devel git cmake gcc g++


These requirements will ensure that your system is ready for installing and using Xmipp. If you encounter a problem, please refer to known and fixed `issues <https://github.com/I2PC/xmipp/issues?q=is%3Aissue>`_. Let us know if something is not working.

