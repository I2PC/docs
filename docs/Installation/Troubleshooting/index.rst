Troubleshooting
--------------------------------------

General error while installing/compiling Xmipp (non-development installations)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

If you are getting an error during the Xmipp compilation, consider to read compilationLog.txt file located in the xmipp folder (by default in scipion3/software/em)/xmippSrc). You can also review the  `requirements of Xmipp <https://i2pc.github.io/docs/Installation/Requirements/index.html>`_.

Alternatively, you can go with the plugin manager or by running

::

    scipion3 installb xmippSrc 

If ``ERROR: Could not find target xmippSrc`` is gotten, try to run

::

    scipion3 installp -p scipion-em-xmipp 


If the problem persist, don't hesitate to `contact us <https://scipion-em.github.io/docs/release-3.0.0/docs/misc/contact-us.html#contact-us>`__.


HDF5: libhdf5.so: undefined reference to ...
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

We sometimes see issues regarding the HDF5 dependency related some incompatibility with *hdf5* and *curl*

.. code-block:: bash

    hdf5/serial/libhdf5.so: undefined reference to `curl_easy_setopt@CURL_OPENSSL_4

- If hdf5 is installed on the Scipion3 enviroment, remove and reinstall it (it might lead to compile/link time issues caused by incompatible version being fetched)

    .. code-block:: bash

        scipion3 run conda remove hdf5 
        scipion3 run conda install -c conda-forge hdf5


- If you have install hdf5 just in your system, we recommend to install hdf5 in the Scipion enviroment. To do that:

    .. code-block:: bash

        scipion3 run conda install -c conda-forge hdf5


- If you have installed hdf5 in your system and you can not use conda, please remove hdf5 an all files it creates and reinstall it:

    .. code-block:: bash

        sudo apt remove hdf5-devel

    Remove all files related to hdf5 in /usr/lib64/libhdf5*, /usr/include/hdf5*   /lib/x86_64-linux-gnu/libhdf5_serial.so and .../anaconda3/include/hdf5*. 

    We strongy recommend you to install it via your default package manager:


    .. code-block:: bash

        sudo apt-get install libhdf5-dev



libstdc++.so. version GLIBCXX_3.4.30 not found 
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
When an error like this appear: 

.. code-block:: bash

    libstdc++.so.6: version GLIBCXX_3.4.30 not found (required by /usr/bin/cmake)

It is because the version of libstdc++.so.6 found (in scipion3 enviroment) is older than the one of the system. This usually happens when the library is recently installed in the Scipion environment but with an older version.

The message could be masked by this message

.. code-block:: bash

    >>> WARNING: XmippImage library not found!
    > Please install Xmipp to get full functionality for cryo electron microscopy workflows. Otherwise ignore this.

If this message arise, please run this command to confirm the cause:

.. code-block:: bash

    ./scipion3 python
    import xmippLib

The best way **to resolve** this issue is to update the library in the scipion enviroment.

.. code-block:: bash

    scipion3 run conda install -c conda-forge libstdcxx-ng


Another less stable option is

.. code-block:: bash

    mv libstdc++.so.VERSION. libstdc++.so.VERSION.old



Cannot compile with Java
^^^^^^^^^^^^^^^^^^^^^^^^^^

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



ImportError: cannot import name 'cmake' from 'cmake' (unknown location)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

This error occurs because a Python package named ``cmake`` (installed via ``pip``) conflicts with the real system-wide CMake tool. The ``cmake`` package from ``pip`` **is not the real CMake**; it is a deprecated wrapper. More `details on <https://github.com/scikit-build/cmake-python-distributions/issues/557>`__

1. **Check the location of the CMake executable:**  

   .. code-block:: bash

      which cmake

   If the output shows a path like ``/home/user/.local/bin/cmake``,
   it means you are using the incorrect version installed via ``pip``.

2. **Uninstall the incorrect version:**  

   .. code-block:: bash

      pip uninstall cmake

3. **Verify that you are now using the correct CMake version:**  

   .. code-block:: bash

      which cmake

   The binary should be located at ``/usr/bin/cmake`` or another system directory.

If CMake is not installed, install it from the appropriate source:

  .. code-block:: bash

     sudo apt install cmake

Linker Error with libLerc
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

**Error** during compilation:

::

    /usr/bin/ld: .../libLerc.so.4: undefined reference to `std::__throw_bad_array_new_length()@GLIBCXX_3.4.29'

**Cause**:
This occurs due to `libLerc` being pulled in by `libtiff >= 4.6.0`, which may have been built against a newer C++ standard or libstdc++ version.

**Fix**:
Downgrade `libtiff` to a version prior to 4.6.0. For example, with Scipion:

::

    scipion3 run conda install libtiff=4.5.1

This prevents `libLerc` from being linked and resolves the incompatibility.



module 'pyworkflow' has no attribute 'VariablesRegistry'
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
That error just appears in v26.0.0 and v26.0.1

To fix it just:

  .. code-block:: bash

    conda activate scipion3
    pip install xmipp3-installer>=2.0.3
    pip install --upgrade scipion-em scipion-app scipion-pyworkflow





Could not find a version that satisfies the requirement xmipp3-installer 
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
The error is caused because a temporary validation of the installation pakage xmipp3-installer in the pypi hub. To fix it:

  .. code-block:: bash
    
    conda activate scipion3
    git clone https://github.com/I2PC/xmipp3-installer.git
    cd xmipp3-installer
    pip install .
    cd ..
    rm -rf ./xmipp3-installer



Error installing scipion-em-xmipp in devel
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
If an error like this arise:

  .. code-block:: bash

    return cls._plugins[name]
    KeyError: 'xmipp3'
    Error at main: 'xmipp3'

Is because you tryed to install xmipp in release mode and you abort the installation. To fix the error you have to move to a path similar to:

/miniconda/envs/scipion3/lib/python3.8/site-packages/xmipp3

and remove that 'xmipp3' folder

