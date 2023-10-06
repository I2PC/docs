Installation Notes
==================
Installing on Ubuntu 22.04
-----------------------------
Required dependencies
^^^^^^^^^^^^^^^^^^^^

**Compiler**

::

   sudo apt install gcc-10 g++-10
   sudo update-alternatives --install /usr/bin/g++ g++ /usr/bin/g++-10 50
   sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-10 50

**GCC-11 version compatible**

GCC-11 is compatible with Xmipp but we have experienced some problems in
the installation; if appear: *undefined reference to \`std::…* Please
follow those instructions: https://github.com/I2PC/xmipp/issues/583 or
use gcc-10 or older

**Other dependencies**

``sudo apt install -y scons libfftw3-dev libopenmpi-dev libhdf5-dev python3-numpy python3-dev libtiff5-dev libsqlite3-dev default-jdk git cmake``

``pip install scons numpy``

Optional dependencies
^^^^^^^^^^^^^^^^^^^^

**CUDA**

We recomend CUDA >=11.2. Older version of CUDA requires an older gcc
(gcc-8 could be difficult to install and cause issues with the OS).
Follow official `install
instructions <https://developer.nvidia.com/cuda-toolkit-archive>`__. We
recommend you to follow the guide for installation of CUDA 11.4 (deb
(local))

**OpenCV** OpenCV is currently not properly supported. See
https://github.com/I2PC/xmipp/issues/436 for details.

Installation
^^^^^^^^^^^^^^^^^^^^

``git clone https://github.com/I2PC/xmipp.git && cd xmipp && ./xmipp``





Installing on Ubuntu 20.04
-----------------------------
Required dependencies
^^^^^^^^^^^^^^^^^^^^

**Compiler (when using CUDA 10.2)**

::

   sudo apt install gcc-8 g++-8
   sudo update-alternatives --remove-all gcc
   sudo update-alternatives --remove-all g++
   sudo update-alternatives --install /usr/bin/g++ g++ /usr/bin/g++-8 50
   sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-8 50

**Compiler (for CUDA 11.2 or without CUDA)**

``sudo apt install gcc g++``

**Other dependencies**

``sudo apt install -y libfftw3-dev libopenmpi-dev libhdf5-dev python3-numpy python3-dev libtiff5-dev libsqlite3-dev default-jdk git cmake``

``pip install scons numpy``

Optional dependencies
^^^^^^^^^^^^^^^^^^^^

**CUDA** Follow official `install
instructions <https://developer.nvidia.com/cuda-toolkit-archive>`__. We
recommend you to follow the guide for installation of CUDA 11.4 (deb
(local)), but then install ``sudo apt install cuda-10-2``

**OpenCV** OpenCV is currently not properly supported. See
https://github.com/I2PC/xmipp/issues/436 for details.

Installation
^^^^^^^^^^^^^^^^^^^^

``git clone https://github.com/I2PC/xmipp.git && cd xmipp && ./xmipp``

Installing on Ubuntu 18.04
---------------------------
Required dependencies
^^^^^^^^^^^^^^^^^^^^

**Compiler**

::

   sudo apt install gcc-8 g++-8
   sudo update-alternatives --remove-all gcc
   sudo update-alternatives --remove-all g++
   sudo update-alternatives --install /usr/bin/g++ g++ /usr/bin/g++-8 50
   sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-8 50

**Other dependencies**

``sudo apt install -y scons libfftw3-dev libopenmpi-dev libhdf5-dev python3-numpy python3-dev libtiff5-dev libsqlite3-dev default-jdk git cmake``

Optional dependencies
^^^^^^^^^^^^^^^^^^^^

**CUDA** Follow official `install
instructions <https://developer.nvidia.com/cuda-toolkit-archive>`__

**OpenCV** ``sudo apt install libopencv-dev``

Installation
^^^^^^^^^^^^^^^^^^^^

``git clone https://github.com/I2PC/xmipp.git && cd xmipp && ./xmipp``

Installing on Centos-7 
---------------------------
Required dependencies
^^^^^^^^^^^^^^^^^^^^

**General dependencies**

``sudo yum install scons fftw-dev openmpi-devel libtiff-devel sqlite3-devel default-jdk git cmake python3 python3-devel python3-numpy python3-tkinter wget libjpeg-devel java-1.8.0-openjdk-devel libsq3-devel libzstd``

**Compiler**

The version of gcc and g++ included in the latest version of CentOS 7 is
too old (4.8) and it is not supported by Xmipp. Also, the latest version
of gcc-8 and g++-8 obtainable from the devtoolset-8 package is too old
(8.3), so we suggest installing the compilers from version 9 onwards
(the example in this guide installs gcc-10 and g++-10).

