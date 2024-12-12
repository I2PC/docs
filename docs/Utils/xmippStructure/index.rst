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