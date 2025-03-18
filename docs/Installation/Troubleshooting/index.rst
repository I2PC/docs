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

        scipion3 conda remove hdf5 
        scipion3 conda install -c conda-forge hdf5


- If you have install hdf5 just in your system, we recommend to install hdf5 in the Scipion enviroment. To do that:

    .. code-block:: bash

        scipion3 conda install -c conda-forge hdf5


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

