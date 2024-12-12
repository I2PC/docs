Xmipp structure
============

XMIPP software is split in three repositories (XmippCore, XmippViz and
Xmipp) plus the repository regarding to the Scipion’s plugin
(scipion-em-xmipp). All this four repositories are in `I2PC
gitHub <https://github.com/i2pc>`__.

-  **scipion-em-xmipp**: It is the Scipion’s plugin. Protocol
   (wrappers), viewers, tests… are there. All Xmipp regarding Scipion is
   there.
-  **xmipp**: EM-reconstraction methods. Usually wrote in C++.
-  **xmippCore**: Low-level image-processing and EM-images definitions.
   In addition, metadata_labels, metadata and data are there.
-  **xmippViz**: Basically ShowJ, coordinates viewer and Xmipp Picker.
   Java code.

We call ``xmipp-bundle`` to the folder that contains the four
repositories listed above in the following structure.

::

   .
   ├── CHANGELOG.md
   ├── cmake
   │   ├── fetch_cifpp.cmake
   │   ├── fetch_ctpl.cmake
   │   ├── fetch_cuFFTAdvisor.cmake
   │   ├── fetch_googletest.cmake
   │   ├── fetch_libsvm.cmake
   │   ├── link_to_scipion.cmake
   │   ├── write_bashrc.cmake
   │   └── xmipp.bashrc.in
   ├── CMakeLists.txt
   ├── installer
   │   ├── api.py
   │   ├── cmake.py
   │   ├── config.py
   │   ├── constants
   │   │   ├── cmake.py
   │   │   ├── config.py
   │   │   ├── errors.py
   │   │   ├── __init__.py
   │   │   ├── main.py
   │   │   ├── parser.py
   │   │   ├── __pycache__
   │   │   │   ├── cmake.cpython-38.pyc
   │   │   │   ├── config.cpython-38.pyc
   │   │   │   ├── errors.cpython-38.pyc
   │   │   │   ├── __init__.cpython-38.pyc
   │   │   │   ├── main.cpython-38.pyc
   │   │   │   ├── parser.cpython-38.pyc
   │   │   │   └── versions.cpython-38.pyc
   │   │   └── versions.py
   │   ├── __init__.py
   │   ├── logger.py
   │   ├── main.py
   │   ├── modelsDLTK.py
   │   ├── parser.py
   │   ├── __pycache__
   │   │   ├── api.cpython-38.pyc
   │   │   ├── cmake.cpython-38.pyc
   │   │   ├── config.cpython-38.pyc
   │   │   ├── __init__.cpython-38.pyc
   │   │   ├── logger.cpython-38.pyc
   │   │   ├── main.cpython-38.pyc
   │   │   ├── modelsDLTK.cpython-38.pyc
   │   │   ├── parser.cpython-38.pyc
   │   │   ├── test.cpython-38.pyc
   │   │   └── utils.cpython-38.pyc
   │   ├── test.py
   │   └── utils.py
   ├── LICENSE
   ├── README.md
   ├── scripts
   │   ├── API.py
   │   ├── config.py
   │   ├── environment.py
   │   ├── __init__.py
   │   ├── tar.py
   │   └── utils.py
   ├── xmipp
   └── xmipp_old
   ├── src


