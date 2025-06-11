Checkout to a Specific Version
------------------------------------------

If you need to revert to a specific version of Xmipp or its associated repositories based on a particular date, you can achieve this using Git. This is useful, for example, when you encounter a new bug that was not present in an earlier version or when you have a long-lived branch in Xmipp that needs to be synchronized with a specific historical state.

Here is a step-by-step guide on how to accomplish this:

1. **Identify the Date**: Determine the date of the version you want to revert to. In the following example, we'll use "2020-09-27 08:57:42" as an example date.

2. **Checkout a Specific Commit**: Use the following command to checkout the latest commit on the "devel" branch before the specified date:

   ```bash
   git checkout `git rev-list -n 1 --first-parent --before="2020-09-27 08:57:42" devel`


Integrating with Visual Studio Code
--------------------------------------------

The CMake based installation script can be tightly integrated with any modern IDE. This section shows the procedure for Visual Studio Code (VSCode).

Before starting with the configuration process open a terminal and run the following commands. Anotate their outputs.

.. code-block:: bash

    conda activate scipion3 && echo $CONDA_PREFIX
    scipion3 printenv | grep SCIPION_SOFTWARE

In visual studio code
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

    1. In the "Extensions" tab install "C/C++ Extension Pack".
    2. File -> Open Folder -> Navigate to "xmipp" directory (previously cloned).
    3. Click "Yes, I trust the authors".
    4. File -> Save workspace as... -> Select a directory outside the Xmipp folder.
    5. Go to 5. File -> Preferences -> Configuration
    6. Select the "Workspace" tab
    7. Navigate to the "CMake Tools" section
    8. Set the following options
        "Cmake: Configure Args" add -DCMAKE_PREFIX_PATH=CONDA_PREFIX (replace CONDA_PREFIX with the value obtained previously)

        "Cmake: Configure Args" add -DCMAKE_SKIP_RPATH=ON

        "Cmake: Configure Environment" add: Element: Python3_ROOT_DIR Value: CONDA_PREFIX (replace CONDA_PREFIX with the value obtained previously)

        "Cmake: Configure Environment" add: Element: SCIPION_SOFTWARE Value: SCIPION_SOFTWARE (replace SCIPION_SOFTWARE with the value obtained previousy)

        "Cmake: Install prefix": /path-to/xmipp/dist (Absolute path)

    9. Go to the CMake tab on the left.
    10. In "Pinned commands" add "Install"

Once VS Code is set up, the Xmipp installation process can be launched though the newly pinned "Install" command. In addition, individual files or sub-projects may be compiled for quick assessment of code.


Parallel Programming
----------------------

Introduction
^^^^^^^^^^^^^^^^^^^^^

In the simplest sense, **parallel computing** is the simultaneous use of
multiple compute resources to solve a computational problem:

-  To be run using multiple CPUs
-  A problem is broken into discrete parts that can be solved
   concurrently
-  Each part is further broken down to a series of instructions
-  Instructions from each part execute simultaneously on different CPUs

The compute resources might be:

-  A single computer with multiple processors (using of **threads**);
-  An arbitrary number of computers connected by a network(using
   parallel library like **MPI**);
-  A combination of both.

The computational problem should be able to:

-  Be broken apart into discrete pieces of work that can be solved
   simultaneously;
-  Execute multiple program instructions at any moment in time;
-  Be solved in less time with multiple compute resources than with a
   single compute resource.

In **Xmipp3.0** we have develop several classes to make easier the use
of threads and MPI when developing parallel programs. If you want to
read more about parallel computing there is a nice introduction
`here <https://computing.llnl.gov/tutorials/parallel_comp/>`__. ## Task
distribution

One of the first steps in designing a parallel program is to break the
problem into discrete “chunks” of work that can be distributed to
multiple tasks. This is known as decomposition or partitioning. There
are two basic ways to partition computational work among parallel tasks:
the data is partitioned or the work to be done.

In image processing for *single particles* on electron microscopy we
usually deal with several thousands of images, so the most common and
easy way to distribute is by data. Then each CPU take care of some part
of the data to perform processing tasks.

We have create the class **[[ParallelTaskDistributor]]** which have the
function to distribute N tasks (without knowing what each “task” really
means) between a group of workers (threads or MPI). Each worker will ask
for a some tasks, process it and ask for more tasks until there is
nothing to be done. The following are several subclasses of
`ParallelTaskDistributor <http://xmipp.cnb.uam.es/~xmipp/trunk/xmipp/documentation/html/classParallelTaskDistributor>`__:

