Installations
----------------------
Installation with Scipion
^^^^^^^^^^^^^^^^^^^^^^^^^^

The recommended way for users (not developers) to install and use Scipion is via the 
`Scipion framework <https://scipion-em.github.io/docs/release-3.0.0/docs/scipion-modes/how-to-install.html>`_, 
where you can use Xmipp with other Cryo-EM-related software. 

Xmipp will not be installed during Scipion installation, to install it use the `plugin manager of Scipion <https://scipion-em.github.io/docs/release-3.0.0/docs/scipion-modes/how-to-install.html#installing-other-plugins>`_


Standlone-installation
^^^^^^^^^^^^^^^^^^^^^^^^^^

This guide explains the standalone installation of Xmipp and the process to link it with Scipion. The standalone version allows you to use Xmipp independently of Scipion.

.. note::

   This `list of libraries <https://i2pc.github.io/docs/Installation/Requirements/index.html#dependencies-automatically-installed-via-scipion>`_ are required in standlone installation and you can install it in the Scipion eviroment if you consider or in the system

Installation
""""""""""""""""""

1. Clone the repository and navigate to the folder:

   .. code-block:: bash

      git clone https://github.com/I2PC/xmipp.git xmipp-bundle && cd xmipp-bundle

2. Compile Xmipp. You have two options:

    **Option 1:** Compile using the Scipion environment. This method installs Xmipp with dependencies managed by Scipion and is the recomended way.

    .. code-block:: bash

        scipion3 run ./xmipp


    **Option 2:** Compile the Xmipp alone. This method installs Xmipp with the required dependencies and versions defined by your environment or defaults.

    .. code-block:: bash

        ./xmipp

   Both methods only compile Xmipp. Linking it to Scipion is explained in the next section.

Note. For additional details about the compilation process, run:

   .. code-block:: bash

      ./xmipp --help

Linking Xmipp to Scipion
""""""""""""""""""""""""""

To use Xmipp within Scipion, link the standalone installation by following these steps:

1. Ensure Scipion is installed (refer to the *Scipion installation guide*).
2. Use the `scipion-em-xmipp` repository, located in `src/scipion-em-xmipp`.
3. Run the following command to link the binaries:

   .. code-block:: bash

      scipion3 installp -p ~/scipion-em-xmipp --devel

   Replace `~/scipion-em-xmipp` with the path to your `scipion-em-xmipp` folder.

Using Xmipp
""""""""""""""""""

Xmipp is installed in the build directory located in the same directory where the xmipp script is located. To run Xmipp standalone (without Scipion) and to set all necessary environment variables and paths to all Xmipp programs, you can simply run 
   
   .. code-block:: bash

      source dist/xmipp.bashrc



Installation for HPC Clusters
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

This guide explains how to install Xmipp on High-Performance Computing (HPC).


1. **Install Scipion for HPC**
   Follow the instructions provided in the Scipion for HPC installation guide: 
   `Scipion HPC Installation Guide <https://scipion-em.github.io/docs/release-3.0.0/docs/scipion-modes/how-to-install.html#for-hpc-clusters>`__.

2. **Install the Scipion Xmipp Plugin**
   Run the following command to install the Xmipp plugin for Scipion:

   .. code-block:: bash

      scipion3 installp -p scipion-em-xmipp
   

3. **Locate and navigate the installation directory** of softwares of Scipion:
   
   .. code-block:: bash

      cd /path/to/scipion3/software/em/
   

4. **Clone the Xmipp Repository**
   Clone there the Xmipp repository and move to the source directory:
   
   .. code-block:: bash

      git clone https://github.com/I2PC/xmipp.git xmippSrc && cd xmippSrc
   

5. **Create the Configuration File**
   Generate the initial configuration file by running:
   
   .. code-block:: bash

      ./xmipp config
   

6. **Edit the Configuration File**
   Open the `configuration file <https://i2pc.github.io/docs/Utils/ConfigurationF/index.html#configuration-file>`__ generated in the previous step and edit the fields as needed. Adjust options such as `CMAKE_C_FLAGS` or `CMAKE_CXX_FLAGS` to match the requirements of your HPC system.



7. **Check the Installed Xmipp Version**
   Use the following command to verify the version of the binaries the plugin scipion-em-Xmipp requires (something like "v3.24.12.0-Poseidon")
   
   .. code-block:: bash

      scipion3 python -c "from xmipp3.version import _binTagVersion; print(_binTagVersion)"  | grep v3
   