scipion-em-xmipp
::
   │   ├── scipion-em-xmipp
   │   │   ├── CHANGELOG.md
   │   │   ├── LICENSE
   │   │   ├── MANIFEST.in
   │   │   ├── pyproject.toml_beta
   │   │   ├── README.md
   │   │   ├── requirements.txt
   │   │   ├── setup.py
   │   │   ├── sonar-project.properties
   │   │   └── xmipp3
   │   │       ├── base.py
   │   │       ├── bibtex.py
   │   │       ├── checkProtocolsConf.py
   │   │       ├── constants.py
   │   │       ├── convert
   │   │       │   ├── convert.py
   │   │       │   ├── dataimport.py
   │   │       │   ├── __init__.py
   │   │       │   └── io_coordinates.py
   │   │       ├── __init__.py
   │   │       ├── legacy
   │   │       │   ├── protocols
   │   │       │   │   ├── protocol_angular_resolution_alignment.py
   │   │       │   │   ├── protocol_apply_deformation_zernike3d.py
   │   │       │   │   ├── protocol_classification_gpuCorr_full.py
   │   │       │   │   ├── protocol_classification_gpuCorr.py
   │   │       │   │   ├── protocol_classification_gpuCorr_semi.py
   │   │       │   │   ├── protocol_classify_kmeans2d.py
   │   │       │   │   ├── protocol_deep_align.py
   │   │       │   │   ├── protocol_deep_denoising.py
   │   │       │   │   ├── protocol_kmeans_clustering.py
   │   │       │   │   ├── protocol_metaprotocol_create_output.py
   │   │       │   │   ├── protocol_metaprotocol_create_subset.py
   │   │       │   │   ├── protocol_metaprotocol_discrete_heterogeneity_scheduler.py
   │   │       │   │   ├── protocol_metaprotocol_golden_highres.py
   │   │       │   │   ├── protocol_mltomo.py
   │   │       │   │   ├── protocol_movie_average.py
   │   │       │   │   ├── protocol_movie_opticalflow.py
   │   │       │   │   ├── protocol_particle_boxsize.py
   │   │       │   │   ├── protocol_reconstruct_heterogeneous.py
   │   │       │   │   ├── protocol_rotational_spectra.py
   │   │       │   │   ├── protocol_solid_angles.py
   │   │       │   │   ├── protocol_split_volume_hierarchical_cluster.py
   │   │       │   │   ├── protocol_split_volume.py
   │   │       │   │   └── protocol_subtract_projection.py
   │   │       │   ├── tests
   │   │       │   │   ├── test_protocol_deep_denoising.py
   │   │       │   │   ├── test_protocols_angular_resolution_alignment.py
   │   │       │   │   ├── test_protocols_gpuCorr_classifier.py
   │   │       │   │   ├── test_protocols_gpuCorr_fullStreaming.py
   │   │       │   │   ├── test_protocols_gpuCorr_semiStreaming.py
   │   │       │   │   ├── test_protocols_metaprotocol_golden_highres.py
   │   │       │   │   ├── test_protocols_metaprotocol_heterogeneity.py
   │   │       │   │   ├── test_protocols_mixed_movies.py
   │   │       │   │   ├── test_protocols_solid_angles.py
   │   │       │   │   └── test_protocols_subtract_projection.py
   │   │       │   └── viewers
   │   │       │       ├── viewer_angular_resolution_alignment.py
   │   │       │       ├── viewer_deep_align.py
   │   │       │       ├── viewer_metaprotocol_golden_highres.py
   │   │       │       ├── viewer_mltomo.py
   │   │       │       ├── viewer_solid_angles.py
   │   │       │       └── viewer_split_volume.py
   │   │       ├── programs.py
   │   │       ├── protocols
   │   │       │   ├── __init__.py
   │   │       │   ├── protocol_align_volume_and_particles.py
   │   │       │   ├── protocol_align_volume.py
   │   │       │   ├── protocol_analyze_local_ctf.py
   │   │       │   ├── protocol_angular_graph_consistency.py
   │   │       │   ├── protocol_apply_alignment.py
   │   │       │   ├── protocol_apply_tilt_to_ctf.py
   │   │       │   ├── protocol_apply_transformation_matrix.py
   │   │       │   ├── protocol_apply_zernike3d.py
   │   │       │   ├── protocol_assignment_tilt_pair.py
   │   │       │   ├── protocol_break_symmetry.py
   │   │       │   ├── protocol_center_particles.py
   │   │       │   ├── protocol_cl2d_align.py
   │   │       │   ├── protocol_cl2d_clustering.py
   │   │       │   ├── protocol_cl2d.py
   │   │       │   ├── protocol_classes_2d_mapping.py
   │   │       │   ├── protocol_classify_pca.py
   │   │       │   ├── protocol_classify_pca_streaming.py
   │   │       │   ├── protocol_compare_angles.py
   │   │       │   ├── protocol_compare_reprojections.py
   │   │       │   ├── protocol_consensus_classes.py
   │   │       │   ├── protocol_consensus_local_ctf.py
   │   │       │   ├── protocol_convert_pdb.py
   │   │       │   ├── protocol_core_analysis.py
   │   │       │   ├── protocol_create_gallery.py
   │   │       │   ├── protocol_ctf_consensus.py
   │   │       │   ├── protocol_ctf_correct_wiener2d.py
   │   │       │   ├── protocol_ctf_defocus_group.py
   │   │       │   ├── protocol_ctf_micrographs.py
   │   │       │   ├── protocol_deep_center_predict.py
   │   │       │   ├── protocol_deep_center.py
   │   │       │   ├── protocol_deep_hand.py
   │   │       │   ├── protocol_deep_micrograph_screen.py
   │   │       │   ├── protocol_denoise_particles.py
   │   │       │   ├── protocol_eliminate_empty_images.py
   │   │       │   ├── protocol_enrich.py
   │   │       │   ├── protocol_extract_asymmetric_unit.py
   │   │       │   ├── protocol_extract_particles_movies.py
   │   │       │   ├── protocol_extract_particles_pairs.py
   │   │       │   ├── protocol_extract_particles.py
   │   │       │   ├── protocol_flexalign.py
   │   │       │   ├── protocol_generate_reprojections.py
   │   │       │   ├── protocol_helical_parameters.py
   │   │       │   ├── protocol_kerdensom.py
   │   │       │   ├── protocol_local_ctf.py
   │   │       │   ├── protocol_mics_defocus_balancer.py
   │   │       │   ├── protocol_ml2d.py
   │   │       │   ├── protocol_movie_alignment_consensus.py
   │   │       │   ├── protocol_movie_dose_analysis.py
   │   │       │   ├── protocol_movie_gain.py
   │   │       │   ├── protocol_movie_max_shift.py
   │   │       │   ├── protocol_movie_split_frames.py
   │   │       │   ├── protocol_multiple_fscs.py
   │   │       │   ├── protocol_multireference_alignability.py
   │   │       │   ├── protocol_normalize_strain.py
   │   │       │   ├── protocol_particle_pick_automatic.py
   │   │       │   ├── protocol_particle_pick_consensus.py
   │   │       │   ├── protocol_particle_pick_pairs.py
   │   │       │   ├── protocol_particle_pick.py
   │   │       │   ├── protocol_particle_pick_remove_duplicates.py
   │   │       │   ├── protocol_phantom_create.py
   │   │       │   ├── protocol_pick_noise.py
   │   │       │   ├── protocol_postProcessing_deepPostProcessing.py
   │   │       │   ├── protocol_preprocess
   │   │       │   │   ├── geometrical_mask.py
   │   │       │   │   ├── __init__.py
   │   │       │   │   ├── protocol_add_noise.py
   │   │       │   │   ├── protocol_create_mask2d.py
   │   │       │   │   ├── protocol_create_mask3d.py
   │   │       │   │   ├── protocol_crop_resize.py
   │   │       │   │   ├── protocol_filter.py
   │   │       │   │   ├── protocol_image_operate.py
   │   │       │   │   ├── protocol_mask.py
   │   │       │   │   ├── protocol_movie_resize.py
   │   │       │   │   ├── protocol_preprocess.py
   │   │       │   │   └── protocol_process.py
   │   │       │   ├── protocol_preprocess_micrographs.py
   │   │       │   ├── protocol_projmatch
   │   │       │   │   ├── __init__.py
   │   │       │   │   ├── projmatch_form.py
   │   │       │   │   ├── projmatch_initialize.py
   │   │       │   │   ├── projmatch_steps.py
   │   │       │   │   └── protocol_projmatch.py
   │   │       │   ├── protocol_random_conical_tilt.py
   │   │       │   ├── protocol_ransac.py
   │   │       │   ├── protocol_reconstruct_fourier.py
   │   │       │   ├── protocol_reconstruct_highres.py
   │   │       │   ├── protocol_reconstruct_significant.py
   │   │       │   ├── protocol_reconstruct_swarm.py
   │   │       │   ├── protocol_resolution3d.py
   │   │       │   ├── protocol_resolution_bfactor.py
   │   │       │   ├── protocol_resolution_deepres.py
   │   │       │   ├── protocol_resolution_directional.py
   │   │       │   ├── protocol_resolution_fso.py
   │   │       │   ├── protocol_resolution_monogenic_signal.py
   │   │       │   ├── protocol_rotate_volume.py
   │   │       │   ├── protocol_rotational_symmetry.py
   │   │       │   ├── protocol_screen_deepConsensus.py
   │   │       │   ├── protocol_screen_deeplearning.py
   │   │       │   ├── protocol_screen_particles.py
   │   │       │   ├── protocol_shift_particles.py
   │   │       │   ├── protocol_shift_volume.py
   │   │       │   ├── protocol_simulate_ctf.py
   │   │       │   ├── protocol_structure_map.py
   │   │       │   ├── protocol_structure_map_zernike3d.py
   │   │       │   ├── protocol_subtract_projection.py
   │   │       │   ├── protocol_tilt_analysis.py
   │   │       │   ├── protocol_trigger_data.py
   │   │       │   ├── protocol_validate_fscq.py
   │   │       │   ├── protocol_validate_nontilt.py
   │   │       │   ├── protocol_validate_overfitting.py
   │   │       │   ├── protocol_volume_adjust_sub.py
   │   │       │   ├── protocol_volume_consensus.py
   │   │       │   ├── protocol_volume_deform_zernike3d.py
   │   │       │   ├── protocol_volume_local_adjust.py
   │   │       │   ├── protocol_volume_local_sharpening.py
   │   │       │   ├── protocol_volume_strain.py
   │   │       │   ├── protocol_write_testC.py
   │   │       │   └── protocol_write_testP.py
   │   │       ├── protocols.conf
   │   │       ├── tests
   │   │       │   ├── __init__.py
   │   │       │   ├── test_convert_xmipp.py
   │   │       │   ├── test_protocol_angular_graph_consistency.py
   │   │       │   ├── test_protocol_apply_transformation_matrix.py
   │   │       │   ├── test_protocol_compare_angles.py
   │   │       │   ├── test_protocol_consensus_classes3D.py
   │   │       │   ├── test_protocol_ctf_consensus.py
   │   │       │   ├── test_protocol_extract_asymmetric_unit.py
   │   │       │   ├── test_protocol_monodir.py
   │   │       │   ├── test_protocol_multiple_fsc.py
   │   │       │   ├── test_protocol_multireference_alignability.py
   │   │       │   ├── test_protocol_reconstruct_fourier.py
   │   │       │   ├── test_protocols_add_noise.py
   │   │       │   ├── test_protocols_continuousflex.py
   │   │       │   ├── test_protocol_screen_deepConsensus.py
   │   │       │   ├── test_protocols_deepcenter_predict.py
   │   │       │   ├── test_protocols_deepres.py
   │   │       │   ├── test_protocols_deepVolPostprocessing.py
   │   │       │   ├── test_protocols_fso.py
   │   │       │   ├── test_protocols_highres.py
   │   │       │   ├── test_protocol_simulate_ctf.py
   │   │       │   ├── test_protocols_localdeblur.py
   │   │       │   ├── test_protocols_local_defocus.py
   │   │       │   ├── test_protocols_monores.py
   │   │       │   ├── test_protocols_realignment_classes.py
   │   │       │   ├── test_protocols_xmipp_2d.py
   │   │       │   ├── test_protocols_xmipp_3d.py
   │   │       │   ├── test_protocols_xmipp_mics.py
   │   │       │   ├── test_protocols_xmipp_movie_resize.py
   │   │       │   ├── test_protocols_xmipp_movies.py
   │   │       │   ├── test_protocols_zernike3d.py
   │   │       │   ├── test_protocol_validate_fscq.py
   │   │       │   └── test_protocol_validate_overfitting.py
   │   │       ├── utils.py
   │   │       ├── version.py
   │   │       ├── viewers
   │   │       │   ├── __init__.py
   │   │       │   ├── plotter.py
   │   │       │   ├── viewer_analyze_local_ctf.py
   │   │       │   ├── viewer_apply_tilt_to_ctf.py
   │   │       │   ├── viewer_cl2d_clustering.py
   │   │       │   ├── viewer_cl2d.py
   │   │       │   ├── viewer_consensus_classes.py
   │   │       │   ├── viewer_ctf_consensus.py
   │   │       │   ├── viewer_deep_consensus.py
   │   │       │   ├── viewer_deepEMHancer.py
   │   │       │   ├── viewer_deep_micrograph_cleaner.py
   │   │       │   ├── viewer_dose_analysis.py
   │   │       │   ├── viewer_eliminate_empty_images.py
   │   │       │   ├── viewer_extract_asymmetric_unit.py
   │   │       │   ├── viewer_local_sharpening.py
   │   │       │   ├── viewer_ml2d.py
   │   │       │   ├── viewer_movie_alignment.py
   │   │       │   ├── viewer_normalize_strain.py
   │   │       │   ├── viewer_pdb_deform_zernike3d.py
   │   │       │   ├── viewer_projmatch.py
   │   │       │   ├── viewer.py
   │   │       │   ├── viewer_ransac.py
   │   │       │   ├── viewer_reconstruct_highres.py
   │   │       │   ├── viewer_resolution3d.py
   │   │       │   ├── viewer_resolution_bfactor.py
   │   │       │   ├── viewer_resolution_deepres.py
   │   │       │   ├── viewer_resolution_directional.py
   │   │       │   ├── viewer_resolution_fso.py
   │   │       │   ├── viewer_resolution_monogenic_signal.py
   │   │       │   ├── viewer_structure_map.py
   │   │       │   ├── viewer_subtract_projection.py
   │   │       │   ├── viewer_swarm.py
   │   │       │   ├── viewer_validate_fscq.py
   │   │       │   ├── viewer_validate_nontilt.py
   │   │       │   ├── viewer_validate_overfitting.py
   │   │       │   ├── viewer_volume_consensus.py
   │   │       │   ├── viewer_volume_deform_zernike3d.py
   │   │       │   ├── viewer_volume_strain.py
   │   │       │   └── viewer_volume_subtraction.py
   │   │       ├── wizards.py
   │   │       ├── xmipp_logo_devel.png
   │   │       └── xmipp_logo.png   


