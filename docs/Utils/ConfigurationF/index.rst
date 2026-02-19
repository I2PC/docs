Configuration File
========================

The Xmipp configuration file is generated at the beginning of the installation process. This file is responsible for loading the necessary libraries and setting up environment variables for Xmipp. To generate a new configuration file, use the following command:

.. code-block:: bash

  ./xmipp config

To edit this file, navigate to the folder where Xmipp is installed. By default, this is located at scipion3/software/em/xmippSrc-3.24.12-Poseidon or a similar path. For development purposes, the folder name may differ. Once inside the directory, locate and edit the xmipp.conf file based on the information provided here. If the file does not exist, generate a new one.

After editing the file:

- If you are installing Xmipp with Scipion, run:

.. code-block:: bash
  
  scipion3 run ./xmipp


- Otherwise, simply run:

.. code-block:: bash

  ./xmipp


.. note::

   To edit any of the variables in the xmipp.conf file you can also set the variable 
   in the environment adding 'XMIPP3_' as name of the variable. For example::

       export XMIPP3_XMIPP_USE_CUDA='OFF'

   After that just run::

       ./xmipp config




xmipp.conf description
----------------------------
This section describes the variables in the Xmipp configuration file and their purpose.

Toggle Section
^^^^^^^^^^^^^^^^^^^^
These options allow activating or deactivating specific software functionalities.

- **SEND_INSTALLATION_STATISTICS**: Enables (`ON`) or disables (`OFF`) the sending of installation statistics.
- **XMIPP_USE_CUDA**: Enables (`ON`) or disables (`OFF`) the use of CUDA to accelerate calculations via GPU.
- **XMIPP_USE_MPI**: Enables (`ON`) or disables (`OFF`) the use of MPI for distributed parallelism.
- **XMIPP_USE_MATLAB**: Enables (`ON`) or disables (`OFF`) the use of functionalities related to MATLAB.
- **XMIPP_LINK_TO_SCIPION**: Enables (`ON`) or disables (`OFF`) linking Xmipp with the Scipion framework.
- **BUILD_TESTING**: Enables (`ON`) or disables (`OFF`) the building of automated tests to verify software integrity.
- **CMAKE_SKIP_RPATH**: Enables (`ON`) or disables (`OFF`) excluding `rpath` during the compilation process.

Package Home Section
^^^^^^^^^^^^^^^^^^^^^^
These variables define custom paths for the installation of required packages. If not specified, CMake will automatically search for these packages on the system.

- **CMAKE**: Path to the CMake executable.
- **CMAKE_C_COMPILER**: C compiler to use.
- **CMAKE_CXX_COMPILER**: C++ compiler to use.
- **CMAKE_INSTALL_PREFIX**: Directory where the software will be installed. Default value: `dist`.
- **CMAKE_PREFIX_PATH**: Additional paths for CMake to search for packages. Example: `/home/agarcia/anaconda3`.
- **MPI_HOME**: Path to the main MPI directory.
- **CMAKE_CUDA_COMPILER**: Path to the CUDA compiler (`nvcc`). Example: `/usr/local/cuda/bin/nvcc`. Works as the XMIPP_CUDA_BIN variable
- **Python3_ROOT_DIR**: Main path to the Python 3 installation.
- **FFTW_ROOT**: Main path to the FFTW library.
- **TIFF_ROOT**: Main path to the TIFF library.
- **HDF5_ROOT**: Main path to the HDF5 package. The path must include the *lib* folder and the *libhdf5.so* inside, and the *include* folder with the *hdf5.h* file.
- **JPEG_ROOT**: Main path to the JPEG library.
- **SQLite_ROOT**: Main path to the SQLite library.
- **CMAKE_CUDA_HOST_COMPILER**: Host compiler for CUDA. Works as the XMIPP_CUDA_LIB variable

Compilation Flags
^^^^^^^^^^^^^^^^^^^^
These variables configure specific options for the compilers. It is recommended not to modify these variables unless experienced with advanced compilation settings.

- **CMAKE_C_FLAGS**: Compilation options for the C compiler. Default value: `-mtune=native`.
- **CMAKE_CXX_FLAGS**: Compilation options for the C++ compiler. Default value: `-mtune=native`.

