Installation Notes
==================

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