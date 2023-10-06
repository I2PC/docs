Configuration file
===============
Reviewed for version 20.07

The main command ``./xmipp`` will try to make the properly configuration
according to your system, generating a config file named ``xmipp.conf``.
Afterwards, XMIPP will be built. You can run ``./xmipp config`` to only
set the configuration.

-  If your Xmipp is intended to run under **Scipion**, you should run
   ``scipion3 run`` as a wrapper (i.e. ``scipion3 run ./xmipp`` or
   ``scipion3 run ./xmipp config``). However, Scipion’s installation
   includes the Xmipp installation, by default.
   Check `this (for
   non-developers) <https://scipion-em.github.io/docs/docs/user/troubleshooting.html#general-error-while-installing-compiling-xmipp-non-development-installations>`__
   or `this (for
   developers) <https://scipion-em.github.io/docs/docs/user/troubleshooting.html#general-error-while-installing-compiling-xmipp-development-installations>`__
   to learn how to trigger a compilation through Scipion.

The Xmipp configuration sets mainly six compiling blocks:
`C++ <#c-configuration>`__, `MPI <#mpi-configuration>`__,
`Java <#java-configuration>`__, `Cuda <#cuda-configuration>`__ (optional
but recommended), `Matlab <#matlab-configuration>`__ (optional),
`OpenCV <#opencv-configuration>`__ (optional, not recommended).

The idea is always the same, Xmipp will try to find compilers in the
PATH (similar to the ``which`` command) and will take the libraries and
headers from them. If some compiler is not found in the PATH, Xmipp will
look for the default paths on the majority of the Linux distros. You can
bypass this automatic searching by means of manually setting the
environment variables described in the sections below.

Xmipp asks users if agree on using automatically found paths in the
system. Include the ``noAsk`` option to the config command in order to
launch an unattended configuration.

-  If your Xmipp is intended to run under **Scipion**, **the environment
   variables described in sections below can be added in the
   ``scipion3/config/scipion.conf``** before launching
   ``scipion3 installb xmippSrc`` (or your compilation command).

-  Note that ``scipion3 installb xmippSrc`` (or other Xmipp compilation
   commands in Scipion) regenerates the ``xmipp.conf``. Therefore, **if
   you want to manually set some variables in the ``xmipp.conf``,
   ``export XMIPP_NOCONFIG=True`` or include ``XMIPP_NOCONFIG=True`` in
   ``scipion3/config/scipion.conf``** to skip that config regeneration.

C++ configuration
-----------------

The default C compiler is ``gcc`` while ``g++`` compiler is for C++ code
and C++ library links. Then Xmipp will ensure that they are visible
prior to assign them to the configuration. You can set any other
compilers by setting the ``CC``, ``CXX`` and ``LINKERFORPROGRAMS``
variables.

Find below a list of tuneable variables regarding to C and C++
compilation. Keep in mind that they are automatically set by Xmipp.
However, you can bypass this automatic setting by exporting them
(e.g. ``export CXX=icc``) prior to launch the command or, even, you can
update the resulting ``xmipp.conf`` file, once created.

| · **``CC``**: C compiler. ``gcc`` by default.
| · **``CCFLAGS``**: Flags to add during C compilations. ``-std=c99`` by
  default

| · **``CXX``**: C++ compiler. ``g++`` by default.
| · **``CXXFLAGS``**: Flags to add during C++ compilations.
  ``-mtune=native -march=native -std=c++11 -O3`` by default.
| · **``INCDIRFLAGS``**: Flags to add headers directories. See note
  below.
| · **``LIBDIRFLAGS``**: Flags to add libraries directories. See note
  below.

| · **``LINKERFORPROGRAMS``**: C++ linker. ``g++`` by default.
| · **``LINKFLAGS``**: Flags to add while linking. Empty by default.

| · **``PYTHON_LIB``**: Python library to make the python binding. Xmipp
  automatically discovers the current python (e.g. ``python3.5m``).
