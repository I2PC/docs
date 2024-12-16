DeepLearningToolkit (DLTK)
============================

The DeepLearningToolkit (DLTK) is a set of environments equipped with several libraries related to deep learning. It enables running protocols in Scipion that require deep learning tools, available for both GPU and CPU. The installer will automatically detect your configuration.

Requirements
------------------------------
- NVIDIA drivers version **450** or higher are required.
- To check your NVIDIA driver version, run:

  .. code-block:: bash

      nvidia-smi

- If an older version is detected, DLTK will be installed without GPU support.

How to Install
------------------------------
To install DLTK, run:

.. code-block:: bash

   scipion3 installb deepLearningToolkit

If the installation would take over 30 minutes, please accelerate the process using the **libmamba** solver, which can provide up to a 4x speed improvement. Note that libmamba is only available for Conda >=4.12 and must be installed and configured in your Conda environment. For more information, refer to the official guide:

`A Faster Conda for a Growing Community <https://www.anaconda.com/blog/a-faster-conda-for-a-growing-community>`_

List of Environments
------------------------------
- **xmipp_DLTK_v0.3**  
  *Protocols using this environment:* `screen_deeplearning`, `deep_denoising`, `resolution_deepres`, `screen_deepConsensus`  
  Libraries and dependencies:  
  - python=3.7  
  - scikit-image=0.14  
  - tensorflow=1.15  
  - keras=2.2  
  - scikit-learn=0.22  
  - pip  
  - numpy==1.21  
  - h5py==2.10.0  

- **xmipp_DLTK_v1.0**  
  *Protocols using this environment:* `deep_misalignment_detection`  
  Libraries and dependencies:  
  - python=3.8  
  - tensorflow=2.7  
  - keras=2.7  
  - pip  
  - numpy==1.23  

- **xmipp_MicCleaner**  
  *Protocols using this environment:* `deepMicrographScreen`  
  Libraries and dependencies:  
  - python=3.6  
  - micrograph-cleaner-em=0.35  

- **xmipp_deepEMhancer**  
  *Protocols using this environment:* `protocol_deepEMhancer`  
  Libraries and dependencies:  
  - python=3.6  
  - deepemhancer=0.12  
  - numba=0.45  

- **xmipp_pyTorch**  
  *Protocols using this environment:* `deepHand`  
  Libraries and dependencies:  
  - python=3.8  
  - numpy=1.23  
  - mrcfile=1.4.3  
  - kornia=0.6.12  
  - starfile=0.4.12  
  - pytorch==1.11  
  - pytorch-cuda=11.7  
  - torchvision=0.12  


- **xtomo_tigre**  
  *Program using this environment:* `tomogram_reconstruction`  
  Libraries and dependencies:  
  - python=3.6
  - mrcfile
  - numpy
  - tigre