::


     //...
     // Create a task distributor with N total task and serve 10 on each request
     ParallelTaskDistributor * td = new ThreadTaskDistributor(N, 10);
     //...
     //function to perform some operation
     //to N images executed in parellel
     void processSeveralImages()
     {
         size_t firstImage, lastImage;
         while (td->getTasks(firstImage, lastImage))
             for (size_t image = firstImage; image <= lastImage; ++image)
             {
                 //...
                 processOneImage(image);
                 //...
             }
     }

Using threads
^^^^^^^^^^^^^^^^^^^^^

Technically, a **thread** is defined as an independent stream of
instructions that can be scheduled to run as such by the operating
system. Before understanding a thread, one first needs to understand a
UNIX process. A process is created by the operating system, and requires
a fair amount of “overhead”. Processes contain information about program
resources and program execution state, including: Process ID, process
group ID, user ID, and group ID, environment, working directory, program
instructions, registers, stack, heap, file descriptors, signal actions,
shared libraries, inter-process communication tools (such as message
queues, pipes, semaphores, or shared memory). Threads use and exist
within these process resources, yet are able to be scheduled by the
operating system and run as independent entities largely because they
duplicate only the bare essential resources that enable them to exist as
executable code.

So, in summary, in the UNIX environment a thread:

-  Exists within a process and uses the process resources
-  Has its own independent flow of control as long as its parent process
   exists and the OS supports it
-  Duplicates only the essential resources it needs to be independently
   schedulable
-  May share the process resources with other threads that act equally
   independently (and dependently)
-  Dies if the parent process dies - or something similar
-  Is “lightweight” because most of the overhead has already been
   accomplished through the creation of its process.

Because threads within the same process share resources:

-  Changes made by one thread to shared system resources (such as
   closing a file) will be seen by all other threads.
-  Two pointers having the same value point to the same data.
-  Reading and writing to the same memory locations is possible, and
   therefore requires explicit synchronization by the programmer.

A more detailed explanation about use of POSIX threads can be found
 here. ### Creating threads and passing parameters

Imagine that you have a program that perform tasks *A*, *B* and *C*, and
tasks *A* and *C* task can be threaded. So, task *A* can be splited in
several concurrent tasks *A1, A2, A3…An* and the same for C. In the
following figure you can see the serial and threaded version of the
program execution:

This type of threading now can be easily done using the following
classes:

-  *[[ThreadManager]]* will create the threads and run diffent functions
   in parallel
-  *[[ThreadFunction]]* prototype of function that can be runned by
   *[[ThreadManager]]*.
-  Its definition is typedef void( **[[ThreadFunction]] )(ThreadArgument
   &arg) typedef void(** [[ThreadFunction]] )(ThreadArgument &arg)
-  *[[ThreadArgument]]*: Argument type that is passed to
   *[[ThreadFunction]]*. It contains:
-  thread_id: number identifying each thread
-  data: void \* pointer to pass additional information
-  workClass: void \* pointer to hold a reference to working class

The previous example can be coded:

::


      void * functionA(ThreadArgument & data)
     {
         //...     
     }
      void * functionB()
     {
         //...     
     }
      void * functionC(ThreadArgument & data)
     {
         //...     
     }

     int main()
     {
     //Start 4 threads to work
     ThreadManager * tm = new ThreadManager(4);
     // Run in parallel functionA
     tm.run(functionA);
     // All threads are syncronized at this point
     functionB(); 
     //If you need to pass some additional information
    // to work on functionB you can do:
    tm.setData(myData);
     // Put the threads works on functionB
     tm.run(functionB);
     }

Synchronizing threads
^^^^^^^^^^^^^^^^^^^^^

Synchronization is vital for almost all parallel programs. We want
things done faster but also we want things done well. Through
synchronization we can guarantee that things are done in the correct
order and provide the same results as if it was done sequentially.

Synchronization between threads is done primarily through mutexes. A
mutex allows to protect a portion of the code so only one thread can
access it at a time. We have created the *Mutex* class wich encapsulates
the mutex creation, initialization and clean up through the *pthreads*
library.

::


   Mutex mutexUpdate;
   //....
   // Inside some threaded function:
   mutexUpdate.lock();
   //Perform the updated
   mutexUpdate.unlock();

Other different synchronization structures exist that can adapt better
to different circumstances. For example, a barrier is used when we want
to synchronize a number of threads at a point of the code so no one can
continue working until all of them have reached such point. Barriers are
not always present on all computing platforms. For example, old Unix
implementations do not have such structure defined on the pthreads
library. To avoid problems of this type, a *Barrier* class have been
implemented base on mutexes. ### Example

 Here you will find a complete example of a parallel program using all
