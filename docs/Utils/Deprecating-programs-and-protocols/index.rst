Visit also: `List of deprecated programs and protocols<https://i2pc.github.io/docs/Utils/List-deprecated/index.html>`_

Deprecating programs
-----------------------

We have a "legacy" folder with programs and code that is outdated. Some of the reasons we did this are uninteresting code, programs that do not have a protocol and are not used, and programs that are not used and are difficult to maintain. You can `visit the issue <https://github.com/I2PC/xmipp/issues/681>`_ with more information and the list of deprecated programs and protocols can be found `here <https://github.com/I2PC/xmipp/wiki/List-of-deprecated-programs-and-protocols>`_.

We managed to speed up the installation time by 25%, and we were also able to reduce the lines of code to maintain and the number of code smells that were reported by `SonarCloud <https://sonarcloud.io/project/issues?id=Xmipp&languages=cpp&resolved=false&rules=cpp%3AS1172&types=CODE_SMELL>`_.

However, it is possible to recover a program if anyone needs it. Here's how to do it:

If you are an external user, please contact us (opening an issue is a good way, `see here <https://github.com/I2PC/xmipp/issues/new>`_).

If you are part of the Xmipp team:

Each deprecated program has an associated `commit <https://github.com/I2PC/xmipp/pull/685>`_. Visit it and review all the changes the program needs to be recovered. Here are some clues:

- Go to the legacy folder and
- Search in the _applications/programs_ folder for the folder of your program.
- Search in the _libraries_ folder for the script of your program.
- Most of the deprecated programs had a test; go to the commit and search in _tests_programs_xmipp.py_ for the test of your program.
- The last step is to remove the program that has been recovered from this list (see listDeprecatedFiles() in utils.py).
