Xmipp Configuration File
========================

This document describes the variables present in the Xmipp configuration file and their purpose. Reviewed for xmipp.3.24.12 - Poseidon
Each section and variable is detailed below:

Toggle Section
--------------
These options allow activating or deactivating specific software functionalities.

- **SEND_INSTALLATION_STATISTICS**: Enables (`ON`) or disables (`OFF`) the sending of installation statistics.
- **XMIPP_USE_CUDA**: Enables (`ON`) or disables (`OFF`) the use of CUDA to accelerate calculations via GPU.
- **XMIPP_USE_MPI**: Enables (`ON`) or disables (`OFF`) the use of MPI for distributed parallelism.
- **XMIPP_USE_MATLAB**: Enables (`ON`) or disables (`OFF`) the use of functionalities related to MATLAB.
- **XMIPP_LINK_TO_SCIPION**: Enables (`ON`) or disables (`OFF`) linking Xmipp with the Scipion framework.
- **BUILD_TESTING**: Enables (`ON`) or disables (`OFF`) the building of automated tests to verify software integrity.
- **CMAKE_SKIP_RPATH**: Enables (`ON`) or disables (`OFF`) excluding `rpath` during the compilation process.

Package Home Section
---------------------
These variables define custom paths for the installation of required packages. If not specified, CMake will automatically search for these packages on the system.

- **CMAKE**: Path to the CMake executable.
- **CMAKE_C_COMPILER**: C compiler to use.
- **CMAKE_CXX_COMPILER**: C++ compiler to use.
- **CMAKE_INSTALL_PREFIX**: Directory where the software will be installed. Default value: `dist`.
- **CMAKE_PREFIX_PATH**: Additional paths for CMake to search for packages. Example: `/home/agarcia/anaconda3`.
- **MPI_HOME**: Path to the main MPI directory.
- **CMAKE_CUDA_COMPILER**: Path to the CUDA compiler (`nvcc`). Example: `/usr/local/cuda/bin/nvcc`.
- **Python3_ROOT_DIR**: Main path to the Python 3 installation.
- **FFTW_ROOT**: Main path to the FFTW library.
- **TIFF_ROOT**: Main path to the TIFF library.
- **HDF5_ROOT**: Main path to the HDF5 library.
- **JPEG_ROOT**: Main path to the JPEG library.
- **SQLite_ROOT**: Main path to the SQLite library.
- **CMAKE_CUDA_HOST_COMPILER**: Host compiler for CUDA.

Compilation Flags
------------------
These variables configure specific options for the compilers. It is recommended not to modify these variables unless experienced with advanced compilation settings.

- **CMAKE_C_FLAGS**: Compilation options for the C compiler. Default value: `-mtune=native`.
- **CMAKE_CXX_FLAGS**: Compilation options for the C++ compiler. Default value: `-mtune=native`.

