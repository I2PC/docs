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

   xmipp-bundle                  # This is the https://github.com/I2PC/xmipp repository
   ├── CHANGELOG.md
   ├── LICENSE
   ├── README.md
   │
   ├── xmipp          # Main script
   ├── xmipp.conf     # Config file
   │
   ├── scripts
   │   └── (...)
   ├── sonar-project.properties
   │
   ├── src      # Sources directory
   │   ├── scipion-em-xmipp      # This is the https://github.com/I2PC/scipion-em-xmipp repository
   │   │   └── (...)
   │   ├── xmipp
   │   │   └── (...)
   │   ├── xmippCore             # This is the https://github.com/I2PC/xmippCore repository
   │   │   └── (...)
   │   └── xmippViz              # This is the https://github.com/I2PC/xmippViz repository
   │       └── (...)
   │
   └── build    # Self-contained directory with all runnable Xmipp (created during the installation)
       ├── bin        # All binaries of Xmipp
       │   └── (...)
       ├── bindings   # Bindings to other languages
       │   └── (...)
       ├── lib        # Libraries that some binaries use
       │   └── (...)
       ├── pylib      # Python modules that some binaries use
       │   └── (...)
       ├── v3.20.07         # Installation token containing the version number
       ├── xmipp.bashrc     # bash script to set Xmipp env. vars. (run 'source xmipp.basrc')
       ├── xmippEnv.json    # Variables to set environ for Xmipp in running time
       └── xmipp.fish       # fish script to set Xmipp env. vars. (run 'fish xmipp.fish')

To get this structure in a certain directory, run

::

   cd certain_directory
   git clone https://github.com/I2PC/xmipp xmipp-bundle
   cd xmipp-bundle
   ./xmipp get_devel_sources


Check below a detailed structure of Xmipp. Please, check also the `Xmipp
API <https://scipion-em.github.io/docs/docs/api/xmipp-API.html>`__.

