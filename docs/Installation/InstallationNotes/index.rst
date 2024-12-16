Installation Notes
==================

Optional dependencies
^^^^^^^^^^^^^^^^^^^^

**CUDA**

We recomend CUDA >=11.2. Older version of CUDA requires an older gcc
(gcc-8 could be difficult to install and cause issues with the OS).
Follow official `install
instructions <https://developer.nvidia.com/cuda-toolkit-archive>`__. We
recommend you to follow the guide for installation of CUDA 11.4 (deb
(local))





Compiling with Matlab
-------------------------
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


Troubleshooting
-----------------


DeepLearningToolkit 
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Error message:
``InvalidVersionSpec: Invalid version '5.11.3imageio>=2.5.0': invalid character(s)``

The package *pyvistaqt* installed by an old version of the plugin
*flexutils* or *tomoviz* in the enviroment *scipion3* has a bug in the
version *pyvistaqt*\ =0.3.0. To fix it and be able to install *DLTK*
run:

``conda activate scipion3``

``pip uninstall pyvistaqt``

``pip install pyvistaqt==0.4.0``

If there is any plugin that require *pyvistaqt*
(`scipion-em-tomoviz <https://github.com/scipion-em/scipion-em-tomoviz>`__),
please update it


HDF5 
^^^^^^^^^^^^^^^^^^^
We sometimes see issues regarding the HDF5 dependency. We recommend
removing all hdf5 versions and install just hdf5-devel. To do that
(Ubuntu-Debian systems):

::

   sudo apt remove hdf5
   sudo apt remove hdf5-devel
   pip uninstall h5py

Remove all files related to hdf5 in: \* ``_/usr/lib64/libhdf5*_`` \*
``_/usr/include/hdf5*_`` \* ``_/usr/lib/x86_64-linux-gnu/hdf5_*`` \*
``_.../anaconda3/include/H5*.h_`` \* ``_.../anaconda3/include/hdf5*.h_``
\* ``_.../anaconda3/lib/libhdf5*_`` \*
``_.../anaconda3/envs/.../libhdf5*_``

We strongy recommend you to install it via your default package manager:
``sudo apt-get install libhdf5-dev`` If you install it using other
package management system (such as Conda), it might lead to compile/link
time issues caused by incompatible version being fetched. Other option
is to run”scipion3 installb xmippSrc” to force the xmipp install its own
HDF5 into its desired directory.