| · **``PYTHONINCFLAGS``**: Flags to add during the binding compilation.
  Usually to include the python header and the numpy header
  (e.g. ``-I/usr/include/python3.5m -I/home/david/scipion3/.scipion3env/lib/python3.5/site-packages/numpy/core/include``)

-  Note regarding **``INCDIRFLAGS``** and **``LIBDIRFLAGS``**

   Xmipp adds the ``include`` and ``lib`` from the current environ
   (using the python function ``sysconfig.get_path('data')``) in order
   to take system or environ headers and libs.

   In addition, if ``hdf5`` is not found there, **Xmipp will look for it
   in ``/usr/lib`` and ``/usr/include/hdf5/serial``**. If found it, the
   paths are appended to the ``INCDIRFLAGS`` and ``LIBDIRFLAGS``. If not
   found and a specific conda environ is present, **Xmipp will try to
   install hdf5 through conda** under the current conda-environ.

   Moreover, if ``fftw3`` or ``tiff`` libraries are not found and a
   specific conda environ is present, **Xmipp will try to install them
   through conda** under the current conda-environ.

-  Note that **``CXXFLAGS``** is optimizing the compilation to the
   architecture found during in compilation time. This will make Xmipp
   incompatible to be run under another architecture.

   To make more flexible this optimization in order to make Xmipp
   compatible on both, Intel and AMD cores, please consider to

   ::

      export CXXFLAGS="-mfma -mavx2 -m3dnow -fomit-frame-pointer -std=c++11 -O3"

   or edit the ``xmipp.conf`` file in such a way, before compiling
   Xmipp.

MPI configuration
-----------------

The default MPI compiler for C is ``mpicc`` while ``mpicxx`` is for C++
code and C++ library links. Then Xmipp will ensure that they are visible
prior to assign them to the configuration. You can set any other
compilers by setting the ``MPI_CC``, ``MPI_CXX`` and
``MPI_LINKERFORPROGRAMS`` variables.

Additionally, ``mpirun`` is the default program to run mpi programs. If
not found, ``mpiexec`` becomes an option. Then, Xmipp will ensure that
they are visible prior to assign them to the configuration (any other
mpi executor can be used by setting the ``MPI_RUN`` variable). You can
set a given MPI toolkit by setting ``MPI_BINDIR``, ``MPI_LIBDIR`` and
``MPI_INCLUDE`` (see `Scipion-config
doc <https://scipion-em.github.io/docs/release-3.0.0/docs/scipion-modes/scipion-configuration.html#mpi-variables>`__).

If ``mpicc``, ``mpicxx`` or ``mpirun`` are not found following
instructions above, Xmipp looks for them in the Linux default paths:
``/usr/lib/openmpi/bin`` or ``/usr/lib64/openmpi/bin``.

Find below a list of tuneable variables regarding to MPI compilations.
Keep in mind that they are automatically set by Xmipp. However, you can
bypass this automatic setting by exporting them
(e.g. ``export MPI_CXX=mpi2-intel``) prior to launch the command or,
even, you can update the resulting ``xmipp.conf`` file, once created.

| · **``MPI_RUN``**: Executor to run MPI programs. ``mpirun`` by
  default.
| · **``MPI_CC``**: MPI compiler for C code. ``mpicc`` by default.
| · **``MPI_CXX``**: MPI compiler for C++ code. ``mpicxx`` by default.
| · **``MPI_CXXFLAGS``**: Flags to add during the MPI compilation. Empty
  by default.
| · **``MPI_LINKERFORPROGRAMS``**: MPI compiler to link C++ libraries.
  ``mpicxx`` by default.
| · **``MPI_LINKFLAGS``**: Flags to add during the MPI linking. Empty by
  default.

Java configuration
------------------