::

   xmipp-bundle                -> this is the https://github.com/I2PC/xmipp repository <-
   │
   ├── xmipp            # Main script
   ├── xmipp.conf       # Config file
   ├── xmippEnv.json    # Temporary compilation environ saving for runtime uses
   ├── CHANGELOG.md
   ├── LICENSE
   ├── README.md
   ├── scripts
   │   ├── install_cuda_travis.sh
   │   └── tar.py
   ├── sonar-project.properties
   │
   ├── src     # Main folder containing sources subrepos (scipion-em-xmipp, xmippCore and xmippViz).
   │   │
   │   ├── scipion-em-xmipp    # Repository of the Scipion's plugin   -> this is the https://github.com/I2PC/scipion-em-xmipp repository <-
   │   │   ├── CHANGES.txt
   │   │   ├── LICENSE
   │   │   ├── MANIFEST.in
   │   │   ├── README.md
   │   │   ├── requirements.txt
   │   │   ├── scipion_em_xmipp.egg-info
   │   │   ├── setup.py
   │   │   ├── sonar-project.properties
   │   │   └── xmipp3               # Xmipp plugin for Scipion
   │   │       ├── base.py
   │   │       ├── bibtex.py
   │   │       ├── constants.py
   │   │       ├── convert
   │   │       │   └── (...)
   │   │       ├── __init__.py
   │   │       ├── programs.py
   │   │       ├── protocols
   │   │       │   └── (...)
   │   │       ├── protocols.conf
   │   │       ├── tests
   │   │       │   └── (...)
   │   │       ├── utils.py
   │   │       ├── viewers
   │   │       │   └── (...)
   │   │       ├── wizards.py
   │   │       └── xmipp_logo.png
   │   │
   │   ├── xmipp        # Main sources for Xmipp
   │   │   │
   │   │   ├── applications
   │   │   │   ├── programs  # This contains the main fuctions for the Xmipp progrmas
   │   │   │   │   ├── angular_accuracy_pca
   │   │   │   │   ├── (...)
   │   │   │   │   └── xray_psf_create
   │   │   │   ├── scripts  # This contains programs coded in non-compiling lenguage (e.g. python)
   │   │   │   │   ├── apropos
   │   │   │   │   ├── (...)
   │   │   │   │   └── volume_align
   │   │   │   └── tests    # This contains some tests
   │   │   │       └── function_tests
   │   │   │           ├── aft_tests.h
   │   │   │           ├── (...)
   │   │   │           └── test_funcs_main.cpp
   │   │   ├── bin  # This is created in compilation time
   │   │   │   ├── xmipp_angular_accuracy_pca
   │   │   │   ├── (...)
   │   │   │   └── xmipp_xray_psf_create
   │   │   ├── bindings    # This contains binding for other lenguages
   │   │   │   ├── matlab
   │   │   │   │   ├── mirt3D_mexinterp.cpp
   │   │   │   │   ├── (...)
   │   │   │   │   └── xmipp_write.m
   │   │   │   └── python
   │   │   │       ├── python_constants.cpp
   │   │   │       ├── (...)
   │   │   │       ├── xmipp_base.py
   │   │   │       ├── xmipp_conda_envs.py
   │   │   │       ├── xmippmodule.cpp
   │   │   │       ├── xmippmodule.h
   │   │   │       ├── xmippmodule.os
   │   │   │       └── xmipp.py
   │   │   ├── external
   │   │   │   ├── condor
   │   │   │   │   ├── CNLSolver.cpp
   │   │   │   │   ├── (...)
   │   │   │   │   └── Vector.cpp
   │   │   │   ├── delaunay
   │   │   │   │   ├── dcel.cpp
   │   │   │   │   ├── (...)
   │   │   │   │   └── voronoi.cpp
   │   │   │   ├── gtest
   │   │   │   │   └── (...)
   │   │   │   └── sh_alignment
   │   │   │       ├── frm.cpp
   │   │   │       ├── (...)
   │   │   │       └── swig_frm.py
   │   │   ├── install    # This is created in compilation time
   │   │   │   ├── scons-tools
   │   │   │   │   ├── AutoConfig.py
   │   │   │   │   ├── Make.py
   │   │   │   │   └── __pycache__
   │   │   │   ├── xmipp.conf
   │   │   │   └── xmipp.template
   │   │   ├── lib    # This contains the compiled final libraries
   │   │   │   ├── libcuFFTAdvisor.so
   │   │   │   ├── libXmippCuda.a
   │   │   │   ├── libXmippInterfaceCuda.so
   │   │   │   ├── libXmippParallelCuda.so
   │   │   │   ├── libXmippParallel.so
   │   │   │   ├── libXmipp.so
   │   │   │   ├── _swig_frm.so
   │   │   │   └── xmippLib.so
   │   │   ├── libraries    # This contains the hard code of Xmipp (xmipp is made of C++ libraries)
   │   │   │   ├── classification
   │   │   │   │   ├── ahc_classifier.cpp
   │   │   │   │   ├── (...)
   │   │   │   │   └── vector_ops.h
   │   │   │   ├── data
   │   │   │   │   ├── aft.h
   │   │   │   │   ├── (...)
   │   │   │   │   └── xmipp_polynomials.cpp
   │   │   │   ├── dimred
   │   │   │   │   ├── diffusionMaps.cpp
   │   │   │   │   ├── (...)
   │   │   │   │   └── transform_dimred.cpp
   │   │   │   ├── interface
   │   │   │   │   ├── docfile.cpp
   │   │   │   │   ├── (...)
   │   │   │   │   └── virus.h
   │   │   │   ├── parallel
   │   │   │   │   ├── mpi_angular_accuracy_pca.cpp
   │   │   │   │   ├── (...)
   │   │   │   │   └── xmipp_mpi.cpp
   │   │   │   ├── parallel_adapt_cuda
   │   │   │   │   ├── mpi_reconstruct_fourier_gpu.cpp
   │   │   │   │   ├── mpi_reconstruct_fourier_gpu.h
   │   │   │   │   └── mpi_reconstruct_fourier_gpu.os
   │   │   │   ├── py_xmipp
   │   │   │   │   ├── coordinatesTools
   │   │   │   │   ├── deepConsensusWorkers
   │   │   │   │   ├── deepDenoising
   │   │   │   │   ├── deepLearningToolkitUtils
   │   │   │   │   ├── deepResLearner
   │   │   │   │   ├── example_module2
   │   │   │   │   └── example_module.py
   │   │   │   ├── reconstruction
   │   │   │   │   ├── aalign_significant.cpp
   │   │   │   │   ├── (...)
   │   │   │   │   └── xray_psf_create.cpp
   │   │   │   ├── reconstruction_adapt_cuda
   │   │   │   │   ├── align_significant_gpu.cpp
   │   │   │   │   ├── (...)
   │   │   │   │   └── xmipp_gpu_utils.cpp
   │   │   │   └── reconstruction_cuda
   │   │   │       ├── cuda_all.cpp
   │   │   │       ├── (...)
   │   │   │       └── gpu.cpp
   │   │   ├── resources
   │   │   │   └── test
   │   │   │       ├── dimred
   │   │   │       ├── EMX
   │   │   │       ├── filters
   │   │   │       ├── funcs
   │   │   │       ├── image
   │   │   │       ├── metadata
   │   │   │       ├── polynomials
   │   │   │       ├── pythoninterface
   │   │   │       └── sampling
   │   │   ├── SConscript           # This contains the instructions to compile Xmipp (SConscript)
   │   │   ├── SConstruct           # This contains the instructions to compile Xmipp (SConstruct)
   │   │   └── tests  # This is created in testing time
   │   │       ├── data
   │   │       │   ├── gold
   │   │       │   │   └── (...)
   │   │       │   ├── input
   │   │       │   │   └── (...)
   │   │       │   ├── MANIFEST
   │   │       │   ├── temp.txt
   │   │       │   └── tmpLink
   │   │       ├── __init__.py
   │   │       ├── _test_internal.py
   │   │       ├── test_programs_xmipp.py
   │   │       ├── test.py
   │   │       └── _test_pythoninferface_xmipp.py
   │   │
   │   ├── xmippCore        # Repository of the Core        -> this is the https://github.com/I2PC/xmippCore repository <-
   │   │   │
   │   │   ├── bindings  # This contains bindings to other lenguages
   │   │   │   └── python
   │   │   │       ├── python_image.h
   │   │   │       └── xmippmoduleCore.h
   │   │   ├── CHANGELOG.md
   │   │   ├── core   # This contains the Xmipp CORE code
   │   │   │   ├── alglib
   │   │   │   │   ├── alglibinternal.cpp
   │   │   │   │   ├── (...)
   │   │   │   │   └── stdafx.h
   │   │   │   ├── args.cpp
   │   │   │   ├── (...)
   │   │   │   ├── bilib
   │   │   │   │   ├── changebasis.cc
   │   │   │   │   ├── (...)
   │   │   │   │   └── window.CC
   │   │   │   ├── gcc_version.h
   │   │   │   ├── (...)
   │   │   │   ├── utils
   │   │   │   │   └── (...)
   │   │   │   ├── xmipp_color.cpp
   │   │   │   ├── (...)
   │   │   │   └── xvsmooth.os
   │   │   ├── install  # This is created in compilation time
   │   │   │   ├── scons-tools
   │   │   │   │   ├── AutoConfig.py
   │   │   │   │   ├── Make.py
   │   │   │   │   └── __pycache__
   │   │   │   ├── xmipp.conf
   │   │   │   └── xmipp.template
   │   │   ├── lib    # Where the final libraries ends up
   │   │   │   ├── libXmippCore.so
   │   │   │   └── xmippCore.so
   │   │   ├── LICENSE
   │   │   ├── README.md
   │   │   ├── SConscript           # This contains the instructions to compile XmippCore (SConscript)
   │   │   └── SConstruct           # This contains the instructions to compile XmippCore (SConstruct)
   │   │
   │   └── xmippViz        # Repository of the Core       -> this is the https://github.com/I2PC/xmippViz repository <-
   │       │
   │       ├── applications
   │       │   └── scripts
   │       │       ├── metadata_plot
   │       │       └── showj
   │       ├── bin
   │       │   ├── xmipp_metadata_plot
   │       │   └── xmipp_showj
   │       ├── bindings
   │       │   ├── java
   │       │   │   ├── src
   │       │   │   │   └── (...)
   │       │   │   ├── xmipp_Aux.cpp
   │       │   │   ├── (...)
   │       │   │   └── xmipp_TiltPairAligner.cpp
   │       │   └── python
   │       │       └── xmippViz.py
   │       ├── CHANGELOG.md
   │       ├── external
   │       │   ├── imagej
   │       │   │   └── (...)
   │       │   └── imagej.tgz
   │       ├── install
   │       │   ├── scons-tools
   │       │   │   ├── AutoConfig.py
   │       │   │   └── Make.py
   │       │   ├── xmipp.conf
   │       │   └── xmipp.template
   │       ├── java
   │       │   ├── build
   │       │   │   ├── HandleExtraFileTypes.class
   │       │   │   ├── (...)
   │       │   │   └── XmippViewer.jar_source.txt
   │       │   ├── lib
   │       │   │   ├── commons-cli-1.1.jar
   │       │   │   ├── (...)
   │       │   │   └── XmippViewer.jar
   │       │   └── src          # This contains the hard code of xmippViz (coded in Java)
   │       │       ├── HandleExtraFileTypes.java
   │       │       └── xmipp
   │       │           └── (...)
   │       ├── lib
   │       │   └── libXmippJNI.so
   │       ├── LICENSE
   │       ├── README.md
   │       ├── resources
   │       │   ├── add.gif
   │       │   ├── (...)
   │       │   └── zoom.png
   │       ├── SConscript           # This contains the instructions to compile XmippViz (SConscript)
   │       ├── SConstruct           # This contains the instructions to compile XmippViz (SConstruct)
   │       └── xmipp_MetaData.cpp
   │
   └── build        # After compilation, all binaries ends up to the self-contained build folder
       ├── bin   # This contains the binaries to be launched
       │   ├── xmipp_angular_accuracy_pca
       │   ├── (...)
       │   └── xmipp_xray_psf_create
       ├── bindings  # This contains the compiled bindings to other lenguages
       │   ├── java
       │   ├── matlab
       │   └── python
       ├── lib    # This contains the compiled libraries (needed to launch binaries in the bin folder)
       │   ├── libcuFFTAdvisor.so
       │   ├── libXmippCore.so
       │   ├── libXmippCuda.a
       │   ├── libXmippInterfaceCuda.so
       │   ├── libXmippJNI.so
       │   ├── libXmippParallelCuda.so
       │   ├── libXmippParallel.so
       │   └── libXmipp.so
       ├── pylib    # Python modules to use in running time
       │   └── xmippPyModules
       │       └── xmippPyModules
       │       ├── coordinatesTools
       │       ├── deepConsensusWorkers
       │       ├── deepDenoising
       │       ├── deepLearningToolkitUtils
       │       ├── deepResLearner
       │       ├── example_module2
       │       ├── example_module.py
       │       └── __init__.py
       ├── resources
       │   ├── add.gif
       │   ├── binocular.png
       │   ├── brush.png
       │   ├── (...)
       │   └── zoom.png
       ├── v3.20.07         # Installation token containing the version number
       ├── xmipp.bashrc     # bash script to set Xmipp env. vars. (run 'source xmipp.basrc')
       ├── xmippEnv.json    # Variables to set environ for Xmipp in running time
       └── xmipp.fish       # fish script to set Xmipp env. vars. (run 'fish xmipp.basrc')