the elements together. This example estimate the value of PI. ### Some
Tips

Programming threads is easy… but debugging threads can be a nightmare.
So take note of these tips:

-  Do not use static variables on threaded code. Such variables are
   shared between all threads and can lead to unexpected results.
-  Do not use threads for everything. Use them when it is clear they
   will represent an advantage. Using too much threads will lead to a
   decreared performance.
-  Try to create threads once and reuse them. Creating and destroying
   threads will represent a slight overhead. On some applications this
   can translate into lower performance. (Create just one
   *[[ThreadManager]]* and run several functions )
-  Be careful with critical regions and the use of *Mutex* and
   *Barrier*. A misuse can lead to race conditions(bad results) or
   deadlock (program will runs forever)

Programming with MPI
^^^^^^^^^^^^^^^^^^^^^

The Message Passing Interface Standard ( **MPI**) is a message passing
library standard based on the consensus of the MPI Forum, which has over
40 participating organizations, including vendors, researchers, software
library developers, and users. The goal of the Message Passing Interface
is to establish a portable, efficient, and flexible standard for message
passing that will be widely used for writing message passing programs.
As such, MPI is the first standardized, vendor independent, message
passing library. The advantages of developing message passing software
using MPI closely match the design goals of portability, efficiency, and
flexibility. MPI is not an IEEE or ISO standard, but has in fact, become
the “industry standard” for writing message passing programs on HPC
platforms. You can find more about MPI  here.

We have created some useful classes like *[[MpiNode]]* that will take
care of some MPI initialization and cleaning. This class also have a
method to synchronize: *barrierWait* and other utilities. The same
concepts for task distribution can be used with MPI through the
*[[MpiTaskDistributor]]* class.

A complete example using the MPI tools is available  Here .



Google C++ Testing Framework
-------------------------------------------------------------------

Summary
^^^^^^^^^^^^^^^^^

Unit testing is a development procedure where programmers create tests
as they develop software. The tests are simple short tests that test
functionality of a particular unit or module of their code, such as a
class or function. Using libraries like gtest these tests can be
automatically run and any problems found quickly. As the tests are
developed in parallel with the source code, when the particular unit is
completed, a successful unit test demonstrates it’s correctness.

Xmipp incorporates in its code the Google C++ Unit Testing Framework,
`gtest <http://code.google.com/p/googletest/>`__ for short (version
1.6). This tutorial explains how you may use this unit testing
framework. ## Basic Concepts

(extract from
`http://code.google.com/p/googletest/wiki/V1_6_Primer#Introduction:_Why_Google_C++_Testing_Framework?) <http://code.google.com/p/googletest/wiki/V1_6_Primer#Introduction:_Why_Google_C++_Testing_Framework?>`__)

When using gtests, you start by writing assertions, which are statements
that check whether a condition is true. An assertion’s result can be
success, nonfatal failure, or fatal failure. If a fatal failure occurs,
it aborts the current function; otherwise the program continues
normally.

Tests use assertions to verify the tested code’s behavior. If a test
crashes or has a failed assertion, then it fails; otherwise it succeeds.

A test case contains one or many tests. You should group your tests into
test cases that reflect the structure of the tested code. When multiple
tests in a test case need to share common objects and subroutines, you
can put them into the same test file. ## Assertions

(extract from
`http://code.google.com/p/googletest/wiki/V1_6_Primer#Introduction:_Why_Google_C++_Testing_Framework?) <http://code.google.com/p/googletest/wiki/V1_6_Primer#Introduction:_Why_Google_C++_Testing_Framework?>`__)

Gtest assertions are macros that resemble function calls. You test a
class or function by making assertions about its behavior. When an
assertion fails, gest prints the assertion’s source file and line number
location, along with a failure message. You may also supply a custom
failure message which will be appended to Google Test’s message.

The assertions come in pairs that test the same thing but have different
effects on the current function. ASSERT_\* versions generate fatal
failures when they fail, and abort the current function. EXPECT_\*
versions generate nonfatal failures, which don’t abort the current
function. Usually EXPECT_\* are preferred, as they allow more than one
failures to be reported in a test. However, you should use ASSERT_\* if
it doesn’t make sense to continue when the assertion in question fails.

Since a failed ASSERT_\* returns from the current function immediately,
possibly skipping clean-up code that comes after it, it may cause a
space leak. Depending on the nature of the leak, it may or may not be
worth fixing - so keep this in mind if you get a heap checker error in
addition to assertion errors.

To provide a custom failure message, simply stream it into the macro
using the << operator. Example:

ASSERT_EQ(x.size(), y.size()) << “Vectors x and y are of unequal
length”;

