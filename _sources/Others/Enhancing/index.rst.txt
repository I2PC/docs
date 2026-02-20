.. _enhancingXmipp:

Data Collection 
==================
Xmipp is a powerful software suite for image processing in electron microscopy, widely used in structural biology. To enhance the software continuously, Xmipp collects specific information about the installation environment, including versions of certain libraries, system architecture, and operating system details.

This data collection provides crucial insights into the various environments where Xmipp is used, helping the development team identify compatibility issues and optimize performance. It ensures that new features and updates are thoroughly tested and validated across diverse setups, contributing to a more robust and reliable user experience.

We understand some users may have privacy concerns. Therefore, Xmipp includes an option to disable data collection. Just set the environment variable as OFF and Xmipp will not send the data.

.. code-block:: bash

   export XMIPP3_SEND_INSTALLATION_STATISTICS='OFF'


The anonymized and aggregated data helps developers quickly address bugs, understand usage patterns, and optimize the software. It also aids in prioritizing new features based on actual user needs and configurations.
