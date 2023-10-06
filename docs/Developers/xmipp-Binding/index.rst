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
^^^^^^^^^^^^^^^^^

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
^^^^^^^^^^^^^^^^^

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
^^^^^^^^^^^^^^^^^

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
^^^^^^^^^^^^^^^^^

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
^^^^^^^^^^^^^^^^^

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