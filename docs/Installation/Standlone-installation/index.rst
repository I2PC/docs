Standalone installation
-----------------------

Standalone installation of Xmipp is recommended for researchers and developers. This installation allows you to use Xmipp without Scipion; however, in the next section, it is explained how to link it with Scipion. The Xmipp script automatically downloads several dependencies and then creates a configuration file that contains paths and flags used during the compilation. Please refer to the `Xmipp configuration <https://github.com/I2PC/xmipp/wiki/Xmipp-configuration>`_ guide for more info.

Start by cloning the repository and then navigate to the right directory.

Refer to ``./xmipp --help`` for additional info on the compilation process and possible customizations.

Next is to compile Xmipp. There are two possibilities, and in both, you will be able to run Xmipp in Scipion (see `linking step <https://github.com/I2PC/xmipp/edit/agm_refactoring_readme/README.md#linking-xmipp-standalone-to-scipion>`_):
- Compile Xmipp by invoking the compilation script, which will take you through the rest of the process: ``./xmipp``. That way, you will install Xmipp with the dependencies and their versions that the environment you decide, or the default one.
- Compile Xmipp via Scipion environment ``scipion3 run ./xmipp``. That way, you will install Xmipp with the dependencies and their versions that Scipion decided. 

It is important to highlight that this step only compiles Xmipp, but it does not link to Scipion. The linking to Scipion is explained in the next section.

Linking Xmipp standalone to Scipion
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Once the Standalone version has been installed, the user can link such installation to Scipion to have the possibility of using Xmipp inside Scipion. Linking with Scipion requires the repository of `scipion-em-xmipp`, which can be found in the folder `src/scipion-em-xmipp`. This repository contains the files that Scipion needs to execute Xmipp programs. However, it remains to link the Xmipp binaries with Scipion. To do that, we need Scipion installed (see `Scipion installation web page <https://scipion-em.github.io/docs/docs/scipion-modes/how-to-install.html#>`_) and just launch the next command to link the binaries:

where `scipion-em-xmipp` is the folder of the repository, it means `src/scipion-em-xmipp`. This command should work in most cases. However, if you do this and Scipion does not find Xmipp, please visit `Linking Xmipp to Scipion Troubleshooting <https://github.com/I2PC/xmipp/wiki/Linking-Xmipp-to-Scipion-Troubleshooting>`_.