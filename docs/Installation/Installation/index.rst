Installation with Scipion
================================

The recommended way for users (not developers) to install and use Xmipp is via the 
`Scipion framework <https://scipion-em.github.io/docs/release-3.0.0/docs/scipion-modes/how-to-install.html>`_, 
where you can use Xmipp with other Cryo-EM-related software. 

Xmipp will be installed during Scipion installation (pay attention to not include the flag *-noXmipp*).
You can also install Xmipp from the `plugin manager of Scipion <https://scipion-em.github.io/docs/release-3.0.0/docs/scipion-modes/how-to-install.html#installing-other-plugins>`_


Standlone-installation
====================================

This guide explains the standalone installation of Xmipp and the process to link it with Scipion. The standalone version allows you to use Xmipp independently of Scipion.

Installation
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

1. Clone the repository and navigate to the folder:

   .. code-block:: bash

      git clone https://github.com/I2PC/xmipp.git xmipp-bundle && cd xmipp-bundle

2. Compile Xmipp. You have two options:

    **Option 1:** Compile using the Scipion environment. This method installs Xmipp with dependencies managed by Scipion and is the recomended way.

    .. code-block:: bash

        scipion3 run ./xmipp


    **Option 2:** Compile the Xmipp alone. This method installs Xmipp with the required dependencies and versions defined by your environment or defaults.

    .. code-block:: bash

        ./xmipp

   Both methods only compile Xmipp. Linking it to Scipion is explained in the next section.

Note. For additional details about the compilation process, run:

   .. code-block:: bash

      ./xmipp --help

Linking Xmipp to Scipion
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

To use Xmipp within Scipion, link the standalone installation by following these steps:

1. Ensure Scipion is installed (refer to the *Scipion installation guide*).
2. Use the `scipion-em-xmipp` repository, located in `src/scipion-em-xmipp`.
3. Run the following command to link the binaries:

   .. code-block:: bash

      scipion3 installp -p ~/scipion-em-xmipp --devel

   Replace `~/scipion-em-xmipp` with the path to your `scipion-em-xmipp` folder.

Using Xmipp
~~~~~~~~~~~~~~

Xmipp is installed in the build directory located in the same directory where the xmipp script is located. To set all necessary environment variables and paths to all Xmipp programs, you can simply run 
   
   .. code-block:: bash

      source dist/xmipp.bashrc



Installation for HPC Clusters
===============================
