.. _thePowerOfXmipp:

.. Note::
    Page under construction

The power of Xmipp 
=====================

Xmipp is a key software suite in the image processing workflow for cryo-electron microscopy (cryo-EM) single-particle analysis. Its modular protocols and deep integration with Scipion enable users to handle the complexity of cryo-EM data and achieve high-resolution 3D reconstructions.

This page highlights the relevance of Xmipp through two concrete examples: **ClpC1P1P2** and **HER2-TZB**. In both cases, Xmipp protocols played a critical role in various stages of data processing, from preprocessing and particle selection to final 3D refinement and validation.

Project: SARS-CoV-2 spike
------------------------------

.. admonition:: Project Summary

   - **Sample**: *SARS-CoV-2 spike*
   - **EMDB ID**: * EMD-11328, EMD-11336, EMD-11337, EMD-11341*
   - **Final Resolution**: * 2.96 A˚ *
   - **Xmipp Version**: *3.20.07 - Boreas*
   - **Publication**: *Melero R, Sorzano COS, Foster B, Vilas JL, Martínez M, Marabini R, Ramírez-Aportela E, Sanchez-Garcia R, Herreros D, Del Caño L, Losana P, Fonseca-Reyna YC, Conesa P, Wrapp D, Chacon P, McLellan JS, Tagare HD, Carazo JM. Continuous flexibility analysis of SARS-CoV-2 spike prefusion structures. IUCrJ. 2020 Sep 29;7(Pt 6):1059–69. doi: 10.1107/S2052252520012725. Epub ahead of print. PMID: 33063791; PMCID: PMC7553147.*


.. rubric:: Protocols Used

- **CTF Correction**:
  - `XmippProtCTFMicrographs`
- **Particle Handling**:
  - `XmippProtParticlePicking`
  - `XmippProtConsensusPicking`
  - `XmippProtDeepMicrographScreen (micCleaner)`
- **3D Visualization and Validation**:
  - `XmippProtReconstructHighRes`
- **Postprocessing**:
  - `XmippProtDeepVolPostProc (EMhancer)`


.. figure:: /_static/images/spike.png
   :alt: spike view
   :width: 300

Project: CLP-C1  (Mycobacterium tuberculosis)
----------------------------------------------------
.. admonition:: Project Summary

   - **Sample**: *ClpC1*
   - **EMDB ID**: * EMD-15240, EMD-15242, EMD-15243, EMD-15241 *
   - **Final Resolution**: * 2.96 A˚ *
   - **Xmipp Version**: *3.22.04 - Gaia*
   - **Publication**: * Weinhäupl K, Gragera M, Bueno-Carrasco MT, et al. Structure of the drug target ClpC1 unfoldase in action provides insights on antibiotic mechanism of action. The Journal of Biological Chemistry. 2022 Nov;298(11):102553. DOI: 10.1016/j.jbc.2022.102553. PMID: 36208775; PMCID: PMC9661721. *

.. rubric:: Protocols Used

- **CTF Correction**:
  - *[To be completed]*
- **Particle Handling**:
  - *[To be completed]*
- **3D Visualization and Validation**:
  - *[To be completed]*
- **Postprocessing**:
  - *[To be completed]*


.. figure:: /_static/images/ClpC1.png
   :alt: spike view
   :width: 300


Project: HER2-TZB 
--------------------

.. admonition:: Project Summary

   - **Sample**: *[To be completed]*
   - **EMDB ID**: *[To be completed]*
   - **Final Resolution**: *[To be completed]*
   - **Xmipp Version**: *[To be completed]*
   - **Publication**:

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
  - `XmippProtDeepVolPostProc (EMhancer)`
- **Model Integration**:
  - `XmippProtConvertPdb`


Conclusion
------------------------------

The projects above exemplify how Xmipp provides a comprehensive toolbox that supports end-to-end cryo-EM workflows. From CTF correction to final volume polishing and validation, Xmipp’s protocols are critical in producing reliable, reproducible, and high-quality structural data.

Future developments in Xmipp continue to incorporate state-of-the-art techniques such as deep learning, automation, and hybrid modeling to push the boundaries of cryo-EM analysis.