Xmipp ensures that ``javac`` command is visible and takes its location
in order to get the ``jar`` and ``java`` programs. If ``javac`` is not
present in the PATH, Xmipp look for it at ``/usr/lib/jvm/java-*/bin``.
If still not found and a specific conda environ is present, **Xmipp will
try to install ``openjdk`` through conda** under that conda-environ.

Find below a list of tuneable variables regarding to Java compilations.
Keep in mind that they are automatically set by Xmipp. However, you can
bypass this automatic setting by exporting them
(e.g. ``export JAVA_HOME=/my/own/java``) prior to launch the command or,
even, you can update the resulting ``xmipp.conf`` file, once created.

| · **``JAVA_HOME``**: Path where java is loacated.
  ``dirname $(dirname $(realpath $(which javac)))`` by default
  (``jre/bin`` is pull out if present).
| · **``JAVA_BINDIR``**: Path where ``jar`` and ``javac`` are located.
  ``%(JAVA_HOME)s/bin`` by default.
| · **``JAVAC``**: JavaC compiler. ``%(JAVA_BIN)s/javac`` by default.
| · **``JAR``**: Jar compiler. ``%(JAVA_BIN)s/jar`` by default.
| · **``JNI_CPPPATH``**: Include paths during the Java compilation.
  ``%(JAVA_HOME)s/include:%(JAVA_HOME)s/include/linux`` by default.

Cuda configuration
------------------

Cuda compilation is optional in Xmipp, but strongly recommended. Xmipp
will find the ``nvcc`` compiler in the PATH and will take its
corresponding cuda toolkit. If no ``nvcc`` is found in the PATH, Xmipp
looks for it in the default Linux locations: ``/usr/local/cuda*/bin``.
In addition, following the Scipion syntax, you can manually set a
certain path where to find the ``nvcc`` by
``export CUDA_BIN=/my/own/cuda/bin`` or even
``export XMIPP_CUDA_BIN=/my/own/cuda/bin`` (or include it in the
``scipion3/config/scipion.conf`` if you are under Scipion structure).

Check below the preference list while looking for a ``nvcc`` compiler:

1. in ``XMIPP_CUDA_BIN``.
2. in ``CUDA_BIN``
3. in ``PATH``
4. in ``/usr/local/cuda/bin``
5. in ``/usr/local/cuda*/bin`` (in this case, the glob-expanding order
   will be defined by the OS)

At the end, Xmipp will take as ``CUDA_HOME`` the directory (resolving
any eventual linking) of the ``nvcc`` found. If it is found using
assumption 4. or 5., Xmipp asks users if they agree (use ``noAsk``
option in the command launching for an unattended behavior).

Find below a list of tuneable variables regarding to CUDA compilations.
Keep in mind that they are automatically set by Xmipp according to that
described above. However, you can bypass this automatic setting by
exporting them (e.g. ``export NVCC=/my/own/cuda/bin/nvcc``) prior to
launch the command or, even, you can update the resulting ``xmipp.conf``
file, once created.

| · **``CUDA``**: Main flag to enable/disable CUDA compilation, set to
  ``True``/``False`` accordingly. By default, it is set to ``True`` if a
  ``nvcc`` is found.
| · **``NVCC``**: Path to the Cuda compiler (it can be just the command
  if it is in the PATH). ``nvcc`` (or the real path to it) by default.
| · **``CXX_CUDA``**: C++ compiler to compile Cuda code. Notice that
  Cuda-8.0 is incompatible with ``g++>5``, then this can be set to
  ``g++-5``, whereas the main C++ compiler still ``g++-8``. By default,
  it is ``g++`` (if compatible).
| · **``NVCC_CXXFLAGS``**: Cuda compilation flags.
  ``--x cu -D_FORCE_INLINES -Xcompiler -fPIC -ccbin %(CXX_CUDA)s -std=c++11 --expt-extended-lambda -gencode=arch=compute_30,code=compute_30 -gencode=arch=compute_35,code=compute_35 -gencode=arch=compute_50,code=compute_50 -gencode=arch=compute_60,code=compute_60 -gencode=arch=compute_61,code=compute_61``,
  by default.
