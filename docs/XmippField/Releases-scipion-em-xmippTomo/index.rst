
Releases scipion-em-xmippTomo
=========================

V3.23.07 - Morpheus
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
- Update requirements.txt
- Fix tests: protocol_extract_subtomos, monotomo, crop, resize, xmipptomo