for (int i = 0; i < x.size(); ++i) { EXPECT_EQ(x[i], y[i]) << “Vectors x
and y differ at index” << i; }

More about assertion is available
`here <http://code.google.com/p/googletest/wiki/Primer#Assertions>`__ #
gtest in Xmipp

Xmipp already incorporates gtest natively so you do not need to compile
any extra library. ## General Rules

-  Ideally they should be a test for each routine.
-  Test can be found in the directory
   $HOME_XMIPP/application/tests/test_className
-  Test output must be written in the /tmp directory as temporary files.
   These files should be deleted once the test is finished.
-  If possible input data should be created on the fly. If some input
   file is needed it should be place in
   $HOME_XMIPP/resources/test/className
-  Test are part of the software development cycle and should be written
   BEFORE and not AFTER the creation of new routines.

Adding a test to an existing file
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

In this section we will assume that you want to add a test for a class
that has already been incorporated in the test system. Let us assume
that we want to add a test for the metadata class. This test will check
that a function called *Factorial(n)* that compute the factorial number
of *n* works properlly.

-  Edit file at
   *$XMIPP_HOME/pplications/tests/test_metadata/test_metadata_main.cpp*
-  Use the TEST_F() macro to define and name a test function, These are
   ordinary C++ functions that don’t return a value.

TEST_F() arguments go from general to specific. The first argument is
the name of the test case, and the second argument is the test’s name
within the test case. Both names must be valid C++ identifiers, and they
should not contain underscore (_).

For example, let’s take a simple integer function: int Factorial(int n);
// Returns the factorial of n.

A test case for this function might look like:

// Tests factorial of 0. TEST_F(MetadataTest, FactorialHandlesZeroInput)
{ EXPECT_EQ(1, Factorial(0)); }

// Tests factorial of positive numbers. TEST_F(MetadataTest,
FactorialHandlesPositiveInput) { EXPECT_EQ(1, Factorial(1));
EXPECT_EQ(2, Factorial(2)); EXPECT_EQ(6, Factorial(3)); EXPECT_EQ(40320,
Factorial(8)); }

In addition to the code you have written gtest will create a “fresh”
environment each time a particular test_f is executed:

-  First, initialize running the routineSetUp() ,
-  Then, execute the test
-  After that, clean up by callingTearDown()
-  No data structures allocated in memory may be reuse from one test to
   the next one

In the case of *metadata*, the *[[SetUp]]* routine creates three basic
metadata and `[TearDown] <>`__ is not defined. ## Case 2: Create Unit
tests for a new class

In this section we will assume that you want to add a test for a class
that has NOT been incorporated in the test system. Let us create a test
for a class called *myPrettyClass*

-  Create a new directory called
   *$XMIPP_HOME/application/test/test_myPrettyClass*
-  Create a new file in this directory called
   *test_myPrettyClass_main.cpp*
-  Edit the *test_myPrettyClass_main.cpp* file, use the bellow template
   for starting
-  Edit *$XMIPP_HOME/SConscript*
-  Look for the line `[AddXmippCTest] <'test_fftw'>`__
-  Add the line `[AddXmippCTest] <'test_myPrettyClass'>`__ in this
   section

.. raw:: html

   <!-- * Set FORMAT_PREPEND=<style type="text/css"> -->

#include “../../../external/gtest-1.6.0/fused-src/gtest/gtest.h”

