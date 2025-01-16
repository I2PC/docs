Troubleshooting
====================================


General error while installing/compiling Xmipp (non-development installations)
==============================================================================

If you are getting an error during the Xmipp compilation, consider to read compilationLog.txt file located in the xmipp floder (by default in scipion2/software/em) and review the `Xmipp's configuration page <https://i2pc.github.io/docs/Utils/ConfigurationF/index.html#configuration-file>`_.

Alternatively, you can go with the plugin manager or by running

::

    scipion3 installb xmippSrc 

If ``ERROR: Could not find target xmippSrc`` is gotten, try to run

::

    scipion3 installp -p scipion-em-xmipp 


If the problem persist, don't hesitate to `contact us <https://scipion-em.github.io/docs/release-3.0.0/docs/misc/contact-us.html#contact-us>`__.


Compiling Xmipp to be used in both Intel and AMD cores
======================================================

Xmipp is optimizing the compilation to the architecture found in the compilation
time. However, this is not a good idea if it must run on both AMD and Intel cores
at once (e.g. in a cluster or so). To make more flexible the optimization on the
compilation, then the ``CXXFLAGS`` can be set properly.

Please, just

::

    export CXXFLAGS="-mfma -mavx2 -m3dnow -fomit-frame-pointer -std=c++11 -O3"

before running the Scipion3 installer.

Please, check `Xmipp's configuration page <https://i2pc.github.io/docs/Utils/ConfigurationF/index.html#configuration-file>`_ for more details.


Xmipp dependencies
======================

HDF5
--------

We sometimes see issues regarding the HDF5 dependency.
We recommend removing all hdf5 versions and install just hdf5-devel. To do that:
```
sudo apt remove hdf5
sudo apt remove hdf5-devel
pip uninstall h5py
```
Remove all files related to hdf5 in /usr/lib64/libhdf5*, /usr/include/hdf5* and .../anaconda3/include/hdf5*. 

We strongy recommend you to install it via your default package manager:
`sudo apt-get install libhdf5-dev` 
If you install it using other package management system (such as Conda), it might lead to compile/link time issues caused by incompatible version being fetched.



Cannot compile with Java
-------------------------

::

    Checking Java configuration...
    /usr/lib/jvm/java-11-openjdk-amd64/bin/javac Xmipp.java
    /bin/sh: 1: /usr/lib/jvm/java-11-openjdk-amd64/bin/javac: not found
    Check the JAVAC
    Cannot compile with Java

Java compiler is missing. Needs to install the jdk-devel version.
In ubuntu would be like:

::

    sudo apt-get install default-jdk

or activate a jdk with javac using alternatives.  

If this is not the case, and you have <SCIPION_HOME>/config/scipion.conf (optional),
review the JAVA_XXX variables there. They might be pointing to a non existing JAVA home.