xmippCore

::

   │   ├── xmippCore
   │   │   ├── bindings
   │   │   │   └── python
   │   │   │       ├── python_image.h
   │   │   │       └── xmippmoduleCore.h
   │   │   ├── CHANGELOG.md
   │   │   ├── cmake
   │   │   │   └── modules
   │   │   │       └── FindFFTW.cmake
   │   │   ├── CMakeLists.txt
   │   │   ├── core
   │   │   │   ├── alglib
   │   │   │   │   ├── alglibinternal.cpp
   │   │   │   │   ├── alglibinternal.h
   │   │   │   │   ├── alglibmisc.cpp
   │   │   │   │   ├── alglibmisc.h
   │   │   │   │   ├── ap.cpp
   │   │   │   │   ├── ap.h
   │   │   │   │   ├── dataanalysis.cpp
   │   │   │   │   ├── dataanalysis.h
   │   │   │   │   ├── diffequations.cpp
   │   │   │   │   ├── diffequations.h
   │   │   │   │   ├── fasttransforms.cpp
   │   │   │   │   ├── fasttransforms.h
   │   │   │   │   ├── integration.cpp
   │   │   │   │   ├── integration.h
   │   │   │   │   ├── interpolation.cpp
   │   │   │   │   ├── interpolation.h
   │   │   │   │   ├── linalg.cpp
   │   │   │   │   ├── linalg.h
   │   │   │   │   ├── optimization.cpp
   │   │   │   │   ├── optimization.h
   │   │   │   │   ├── solvers.cpp
   │   │   │   │   ├── solvers.h
   │   │   │   │   ├── specialfunctions.cpp
   │   │   │   │   ├── specialfunctions.h
   │   │   │   │   ├── statistics.cpp
   │   │   │   │   ├── statistics.h
   │   │   │   │   └── stdafx.h
   │   │   │   ├── args.cpp
   │   │   │   ├── args.h
   │   │   │   ├── argsparser.cpp
   │   │   │   ├── argsparser.h
   │   │   │   ├── argsprinter.cpp
   │   │   │   ├── argsprinter.h
   │   │   │   ├── axis_view.h
   │   │   │   ├── bilib
   │   │   │   │   ├── changebasis.cc
   │   │   │   │   ├── changebasis.h
   │   │   │   │   ├── configs.h
   │   │   │   │   ├── convert.cc
   │   │   │   │   ├── convert.h
   │   │   │   │   ├── debug.h
   │   │   │   │   ├── dft.cc
   │   │   │   │   ├── dft.h
   │   │   │   │   ├── dht.cc
   │   │   │   │   ├── dht.h
   │   │   │   │   ├── error.h
   │   │   │   │   ├── findroot.cc
   │   │   │   │   ├── findroot.h
   │   │   │   │   ├── firconvolve.cc
   │   │   │   │   ├── firconvolve.h
   │   │   │   │   ├── flip.cc
   │   │   │   │   ├── flip.h
   │   │   │   │   ├── fold.cc
   │   │   │   │   ├── fold.h
   │   │   │   │   ├── fourierconvolve.cc
   │   │   │   │   ├── fourierconvolve.h
   │   │   │   │   ├── geometry.cc
   │   │   │   │   ├── geometry.h
   │   │   │   │   ├── getpoles.cc
   │   │   │   │   ├── getpoles.h
   │   │   │   │   ├── getput.cc
   │   │   │   │   ├── getputd.cc
   │   │   │   │   ├── getputd.h
   │   │   │   │   ├── getput.h
   │   │   │   │   ├── gradient.cc
   │   │   │   │   ├── gradient.h
   │   │   │   │   ├── histogram.cc
   │   │   │   │   ├── histogram.h
   │   │   │   │   ├── iirconvolve.cc
   │   │   │   │   ├── iirconvolve.h
   │   │   │   │   ├── interpolate.cc
   │   │   │   │   ├── interpolate.h
   │   │   │   │   ├── kernel.cc
   │   │   │   │   ├── kerneldiff1.cc
   │   │   │   │   ├── kerneldiff1.h
   │   │   │   │   ├── kerneldiff2.cc
   │   │   │   │   ├── kerneldiff2.h
   │   │   │   │   ├── kerneldiff.cc
   │   │   │   │   ├── kerneldiff.h
   │   │   │   │   ├── kernel.h
   │   │   │   │   ├── kernelintegrate.cc
   │   │   │   │   ├── kernelintegrate.h
   │   │   │   │   ├── linearalgebra.cc
   │   │   │   │   ├── linearalgebra.h
   │   │   │   │   ├── messagedisplay.cc
   │   │   │   │   ├── messagedisplay.h
   │   │   │   │   ├── minmax.cc
   │   │   │   │   ├── minmax.h
   │   │   │   │   ├── morphology.cc
   │   │   │   │   ├── morphology.h
   │   │   │   │   ├── movingaverage.cc
   │   │   │   │   ├── movingaverage.h
   │   │   │   │   ├── polynomial.cc
   │   │   │   │   ├── polynomial.h
   │   │   │   │   ├── positivepower.cc
   │   │   │   │   ├── positivepower.h
   │   │   │   │   ├── pyramidfilters.cc
   │   │   │   │   ├── pyramidfilters.h
   │   │   │   │   ├── pyramidtools.cc
   │   │   │   │   ├── pyramidtools.h
   │   │   │   │   ├── round.cc
   │   │   │   │   ├── round.h
   │   │   │   │   ├── swap.cc
   │   │   │   │   ├── swap.h
   │   │   │   │   ├── tboundaryconvention.h
   │   │   │   │   ├── timestamp.cc
   │   │   │   │   ├── timestamp.h
   │   │   │   │   ├── traceline.cc
   │   │   │   │   ├── traceline.h
   │   │   │   │   ├── tsplinebasis.h
   │   │   │   │   ├── ttimestamp.h
   │   │   │   │   ├── ttraceline.h
   │   │   │   │   ├── wavelet.cc
   │   │   │   │   ├── waveletfilters.cc
   │   │   │   │   ├── waveletfiltersfract.cc
   │   │   │   │   ├── waveletfiltersfract.h
   │   │   │   │   ├── waveletfilters.h
   │   │   │   │   ├── wavelet.h
   │   │   │   │   ├── wavelettools.cc
   │   │   │   │   ├── wavelettools.h
   │   │   │   │   ├── window.cc
   │   │   │   │   └── window.h
   │   │   │   ├── choose.h
   │   │   │   ├── comment_list.cpp
   │   │   │   ├── comment_list.h
   │   │   │   ├── gcc_version.h
   │   │   │   ├── geometry.cpp
   │   │   │   ├── geometry.h
   │   │   │   ├── histogram.cpp
   │   │   │   ├── histogram.h
   │   │   │   ├── linear_system_helper.cpp
   │   │   │   ├── linear_system_helper.h
   │   │   │   ├── matrix1d.cpp
   │   │   │   ├── matrix1d.h
   │   │   │   ├── matrix2d.cpp
   │   │   │   ├── matrix2d.h
   │   │   │   ├── metadata_base.cpp
   │   │   │   ├── metadata_base.h
   │   │   │   ├── metadata_base_it.h
   │   │   │   ├── metadata_db.cpp
   │   │   │   ├── metadata_db.h
   │   │   │   ├── metadata_extension.cpp
   │   │   │   ├── metadata_extension.h
   │   │   │   ├── metadata_generator.cpp
   │   │   │   ├── metadata_generator.h
   │   │   │   ├── metadata_label.h
   │   │   │   ├── metadata_object.cpp
   │   │   │   ├── metadata_object.h
   │   │   │   ├── metadata_query.cpp
   │   │   │   ├── metadata_query.h
   │   │   │   ├── metadata_row_base.h
   │   │   │   ├── metadata_row_sql.cpp
   │   │   │   ├── metadata_row_sql.h
   │   │   │   ├── metadata_row_vec.cpp
   │   │   │   ├── metadata_row_vec.h
   │   │   │   ├── metadata_sql.cpp
   │   │   │   ├── metadata_sql.h
   │   │   │   ├── metadata_sql_operations.h
   │   │   │   ├── metadata_static.cpp
   │   │   │   ├── metadata_static.h
   │   │   │   ├── metadata_vec.cpp
   │   │   │   ├── metadata_vec.h
   │   │   │   ├── metadata_writemode.h
   │   │   │   ├── multidim_array_base.cpp
   │   │   │   ├── multidim_array_base.h
   │   │   │   ├── multidim_array.cpp
   │   │   │   ├── multidim_array_generic.cpp
   │   │   │   ├── multidim_array_generic.h
   │   │   │   ├── multidim_array.h
   │   │   │   ├── numerical_recipes.cpp
   │   │   │   ├── numerical_recipes.h
   │   │   │   ├── optional.h
   │   │   │   ├── rerunable_program.h
   │   │   │   ├── rwDM3.cpp
   │   │   │   ├── rwDM3.h
   │   │   │   ├── rwDM4.cpp
   │   │   │   ├── rwDM4.h
   │   │   │   ├── rwEER.cpp
   │   │   │   ├── rwEER.h
   │   │   │   ├── rwEM.cpp
   │   │   │   ├── rwEM.h
   │   │   │   ├── rwHDF5.cpp
   │   │   │   ├── rwHDF5.h
   │   │   │   ├── rwIMAGIC.cpp
   │   │   │   ├── rwIMAGIC.h
   │   │   │   ├── rwINF.cpp
   │   │   │   ├── rwINF.h
   │   │   │   ├── rwJPEG.cpp
   │   │   │   ├── rwJPEG.h
   │   │   │   ├── rwMRC.cpp
   │   │   │   ├── rwMRC.h
   │   │   │   ├── rwPIF.cpp
   │   │   │   ├── rwPIF.h
   │   │   │   ├── rwRAW.cpp
   │   │   │   ├── rwRAW.h
   │   │   │   ├── rwSPE.cpp
   │   │   │   ├── rwSPE.h
   │   │   │   ├── rwSPIDER.cpp
   │   │   │   ├── rwSPIDER.h
   │   │   │   ├── rwTIA.cpp
   │   │   │   ├── rwTIA.h
   │   │   │   ├── rwTIFF.cpp
   │   │   │   ├── rwTIFF.h
   │   │   │   ├── sqlite3-extension-functions.c
   │   │   │   ├── symmetries.cpp
   │   │   │   ├── symmetries.h
   │   │   │   ├── transformations.cpp
   │   │   │   ├── transformations_defines.h
   │   │   │   ├── transformations.h
   │   │   │   ├── userSettings.cpp
   │   │   │   ├── userSettings.h
   │   │   │   ├── utils
   │   │   │   │   ├── half.hpp
   │   │   │   │   ├── memory_utils.h
   │   │   │   │   ├── sql_utils.cpp
   │   │   │   │   ├── sql_utils.h
   │   │   │   │   ├── time_utils.cpp
   │   │   │   │   └── time_utils.h
   │   │   │   ├── xmipp_array_coord.h
   │   │   │   ├── xmipp_array_dim.h
   │   │   │   ├── xmipp_color.cpp
   │   │   │   ├── xmipp_color.h
   │   │   │   ├── xmipp_datatype.cpp
   │   │   │   ├── xmipp_datatype.h
   │   │   │   ├── xmipp_error.cpp
   │   │   │   ├── xmipp_error.h
   │   │   │   ├── xmipp_fft.cpp
   │   │   │   ├── xmipp_fft.h
   │   │   │   ├── xmipp_fftw.cpp
   │   │   │   ├── xmipp_fftw.h
   │   │   │   ├── xmipp_filename.cpp
   │   │   │   ├── xmipp_filename.h
   │   │   │   ├── xmipp_funcs.cpp
   │   │   │   ├── xmipp_funcs.h
   │   │   │   ├── xmipp_hdf5.cpp
   │   │   │   ├── xmipp_hdf5.h
   │   │   │   ├── xmipp_image_base.cpp
   │   │   │   ├── xmipp_image_base.h
   │   │   │   ├── xmipp_image.cpp
   │   │   │   ├── xmipp_image_extension.cpp
   │   │   │   ├── xmipp_image_extension.h
   │   │   │   ├── xmipp_image_generic.cpp
   │   │   │   ├── xmipp_image_generic.h
   │   │   │   ├── xmipp_image.h
   │   │   │   ├── xmipp_image_macros.h
   │   │   │   ├── xmipp_log.cpp
   │   │   │   ├── xmipp_log.h
   │   │   │   ├── xmipp_macros.h
   │   │   │   ├── xmipp_marsaglia.h
   │   │   │   ├── xmipp_memory.cpp
   │   │   │   ├── xmipp_memory.h
   │   │   │   ├── xmipp_metadata_program.cpp
   │   │   │   ├── xmipp_metadata_program.h
   │   │   │   ├── xmipp_program.cpp
   │   │   │   ├── xmipp_program.h
   │   │   │   ├── xmipp_program_sql.cpp
   │   │   │   ├── xmipp_program_sql.h
   │   │   │   ├── xmipp_random_mode.h
   │   │   │   ├── xmipp_strings.cpp
   │   │   │   ├── xmipp_strings.h
   │   │   │   ├── xmipp_threads.cpp
   │   │   │   ├── xmipp_threads.h
   │   │   │   ├── xmipp_types.h
   │   │   │   ├── xmipp_write_mode.h
   │   │   │   ├── xvsmooth.cpp
   │   │   │   └── xvsmooth.h
   │   │   ├── legacy
   │   │   ├── LICENSE
   │   │   ├── README.md
   │   │   ├── scripts
   │   │   │   ├── ci_build
   │   │   │   └── version.py
   │   │   └── sonar-project.properties


