Guidelines
------------

Programming - Handling images
^^^^^^^^^^

Although Xmipp supports stacks of volumes (4 dimensions arrays) in
memory, it is recommended to avoid allocate in memory as much images as
possible at once. If your code is going to iterate over a set of images
stored in a stack file, then you should try accessing each image at
once. 

Coding - C++ guidelines
^^^^^^^^^^^^^^^^^^^^^^^

Source code is like the text of a book, it is possible to be understood
with almost any formatting but much more easier if it is done properly.
Forcing a certain indentation style is important in free-form languages
like C or C++, just as publishers and book printers do.

That said, these are the proposed guidelines for writing C++ code:

1. Same language for code and comments, English in this case.

2. Use the header guard standard. The easiest option is the file name,
   in caps, without in-between underscores, and with a =_H= at the end:

::


      #ifndef HASHINFO_H
      #define HASHINFO_H

      // This file is called "HashInfo.h"

      #endif
      

1. Group the system includes (``&lt; &gt;``), as well as the local ones
   (``" "``). A blank line should be in between:

::


      #include <iostream>
      #include <string>
      #include <vector>

      #include "Timer.h"
      #include "HashInfo.h"
      

1. Do not use more than one blank line to separate sections:

::


      const int globalVar = 0;

      // Just one blank line
      struct Foo
      {
              // ...
      };

      // Just one blank line
      

1. Choose a consistent name criteria. The following is very common:

-  CamelCase notation: use a capital letter when a new word starts.

-  Classes/structs begin with a capital letter.

-  Variables and functions begin in lowercase.

-  Functions have imperative names

-  Use descriptive variable names, the only exception are those with a
   very limited lifespan, like:``i``,\ ``j``,\ ``tmp``,\ ``aux``\ …

1. Indent with spaces, not with tabs. The recommended value is__4_\_
   spaces. Most_decent\_ editors can convert automatically tabs into
   spaces.

2. Save files with\ ``UNIX`` end-of-line characters.

3. Use a pair of files for each class (``.cpp`` y\ ``.h``). Avoid inner
   classes.

4. Follow\ ``Doxygen`` guidelines for documentation.

5. Position of\ ``{}``:

-  for

::


      for (int i=0; i<limit; i++)
      {
          // do something
      }
      

-  if, else

::


      if (something)
      {
          // do something
      }
      else
      {
          // do something else
      }
      

-  while

::


      while (i>0)
      {
          // do something
      }
      

-  switch, case

::


      switch (tmp)
      {
          case 0:
              // do something
              break;
          case 1:
              // do something
              break;
          default:
              // do something
      }
      

1. Limit line lenght to__80_\_ chars (printing). Indent one time
   afterwards.

2. Use methods with few parameters, but on those times when it’s not
   possible, give each parameter a line:

::


      void functionWithManyParams(int par1,
          float par2,
          char* par3,
          std::vector< double >& par4,
          double par5);
      

1.  Compile with at least\ ``-Wall -ansi``. Pay attention to warnings
    too.

2.  Make a test program for each class.

3.  Do not make optimizations without verifying they are needed. Aim for
    clear code.

4.  Do not open namespaces in global scope.

5.  Include every header that is needed for the code in that particular
    file. In\ ``.h`` files use forward declarations when possible.

6.  Use a good editor with the following feature: folding, syntax
    highlighting, autocompletion, line numbers…

7.  Do not use\ ``malloc`` or\ ``free``, C++ uses\ ``new``
    and\ ``delete``.

8.  Use\ ``const`` instead of\ ``#define``. Avoid the preprocessor.

9.  Use variables as local as possible. Do not group variable
    definitions at the beginning of a method (old\ ``ANSI C``
    requirement).

10. Always clean up your code of unused variables. ## Code formatting

Automatic code formatting can be achieved using a program like astyle.
It can reindent and reformat C, C++ and Java code. It can be used from
the command-line or integrated into another program, like Eclipse or
Emacs.

Although not 100% accurate it performs most of the hard work required to
follow basic style guidelines.

It accepts several command-line options, or an options file with the
equivalent entries. Command-line use is:

::


   $ astyle [options] < !OriginalSourceFile > !BeautifiedSourceFile

From the various predefined styles we are currently using ANSI, and the
full options file\ ``.astylerc`` is:

::


   style=ansi
   brackets=break
   indent-preprocessor
   min-conditional-indent=0
   unpad=paren
   pad=oper
   convert-tabs



   