class myPrettyClassTest : public ::testing::Test { protected:

virtual void `[SetUp] <>`__ { // Code here will be called immediately
after the constructor (right // before each test). }

virtual void `[TearDown] <>`__ { // Code here will be called immediately
after each test (right // before the destructor). }

// Objects declared here can be used by all tests in the test case for
Foo. };

// Tests that the myPrettyClassTest::Bar() method does Abc.
TEST_F(myPrettyClass, MethodBarDoesAbc) { FileName input_filepath =
“this/package/testdata/myinputfile.dat”; FileName output_filepath =
“this/package/testdata/myoutputfile.dat”; Foo f; EXPECT_EQ(0,
f.Bar(input_filepath, output_filepath)); }

// Tests that Foo does Xyz. TEST_F(myPrettyClass, DoesXyz) { //
Exercises the Xyz feature of Foo. }

GTEST_API\_ int main(int argc, char \**argv) {
testing::InitGoogleTest(&argc, argv); return RUN_ALL_TESTS(); } ##
Compile and Invoke the Tests

In a few words:

-  compile:

   .. raw:: html

      <pre> xcompile xmipp_test_myPrettyClass</pre>

-  compile and execute:

   .. raw:: html

      <pre> xcompile run_test_myPrettyClass</pre>

-  execute:

   .. raw:: html

      <pre> xmipp_test_myPrettyClass</pre>

Example of execution of the test *xmipp_test_matrix* :

.. raw:: html

   <pre>roberto@tumbao:~/xmipp_svn$ xmipp_test_matrix
   [==========] Running 4 tests from 1 test case.
   [----------] Global test environment set-up.
   [----------] 4 tests from [[MatrixTest]]
   [ RUN      ] [[MatrixTest]].inverse
   [       OK ] [[MatrixTest]].inverse (0 ms)
   [ RUN      ] [[MatrixTest]].det3x3
   [       OK ] [[MatrixTest]].det3x3 (0 ms)
   [ RUN      ] [[MatrixTest]].solveLinearSystem
   [       OK ] MatrixTest.solveLinearSystem (0 ms)
   [ RUN      ] MatrixTest.initGaussian
   [       OK ] MatrixTest.initGaussian (0 ms)
   [----------] 4 tests from MatrixTest (1 ms total)

   [----------] Global test environment tear-down [==========] 4 tests from 1 test case ran. (1 ms total) [  PASSED  ] 4 tests. roberto@tumbao:~/xmipp_svn$  </pre>

Unittest checking workflow
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

When a unittest is generated, sometimes its result is very tied to the
machine where it is generated (some mathematical results depends on the
compiler, libraries that may differ). This may drive the test to a
failure as long as the result in the testing machine could be a little
different from the goldStandard machine. We recommend giving the test a
little tolerance to avoid this false failures. The workflow after a test
is generated is the following:

1 A test is generated, the goldStandard is generated in the owner’s
machine. 1 The test is uploaded to the repository. 1 That night, tests
will be passed on einstein, and results are sent to the sysadmins. 1 In
case of failure sysadmins check with the owner whether or not it is a
tolerance problem. 1 If it’s just a tolerance problem, then goldStandard
is regenerated on einstein and owner assume that a failure in that test
in his machine doesn’t mean a thing. 1 If it’s not, then the owner takes
the responsability of repairing the test

Setting the gold standard
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

You may update the gold standard of the tests at the server by doing:

.. raw:: html

   <pre>
   bin/xmipp_sync_data update tests/data http://scipion.cnb.csic.es/downloads/scipion/data/tests xmipp_programs
   </pre>


   Python Binding 
--------------------

`Text borrowed from here <http://www.tutorialspoint.com/python/python_further_extensions.htm>`_

Any code that you write using any compiled language like C, C++ or Java
can be integrated or imported into a Python script. This code is
considered as an “extension”. A Python extension module is nothing more
than a normal C library. On Unix machines, writting extensions, usually
requires installing a developer-specific package such as python2.5-dev.

For your first look at a Python extension module, you’ll be grouping
your code into three parts:

-  The C functions you want to expose as the interface from your module.
-  A table mapping the names of your functions as Python developers will
   see them to C functions inside the extension module.
-  An initialization function.

The C functions:
^^^^^^^^^^^^^^^^^

The signatures of the C implementations of your functions will always
take one of the following three forms:

static [[PyObject]] *MyFunction( PyObject*\ self, PyObject \*args );

static [[PyObject]] *MyFunctionWithKeywords(PyObject*\ self, PyObject
*args, PyObject*\ kw);

static [[PyObject]] *MyFunctionWithNoArgs( PyObject*\ self );

Each one of the preceding declarations returns a Python object. There’s
no such thing as a void function in Python as there is in C. If you
don’t want your functions to return a value, return the C equivalent of
Python’s None value. The Python headers define a macro, Py_RETURN_NONE,
that does this for us.

The names of your C functions can be whatever you like as they will
never be seen outside of the extension module. So they would be defined
as static function.

Your C functions usually are named by combining the Python module and
function names together, as shown here: static [[PyObject]] \*
[[FileName]] \_isImage(PyObject *obj, PyObject*\ args, PyObject
\*kwargs) { if (isImage(FileName \_Value(obj))) Py_RETURN_TRUE; else
Py_RETURN_FALSE; }

This would be a Python function called isImage inside of the module
[[FileName]]. You’ll be putting pointers to your C functions into the
method table for the module that usually comes next in your source code.

The method mapping table
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

This method table is a simple array of [[PyMethodDef]] structures. That
structure looks something like this: struct [[PyMethodDef]] { char
*ml_name; [[PyCFunction]] ml_meth; int ml_flags; char*\ ml_doc; };

Here is the description of the members of this structure:

``ml_name:`` This is the name of the function as the Python interpreter
will present it when it is used in Python programs.

``ml_meth:`` This must be the address to a function that has any one of
the signatures described in previous seection.

``ml_flags:`` This tells the interpreter which of the three signatures
ml_meth is using.

This flag will usually have a value of METH_VARARGS.

This flag can be bitwise or’ed with METH_KEYWORDS if you want to allow
keyword arguments into your function.

This can also have a value of METH_NOARGS that indicates you don’t want
to accept any arguments.

``ml_doc:`` This is the docstring for the function, which could be NULL
if you don’t feel like writing one

This table needs to be terminated with a sentinel that consists of NULL
and 0 values for the appropriate members.

Example:

static[[PyMethodDef]][[FileName]]_methods[] = { { “compose”,
(PyCFunction) FileName_compose, METH_VARARGS, “Compose from root, number
and extension OR prefix with number @” }, { “composeBlock”,
(PyCFunction) FileName_composeBlock, METH_VARARGS, “Compose from
blockname, number, root and extension” }, { NULL } /\* Sentinel \*/ };

The initialization function
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The last part of your extension module is the initialization function.
This function is called by the Python interpreter when the module is
loaded. It’s required that the function be named\ ``initModule``, where
Module is the name of the module (the name is\ ``initxmipp`` in our
case).

Your C initialization function generally has the following overall
structure:

[[PyMODINIT]]\ *FUNC initModule() {
Py*\ `[InitModule3] <func,%20module_methods,>`__; }

Here is the description of Py_InitModule3 function:

``func:`` This is the function to be exported.

``module_methods:`` This is the mapping table name defined above.

``docstring:`` This is the comment you want to give in your extension.

Example:

[[PyMODINIT]]_FUNC initxmipp(void) { //Initialize module
variable[[PyObject]]\* module; module = Py_InitModule3(“xmipp”,
xmipp_methods, “Xmipp module as a Python extension.”);

… }

All together
^^^^^^^^^^^^^^^^^

A simple example that makes use of all the above concepts:

#include <Python.h>

static[[PyObject]]\* helloworld(PyObject\* self) { return
Py_BuildValue(“s”, “Hello, Python extensions!!”); }

static char helloworld_docs[] = “helloworld( ): Any message you want to
put here!!:raw-latex:`\n`”;

static[[PyMethodDef]] helloworld_funcs[] = { {“helloworld”,
(PyCFunction)helloworld, METH_NOARGS, helloworld_docs}, {NULL} };

void inithelloworld(void) { Py_InitModule3(“helloworld”,
helloworld_funcs, “Extension module example!”); }

Passing Function parameters
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Most of the time you will add functions to an existing module. For
example, the following function, that accepts some number of parameters,
would be defined like this:

static[[PyObject]]\ **module_func(PyObject self, PyObject\ args) { /**
Parse args and do something interesting here. \*/ Py_RETURN_NONE; }

The method table containing an entry for the new function would look
like this:

static[[PyMethodDef]] module_methods[] = {

{ “func”, module_func, METH_VARARGS, “help message” }, { NULL, NULL, 0,
NULL } };

You can use API\ ``[[PyArg]]_ParseTuple`` function to extract the
arguments from the one[[PyObject]] pointer passed into your C function.

The first argument to\ ``[[PyArg]]_ParseTuple`` is the args argument.
This is the object you’ll be parsing. The second argument is a format
string describing the arguments as you expect them to appear. Each
argument is represented by one or more characters in the format string
as follows.

static[[PyObject]] *module_func(PyObject*\ self, PyObject *args) { int
i; double d; char*\ s;

if (!PyArg_ParseTuple(args, “ids”, &i, &d, &s)) { return NULL; }

/\* Do something interesting here. \*/ Py_RETURN_NONE; }

Compiling the new version of your module and importing it will enable
you to invoke the new function with any number of arguments of any type:

The PyArg \_ParseTuple Function
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Here is a list of format codes for[[PyArg]] \_ParseTuple function:

.. raw:: html

   <table>

.. raw:: html

   <tr>

.. raw:: html

   <td>

Code

.. raw:: html

   </td>

.. raw:: html

   <td>

C type

.. raw:: html

   </td>

.. raw:: html

   <td>

Meaning

.. raw:: html

   </td>

.. raw:: html

   </tr>

.. raw:: html

   <tr>

.. raw:: html

   <td>

c

.. raw:: html

   </td>

.. raw:: html

   <td>

char

.. raw:: html

   </td>

.. raw:: html

   <td>

A Python string of length 1 becomes a C char.

.. raw:: html

   </td>

.. raw:: html

   </tr>

.. raw:: html

   <tr>

.. raw:: html

   <td>

d

.. raw:: html

   </td>

.. raw:: html

   <td>

double

.. raw:: html

   </td>

.. raw:: html

   <td>

A Python float becomes a C double.

.. raw:: html

   </td>

.. raw:: html

   </tr>

.. raw:: html

   <tr>

.. raw:: html

   <td>

f

.. raw:: html

   </td>

.. raw:: html

   <td>

float

.. raw:: html

   </td>

.. raw:: html

   <td>

A Python float becomes a C float.

.. raw:: html

   </td>

.. raw:: html

   </tr>

.. raw:: html

   <tr>

.. raw:: html

   <td>

i

.. raw:: html

   </td>

.. raw:: html

   <td>

int

.. raw:: html

   </td>

.. raw:: html

   <td>

A Python int becomes a C int.

.. raw:: html

   </td>

.. raw:: html

   </tr>

.. raw:: html

   <tr>

.. raw:: html

   <td>

l

.. raw:: html

   </td>

.. raw:: html

   <td>

long

.. raw:: html

   </td>

.. raw:: html

   <td>

A Python int becomes a C long.

.. raw:: html

   </td>

.. raw:: html

   </tr>

.. raw:: html

   <tr>

.. raw:: html

   <td>

L

.. raw:: html

   </td>

.. raw:: html

   <td>

long long

.. raw:: html

   </td>

.. raw:: html

   <td>

A Python int becomes a C long long

.. raw:: html

   </td>

.. raw:: html

   </tr>

.. raw:: html

   <tr>

.. raw:: html

   <td>

O

.. raw:: html

   </td>

.. raw:: html

   <td>

[[PyObject]]\*

.. raw:: html

   </td>

.. raw:: html

   <td>

Gets non-NULL borrowed reference to Python argument.

.. raw:: html

   </td>

.. raw:: html

   </tr>

.. raw:: html

   <tr>

.. raw:: html

   <td>

s

.. raw:: html

   </td>

.. raw:: html

   <td>

char\*

.. raw:: html

   </td>

.. raw:: html

   <td>

Python string without embedded nulls to C char*.

.. raw:: html

   </td>

.. raw:: html

   </tr>

.. raw:: html

   <tr>

.. raw:: html

   <td>

s#

.. raw:: html

   </td>

.. raw:: html

   <td>

char*+int

.. raw:: html

   </td>

.. raw:: html

   <td>

Any Python string to C address and length.

.. raw:: html

   </td>

.. raw:: html

   </tr>

.. raw:: html

   <tr>

.. raw:: html

   <td>

t#

.. raw:: html

   </td>

.. raw:: html

   <td>

char*+int

.. raw:: html

   </td>

.. raw:: html

   <td>

Read-only single-segment buffer to C address and length.

.. raw:: html

   </td>

.. raw:: html

   </tr>

.. raw:: html

   <tr>

.. raw:: html

   <td>

u

.. raw:: html

   </td>

.. raw:: html

   <td>

Py_UNICODE\*

.. raw:: html

   </td>

.. raw:: html

   <td>

Python Unicode without embedded nulls to C.

.. raw:: html

   </td>

.. raw:: html

   </tr>

.. raw:: html

   <tr>

.. raw:: html

   <td>

u#

.. raw:: html

   </td>

.. raw:: html

   <td>

Py_UNICODE*+int

.. raw:: html

   </td>

.. raw:: html

   <td>

Any Python Unicode C address and length.

.. raw:: html

   </td>

.. raw:: html

   </tr>

.. raw:: html

   <tr>

.. raw:: html

   <td>

w#

.. raw:: html

   </td>

.. raw:: html

   <td>

char*+int

.. raw:: html

   </td>

.. raw:: html

   <td>

Read/write single-segment buffer to C address and length.

.. raw:: html

   </td>

.. raw:: html

   </tr>

.. raw:: html

   <tr>

.. raw:: html

   <td>

z

.. raw:: html

   </td>

.. raw:: html

   <td>

char\*

.. raw:: html

   </td>

.. raw:: html

   <td>

Like s, also accepts None (sets C char\* to NULL).

.. raw:: html

   </td>

.. raw:: html

   </tr>

.. raw:: html

   <tr>

.. raw:: html

   <td>

z#

.. raw:: html

   </td>

.. raw:: html

   <td>

char*+int

.. raw:: html

   </td>

.. raw:: html

   <td>

Like s#, also accepts None (sets C char\* to NULL).

.. raw:: html

   </td>

.. raw:: html

   </tr>

.. raw:: html

   <tr>

.. raw:: html

   <td>

(…)

.. raw:: html

   </td>

.. raw:: html

   <td>

as per …

.. raw:: html

   </td>

.. raw:: html

   <td>

A Python sequence is treated as one argument per item.

.. raw:: html

   </td>

.. raw:: html

   </tr>

.. raw:: html

   <tr>

.. raw:: html

   <td>

.. raw:: html

   </td>

.. raw:: html

   <td>

.. raw:: html

   </td>

.. raw:: html

   <td>

The following arguments are optional.

.. raw:: html

   </td>

.. raw:: html

   </tr>

.. raw:: html

   <tr>

.. raw:: html

   <td>

:

.. raw:: html

   </td>

.. raw:: html

   <td>

.. raw:: html

   </td>

.. raw:: html

   <td>

Format end, followed by function name for error messages.

.. raw:: html

   </td>

.. raw:: html

   </tr>

.. raw:: html

   <tr>

.. raw:: html

   <td>

;

.. raw:: html

   </td>

.. raw:: html

   <td>

.. raw:: html

   </td>

.. raw:: html

   <td>

Format end, followed by entire error message text.

.. raw:: html

   </td>

.. raw:: html

   </tr>

.. raw:: html

   </table>

Returning Values:
^^^^^^^^^^^^^^^^^

Py_BuildValue takes in a format string much like PyArg \_ParseTuple
does. Instead of passing in the addresses of the values you’re building,
you pass in the actual values. Here’s an example showing how to
implement an add function:

static[[PyObject]] *foo_add(PyObject*\ self, PyObject \*args) { int a;
int b;

if (!PyArg_ParseTuple(args, “ii”, &a, &b)) { return NULL; } return
Py_BuildValue(“i”, a + b); }

This is what it would look like if implemented in Python:

You can return two values from your function as follows, this would be
cauptured using a list in Python.

static[[PyObject]] *foo_add_subtract(PyObject*\ self, PyObject \*args) {
int a; int b;

if (!PyArg_ParseTuple(args, “ii”, &a, &b)) { return NULL; } return
Py_BuildValue(“ii”, a + b, a - b); }

This is what it would look like if implemented in Python:

Calling Python (+numpy) from C
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Here is an example code to perform the sum of two volumes in Python:

#include <data/xmipp_image.h>

#include <Python.h> #include <numpy/ndarrayobject.h>

void myImport_array() { import_array(); }

int main() { try { time_config();

Image I;
I.read(“/home/coss/temp/BPV_Project/BPV_scale_filtered_windowed.vol”);[[ProcessorTimeStamp]]
t0; const[[MultidimArray]] &mI=I(); annotate_processor_time(&t0); double
retval=0.0; FOR_ALL_DIRECT_ELEMENTS_IN_MULTIDIMARRAY(mI)
retval+=DIRECT_MULTIDIM_ELEM(mI,n)+DIRECT_MULTIDIM_ELEM(mI,n); std::cout
<< elapsed_time(t0,false) << std::endl; std::cout << “In C++:” << retval
<< std::endl;

std::cout << “Initializing Python:raw-latex:`\n`”;
annotate_processor_time(&t0); Py_Initialize(); myImport_array();
std::cout << elapsed_time(t0,false) << std::endl;

// Create numpy array in Python with I() std::cout << “Creating numpy
array:raw-latex:`\n`”; annotate_processor_time(&t0); npy_intp dim[3];
dim[0]=ZSIZE(I()); dim[1]=YSIZE(I()); dim[2]=XSIZE(I());[[PyObject]]
*pyI=PyArray_SimpleNewFromData(3, dim, NPY_DOUBLE,
(void*)MULTIDIM_ARRAY(I())); std::cout << elapsed_time(t0,false) <<
std::endl;

// Import testPython std::cout << “Importing module:raw-latex:`\n`”;
annotate_processor_time(&t0);[[PyObject]]\* pName
=[[PyString]]_FromString(“testPython”); // Import testPython PyObject\*
pModule = PyImport_Import(pName); Py_DECREF(pName); std::cout <<
elapsed_time(t0,false) << std::endl;

// Call sum std::cout << “Calling sum:raw-latex:`\n`”;
annotate_processor_time(&t0); [[PyObject]] *arglist =
Py_BuildValue(“OO”, pyI, pyI); PyObject*\ pFunc =
PyObject_GetAttrString(pModule, “sum”); PyObject \*result =
PyObject_CallObject(pFunc, arglist); std::cout << elapsed_time(t0,false)
<< std::endl; std::cout << “In Python:” << PyFloat_AsDouble(result) <<
std::endl; } catch (XmippError e) { std::cout << e << std::endl; }
return 0; }

You have to compile with

xmipp_compile -i myCode.cpp –python

And the Python code is