xmippViz

::
   │   └── xmippViz
   │       ├── applications
   │       │   ├── CMakeLists.txt
   │       │   └── scripts
   │       │       ├── CMakeLists.txt
   │       │       ├── metadata_plot
   │       │       │   └── batch_metadata_plot.py
   │       │       └── showj
   │       │           └── batch_showj.py
   │       ├── bindings
   │       │   ├── java
   │       │   │   ├── xmipp_Aux.cpp
   │       │   │   ├── xmipp_Aux.h
   │       │   │   ├── xmipp_CTFDescription.cpp
   │       │   │   ├── xmipp_CTFDescription.h
   │       │   │   ├── xmipp_ExceptionsHandler.cpp
   │       │   │   ├── xmipp_ExceptionsHandler.h
   │       │   │   ├── xmipp_Filename.cpp
   │       │   │   ├── xmipp_Filename.h
   │       │   │   ├── xmipp_ImageGeneric.cpp
   │       │   │   ├── xmipp_ImageGeneric.h
   │       │   │   ├── xmipp_InternalData.h
   │       │   │   ├── xmipp_java_adapter.h
   │       │   │   ├── xmipp_MDRow.cpp
   │       │   │   ├── xmipp_MDRow.h
   │       │   │   ├── xmipp_MetaData.cpp
   │       │   │   ├── xmipp_MetaData.h
   │       │   │   ├── xmipp_PickingClassifier.cpp
   │       │   │   ├── xmipp_PickingClassifier.h
   │       │   │   ├── xmipp_Program.cpp
   │       │   │   ├── xmipp_Program.h
   │       │   │   ├── xmipp_Projection.cpp
   │       │   │   ├── xmipp_Projection.h
   │       │   │   ├── xmipp_TiltPairAligner.cpp
   │       │   │   └── xmipp_TiltPairAligner.h
   │       │   └── python
   │       │       └── xmippViz.py
   │       ├── CHANGELOG.md
   │       ├── cmake
   │       │   └── enum.java.in
   │       ├── CMakeLists.txt
   │       ├── external
   │       │   └── imagej.tgz
   │       ├── java
   │       │   ├── lib
   │       │   │   ├── commons-cli-1.1.jar
   │       │   │   ├── core-1.1.jar
   │       │   │   ├── ImageJ_3D_Viewer.jar
   │       │   │   ├── ImageJ_SURF_2009-12-01_08.19.jar
   │       │   │   ├── j3dcore.jar
   │       │   │   ├── j3dutils.jar
   │       │   │   ├── Jama-1.0.2.jar
   │       │   │   ├── jcommon-1.0.16.jar
   │       │   │   ├── jfreechart-1.0.13.jar
   │       │   │   ├── junit4-4.8.2.jar
   │       │   │   ├── sqlite-jdbc-3.7.15-M1.jar
   │       │   │   ├── vecmath.jar
   │       │   │   └── VIB-lib.jar
   │       │   └── src
   │       │       ├── HandleExtraFileTypes.java
   │       │       └── xmipp
   │       │           ├── ij
   │       │           │   ├── commons
   │       │           │   │   ├── DesignMaskJFrame.java
   │       │           │   │   ├── Geometry.java
   │       │           │   │   ├── IJCommand.java
   │       │           │   │   ├── ImageJPanel.java
   │       │           │   │   ├── ImagePlusFromFile.java
   │       │           │   │   ├── ImagePlusLoader.java
   │       │           │   │   ├── ImagePlusNotFromFile.java
   │       │           │   │   ├── ImagePlusReader.java
   │       │           │   │   ├── InputFieldsMessageDialog.java
   │       │           │   │   ├── PollTimer.java
   │       │           │   │   ├── Tool.java
   │       │           │   │   ├── XmippApplication.java
   │       │           │   │   ├── XmippIJWindow.java
   │       │           │   │   ├── XmippImageCanvas.java
   │       │           │   │   ├── XmippImageConverter.java
   │       │           │   │   ├── XmippImageJ.java
   │       │           │   │   ├── XmippImageWindow.java
   │       │           │   │   ├── XmippMenuBar.java
   │       │           │   │   ├── XmippStackWindow.java
   │       │           │   │   └── XmippUtil.java
   │       │           │   └── plugins
   │       │           │       └── maskstoolbar
   │       │           │           ├── AboutMasksToolBar.java
   │       │           │           ├── ICONS.java
   │       │           │           ├── LABELS.java
   │       │           │           ├── MasksToolBar.java
   │       │           │           ├── MasksToolBarPlugin.java
   │       │           │           ├── Operations.java
   │       │           │           └── plugins.config
   │       │           ├── jni
   │       │           │   ├── CastWriteMode.java
   │       │           │   ├── Classifier.java
   │       │           │   ├── CTFDescription.java
   │       │           │   ├── EllipseCTF.java
   │       │           │   ├── Filename.java
   │       │           │   ├── ImageGeneric.java
   │       │           │   ├── ImageWriteMode.java
   │       │           │   ├── LinearAlgebra.java
   │       │           │   ├── MDRow.java
   │       │           │   ├── MetaData.java
   │       │           │   ├── Particle.java
   │       │           │   ├── PickingClassifier.java
   │       │           │   ├── Program.java
   │       │           │   ├── ProgTomographAlignment.java
   │       │           │   ├── Projection.java
   │       │           │   └── TiltPairAligner.java
   │       │           ├── test
   │       │           │   ├── FilenameTest.java
   │       │           │   ├── imagegeneric.stk
   │       │           │   ├── ImageGenericTest.java
   │       │           │   ├── MetadataTest.java
   │       │           │   ├── singleImage2.spi
   │       │           │   ├── singleImage.spi
   │       │           │   ├── tux.xmd
   │       │           │   └── XmippTest.java
   │       │           ├── tomography
   │       │           │   └── alignment
   │       │           │       ├── Matrix.java
   │       │           │       ├── Tomography.java
   │       │           │       └── TomoSerieAligner.java
   │       │           ├── utils
   │       │           │   ├── Cache.java
   │       │           │   ├── ColorEditor.java
   │       │           │   ├── ColorIcon.java
   │       │           │   ├── ColorRenderer.java
   │       │           │   ├── CompoundIcon.java
   │       │           │   ├── DEBUG.java
   │       │           │   ├── ImageRenderer.java
   │       │           │   ├── InfiniteProgressPanel.java
   │       │           │   ├── MultilineCellRenderer.java
   │       │           │   ├── Params.java
   │       │           │   ├── QuickHelpJDialog.java
   │       │           │   ├── QuickHelpPane.java
   │       │           │   ├── ScipionParams.java
   │       │           │   ├── SpringUtilities.java
   │       │           │   ├── StopWatch.java
   │       │           │   ├── Task.java
   │       │           │   ├── TaskTimer.java
   │       │           │   ├── XmippDialog.java
   │       │           │   ├── XmippFileChooser.java
   │       │           │   ├── XmippFilePreview.java
   │       │           │   ├── XmippFileView.java
   │       │           │   ├── XmippLabel.java
   │       │           │   ├── XmippMenuBarCreator.java
   │       │           │   ├── XmippMenuCreator.java
   │       │           │   ├── XmippMessageDialog.java
   │       │           │   ├── XmippMessage.java
   │       │           │   ├── XmippPopupMenuCreator.java
   │       │           │   ├── XmippQuestionDialog.java
   │       │           │   ├── XmippResource.java
   │       │           │   ├── XmippStringUtils.java
   │       │           │   └── XmippWindowUtil.java
   │       │           └── viewer
   │       │               ├── ctf
   │       │               │   ├── CommandTask.java
   │       │               │   ├── CTFAnalyzerImagePane.java
   │       │               │   ├── CTFAnalyzerJFrame.java
   │       │               │   ├── CTFCanvas.java
   │       │               │   ├── CTFRecalculateImageWindow.java
   │       │               │   ├── EstimateFromCTFTask.java
   │       │               │   ├── iCTFGUI.java
   │       │               │   ├── iTaskCompletionListener.java
   │       │               │   ├── SortPSDSTask.java
   │       │               │   └── TasksEngine.java
   │       │               ├── FloatRenderer.java
   │       │               ├── ImageDimension.java
   │       │               ├── ImageItemRenderer.java
   │       │               ├── JMetaDataIO.java
   │       │               ├── models
   │       │               │   ├── ClassInfo.java
   │       │               │   ├── ColumnInfo.java
   │       │               │   ├── GalleryColumnModel.java
   │       │               │   ├── GalleryData.java
   │       │               │   ├── GalleryRowHeaderModel.java
   │       │               │   ├── ImageGalleryTableModel.java
   │       │               │   ├── MetadataGalleryTableModel.java
   │       │               │   ├── MetadataRowTableModel.java
   │       │               │   ├── MetadataTableModel.java
   │       │               │   └── VolumeGalleryTableModel.java
   │       │               ├── particlepicker
   │       │               │   ├── ColorHelper.java
   │       │               │   ├── CtfInfo.java
   │       │               │   ├── extract
   │       │               │   │   ├── ExtractCanvas.java
   │       │               │   │   ├── ExtractMicrograph.java
   │       │               │   │   ├── ExtractParticle.java
   │       │               │   │   ├── ExtractParticlePicker.java
   │       │               │   │   ├── ExtractPickerJFrame.java
   │       │               │   │   ├── MicrographCanvas.java
   │       │               │   │   └── MicrographData.java
   │       │               │   ├── Format.java
   │       │               │   ├── ImportParticlesJDialog.java
   │       │               │   ├── Micrograph.java
   │       │               │   ├── ParticleCanvas.java
   │       │               │   ├── ParticlePickerCanvas.java
   │       │               │   ├── ParticlePicker.java
   │       │               │   ├── ParticlePickerJFrame.java
   │       │               │   ├── ParticlePickerParams.java
   │       │               │   ├── ParticlesDialog.java
   │       │               │   ├── PickerParticle.java
   │       │               │   ├── Shape.java
   │       │               │   ├── tiltpair
   │       │               │   │   ├── gui
   │       │               │   │   │   ├── ImportParticlesFromFilesTiltPairJDialog.java
   │       │               │   │   │   ├── MicrographPairsTableModel.java
   │       │               │   │   │   ├── TiltedMicrographCanvas.java
   │       │               │   │   │   ├── TiltPairParticlesDialog.java
   │       │               │   │   │   ├── TiltPairPickerJFrame.java
   │       │               │   │   │   └── UntiltedMicrographCanvas.java
   │       │               │   │   ├── model
   │       │               │   │   │   ├── TiltedMicrograph.java
   │       │               │   │   │   ├── TiltedParticle.java
   │       │               │   │   │   ├── TiltPairPicker.java
   │       │               │   │   │   ├── UntiltedMicrograph.java
   │       │               │   │   │   └── UntiltedParticle.java
   │       │               │   │   └── TiltPairPickerRunner.java
   │       │               │   └── training
   │       │               │       ├── AutopickRunnable.java
   │       │               │       ├── CorrectAndAutopickRunnable.java
   │       │               │       ├── gui
   │       │               │       │   ├── MicrographsTableModel.java
   │       │               │       │   ├── SupervisedPickerCanvas.java
   │       │               │       │   ├── SupervisedPickerJFrame.java
   │       │               │       │   └── TemplatesJDialog.java
   │       │               │       ├── model
   │       │               │       │   ├── AutomaticParticle.java
   │       │               │       │   ├── CenterParticleTask.java
   │       │               │       │   ├── GenericClassifier.java
   │       │               │       │   ├── ManualParticle.java
   │       │               │       │   ├── MicrographState.java
   │       │               │       │   ├── Mode.java
   │       │               │       │   ├── ParticleToTemplatesTask.java
   │       │               │       │   ├── SupervisedParticlePicker.java
   │       │               │       │   └── SupervisedPickerMicrograph.java
   │       │               │       ├── SupervisedPickerRunner.java
   │       │               │       └── TrainRunnable.java
   │       │               ├── RowHeaderRenderer.java
   │       │               ├── scipion
   │       │               │   ├── ScipionGalleryData.java
   │       │               │   ├── ScipionGalleryJFrame.java
   │       │               │   ├── ScipionMetaData.java
   │       │               │   └── ScipionViewer.java
   │       │               ├── StrokeBorder.java
   │       │               ├── Viewer.java
   │       │               ├── ViewerTest.java
   │       │               └── windows
   │       │                   ├── AddFillLabelsJDialog.java
   │       │                   ├── AddObjectJDialog.java
   │       │                   ├── ClassesJDialog.java
   │       │                   ├── ColumnsJDialog.java
   │       │                   ├── CTFProfileWindow.java
   │       │                   ├── EditLabelsJDialog.java
   │       │                   ├── ExportImagesJDialog.java
   │       │                   ├── FSCJFrame.java
   │       │                   ├── GalleryJFrame.java
   │       │                   ├── ImagesWindowFactory.java
   │       │                   ├── iPollImageWindow.java
   │       │                   ├── MDSearchJDialog.java
   │       │                   ├── PlotJDialog.java
   │       │                   ├── SaveImagesJDialog.java
   │       │                   ├── SaveJDialog.java
   │       │                   ├── TextfileJFrame.java
   │       │                   └── Worker.java
   │       ├── LICENSE
   │       ├── README.md
   │       ├── resources
   │       │   ├── add.gif
   │       │   ├── binocular.png
   │       │   ├── brush.png
   │       │   ├── brush_size.png
   │       │   ├── bulb.png
   │       │   ├── Bundle.properties
   │       │   ├── center.png
   │       │   ├── chimera.png
   │       │   ├── circle.png
   │       │   ├── columns.gif
   │       │   ├── copy.gif
   │       │   ├── create_mask.png
   │       │   ├── create_selection.png
   │       │   ├── delete.gif
   │       │   ├── delete_item.png
   │       │   ├── disable.gif
   │       │   ├── down.gif
   │       │   ├── edit.gif
   │       │   ├── ellipse.png
   │       │   ├── enable.gif
   │       │   ├── eraserC.png
   │       │   ├── eraser.png
   │       │   ├── err.gif
   │       │   ├── error.gif
   │       │   ├── export.gif
   │       │   ├── export_wiz.gif
   │       │   ├── fa-cogs.png
   │       │   ├── fa-plus-circle.png
   │       │   ├── fa-refresh.png
   │       │   ├── fa-times.png
   │       │   ├── fileopen.gif
   │       │   ├── file.png
   │       │   ├── fill.png
   │       │   ├── find.gif
   │       │   ├── foderopen.gif
   │       │   ├── folderopen.gif
   │       │   ├── folder.png
   │       │   ├── freehand.png
   │       │   ├── generic_file.gif
   │       │   ├── goto.gif
   │       │   ├── help.gif
   │       │   ├── histogram.png
   │       │   ├── I2PC.png
   │       │   ├── ij.gif
   │       │   ├── image.gif
   │       │   ├── import_wiz.gif
   │       │   ├── info.gif
   │       │   ├── invert_mask.png
   │       │   ├── invert_selection.png
   │       │   ├── java_file.gif
   │       │   ├── left.gif
   │       │   ├── level_warning.gif
   │       │   ├── linearPickingC.png
   │       │   ├── linearPicking.png
   │       │   ├── locked.png
   │       │   ├── log.gif
   │       │   ├── md.gif
   │       │   ├── md_view.gif
   │       │   ├── merge.gif
   │       │   ├── missing2.png
   │       │   ├── missing.png
   │       │   ├── new_object.gif
   │       │   ├── no-image.jpg
   │       │   ├── no-image.png
   │       │   ├── online_help.gif
   │       │   ├── out.gif
   │       │   ├── oval.png
   │       │   ├── pdb.gif
   │       │   ├── pdbSmall.gif
   │       │   ├── picking1.png
   │       │   ├── pickingC1.png
   │       │   ├── picking.png
   │       │   ├── pick.png
   │       │   ├── plot.png
   │       │   ├── plus.png
   │       │   ├── polygon.png
   │       │   ├── progress_error.gif
   │       │   ├── progress_none.gif
   │       │   ├── progress_ok.gif
   │       │   ├── python_file.gif
   │       │   ├── question.gif
   │       │   ├── rectangle.png
   │       │   ├── refresh.gif
   │       │   ├── resize.png
   │       │   ├── right.gif
   │       │   ├── rotate.png
   │       │   ├── roundrectangle.png
   │       │   ├── run_steps.gif
   │       │   ├── save_as.gif
   │       │   ├── save.gif
   │       │   ├── save_small.gif
   │       │   ├── scipion_logo.png
   │       │   ├── search.gif
   │       │   ├── select_run.gif
   │       │   ├── specify_selection.png
   │       │   ├── square.png
   │       │   ├── stack.gif
   │       │   ├── step_finished.gif
   │       │   ├── step.gif
   │       │   ├── stop.gif
   │       │   ├── table_view.gif
   │       │   ├── topview.png
   │       │   ├── tree2.gif
   │       │   ├── tree.gif
   │       │   ├── unlocked.png
   │       │   ├── up.gif
   │       │   ├── visualize.gif
   │       │   ├── vol.gif
   │       │   ├── wait.gif
   │       │   ├── wait_menu.gif
   │       │   ├── warning.gif
   │       │   ├── wizard.gif
   │       │   ├── xmipp_logoFull.png
   │       │   ├── xmipp_logo.gif
   │       │   ├── xmipp_logo.psd
   │       │   └── zoom.png
   │       └── version.py