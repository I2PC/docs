Installations
----------------------
Installation with Scipion
^^^^^^^^^^^^^^^^^^^^^^^^^^

The recommended way for users (not developers) to install and use Xmipp is via the 
`Scipion framework <https://scipion-em.github.io/docs/release-3.0.0/docs/scipion-modes/how-to-install.html>`_, 
where you can use Xmipp with other Cryo-EM-related software. 

Xmipp will be installed during Scipion installation (pay attention to not include the flag *-noXmipp*).
You can also install Xmipp from the `plugin manager of Scipion <https://scipion-em.github.io/docs/release-3.0.0/docs/scipion-modes/how-to-install.html#installing-other-plugins>`_


Standlone-installation
^^^^^^^^^^^^^^^^^^^^^^^^^^

This guide explains the standalone installation of Xmipp and the process to link it with Scipion. The standalone version allows you to use Xmipp independently of Scipion.

Installation
""""""""""""""""""

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
""""""""""""""""""""""""""

To use Xmipp within Scipion, link the standalone installation by following these steps:

1. Ensure Scipion is installed (refer to the *Scipion installation guide*).
2. Use the `scipion-em-xmipp` repository, located in `src/scipion-em-xmipp`.
3. Run the following command to link the binaries:

   .. code-block:: bash

      scipion3 installp -p ~/scipion-em-xmipp --devel

   Replace `~/scipion-em-xmipp` with the path to your `scipion-em-xmipp` folder.

Using Xmipp
""""""""""""""""""

Xmipp is installed in the build directory located in the same directory where the xmipp script is located. To run Xmipp standalone (without Scipion) and to set all necessary environment variables and paths to all Xmipp programs, you can simply run 
   
   .. code-block:: bash

      source dist/xmipp.bashrc



Installation for HPC Clusters
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

This guide explains how to install Xmipp on High-Performance Computing (HPC).


1. **Install Scipion for HPC**
   Follow the instructions provided in the Scipion for HPC installation guide: 
   `Scipion HPC Installation Guide <https://scipion-em.github.io/docs/release-3.0.0/docs/scipion-modes/how-to-install.html#for-hpc-clusters>`__.

2. **Install the Scipion Xmipp Plugin**
   Run the following command to install the Xmipp plugin for Scipion:

   .. code-block:: bash

      scipion3 installp -p scipion-em-xmipp
   

3. **Locate and navigate the installation directory** of softwares of Scipion:
   
   .. code-block:: bash

      cd /path/to/scipion3/software/em/
   

4. **Clone the Xmipp Repository**
   Clone there the Xmipp repository and move to the source directory:
   
   .. code-block:: bash

      git clone https://github.com/I2PC/xmipp.git xmippSrc && cd xmippSrc
   

5. **Create the Configuration File**
   Generate the initial configuration file by running:
   
   .. code-block:: bash

      ./xmipp config
   

6. **Edit the Configuration File**
   Open the `configuration file <https://i2pc.github.io/docs/Utils/ConfigurationF/index.html#configuration-file>`__ generated in the previous step and edit the fields as needed. Adjust options such as `CMAKE_C_FLAGS` or `CMAKE_CXX_FLAGS` to match the requirements of your HPC system.


7. **Check the Installed Xmipp Version**
   Use the following command to verify the version of the binaries the plugin scipion-em-Xmipp requires:
   
   .. code-block:: bash

      scipion3 python -c "from xmipp3.version import _binTagVersion; print(_binTagVersion)"
   

8. **Compile and Install Xmipp**
   Compile Xmipp in production mode with the command:
   
   .. code-block:: bash

      ./xmipp --production True


After completing these steps, Xmipp should be successfully installed and configured on your HPC environment. But in any case you can `contact us <https://i2pc.github.io/docs/contact.htmlrefer>`__ for advice or support.
