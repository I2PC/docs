Tutorial: A quick introduction to the Google C++ Testing Framework
==================================================================

Summary
-------

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

Case 1: Adding a test to an existing file
-----------------------------------------

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
--------------------------

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
-------------------------

You may update the gold standard of the tests at the server by doing:

.. raw:: html

   <pre>
   bin/xmipp_sync_data update tests/data http://scipion.cnb.csic.es/downloads/scipion/data/tests xmipp_programs
   </pre>