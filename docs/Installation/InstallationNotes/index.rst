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


Compiler
---------


Compiling with Matlab
---------


DeepLearningToolKit
---------------------


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