Integrating with Visual Studio Code
--------------------------------------------

The CMake based installation script can be tightly integrated with any modern IDE. This section shows the procedure for Visual Studio Code (VSCode).

Before starting with the configuration process open a terminal and run the following commands. Anotate their outputs.

    conda activate scipion3 && echo $CONDA_PREFIX
    scipion3 printenv | grep SCIPION_SOFTWARE

In visual studio code:

    In the "Extensions" tab install "C/C++ Extension Pack".
    File -> Open Folder -> Navigate to "xmipp" directory (previously cloned).
    Click "Yes, I trust the authors".
    File -> Save workspace as... -> Select a directory outside the Xmipp folder.
    Go to 5. File -> Preferences -> Configuration
    Select the "Workspace" tab
    Navigate to the "CMake Tools" section
    Set the following options:
        "Cmake: Configure Args" add -DCMAKE_PREFIX_PATH=CONDA_PREFIX (replace CONDA_PREFIX with the value obtained previously)
        "Cmake: Configure Args" add -DCMAKE_SKIP_RPATH=ON
        "Cmake: Configure Environment" add: Element: Python3_ROOT_DIR Value: CONDA_PREFIX (replace CONDA_PREFIX with the value obtained previously)
        "Cmake: Configure Environment" add: Element: SCIPION_SOFTWARE Value: SCIPION_SOFTWARE (replace SCIPION_SOFTWARE with the value obtained previousy)
        "Cmake: Install prefix": /path-to/xmipp/dist (Absolute path)
    Go to the CMake tab on the left.
    In "Pinned commands" add "Install"

Once VS Code is set up, the Xmipp installation process can be launched though the newly pinned "Install" command. In addition, individual files or sub-projects may be compiled for quick assessment of code.