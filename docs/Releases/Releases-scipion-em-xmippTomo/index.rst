
Releases scipion-em-xmippTomo
=============================
3.24.06 Oceanus
--------------------------
   - New protocols:
      - apply_segmentation: Applies a segmentation to a set of tomograms.
      - segment_morphology: Segments a tomogram by means of thresholding, different kind of filters and morphological operations.

   - Protocols updated
      - deep_misalignment: updated model, minor improvements
      - extract_subtomos: improve extract subtomos readability
   - Protocls fixed
      - dose_filter: Dose filter, removing extract stacks
   - More xmippTomo
      - New xmippBase repository to manage shared protocols with Xmipp
      - protocols deprecated: score_transform, denoising_confidence
      - Removed tilt particles object (not used)

3.23.11 Nereus
--------------------------

- Protocols updated
   - applyAlignmentTS
   - extract_particlesstacks: Added angles from Tilt Series
   - extract_subtomos: Keeping directions in extract subtomos
   - project_subtomograms: Added angles from Tilt Series
   - deep_misalignment_detection: Update deep misalignment detection with new version of subtomo extraction and fiducial size options
   - subtraction_subtomo: Improved implementation with MPI and md convert
   - cltomo:
   - resolution_local_monotomo: Allowing odd-even associated to the full tomogram
- Protocls fixed
   - extract_particlestacks: Dose fixes
   - deep_misalignment_detection:  Recover deleted methods
   - dose_filter: Dose validation fixed
   - score_coordinates: Test improvements and carbon score fixes
- More xmippTomo
   - Fixed calculateRotationAngleAndShiftsFromTM
   - Test refactoring

3.23.07 - Morpheus
--------------------------
- New protocols
   - project_subtomograms (for obtaining sobtomogram projections)
   - extract_particlestacks (extract from tilt series and SetOfTiltSeriesParticle)
   - denoising_confidence
   - extract_particlestacks
   - deep_misalignment_detection (misalignment detection in tomographic reconstructions from high-contrast regions)
   - peak_high_contrast (for detecting high contrast regions in tomographic reconstruction)
- Protocols updated 
   - project_top: Subtomo projector compatible with hdf stacks. Test fixed. Projections keep orientation, Ignore alignments in projection
   - subtomo_map_back, score_coordinates: Mapback scales any reference to match the tomogram sampling
   - subtomo_map_back: Mapback waits now when scheduled and not the reference is needed,  works with 3d classes, works with "other tomograms"
   - project_subtomograms: Parallelized protocol 
- More xmipptomo
   - Update requirements.txt
   - Fix tests: protocol_extract_subtomos, monotomo, crop, resize, xmipptomo