In CentOS, you can install a *devtoolset* to incorporate a newer version
of the compilers. To do this, you must first enable the RedHat CentOS
SCL repository. Please ask your system administrator to do this for you
if you have no permission or have any kind of doubt. The following
commands will install the devtoolset and use it by default for all
users:

::

   # Enable the repository and install the binaries
   yum install centos-release-scl
   yum install devtoolset-10-gcc devtoolset-10-gcc-c++
   # Add the newly installed binaries as options for gcc and g++
   sudo update-alternatives --install /usr/bin/gcc gcc /opt/rh/devtoolset-10/usr/bin/gcc 10
   sudo update-alternatives --install /usr/bin/g++ g++ /opt/rh/devtoolset-10/usr/bin/g++ 10
   # Select them as the default option - this will show an interactive menu: choose the installed version and hit enter
   sudo update-alternatives --config gcc
   sudo update-alternatives --config g++

The packages devtoolset-10-gcc and devtoolset-10-g++ can be found in
``/opt/rh/devtoolset-10/root/usr/bin/gcc`` and
``/opt/rh/devtoolset-10/root/usr/bin/g++``. To temporarily enable them
in a console you can execute ``scl enable devtoolset-10 -- bash`` (bear
in mind it will be disabled on console closing). You can check if you
are using the correct version of the compilers with ``mpicc --version``,
``gcc --version`` and ``g++ --version``.

Troubleshooting
^^^^^^^^^^^^^^^^^^^^

**Errors with hdf5**

We recommend removing all hdf5 versions and install just hdf5-devel. To
do that:

::

   sudo yum remove hdf5
   sudo yum remove hdf5-devel
   pip uninstall h5py

remove all files related to hdf5 in: \* ``_/usr/lib64/libhdf5*_`` \*
``_/usr/include/hdf5*_`` \* ``_/usr/lib/x86_64-linux-gnu/hdf5_*`` \*
``_.../anaconda3/include/H5*.h_`` \* ``_.../anaconda3/include/hdf5*.h_``
\* ``_.../anaconda3/lib/libhdf5*_`` \*
``_.../anaconda3/envs/.../libhdf5*_``

be sure about the gcc version (gcc –version) install hdf5-devel
``sudo yum install hdf5-devel``

Optional dependencies
^^^^^^^^^^^^^^^^^^^^

**CUDA** Follow official `install
instructions <https://developer.nvidia.com/cuda-toolkit-archive>`__ Take
care on the version of GCC/G++ installed. `This
StackOverflow <https://stackoverflow.com/a/46380601>`__ post contains
the compatibility chart of CUDA + GCC/G++. You can have different
versions working at the same time but it can be complex for basic linux
users.

**OpenCV** ``sudo yum install opencv-devel``

Installation
^^^^^^^^^^^^^^^^^^^^
``git clone https://github.com/I2PC/xmipp.git && cd xmipp && ./xmipp``


Cmake
--------
Xmipp requires a Cmake version 3.16 or above. To update and install it follow these steps.

Ubuntu and Debian
^^^^^^^^^^^^^^^^^^^^

If you have not installed cmake please

``sudo apt-get install -y cmake cmake-data``

If you have an older version, to install the newest:

-  ``sudo apt remove -y cmake cmake-data``
-  ``hash -r``
-  ``sudo apt-get install -y cmake cmake-data``
-  ``hash -r``

Centos
^^^^^^^^^^^^^^^^^^^^

To uninstall cmake \* Go to the cmake directory
(``cd / && find . -type d -name "*cmake*"``) \* ``sudo make uninstall``
\* ``cd .. && rm -rf path/to/cmake``

To install cmake \*
``wget https://github.com/Kitware/CMake/releases/download/v3.17.3/cmake-3.17.3.tar.gz``
\* ``tar -zxvf cmake-3.17.3.tar.gz`` \* ``cd cmake-3.17.3`` \*
``./bootstrap`` \* ``make`` \* ``sudo make install`` \* Verify the
installed version by typing ``sudo --version``

Older Ubuntu (18.0.4)
^^^^^^^^^^^^^^^^^^^^

To update gcc from v7 \* ``sudo apt-get remove gcc-7`` \*
``sudo apt-get install gcc-8`` \*
``sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-8 800 --slave /usr/bin/g++ g++ /usr/bin/g++-8``

To Update Cmake

-  ``wget -O - https://apt.kitware.com/keys/kitware-archive-latest.asc 2>/dev/null | sudo apt-key add -``

-  ``sudo apt-add-repository 'deb https://apt.kitware.com/ubuntu/ bionic main'``

-  ``sudo apt-get update``

Compiler
---------
Xmipp consists of multiple standalone programs written primarily in C++.
For that reason, the Xmipp suite has to be compiled before its use. The
compilation process is driven by the xmipp script located in this
repository. Xmipp requires C++17 compatible compiler. We recommend
either GCC or CLANG, in the newest version possible. We have good
experience with GCC-8 and bad experience with GCC-7, in any case a
version > 6 is required. If use GCC-11 and experience issues, `please
visit this. <https://github.com/I2PC/xmipp/issues/583>`__

