Xmipp structure
============

XMIPP software is split in three repositories (XmippCore, XmippViz and
Xmipp) plus the repository regarding to the Scipion’s plugin
(scipion-em-xmipp). All this four repositories are in `I2PC
gitHub <https://github.com/i2pc>`__.

-  **scipion-em-xmipp**: It is the Scipion’s plugin. Protocol
   (wrappers), viewers, tests… are there. All Xmipp regarding Scipion is
   there.
-  **xmipp**: EM-reconstraction methods. Usually wrote in C++.
-  **xmippCore**: Low-level image-processing and EM-images definitions.
   In addition, metadata_labels, metadata and data are there.
-  **xmippViz**: Basically ShowJ, coordinates viewer and Xmipp Picker.
   Java code.

We call ``xmipp-bundle`` to the folder that contains the four
repositories listed above in the following structure.

::

   .
   ├── CHANGELOG.md
   ├── cmake
   │   ├── fetch_cifpp.cmake
   │   ├── fetch_ctpl.cmake
   │   ├── fetch_cuFFTAdvisor.cmake
   │   ├── fetch_googletest.cmake
   │   ├── fetch_libsvm.cmake
   │   ├── link_to_scipion.cmake
   │   ├── write_bashrc.cmake
   │   └── xmipp.bashrc.in
   ├── CMakeLists.txt
   ├── installer
   │   ├── api.py
   │   ├── cmake.py
   │   ├── config.py
   │   ├── constants
   │   │   ├── cmake.py
   │   │   ├── config.py
   │   │   ├── errors.py
   │   │   ├── __init__.py
   │   │   ├── main.py
   │   │   ├── parser.py
   │   │   ├── __pycache__
   │   │   │   ├── cmake.cpython-38.pyc
   │   │   │   ├── config.cpython-38.pyc
   │   │   │   ├── errors.cpython-38.pyc
   │   │   │   ├── __init__.cpython-38.pyc
   │   │   │   ├── main.cpython-38.pyc
   │   │   │   ├── parser.cpython-38.pyc
   │   │   │   └── versions.cpython-38.pyc
   │   │   └── versions.py
   │   ├── __init__.py
   │   ├── logger.py
   │   ├── main.py
   │   ├── modelsDLTK.py
   │   ├── parser.py
   │   ├── __pycache__
   │   │   ├── api.cpython-38.pyc
   │   │   ├── cmake.cpython-38.pyc
   │   │   ├── config.cpython-38.pyc
   │   │   ├── __init__.cpython-38.pyc
   │   │   ├── logger.cpython-38.pyc
   │   │   ├── main.cpython-38.pyc
   │   │   ├── modelsDLTK.cpython-38.pyc
   │   │   ├── parser.cpython-38.pyc
   │   │   ├── test.cpython-38.pyc
   │   │   └── utils.cpython-38.pyc
   │   ├── test.py
   │   └── utils.py
   ├── LICENSE
   ├── README.md
   ├── scripts
   │   ├── API.py
   │   ├── config.py
   │   ├── environment.py
   │   ├── __init__.py
   │   ├── tar.py
   │   └── utils.py
   ├── xmipp
   └── xmipp_old
   ├── src