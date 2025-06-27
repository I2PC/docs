.. _thePowerOfXmipp:

.. Note::
    Page under construction

The power of Xmipp 
=====================

Xmipp is a key software suite in the image processing workflow for cryo-electron microscopy (cryo-EM) single-particle analysis. Its modular protocols and deep integration with Scipion enable users to handle the complexity of cryo-EM data and achieve high-resolution 3D reconstructions.

This page highlights the relevance of Xmipp through two concrete examples: **ClpC1P1P2** and **HER2-TZB**. In both cases, Xmipp protocols played a critical role in various stages of data processing, from preprocessing and particle selection to final 3D refinement and validation.



Example: HER2-TZB project
------------------------------

.. admonition:: Project Summary

   - **Protein**: *[To be completed]*
   - **Final Resolution**: *[To be completed]*
   - **Number of Movies**: *[To be completed]*
   - **EMDB ID**: *[To be completed]*
   - **Resolution Method**: *[To be completed]*
   - **Xmipp Version**: *[To be completed]*

.. rubric:: Protocols Used

- **CTF Correction**:
  - `XmippProtCTFCorrectWiener2D`
- **Volume Processing and Refinement**:
  - `XmippProtAlignVolumeParticles`
  - `XmippProtReconstructFourier`
  - `XmippProtPreprocessVolumes`
  - `XmippProtFilterVolumes`
  - `XmippProtMaskVolumes`
  - `XmippProtMonoRes`
  - `XmippProtStructureMap`
  - `XmippProtSubtractProjection`
- **Particle Handling**:
  - `XmippProtCropResizeParticles`
- **3D Visualization and Validation**:
  - `XmippProtCompareAngles`
  - `XmippProtCompareReprojections`
  - `XmippProtConsensusClasses`
  - `XmippProtCreateGallery`
  - `XmippProtCreateMask3D`
  - `XmippProtFSO`
- **Postprocessing**:
  - `emhancer`
- **Model Integration**:
  - `XmippProtConvertPdb`


Conclusion
------------------------------

The projects above exemplify how Xmipp provides a comprehensive toolbox that supports end-to-end cryo-EM workflows. From CTF correction to final volume polishing and validation, Xmipp’s protocols are critical in producing reliable, reproducible, and high-quality structural data.

Future developments in Xmipp continue to incorporate state-of-the-art techniques such as deep learning, automation, and hybrid modeling to push the boundaries of cryo-EM analysis.