We strongly recommend you to have this compiler linked to ``gcc`` and
``g++``. Otherwise it might not be properly picked up by wrappers, such
as MPI’s wrapper. We have good experince with using ``alternatives``:

::

   sudo apt install gcc-8 g++-8
   sudo update-alternatives --remove-all gcc
   sudo update-alternatives --remove-all g++
   sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-8 50
   sudo update-alternatives --install /usr/bin/g++ g++ /usr/bin/g++-8 50

**Note:** If you compiled Xmipp with a GCC/G++ version, and you change
the compiler version, you will need to run ``./xmipp cleanAll`` before
compiling again in case you need to.

Compiling with Matlab
---------
Xmipp has a binding to MATLAB, which allows the user to run specific
Xmipp functions inside MATLAB.

Previous requirements
^^^^^^^^^^^^^^^^^^^^

It is required to have a regular MATLAB installation.

Settings
^^^^^^^^^^^^^^^^^^^^

Make sure you have these settings in your Xmipp configuration file
(``xmipp-bundle/xmipp.conf``) before compiling Xmipp:

``MATLAB=True``

``MATLAB_DIR=<path to your MATLAB instalation>`` (usually something
like: ``MATLAB_DIR=/home/user/MATLAB/R2021b``)

Run
^^^^^^^^^^^^^^^^^^^^

1. Compile Xmipp normally (once the settings are as above): ``./xmipp``
   or ``scipion run ./xmipp``
2. Open MATLAB
3. In MATLAB, set the path to Xmipp binding:
   ``HOME > Set Path > Add Folder...`` and select the path to the
   binding (``<path to xmipp>/xmipp-bundle/build/bindings/matlab``),
   then, click in ``Open`` and ``Save``
4. Now you should be able to run functions like ``xmipp_read()`` in
   MATLAB

DeepLearningToolKit
---------------------
The DeepLearningToolkit (DLTK) is a set of environments populated with
several libraries related to deep learning and allows running protocols
on Scipion which require deep learning tools. All of them are available
for GPU or CPU only (the installator’ll detect your configuraction)

Requirements
^^^^^^^^^^^^^^^^^^^

A nvidia drivers 450 or higher is required, to review the nvidia driver
version please run ``nvidia-smi``. If older version is detected, the
DLTK will be installed without GPU support.

How to install
^^^^^^^^^^^^^^^^^^^

Run ``scipion3 installb deepLearningToolkit``

It could take more than 30 minutes. To speedup the installation we
propose to use libmamba solver (we experienced a x4 speedup) . It is
only available for conda >=4.12 and has to be installed and setup on
your conda installation. For more details, please visit:
https://www.anaconda.com/blog/a-faster-conda-for-a-growing-community

List environments
^^^^^^^^^^^^^^^^^^^

-  xmipp_DLTK_v0.3 > \* Protocols ussing it: screen_deeplearning,
   deep_denoising, resolution_deepres, screen_deepConsensus > \*
   python=3.7 > \* scikit-image=0.14 > \* tensorflow=1.15 > \* keras=2.2
   > \* scikit-learn=0.22 > \* pip > \* numpy==1.21 > \* h5py==2.10.0

-  xmipp_DLTK_v1.0 > \* Protocols ussing it: deep_misalingment_detection
   > \* python=3.8 > \* tensorflow=2.7 > \* keras=2.7 > \* pip > \*
   numpy==1.23

-  xmipp_MicCleaner > \* Protocols ussing it: deepMicrographScreen > \*
   python=3.6 > \* micrograph-cleaner-em=0.35

-  xmipp_deepEMhancer > \* Protocols ussing it: protocol_deepEMhancer >
   \* python=3.6 > \* deepemhancer=0.12 > \* numba=0.45

-  xmipp_pyTorch > \* Protocols ussing it: deepHand > \* python=3.8 > \*
   numpy=1.23 > \* mrcfile=1.4.3 > \* kornia=0.6.12 > \* starfile=0.4.12
   > \* pytorch==1.11 > \* pytorch-cuda=11.7 > \* torchvision=0.12

Troubleshooting
^^^^^^^^^^^^^^^^^^^

Visit:
`troubleshooting <https://github.com/I2PC/xmipp/wiki/DeepLearningToolkit-troubleshooting>`__


Troubleshooting
-----------------
Cmake troubleshooting
~~~~~~~~~~~~~~~~~~~~~


DeepLearningToolkit troubleshooting
~~~~~~~~~~~~~~~~~~~~~


Linking Xmipp to Scipion troubleshooting
~~~~~~~~~~~~~~~~~~~~~


HDF5 troubleshooting
~~~~~~~~~~~~~~~~~~~~~