| · **``NVCC_LINKFLAGS``**: Cuda linking flags.
  ``-L/usr/local/cuda-X.Y/targets/x86_64-linux/lib -L/usr/local/cuda-X.Y/targets/x86_64-linux/lib/stubs``
  by default.

Notice that ``NVCC_LINKFLAGS`` contain the libraries according to the
``nvcc`` found (in the default example there is ``cuda-X.Y`` indicating
a certain cuda version). That libraries are set by looking for the
``libcudart.so`` lib following the preference list below:

1. in ``$CUDA_HOME/lib``
2. in ``$CUDA_HOME/lib64``
3. in ``$CUDA_HOME/targets/x86_64-linux/lib``
4. in ``$CUDA_HOME/lib/x86_64-linux-gnu``
5. in ``/usr/lib``
6. in ``/usr/lib64``
7. in ``/usr/targets/x86_64-linux/lib``
8. in ``/usr/lib/x86_64-linux-gnu``

If it is found using assumptions from 5. to 8., Xmipp asks users if they
agree (use ``noAsk`` option in the command launching for an unattended
behavior).

Matlab configuration
--------------------

Some programs in Xmipp are coded in Matlab and they needs to be compiled
with. (*TODO: list those programs*)

Find below a list of tuneable variables regarding to Matlab
compilations. Keep in mind that they are automatically set by Xmipp.
However, you can bypass this automatic setting by exporting them
(e.g. ``export MATLAB_DIR=/my/own/matlab``) prior to launch the command
or, even, you can update the resulting ``xmipp.conf`` file, once
created.

| · **``MATLAB``**: Main flag to enable/disable Matlab compilation, set
  to ``True``/``False`` accordingly. By default is set to ``True`` if a
  ``matlab`` is found in the PATH.
| · **``MATLAB_DIR``**: Matlab home directory where ``bin/mex`` is
  expected to compile Matlab code.
  ``dirname $(dirname $(which matlab))`` by default.

OpenCV configuration
--------------------

A few programs in Xmipp are coded using the OpenCV library and they
needs to be compiled against it. (*TODO: list those programs*)

Find below a list of tuneable variables regarding to OpenCV
compilations. Keep in mind that they are automatically set by Xmipp.
However, you can bypass this automatic setting by exporting them
(e.g. ``export OPENCV=False``) prior to launch the command or, even, you
can update the resulting ``xmipp.conf`` file, once created.

| · **``OPENCV``**: Main flag to enable/disable OpenCV compilation, set
  to ``True``/``False`` accordingly. By default, it is set to ``True``
  if a basic code including the ``opencv2/core/core.hpp`` header
  compiles.
| · **``OPENCV3``**: Flag to indicate if openCV-v3 is present, set to
  ``True``/``False`` accordingly. By default, it is set to ``True`` if
  the ``CV_MAJOR_VERSION >= 3`` in the ``opencv2/core/version.hpp``.
| · **``OPENCVSUPPORTSCUDA``**: Flag to enable/disable OpenCV
  compilation against CUDA, set to ``True``/``False`` accordingly. By
  default, it is set to ``True`` if a basic code including the
  ``cudaoptflow.hpp`` header compiles (if OpenCV-v3 is used, the
  ``cuda.hpp`` is used to check it).

Others
------

| · **``VERIFIED``**: Firstly, it is set to ``False`` and, then
  ``./xmipp check_config`` swaps it to ``True`` (if checks passes). This
  prevents to check the configuration twice.
| · **``CONFIG_VERSION``**: Config generator’s (``xmipp`` script) hash
  version. An error is raised if trying to compile Xmipp with a
  different hash than the current in the github repository.
| · **``USE_DL``**: Flag to download deep learning models during the
  compilation process. ``False`` by default.
| · **``DEBUG``**: Flag to compile the code under the debug mode.
  ``False`` by default.