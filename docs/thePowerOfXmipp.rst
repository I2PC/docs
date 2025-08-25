.. _thePowerOfXmipp:


The power of Xmipp 
=====================

Xmipp is a key software suite in the image processing workflow for cryo-electron microscopy (cryo-EM) single-particle analysis. Its modular protocols and deep integration with Scipion enable users to handle the complexity of cryo-EM data and achieve high-resolution 3D reconstructions.

This page highlights the relevance of Xmipp through three concrete examples: **SARS-CoV-2 spike**,  **ClpC1** and **HER2-TZB**. In all cases, Xmipp protocols played a critical role in various stages of data processing, from preprocessing and particle selection to final 3D refinement and validation.

Project: SARS-CoV-2 spike
------------------------------

.. admonition:: Project Summary

   - **Sample**: *SARS-CoV-2 spike*
   - **EMDB ID**: *EMD-11328, EMD-11336, EMD-11337, EMD-11341*
   - **Final Resolution**: *2.96 A˚*
   - **Xmipp Version**: *3.20.07 - Boreas*
   - **Publication** `Melero R, Sorzano COS, Foster B, Vilas JL, Martínez M, Marabini R, Ramírez-Aportela E, Sanchez-Garcia R, Herreros D, Del Caño L, Losana P, Fonseca-Reyna YC, Conesa P, Wrapp D, Chacon P, McLellan JS, Tagare HD, Carazo JM. Continuous flexibility analysis of SARS-CoV-2 spike prefusion structures. IUCrJ. 2020 Sep 29;7(Pt 6):1059–69. doi: 10.1107/S2052252520012725. Epub ahead of print. PMID: 33063791; PMCID: PMC7553147. <https://europepmc.org/article/MED/36208775>`_ 


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
   - **EMDB ID**: *EMD-15240, EMD-15242, EMD-15243, EMD-15241*
   - **Final Resolution**: *2.96 A˚*
   - **Xmipp Version**: *3.22.04 - Gaia (Mainly)*
   - **Publication** `Weinhäupl K, Gragera M, Bueno-Carrasco MT, et al. Structure of the drug target ClpC1 unfoldase in action provides insights on antibiotic mechanism of action. The Journal of Biological Chemistry. 2022 Nov;298(11):102553. DOI: 10.1016/j.jbc.2022.102553. PMID: 36208775; PMCID: PMC9661721 <https://pubmed.ncbi.nlm.nih.gov/36208775/>`_

.. rubric:: Protocols Used

- **Particle Handling**:
  - `XmippProtParticlePicking`
- **Postprocessing**:
  - `XmippProtDeepVolPostProc (EMhancer)`


.. figure:: /_static/images/ClpC1.png
   :alt: A, cryo-EM map of the apo MtbClpC1 hexamer bound to a substrate peptide in top
   :width: 600


Project: HER2-TZB 
--------------------

.. admonition:: Project Summary

   - **Sample**: *HER2-TZB (HER2-trastuzumab)*
   - **EMDB ID**: *EMD-52999*
   - **Final Resolution**: *3.77 A˚*
   - **Xmipp Version**: *3.24.06 - Oceanus (Mainly)*
   - **Publication**: `Santiago Vacca  and Marcos Gragera  and Alejandro Buschiazzo  and David Herreros  and James M. Krieger  and Santiago Bonn-Garcia  and Roberto Melero  and Carlos OS. Sorzano  and Jose M. Carazo  and Ohad Medalia  and Andreas Plückthun  <https://www.science.org/doi/full/10.1126/sciadv.adu9945>`_

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
  - `XmippProtDeepVolPostProc (deepEMhancer)`
- **Model Integration**:
  - `XmippProtConvertPdb`


Conclusion
------------------------------

The projects presented here demonstrate the transformative power of Xmipp in cryo-EM single-particle analysis. By offering an extensive suite of robust protocols—from early-stage CTF correction to advanced 3D reconstruction and postprocessing—Xmipp streamlines the entire workflow, enabling researchers to achieve exceptional structural resolutions and scientific insight.

In high-impact studies such as SARS-CoV-2 spike and ClpC1, Xmipp played a decisive role in achieving high resolution and validating structural models, directly contributing to key biological discoveries and impactful publications.

Using tools like Xmipp doesn’t just simplify data processing—it empowers users to extract the full potential of their data, reduce processing bottlenecks, and ensure reproducibility and scientific rigor. As the field evolves, Xmipp continues to integrate cutting-edge methods like deep learning, adaptive workflows, and hybrid modeling, reinforcing its role as a cornerstone for next-generation cryo-EM research.

In short, Xmipp is not just a tool—it’s an enabler of breakthrough science.