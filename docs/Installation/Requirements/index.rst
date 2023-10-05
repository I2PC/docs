Installation requirements
-------------------------

Supported OS
^^^^^^^^^^^^^

We have tested Xmipp compilation on the following operating systems:
- `Ubuntu 18.04 <https://github.com/I2PC/xmipp/wiki/Installing-Xmipp-on-Ubuntu-18.04>`_
- `Ubuntu 20.04 <https://github.com/I2PC/xmipp/wiki/Installing-Xmipp-on-Ubuntu-20.04>`_
- `Ubuntu 22.04 <https://github.com/I2PC/xmipp/wiki/Installing-Xmipp-on-Ubuntu-22.04>`_
- `Centos 7 <https://github.com/I2PC/xmipp/wiki/Installing-Xmipp-on-CentOS-7-9.2009>`_
Visit the OS wiki page for more details.

While compilation and execution might be possible on other systems, it might not be straightforward. If you encounter a problem, please refer to known and fixed `issues <https://github.com/I2PC/xmipp/issues?q=is%3Aissue>`_. Let us know if something is not working.

Hardware requirements
^^^^^^^^^^^^^^^^^^^^

At least 2 processors are required to run Xmipp. In some virtual machine tools only one is assigned, please check that at least two processors are assigned to the virtual machine.

Software dependencies
^^^^^^^^^^^^^^^^^^^^^

Compiler
^^^^^^^^

Xmipp requires a C++17 compatible compiler. We recommend GCC with G++; we have good experience with GCC/G++-8.4; in any case, a version >= 8.4 is required. If you use GCC/G++-10.3 and CUDA=11 and experience issues, `please change the compiler version <https://github.com/NVIDIA/nccl/issues/494>`_. If you use GCC-11 and experience issues, `please visit this <https://github.com/I2PC/xmipp/issues/583>`_. For more details about the compilation process and installation of gcc, please visit `compiler <https://github.com/I2PC/xmipp/wiki/Compiler>`_.

Cmake
^^^^^

Xmipp requires Cmake 3.16 or above. To update it, please `visit <https://github.com/I2PC/xmipp/wiki/Cmake-update-and-install>`_.

Cuda
^^^^

Xmipp supports Cuda 8 through 11.7. CUDA is optional but highly recommended. We recommend you to use the newest version available for your operating system; though Cuda 10.2 has the widest support among other Scipion plugins. Pay attention to the `compiler - CUDA compatibility <https://gist.github.com/ax3l/9489132>`_.

To install CUDA for your operating system, follow the `official install guide <https://developer.nvidia.com/cuda-toolkit-archive>`_.

OpenCV
^^^^^^

OpenCV is used for some programs: movie_optical_alignment (with GPU support) and volume_homogenizer; however, it is not required. If you installed OpenCV via apt (``sudo apt install libopencv-dev``), it should be automatically picked up by the Xmipp script.

HDF5
^^^^

We sometimes see issues regarding the HDF5 dependency. Please visit the `HDF5 Troubleshooting wiki <https://github.com/I2PC/xmipp/wiki/HDF5-Troubleshooting>`_.

Full list of dependencies
^^^^^^^^^^^^^^^^^^^^^^^^^