8. **Checkout to the specific release**

   .. code-block:: bash

      git checkout v3.24.12.0-Poseidon


9. **Compile and Install Xmipp**
   Compile Xmipp in production mode with the command:
   
   .. code-block:: bash

      scipion3 run ./xmipp --production True


After completing these steps, Xmipp should be successfully installed and configured on your HPC environment. But in any case you can `contact us <https://i2pc.github.io/docs/contact.html#contact-us>`__ for advice or support.


Xmipp on MareNostrum5 cluster; a successful Installation
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

.. note::

   The following is a user-contributed installation report from MareNostrum5 (BSC-CNS, Barcelona),
   which may serve as a helpful reference when installing Xmipp on similar HPC systems.


This is a summary of the steps followed to successfully install Xmipp on the **MareNostrum5** cluster.
Due to the restricted environment (no outgoing requests allowed), some manual pre-fetching and
modification of build scripts were required.

**Fetch Phase (local, in `xmipp` folder)**

Dependencies are separated based on how they're used in the build system:

1. **FetchContent_Declare-based dependencies**: must be placed in the `_deps` folder.
2. **ExternalProject_Add-based dependencies**: must be cloned directly in `build`.

.. code-block:: bash

   mkdir build
   cd build

   # Case 1: FetchContent_Declare (stored in _deps)
   mkdir _deps
   cd _deps
   git clone https://github.com/MartinSalinas98/libcifpp.git
   mv libcifpp libcifpp-src
   git clone https://github.com/google/googletest.git
   mv googletest googletest-src

   # Patch libcifpp to fix valarray constexpr conflict
   nano libcifpp-src/include/cif++/point.hpp
   # -> Comment out lines 324–331
   # -> Replace line 333 with:
   #    value_type length = std::sqrt(q.a*q.a+q.b*q.b+q.c*q.c+q.d*q.d);

   # Case 2: ExternalProject_Add (cloned in main build directory)
   cd ..
   git clone https://github.com/HiPerCoRe/cuFFTAdvisor.git
   git clone https://github.com/cossorzano/libsvm.git
   git clone https://github.com/vit-vit/CTPL.git

**Disable Auto-Fetching (local)**

The `cmake/fetch_*.cmake` scripts must be modified to disable network fetching during CMake configuration.
There are **two types** of fetch scripts:

1. **FetchContent_Declare-based**: modify inside the macro to indicate dependency is already "POPULATED".
2. **ExternalProject_Add-based**: remove or comment out the full `ExternalProject_Add()` block.

.. code-block:: bash

   cd ../cmake

   # Case 1: FetchContent_Declare
   nano fetch_cifpp.cmake
   nano fetch_googletest.cmake
   # -> Inside FetchContent_Declare:
   #    Comment out GIT_REPOSITORY and GIT_TAG lines
   #    Add line: POPULATED TRUE

   # Case 2: ExternalProject_Add
   nano fetch_ctpl.cmake
   nano fetch_libsvm.cmake
   nano fetch_cuFFTAdvisor.cmake
   # -> Comment out or remove the entire ExternalProject_Add() block

**Prepare Environment (remote, on MareNostrum5)**


Load required modules:

.. code-block:: bash

   module load intel
   module load mkl
   module load python
   module load cmake
   module load openmpi/4.1.5-gcc
   module load eigen/3.3.4-gcc-ompi
   module load boost/1.84.0-gcc-ompi
   module load nvidia-hpc-sdk
   module load hdf5/1.10.11-nvidia-nvhpcx
   module load sqlite3/3.45.2-gcc
   module load fftw/3.3.10-gcc-ompi
   module load java-openjdk/22.0.1

Set the Eigen path:

.. code-block:: bash

   export Eigen3_DIR=/apps/ACC/EIGEN/3.3.4/GCC/OPENMPI/share/eigen3/cmake

**Installation (remote)**


Launch the build process:

.. code-block:: bash

   ./xmipp

**Remarks**

- MareNostrum5 blocks all outgoing HTTP(S) requests, so **all dependencies must be fetched locally and transferred manually** to the build environment.
- Distinguish between dependencies using `FetchContent_Declare` and those using `ExternalProject_Add`, as their locations and how they are disabled differ.
- Patching `libcifpp` was necessary to resolve `constexpr`/`valarray` issues during compilation.
