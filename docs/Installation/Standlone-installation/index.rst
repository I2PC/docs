Standlone-installation
====================================

This guide explains the standalone installation of Xmipp and the process to link it with Scipion. The standalone version allows you to use Xmipp independently of Scipion. For details on linking, see the section *Linking Xmipp to Scipion*.

Standalone Installation
----------------------------

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

3. For additional details about the compilation process, run:

   .. code-block:: bash

      ./xmipp --help

Linking Xmipp to Scipion
----------------------------

To use Xmipp within Scipion, link the standalone installation by following these steps:

1. Ensure Scipion is installed (refer to the *Scipion installation guide*).
2. Use the `scipion-em-xmipp` repository, located in `src/scipion-em-xmipp`.
3. Run the following command to link the binaries:

   .. code-block:: bash

      scipion3 installp -p ~/scipion-em-xmipp --devel

   Replace `~/scipion-em-xmipp` with the path to your `scipion-em-xmipp` folder.

If Scipion does not detect Xmipp after linking, refer to *Linking Xmipp to Scipion Troubleshooting*.

