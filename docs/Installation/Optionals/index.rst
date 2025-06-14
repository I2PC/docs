Optional Tools and Libraries
------------------------------------------

DeepLearningToolkit 
^^^^^^^^^^^^^^^^^^^^^^^^^^

The DeepLearningToolkit (DLTK) is a set of environments equipped with several libraries related to deep learning. It enables running protocols in Scipion that require deep learning tools, available for both GPU and CPU. The installer will automatically detect your configuration.

Requirements
""""""""""""""""""
 NVIDIA drivers version **450** or higher are required.
- To check your NVIDIA driver version, run:

  .. code-block:: bash

      nvidia-smi

- If an older version is detected, DLTK will be installed without GPU support.

How to Install
""""""""""""""""""
To install DLTK, run:

.. code-block:: bash

   scipion3 installb deepLearningToolkit

If the installation would take over 30 minutes, please accelerate the process using the **libmamba** solver, which can provide up to a 4x speed improvement. Note that libmamba is only available for Conda >=4.12 and must be installed and configured in your Conda environment. For more information, refer to the official guide: `A Faster Conda for a Growing Community <https://www.anaconda.com/blog/a-faster-conda-for-a-growing-community>`_

List of Environments
""""""""""""""""""""""""""""""""""""
- **xmipp_DLTK_v0.3**  
Protocols using this environment:  `resolution_deepres`, `screen_deepConsensus`  

.. code-block:: text

    - python=3.7  
    - scikit-image=0.14  
    - tensorflow=1.15  
    - keras=2.2  
    - scikit-learn=0.22  
    - pip  
    - numpy==1.21  
    - h5py==2.10.0  

- **xmipp_DLTK_v1.0**  
Protocols using this environment: `deep_misalignment_detection`, `deep_center_predict`

.. code-block:: text
    
    - python=3.8  
    - tensorflow=2.7  
    - keras=2.7  
    - pip  
    - numpy==1.23  

- **xmipp_MicCleaner**  
Protocols using this environment: `deepMicrographScreen`  

.. code-block:: text

    - python=3.6  
    - micrograph-cleaner-em=0.35  

- **xmipp_deepEMhancer**  
Protocols using this environment: `protocol_deepEMhancer`  

.. code-block:: text

    - python=3.6  
    - deepemhancer=0.12  
    - numba=0.45  

- **xmipp_pyTorch**  
Protocols using this environment: `deepHand`,  `classify_pca`


.. code-block:: text

    - python=3.8  
    - numpy=1.23  
    - mrcfile=1.4.3  
    - kornia=0.6.12  
    - starfile=0.4.12  
    - pytorch==1.11  
    - pytorch-cuda=11.7  
    - torchvision=0.12  



Matlab
^^^^^^^^^^^^^^^^^^^^^^^^^^

Xmipp has a binding to MATLAB, which allows the user to run specific
Xmipp functions inside MATLAB. It is required to have a regular MATLAB installation.

Make sure you have these settings in your `configuration file <https://i2pc.github.io/docs/Utils/ConfigurationF/index.html>`__
(``xmipp-bundle/xmipp.conf``) before compiling Xmipp:

``XMIPP_USE_MATLAB=ON``

``MATLAB_DIR=<path to your MATLAB instalation>`` (usually something
like: ``MATLAB_DIR=/home/user/MATLAB/R2021b``)

Run
""""""""""""""""""

1. Compile Xmipp normally (once the settings are as above): ``./xmipp``
   or ``scipion run ./xmipp``
2. Open MATLAB
3. In MATLAB, set the path to Xmipp binding:
   ``HOME > Set Path > Add Folder...`` and select the path to the
   binding (``<path to xmipp>/xmipp-bundle/build/bindings/matlab``),
   then, click in ``Open`` and ``Save``
4. Now you should be able to run functions like ``xmipp_read()`` in
   MATLAB

