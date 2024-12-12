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

Xmipp
--------------------------
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


The schematic of the four repositories is shown below.

Xmipp

::
   │   │   ├── applications
   │   │   │   ├── CMakeLists.txt
   │   │   │   ├── programs
   │   │   │   │   ├── angular_accuracy_pca
   │   │   │   │   │   └── angular_accuracy_pca_main.cpp
   │   │   │   │   ├── angular_assignment_mag
   │   │   │   │   │   └── angular_assignment_mag_main.cpp
   │   │   │   │   ├── angular_break_symmetry
   │   │   │   │   │   └── angular_break_symmetry_main.cpp
   │   │   │   │   ├── angular_commonline
   │   │   │   │   │   └── angular_commonline_main.cpp
   │   │   │   │   ├── angular_continuous_assign
   │   │   │   │   │   └── angular_continuous_assign_main.cpp
   │   │   │   │   ├── angular_continuous_assign2
   │   │   │   │   │   └── angular_continuous_assign_main2.cpp
   │   │   │   │   ├── angular_discrete_assign
   │   │   │   │   │   └── angular_discrete_assign_main.cpp
   │   │   │   │   ├── angular_distance
   │   │   │   │   │   └── angular_distance_main.cpp
   │   │   │   │   ├── angular_distribution_show
   │   │   │   │   │   └── angular_distribution_show_main.cpp
   │   │   │   │   ├── angular_estimate_tilt_axis
   │   │   │   │   │   └── angular_estimate_tilt_axis_main.cpp
   │   │   │   │   ├── angular_neighbourhood
   │   │   │   │   │   └── angular_neighbourhood_main.cpp
   │   │   │   │   ├── angular_projection_matching
   │   │   │   │   │   └── angular_projection_matching_main.cpp
   │   │   │   │   ├── angular_project_library
   │   │   │   │   │   └── angular_project_library_main.cpp
   │   │   │   │   ├── angular_rotate
   │   │   │   │   │   └── angular_rotate_main.cpp
   │   │   │   │   ├── angular_sph_alignment
   │   │   │   │   │   └── angular_sph_alignment_main.cpp
   │   │   │   │   ├── art_zernike3d
   │   │   │   │   │   └── art_zernike3d_main.cpp
   │   │   │   │   ├── classify_analyze_cluster
   │   │   │   │   │   └── classify_analyze_cluster_main.cpp
   │   │   │   │   ├── classify_compare_classes
   │   │   │   │   │   └── classify_compare_classes_main.cpp
   │   │   │   │   ├── classify_evaluate_classes
   │   │   │   │   │   └── classify_evaluate_classes_main.cpp
   │   │   │   │   ├── classify_extract_features
   │   │   │   │   │   └── classify_extract_features_main.cpp
   │   │   │   │   ├── classify_first_split
   │   │   │   │   │   └── classify_first_split_main.cpp
   │   │   │   │   ├── classify_first_split3
   │   │   │   │   │   └── classify_first_split3_main.cpp
   │   │   │   │   ├── classify_kerdensom
   │   │   │   │   │   └── classify_kerdensom_main.cpp
   │   │   │   │   ├── CMakeLists.txt
   │   │   │   │   ├── compare_density
   │   │   │   │   │   └── compare_density_main.cpp
   │   │   │   │   ├── compare_views
   │   │   │   │   │   └── compare_views_main.cpp
   │   │   │   │   ├── coordinates_noisy_zones_filter
   │   │   │   │   │   └── coordinates_noisy_zones_filter_main.cpp
   │   │   │   │   ├── ctf_correct_phase
   │   │   │   │   │   └── ctf_correct_phase_main.cpp
   │   │   │   │   ├── ctf_correct_wiener2d
   │   │   │   │   │   └── ctf_correct_wiener2d_main.cpp
   │   │   │   │   ├── ctf_correct_wiener3d
   │   │   │   │   │   └── ctf_correct_wiener3d_main.cpp
   │   │   │   │   ├── ctf_enhance_psd
   │   │   │   │   │   └── ctf_enhance_psd_main.cpp
   │   │   │   │   ├── ctf_estimate_from_micrograph
   │   │   │   │   │   └── ctf_estimate_from_micrograph_main.cpp
   │   │   │   │   ├── ctf_estimate_from_psd
   │   │   │   │   │   └── ctf_estimate_from_psd_main.cpp
   │   │   │   │   ├── ctf_estimate_from_psd_fast
   │   │   │   │   │   └── ctf_estimate_from_psd_fast_main.cpp
   │   │   │   │   ├── ctf_group
   │   │   │   │   │   └── ctf_group_main.cpp
   │   │   │   │   ├── ctf_phase_flip
   │   │   │   │   │   └── ctf_phase_flip_main.cpp
   │   │   │   │   ├── ctf_sort_psds
   │   │   │   │   │   └── ctf_sort_psds_main.cpp
   │   │   │   │   ├── cuda11_forward_art_zernike3d
   │   │   │   │   │   └── cuda_forward_art_zernike3d_main.cpp
   │   │   │   │   ├── cuda_align_significant
   │   │   │   │   │   └── cuda_align_significant.cpp
   │   │   │   │   ├── cuda_angular_continuous_assign2
   │   │   │   │   │   └── cuda_angular_continuous_assign2_main.cpp
   │   │   │   │   ├── cuda_angular_sph_alignment
   │   │   │   │   │   └── cuda_angular_sph_alignment_main.cpp
   │   │   │   │   ├── cuda_movie_alignment_correlation
   │   │   │   │   │   └── cuda_movie_alignment_correlation.cpp
   │   │   │   │   ├── cuda_reconstruct_fourier
   │   │   │   │   │   └── cuda_reconstruct_fourier_main.cpp
   │   │   │   │   ├── cuda_volume_deform_sph
   │   │   │   │   │   └── cuda_volume_deform_sph_main.cpp
   │   │   │   │   ├── cuda_volume_halves_restoration
   │   │   │   │   │   └── cuda_volume_halves_restoration.cpp
   │   │   │   │   ├── flexible_alignment
   │   │   │   │   │   └── flexible_alignment_main.cpp
   │   │   │   │   ├── forward_art_zernike3d_subtomos
   │   │   │   │   │   └── forward_art_zernike3d_subtomos.cpp
   │   │   │   │   ├── forward_zernike_images
   │   │   │   │   │   └── forward_zernike_images_main.cpp
   │   │   │   │   ├── forward_zernike_images_priors
   │   │   │   │   │   └── forward_zernike_images_priors_main.cpp
   │   │   │   │   ├── forward_zernike_subtomos
   │   │   │   │   │   └── forward_zernike_subtomos.cpp
   │   │   │   │   ├── forward_zernike_volume
   │   │   │   │   │   └── forward_zernike_volume.cpp
   │   │   │   │   ├── image_align
   │   │   │   │   │   └── image_align_main.cpp
   │   │   │   │   ├── image_align_tilt_pairs
   │   │   │   │   │   └── image_align_tilt_pairs.cpp
   │   │   │   │   ├── image_assignment_tilt_pair
   │   │   │   │   │   └── assignment_tilt_pair_main.cpp
   │   │   │   │   ├── image_convert
   │   │   │   │   │   └── image_convert_main.cpp
   │   │   │   │   ├── image_eliminate_byEnergy
   │   │   │   │   │   └── image_eliminate_byEnergy_main.cpp
   │   │   │   │   ├── image_eliminate_empty_particles
   │   │   │   │   │   └── image_eliminate_empty_particles_main.cpp
   │   │   │   │   ├── image_find_center
   │   │   │   │   │   └── image_find_center_main.cpp
   │   │   │   │   ├── image_header
   │   │   │   │   │   └── image_header_main.cpp
   │   │   │   │   ├── image_histogram
   │   │   │   │   │   └── image_histogram_main.cpp
   │   │   │   │   ├── image_odd_even
   │   │   │   │   │   └── image_odd_even_main.cpp
   │   │   │   │   ├── image_operate
   │   │   │   │   │   └── image_operate_main.cpp
   │   │   │   │   ├── image_peak_high_contrast
   │   │   │   │   │   └── image_peak_high_contrast.cpp
   │   │   │   │   ├── image_residuals
   │   │   │   │   │   └── image_residuals_main.cpp
   │   │   │   │   ├── image_resize
   │   │   │   │   │   └── image_resize.cpp
   │   │   │   │   ├── image_rotational_pca
   │   │   │   │   │   └── image_rotational_pca_main.cpp
   │   │   │   │   ├── image_sort_by_statistics
   │   │   │   │   │   └── image_sort_by_statistics_main.cpp
   │   │   │   │   ├── image_ssnr
   │   │   │   │   │   └── image_ssnr_main.cpp
   │   │   │   │   ├── image_statistics
   │   │   │   │   │   └── image_statistics_main.cpp
   │   │   │   │   ├── image_vectorize
   │   │   │   │   │   └── image_vectorize_main.cpp
   │   │   │   │   ├── local_volume_adjust
   │   │   │   │   │   └── local_volume_adjust_main.cpp
   │   │   │   │   ├── matrix_dimred
   │   │   │   │   │   └── matrix_dimred_main.cpp
   │   │   │   │   ├── metadata_histogram
   │   │   │   │   │   └── metadata_histogram_main.cpp
   │   │   │   │   ├── metadata_import
   │   │   │   │   │   └── metadata_import_main.cpp
   │   │   │   │   ├── metadata_split
   │   │   │   │   │   └── metadata_split_main.cpp
   │   │   │   │   ├── metadata_split_3D
   │   │   │   │   │   └── metadata_split_3D_main.cpp
   │   │   │   │   ├── metadata_utilities
   │   │   │   │   │   └── metadata_utilities_main.cpp
   │   │   │   │   ├── metadata_xml
   │   │   │   │   │   └── metadata_xml_main.cpp
   │   │   │   │   ├── micrograph_automatic_picking
   │   │   │   │   │   └── micrograph_automatic_picking_main.cpp
   │   │   │   │   ├── micrograph_scissor
   │   │   │   │   │   └── micrograph_scissor_main.cpp
   │   │   │   │   ├── ml_align2d
   │   │   │   │   │   └── ml_align2d_main.cpp
   │   │   │   │   ├── mlf_align2d
   │   │   │   │   │   └── mlf_align2d_main.cpp
   │   │   │   │   ├── movie_alignment_correlation
   │   │   │   │   │   └── movie_alignment_correlation.cpp
   │   │   │   │   ├── movie_estimate_gain
   │   │   │   │   │   └── movie_estimate_gain_main.cpp
   │   │   │   │   ├── movie_filter_dose
   │   │   │   │   │   └── movie_filter_dose.cpp
   │   │   │   │   ├── mpi_angular_accuracy_pca
   │   │   │   │   │   └── mpi_angular_accuracy_pca_main.cpp
   │   │   │   │   ├── mpi_angular_assignment_mag
   │   │   │   │   │   └── mpi_angular_assignment_mag_main.cpp
   │   │   │   │   ├── mpi_angular_class_average
   │   │   │   │   │   └── mpi_angular_class_average_main.cpp
   │   │   │   │   ├── mpi_angular_continuous_assign
   │   │   │   │   │   └── mpi_angular_continuous_assign_main.cpp
   │   │   │   │   ├── mpi_angular_continuous_assign2
   │   │   │   │   │   └── mpi_angular_continuous_assign_main2.cpp
   │   │   │   │   ├── mpi_angular_discrete_assign
   │   │   │   │   │   └── mpi_angular_discrete_assign_main.cpp
   │   │   │   │   ├── mpi_angular_projection_matching
   │   │   │   │   │   └── mpi_angular_projection_matching_main.cpp
   │   │   │   │   ├── mpi_angular_project_library
   │   │   │   │   │   └── mpi_angular_project_library_main.cpp
   │   │   │   │   ├── mpi_angular_sph_alignment
   │   │   │   │   │   └── mpi_angular_sph_alignment_main.cpp
   │   │   │   │   ├── mpi_classify_CL2D
   │   │   │   │   │   └── mpi_classify_CL2D_main.cpp
   │   │   │   │   ├── mpi_classify_CL2D_core_analysis
   │   │   │   │   │   └── mpi_classify_CL2D_core_analysis_main.cpp
   │   │   │   │   ├── mpi_classify_CLTomo_prog
   │   │   │   │   │   └── mpi_classify_CLTomo_prog_main.cpp
   │   │   │   │   ├── mpi_classify_FTTRI
   │   │   │   │   │   └── mpi_classify_FTTRI_main.cpp
   │   │   │   │   ├── mpi_ctf_correct_phase
   │   │   │   │   │   └── mpi_ctf_correct_phase_main.cpp
   │   │   │   │   ├── mpi_ctf_correct_wiener2d
   │   │   │   │   │   └── mpi_ctf_correct_wiener2d_main.cpp
   │   │   │   │   ├── mpi_ctf_sort_psds
   │   │   │   │   │   └── mpi_ctf_sort_psds_main.cpp
   │   │   │   │   ├── mpi_cuda_reconstruct_fourier
   │   │   │   │   │   └── mpi_cuda_reconstruct_fourier_main.cpp
   │   │   │   │   ├── mpi_forward_zernike_images
   │   │   │   │   │   └── mpi_forward_zernike_images_main.cpp
   │   │   │   │   ├── mpi_forward_zernike_images_priors
   │   │   │   │   │   └── mpi_forward_zernike_images_priors_main.cpp
   │   │   │   │   ├── mpi_forward_zernike_subtomos
   │   │   │   │   │   └── mpi_forward_zernike_subtomos.cpp
   │   │   │   │   ├── mpi_image_eliminate_byEnergy
   │   │   │   │   │   └── mpi_image_eliminate_byEnergy_main.cpp
   │   │   │   │   ├── mpi_image_operate
   │   │   │   │   │   └── mpi_image_operate_main.cpp
   │   │   │   │   ├── mpi_image_resize
   │   │   │   │   │   └── mpi_image_resize_main.cpp
   │   │   │   │   ├── mpi_image_rotational_pca
   │   │   │   │   │   └── mpi_image_rotational_pca_main.cpp
   │   │   │   │   ├── mpi_image_sort
   │   │   │   │   │   └── mpi_image_sort_main.cpp
   │   │   │   │   ├── mpi_image_ssnr
   │   │   │   │   │   └── mpi_image_ssnr_main.cpp
   │   │   │   │   ├── mpi_ml_align2d
   │   │   │   │   │   └── mpi_ml_align2d_main.cpp
   │   │   │   │   ├── mpi_mlf_align2d
   │   │   │   │   │   └── mpi_mlf_align2d_main.cpp
   │   │   │   │   ├── mpi_multireference_aligneability
   │   │   │   │   │   └── mpi_multireference_aligneability_main.cpp
   │   │   │   │   ├── mpi_nma_alignment
   │   │   │   │   │   └── mpi_nma_alignment_main.cpp
   │   │   │   │   ├── mpi_nma_alignment_vol
   │   │   │   │   │   └── mpi_nma_alignment_vol_main.cpp
   │   │   │   │   ├── mpi_performance_test
   │   │   │   │   │   └── mpi_performance_test_main.cpp
   │   │   │   │   ├── mpi_reconstruct_art
   │   │   │   │   │   └── mpi_reconstruct_art_main.cpp
   │   │   │   │   ├── mpi_reconstruct_fourier
   │   │   │   │   │   └── mpi_reconstruct_fourier_main.cpp
   │   │   │   │   ├── mpi_reconstruct_fourier_accel
   │   │   │   │   │   └── mpi_reconstruct_fourier_accel_main.cpp
   │   │   │   │   ├── mpi_reconstruct_significant
   │   │   │   │   │   └── mpi_reconstruct_significant_main.cpp
   │   │   │   │   ├── mpi_reconstruct_wbp
   │   │   │   │   │   └── mpi_reconstruct_wbp_main.cpp
   │   │   │   │   ├── mpi_run
   │   │   │   │   │   └── mpi_run_main.cpp
   │   │   │   │   ├── mpi_subtomo_subtraction
   │   │   │   │   │   └── mpi_subtomo_subtraction.cpp
   │   │   │   │   ├── mpi_subtract_projection
   │   │   │   │   │   └── mpi_subtract_projection_main.cpp
   │   │   │   │   ├── mpi_transform_adjust_image_grey_levels
   │   │   │   │   │   └── mpi_transform_adjust_image_grey_levels_main.cpp
   │   │   │   │   ├── mpi_transform_filter
   │   │   │   │   │   └── mpi_transform_filter_main.cpp
   │   │   │   │   ├── mpi_transform_geometry
   │   │   │   │   │   └── mpi_transform_geometry_main.cpp
   │   │   │   │   ├── mpi_transform_mask
   │   │   │   │   │   └── mpi_transform_mask_main.cpp
   │   │   │   │   ├── mpi_transform_normalize
   │   │   │   │   │   └── mpi_transform_normalize_main.cpp
   │   │   │   │   ├── mpi_transform_symmetrize
   │   │   │   │   │   └── mpi_transform_symmetrize.cpp
   │   │   │   │   ├── mpi_transform_threshold
   │   │   │   │   │   └── mpi_transform_threshold_main.cpp
   │   │   │   │   ├── mpi_validation_nontilt
   │   │   │   │   │   └── mpi_validation_nontilt_main.cpp
   │   │   │   │   ├── mpi_volumeset_align
   │   │   │   │   │   └── mpi_volumeset_align_main.cpp
   │   │   │   │   ├── mpi_write_test
   │   │   │   │   │   └── mpi_write_test.cpp
   │   │   │   │   ├── multireference_aligneability
   │   │   │   │   │   └── multireference_aligneabililty_main.cpp
   │   │   │   │   ├── nma_alignment
   │   │   │   │   │   └── nma_alignment_main.cpp
   │   │   │   │   ├── nma_alignment_vol
   │   │   │   │   │   └── nma_alignment_vol_main.cpp
   │   │   │   │   ├── pdb_analysis
   │   │   │   │   │   └── pdb_analysis_main.cpp
   │   │   │   │   ├── pdb_label_from_volume
   │   │   │   │   │   └── pdb_label_from_volume_main.cpp
   │   │   │   │   ├── pdb_nma_deform
   │   │   │   │   │   └── pdb_nma_deform_main.cpp
   │   │   │   │   ├── pdb_reduce_pseudoatoms
   │   │   │   │   │   └── pdb_reduce_pseudoatoms_main.cpp
   │   │   │   │   ├── pdb_sph_deform
   │   │   │   │   │   └── pdb_sph_deform_main.cpp
   │   │   │   │   ├── phantom_create
   │   │   │   │   │   └── phantom_create_main.cpp
   │   │   │   │   ├── phantom_movie
   │   │   │   │   │   └── phantom_movie_main.cpp
   │   │   │   │   ├── phantom_project
   │   │   │   │   │   └── phantom_project_main.cpp
   │   │   │   │   ├── phantom_simulate_microscope
   │   │   │   │   │   └── phantom_simulate_microscope_main.cpp
   │   │   │   │   ├── phantom_transform
   │   │   │   │   │   └── phantom_transform_main.cpp
   │   │   │   │   ├── psd_estimate
   │   │   │   │   │   └── psd_estimate_main.cpp
   │   │   │   │   ├── reconstruct_art
   │   │   │   │   │   └── reconstruct_art_main.cpp
   │   │   │   │   ├── reconstruct_fourier
   │   │   │   │   │   └── reconstruct_fourier_main.cpp
   │   │   │   │   ├── reconstruct_fourier_accel
   │   │   │   │   │   └── reconstruct_fourier_accel_main.cpp
   │   │   │   │   ├── reconstruct_significant
   │   │   │   │   │   └── reconstruct_significant_main.cpp
   │   │   │   │   ├── reconstruct_wbp
   │   │   │   │   │   └── reconstruct_wbp_main.cpp
   │   │   │   │   ├── resolution_directional
   │   │   │   │   │   └── resolution_directional_main.cpp
   │   │   │   │   ├── resolution_fsc
   │   │   │   │   │   └── resolution_fsc_main.cpp
   │   │   │   │   ├── resolution_fso
   │   │   │   │   │   └── resolution_fso.cpp
   │   │   │   │   ├── resolution_localfilter
   │   │   │   │   │   └── resolution_localfilter_main.cpp
   │   │   │   │   ├── resolution_monogenic_signal
   │   │   │   │   │   └── resolution_monogenic_signal_main.cpp
   │   │   │   │   ├── resolution_monotomo
   │   │   │   │   │   └── resolution_monotomo_main.cpp
   │   │   │   │   ├── resolution_pdb_bfactor
   │   │   │   │   │   └── resolution_pdb_bfactor_main.cpp
   │   │   │   │   ├── subtomo_subtraction
   │   │   │   │   │   └── subtomo_subtraction_main.cpp
   │   │   │   │   ├── subtract_projection
   │   │   │   │   │   └── subtract_projection_main.cpp
   │   │   │   │   ├── tomo_average_subtomos
   │   │   │   │   │   └── tomo_average_subtomos.cpp
   │   │   │   │   ├── tomo_detect_missing_wedge
   │   │   │   │   │   └── tomo_detect_missing_wedge_main.cpp
   │   │   │   │   ├── tomo_extract_particlestacks
   │   │   │   │   │   └── tomo_extract_particlestacks_main.cpp
   │   │   │   │   ├── tomo_extract_subtomograms
   │   │   │   │   │   └── tomo_extract_subtomograms_main.cpp
   │   │   │   │   ├── tomo_filter_coordinates
   │   │   │   │   │   └── tomo_filter_coordinates.cpp
   │   │   │   │   ├── tomo_map_back
   │   │   │   │   │   └── tomo_map_back_main.cpp
   │   │   │   │   ├── tomo_project
   │   │   │   │   │   └── tomo_project_main.cpp
   │   │   │   │   ├── tomo_simulate_tilt_series
   │   │   │   │   │   └── tomo_simulate_tilt_series_main.cpp
   │   │   │   │   ├── tomo_tiltseries_dose_filter
   │   │   │   │   │   └── tomo_tiltseries_dose_filter_main.cpp
   │   │   │   │   ├── transform_add_noise
   │   │   │   │   │   └── transform_add_noise_main.cpp
   │   │   │   │   ├── transform_adjust_image_grey_levels
   │   │   │   │   │   └── transform_adjust_image_grey_levels_main.cpp
   │   │   │   │   ├── transform_adjust_volume_grey_levels
   │   │   │   │   │   └── transform_adjust_volume_grey_levels_main.cpp
   │   │   │   │   ├── transform_center_image
   │   │   │   │   │   └── transform_center_image_main.cpp
   │   │   │   │   ├── transform_dimred
   │   │   │   │   │   └── transform_dimred_main.cpp
   │   │   │   │   ├── transform_downsample
   │   │   │   │   │   └── transform_downsample_main.cpp
   │   │   │   │   ├── transform_filter
   │   │   │   │   │   └── transform_filter_main.cpp
   │   │   │   │   ├── transform_geometry
   │   │   │   │   │   └── transform_geometry_main.cpp
   │   │   │   │   ├── transform_mask
   │   │   │   │   │   └── transform_mask_main.cpp
   │   │   │   │   ├── transform_mirror
   │   │   │   │   │   └── transform_mirror_main.cpp
   │   │   │   │   ├── transform_morphology
   │   │   │   │   │   └── transform_morphology_main.cpp
   │   │   │   │   ├── transform_normalize
   │   │   │   │   │   └── transform_normalize_main.cpp
   │   │   │   │   ├── transform_randomize_phases
   │   │   │   │   │   └── transform_randomize_phases_main.cpp
   │   │   │   │   ├── transform_symmetrize
   │   │   │   │   │   └── transform_symmetrize_main.cpp
   │   │   │   │   ├── transform_threshold
   │   │   │   │   │   └── transform_threshold_main.cpp
   │   │   │   │   ├── transform_window
   │   │   │   │   │   └── transform_window_main.cpp
   │   │   │   │   ├── validation_nontilt
   │   │   │   │   │   └── validation_nontilt_main.cpp
   │   │   │   │   ├── volume_align
   │   │   │   │   │   └── volume_align_main.cpp
   │   │   │   │   ├── volume_apply_coefficient_zernike3d
   │   │   │   │   │   └── volume_apply_coefficient_zernike3d.cpp
   │   │   │   │   ├── volume_apply_deform_sph
   │   │   │   │   │   └── volume_apply_deform_sph.cpp
   │   │   │   │   ├── volume_center
   │   │   │   │   │   └── volume_center_main.cpp
   │   │   │   │   ├── volume_correct_bfactor
   │   │   │   │   │   └── volume_correct_bfactor_main.cpp
   │   │   │   │   ├── volume_deform_sph
   │   │   │   │   │   └── volume_deform_sph_main.cpp
   │   │   │   │   ├── volume_find_symmetry
   │   │   │   │   │   └── volume_find_symmetry_main.cpp
   │   │   │   │   ├── volume_from_pdb
   │   │   │   │   │   └── volume_from_pdb_main.cpp
   │   │   │   │   ├── volume_halves_restoration
   │   │   │   │   │   └── volume_halves_restoration_main.cpp
   │   │   │   │   ├── volume_initial_simulated_annealing
   │   │   │   │   │   └── volume_initial_simulated_annealing_main.cpp
   │   │   │   │   ├── volume_local_sharpening
   │   │   │   │   │   └── volume_local_sharpening_main.cpp
   │   │   │   │   ├── volume_segment
   │   │   │   │   │   └── volume_segment_main.cpp
   │   │   │   │   ├── volumeset_align
   │   │   │   │   │   └── volumeset_align_main.cpp
   │   │   │   │   ├── volume_structure_factor
   │   │   │   │   │   └── volume_structure_factor_main.cpp
   │   │   │   │   ├── volume_subtraction
   │   │   │   │   │   └── volume_subtraction_main.cpp
   │   │   │   │   ├── volume_to_pseudoatoms
   │   │   │   │   │   └── volume_to_pseudoatoms_main.cpp
   │   │   │   │   └── volume_to_web
   │   │   │   │       └── volume_to_web_main.cpp
   │   │   │   ├── scripts
   │   │   │   │   ├── cl2d_clustering
   │   │   │   │   │   └── cl2d_clustering.py
   │   │   │   │   ├── classify_pca
   │   │   │   │   │   └── batch_classify_pca.py
   │   │   │   │   ├── classify_pca_train
   │   │   │   │   │   └── batch_classify_pca_train.py
   │   │   │   │   ├── CMakeLists.txt
   │   │   │   │   ├── compile
   │   │   │   │   │   └── batch_compile.py
   │   │   │   │   ├── coordinates_consensus
   │   │   │   │   │   └── coordinates_consensus.py
   │   │   │   │   ├── deep_center
   │   │   │   │   │   └── batch_deep_center.py
   │   │   │   │   ├── deep_center_predict
   │   │   │   │   │   └── batch_deep_center_predict.py
   │   │   │   │   ├── deep_consensus
   │   │   │   │   │   ├── deep_consensus.py
   │   │   │   │   │   └── helpers
   │   │   │   │   │       ├── howToPretrainDeepConsensus.txt
   │   │   │   │   │       └── protocol_prepare_deepConsensus.py
   │   │   │   │   ├── deep_global_assignment
   │   │   │   │   │   └── batch_deep_global_assignment.py
   │   │   │   │   ├── deep_global_assignment_predict
   │   │   │   │   │   └── batch_deep_global_assignment_predict.py
   │   │   │   │   ├── deep_hand
   │   │   │   │   │   └── batch_deep_hand.py
   │   │   │   │   ├── deep_micrograph_cleaner
   │   │   │   │   │   └── deep_micrograph_cleaner.py
   │   │   │   │   ├── deep_misalignment_detection
   │   │   │   │   │   └── batch_deep_misalignment_detection.py
   │   │   │   │   ├── deepRes_resolution
   │   │   │   │   │   └── batch_deepRes_resolution.py
   │   │   │   │   ├── deep_volume_postprocessing
   │   │   │   │   │   └── deep_volume_postprocessing.py
   │   │   │   │   ├── denoising_tv
   │   │   │   │   │   └── denoising_tv.py
   │   │   │   │   ├── extract_particles
   │   │   │   │   │   └── extract_particles.py
   │   │   │   │   ├── graph_max_cut
   │   │   │   │   │   └── graph_max_cut.py
   │   │   │   │   ├── metadata_selfile_create
   │   │   │   │   │   └── batch_metadata_selfile_create.py
   │   │   │   │   ├── mpi_classify_CLTomo
   │   │   │   │   │   └── batch_mpi_classify_CLTomo.sh
   │   │   │   │   ├── pdb_center
   │   │   │   │   │   └── batch_pdb_center.py
   │   │   │   │   ├── pdb_select
   │   │   │   │   │   └── batch_pdb_select.py
   │   │   │   │   ├── pick_noise
   │   │   │   │   │   └── pick_noise.py
   │   │   │   │   ├── preprocess_mics
   │   │   │   │   │   └── preprocess_mics.py
   │   │   │   │   ├── swiftalign_aligned_2d_classification
   │   │   │   │   │   └── swiftalign_aligned_2d_classfication.py
   │   │   │   │   ├── sync_data
   │   │   │   │   │   └── batch_sync_data.py
   │   │   │   │   ├── test_script_importing_module
   │   │   │   │   │   └── batch_test_script_importing_module.py
   │   │   │   │   ├── tomogram_reconstruction
   │   │   │   │   │   └── tomogram_reconstruction.py
   │   │   │   │   └── volume_consensus
   │   │   │   │       └── volume_consensus.py
   │   │   │   └── tests
   │   │   │       ├── CMakeLists.txt
   │   │   │       └── function_tests
   │   │   │           ├── aft_tests.h
   │   │   │           ├── aiterative_alignment_tests.h
   │   │   │           ├── alignment_test_utils.h
   │   │   │           ├── arotation_estimator_tests.h
   │   │   │           ├── ashift_corr_estimator_tests.h
   │   │   │           ├── ashift_estimator_tests.h
   │   │   │           ├── asingle_extrema_finder_tests.h
   │   │   │           ├── test_cif_main.cpp
   │   │   │           ├── test_ctf_main.cpp
   │   │   │           ├── test_cuda_fft.cpp
   │   │   │           ├── test_cuda_flexalign_correlate.cpp
   │   │   │           ├── test_cuda_geo_transformer_apply_bspline_transform.cpp
   │   │   │           ├── test_cuda_geo_transformer_produce_and_load_coeffs.cpp
   │   │   │           ├── test_cuda_iterative_alignment_estimator.cpp
   │   │   │           ├── test_cuda_polar_rotation_estimator.cpp
   │   │   │           ├── test_cuda_shift_corr_estimator.cpp
   │   │   │           ├── test_cuda_single_extrema_finder.cpp
   │   │   │           ├── test_cuda_volume_halves_restoration.cpp
   │   │   │           ├── test_dimred_main.cpp
   │   │   │           ├── test_euler_main.cpp
   │   │   │           ├── test_fftw_main.cpp
   │   │   │           ├── test_fftwt.cpp
   │   │   │           ├── test_filename_main.cpp
   │   │   │           ├── test_filters_main.cpp
   │   │   │           ├── test_fringe_processing_main.cpp
   │   │   │           ├── test_funcs_main.cpp
   │   │   │           ├── test_geometry_main.cpp
   │   │   │           ├── test_image_generic_main.cpp
   │   │   │           ├── test_image_main.cpp
   │   │   │           ├── test_iterative_alignment_estimator.cpp
   │   │   │           ├── test_matrix_main.cpp
   │   │   │           ├── test_metadata_db_main.cpp
   │   │   │           ├── test_metadata_vec_main.cpp
   │   │   │           ├── test_movie_filter_dose.cpp
   │   │   │           ├── test_multidim_main.cpp
   │   │   │           ├── test_pocs_main.cpp
   │   │   │           ├── test_polar_main.cpp
   │   │   │           ├── test_polar_rotation_estimator.cpp
   │   │   │           ├── test_polynomials_main.cpp
   │   │   │           ├── test_psd_estimator.cpp
   │   │   │           ├── test_radAvgNonCubic_main.cpp
   │   │   │           ├── test_resolution_frc.cpp
   │   │   │           ├── test_sampling_main.cpp
   │   │   │           ├── test_shift_corr_estimator.cpp
   │   │   │           ├── test_single_extrema_finder.cpp
   │   │   │           ├── test_symmetries_main.cpp
   │   │   │           ├── test_transformation_main.cpp
   │   │   │           ├── test_transform_window.cpp
   │   │   │           ├── test_volume_subtraction_main.cpp
   │   │   │           └── test_wavelets_main.cpp
   │   │   ├── bindings
   │   │   │   ├── matlab
   │   │   │   │   ├── mirt3D_mexinterp.cpp
   │   │   │   │   ├── mirt3D_mexinterp.m
   │   │   │   │   ├── README
   │   │   │   │   ├── tom_calc_periodogram.m
   │   │   │   │   ├── tom_xmipp_adjust_ctf.cpp
   │   │   │   │   ├── tom_xmipp_adjust_ctf.m
   │   │   │   │   ├── tom_xmipp_align2d.cpp
   │   │   │   │   ├── tom_xmipp_align2d.m
   │   │   │   │   ├── tom_xmipp_align2d_stack.m
   │   │   │   │   ├── tom_xmipp_ctf_correct_phase.cpp
   │   │   │   │   ├── tom_xmipp_ctf_correct_phase.m
   │   │   │   │   ├── tom_xmipp_helpers.h
   │   │   │   │   ├── tom_xmipp_mask.cpp
   │   │   │   │   ├── tom_xmipp_mask.m
   │   │   │   │   ├── tom_xmipp_mirror.cpp
   │   │   │   │   ├── tom_xmipp_mirror.m
   │   │   │   │   ├── tom_xmipp_morphology.cpp
   │   │   │   │   ├── tom_xmipp_morphology.m
   │   │   │   │   ├── tom_xmipp_normalize.cpp
   │   │   │   │   ├── tom_xmipp_normalize.m
   │   │   │   │   ├── tom_xmipp_psd_enhance.cpp
   │   │   │   │   ├── tom_xmipp_psd_enhance.m
   │   │   │   │   ├── tom_xmipp_resolution.cpp
   │   │   │   │   ├── tom_xmipp_resolution.m
   │   │   │   │   ├── tom_xmipp_rotate.cpp
   │   │   │   │   ├── tom_xmipp_rotate.m
   │   │   │   │   ├── tom_xmipp_scale.cpp
   │   │   │   │   ├── tom_xmipp_scale.m
   │   │   │   │   ├── tom_xmipp_scale_pyramid.cpp
   │   │   │   │   ├── tom_xmipp_scale_pyramid.m
   │   │   │   │   ├── tom_xmipp_volume_segment.cpp
   │   │   │   │   ├── tom_xmipp_volume_segment.m
   │   │   │   │   ├── xmipp_calculate_strain.m
   │   │   │   │   ├── xmipp_ctf_for_metadata_row.m
   │   │   │   │   ├── xmipp_ctf_generate_filter.cpp
   │   │   │   │   ├── xmipp_nma_read_alignment.cpp
   │   │   │   │   ├── xmipp_nma_read_alignment.m
   │   │   │   │   ├── xmipp_nma_save_cluster.cpp
   │   │   │   │   ├── xmipp_nma_save_cluster.m
   │   │   │   │   ├── xmipp_nma_selection_tool_gui.fig
   │   │   │   │   ├── xmipp_nma_selection_tool_gui.m
   │   │   │   │   ├── xmipp_nma_selection_tool.m
   │   │   │   │   ├── xmipp_read.cpp
   │   │   │   │   ├── xmipp_read.m
   │   │   │   │   ├── xmipp_read_metadata.m
   │   │   │   │   ├── xmipp_read_structure_factor.cpp
   │   │   │   │   ├── xmipp_show_structure_factor.m
   │   │   │   │   ├── xmipp_write.cpp
   │   │   │   │   └── xmipp_write.m
   │   │   │   └── python
   │   │   │       ├── envs_DLTK
   │   │   │       │   ├── condaVersionRestriction.md
   │   │   │       │   ├── xmipp_deepEMhancer.yml
   │   │   │       │   ├── xmipp_DLTK_v0.3-gpu.yml
   │   │   │       │   ├── xmipp_DLTK_v0.3.yml
   │   │   │       │   ├── xmipp_DLTK_v1.0-gpu.yml
   │   │   │       │   ├── xmipp_DLTK_v1.0.yml
   │   │   │       │   ├── xmipp_graph.yml
   │   │   │       │   ├── xmipp_MicCleaner.yml
   │   │   │       │   ├── xmipp_pyTorch-gpu.yml
   │   │   │       │   ├── xmipp_pyTorch.yml
   │   │   │       │   └── xtomo_tigre.yml
   │   │   │       ├── python_constants.cpp
   │   │   │       ├── python_filename.cpp
   │   │   │       ├── python_filename.h
   │   │   │       ├── python_fourierprojector.cpp
   │   │   │       ├── python_fourierprojector.h
   │   │   │       ├── python_image.cpp
   │   │   │       ├── python_image.h
   │   │   │       ├── python_metadata.cpp
   │   │   │       ├── python_metadata.h
   │   │   │       ├── python_program.cpp
   │   │   │       ├── python_program.h
   │   │   │       ├── python_symmetry.cpp
   │   │   │       ├── python_symmetry.h
   │   │   │       ├── xmipp_base.py
   │   │   │       ├── xmipp_conda_envs.py
   │   │   │       ├── xmippmodule.cpp
   │   │   │       ├── xmippmodule.h
   │   │   │       └── xmipp.py
   │   │   ├── CMakeLists.txt
   │   │   ├── external
   │   │   │   ├── condor
   │   │   │   │   ├── CNLSolver.cpp
   │   │   │   │   ├── CTRSSolver.cpp
   │   │   │   │   ├── IntPoly.cpp
   │   │   │   │   ├── IntPoly.h
   │   │   │   │   ├── KeepBests.cpp
   │   │   │   │   ├── KeepBests.h
   │   │   │   │   ├── Matrix.cpp
   │   │   │   │   ├── Matrix.h
   │   │   │   │   ├── MatrixTriangle.cpp
   │   │   │   │   ├── MatrixTriangle.h
   │   │   │   │   ├── MSSolver.cpp
   │   │   │   │   ├── MultInd.cpp
   │   │   │   │   ├── MultInd.h
   │   │   │   │   ├── ObjectiveFunction.cpp
   │   │   │   │   ├── ObjectiveFunction.h
   │   │   │   │   ├── parallel.cpp
   │   │   │   │   ├── parallel.h
   │   │   │   │   ├── Poly.cpp
   │   │   │   │   ├── Poly.h
   │   │   │   │   ├── QPSolver.cpp
   │   │   │   │   ├── Solver.h
   │   │   │   │   ├── tools.cpp
   │   │   │   │   ├── tools.h
   │   │   │   │   ├── UTRSSolver.cpp
   │   │   │   │   ├── VectorChar.cpp
   │   │   │   │   ├── VectorChar.h
   │   │   │   │   ├── Vector.cpp
   │   │   │   │   ├── Vector.h
   │   │   │   │   ├── VectorInt.cpp
   │   │   │   │   └── VectorInt.h
   │   │   │   ├── delaunay
   │   │   │   │   ├── dcel.cpp
   │   │   │   │   ├── dcel.h
   │   │   │   │   ├── defines.h
   │   │   │   │   ├── delaunay.cpp
   │   │   │   │   ├── delaunay.h
   │   │   │   │   ├── graph.cpp
   │   │   │   │   ├── graph.h
   │   │   │   │   ├── point.cpp
   │   │   │   │   ├── point.h
   │   │   │   │   ├── polygon.cpp
   │   │   │   │   ├── polygon.h
   │   │   │   │   ├── sorting.cpp
   │   │   │   │   ├── sorting.h
   │   │   │   │   ├── stack.cpp
   │   │   │   │   ├── stack.h
   │   │   │   │   ├── triangulation.cpp
   │   │   │   │   ├── triangulation.h
   │   │   │   │   ├── voronoi.cpp
   │   │   │   │   └── voronoi.h
   │   │   │   └── sh_alignment
   │   │   │       ├── frm.cpp
   │   │   │       ├── frm.i
   │   │   │       ├── frm_wrap.cpp
   │   │   │       ├── lib_err.cpp
   │   │   │       ├── lib_err.h
   │   │   │       ├── lib_eul.cpp
   │   │   │       ├── lib_eul.h
   │   │   │       ├── lib_pio.cpp
   │   │   │       ├── lib_pio.h
   │   │   │       ├── lib_pwk.cpp
   │   │   │       ├── lib_pwk.h
   │   │   │       ├── lib_std.cpp
   │   │   │       ├── lib_std.h
   │   │   │       ├── lib_tim.cpp
   │   │   │       ├── lib_tim.h
   │   │   │       ├── lib_vec.cpp
   │   │   │       ├── lib_vec.h
   │   │   │       ├── lib_vio.cpp
   │   │   │       ├── lib_vio.h
   │   │   │       ├── lib_vwk.cpp
   │   │   │       ├── lib_vwk.h
   │   │   │       ├── numpy.i
   │   │   │       ├── python
   │   │   │       │   ├── constrained_frm.py
   │   │   │       │   ├── frm.py
   │   │   │       │   ├── __init__.py
   │   │   │       │   ├── tompy
   │   │   │       │   │   ├── filter.py
   │   │   │       │   │   ├── __init__.py
   │   │   │       │   │   ├── io.py
   │   │   │       │   │   ├── plot.py
   │   │   │       │   │   ├── score.py
   │   │   │       │   │   ├── tools.py
   │   │   │       │   │   └── transform.py
   │   │   │       │   └── vol2sf.py
   │   │   │       ├── README
   │   │   │       ├── situs.h
   │   │   │       ├── SpharmonicKit27
   │   │   │       │   ├── BACKGROUND
   │   │   │       │   ├── config.h
   │   │   │       │   ├── cospmls.cpp
   │   │   │       │   ├── cospmls.h
   │   │   │       │   ├── csecond.cpp
   │   │   │       │   ├── csecond.h
   │   │   │       │   ├── FFTcode.cpp
   │   │   │       │   ├── FFTcode.h
   │   │   │       │   ├── fft_grids.cpp
   │   │   │       │   ├── fft_grids.h
   │   │   │       │   ├── fftpack.h
   │   │   │       │   ├── FST_semi_memo.cpp
   │   │   │       │   ├── FST_semi_memo.h
   │   │   │       │   ├── indextables.cpp
   │   │   │       │   ├── indextables.h
   │   │   │       │   ├── LICENSE
   │   │   │       │   ├── MathFace.cpp
   │   │   │       │   ├── MathFace.h
   │   │   │       │   ├── naive_synthesis.cpp
   │   │   │       │   ├── naive_synthesis.h
   │   │   │       │   ├── newFCT.cpp
   │   │   │       │   ├── newFCT.h
   │   │   │       │   ├── oddweights.cpp
   │   │   │       │   ├── oddweights.h
   │   │   │       │   ├── OURmods.cpp
   │   │   │       │   ├── OURmods.h
   │   │   │       │   ├── OURperms.cpp
   │   │   │       │   ├── OURperms.h
   │   │   │       │   ├── permroots.h
   │   │   │       │   ├── primitive.cpp
   │   │   │       │   ├── primitive_FST.cpp
   │   │   │       │   ├── primitive_FST.h
   │   │   │       │   ├── primitive.h
   │   │   │       │   ├── README
   │   │   │       │   ├── seminaive.cpp
   │   │   │       │   ├── seminaive.h
   │   │   │       │   ├── weights.cpp
   │   │   │       │   └── weights.h
   │   │   │       └── swig_frm.py
   │   │   ├── legacy
   │   │   │   ├── applications
   │   │   │   │   ├── programs
   │   │   │   │   │   ├── angular_resolution_alignment
   │   │   │   │   │   │   └── angular_resolution_alignment_main.cpp
   │   │   │   │   │   ├── classify_kmeans_2d
   │   │   │   │   │   │   └── classify_kmeans_2d_main.cpp
   │   │   │   │   │   ├── classify_significant
   │   │   │   │   │   │   └── classify_significant_main.cpp
   │   │   │   │   │   ├── ctf_correct_idr
   │   │   │   │   │   │   └── ctf_correct_idr_main.cpp
   │   │   │   │   │   ├── ctf_create_ctfdat
   │   │   │   │   │   │   └── ctf_create_ctfdat_main.cpp
   │   │   │   │   │   ├── ctf_show
   │   │   │   │   │   │   └── ctf_show_main.cpp
   │   │   │   │   │   ├── cuda_correlation
   │   │   │   │   │   │   └── cuda_correlation_main.cpp
   │   │   │   │   │   ├── evaluate_coordinates
   │   │   │   │   │   │   └── evaluate_coordinates_main.cpp
   │   │   │   │   │   ├── extract_subset
   │   │   │   │   │   │   ├── prog_extract_subset_main.cpp
   │   │   │   │   │   │   └── prog_extract_subset_main.h
   │   │   │   │   │   ├── forward_art_zernike3d
   │   │   │   │   │   │   └── forward_art_zernike3d_main.cpp
   │   │   │   │   │   ├── idr_xray_tomo
   │   │   │   │   │   │   └── idr_xray_tomo_main.cpp
   │   │   │   │   │   ├── image_common_lines
   │   │   │   │   │   │   └── image_common_lines_main.cpp
   │   │   │   │   │   ├── image_rotational_spectra
   │   │   │   │   │   │   └── image_rotational_spectra_main.cpp
   │   │   │   │   │   ├── image_separate_objects
   │   │   │   │   │   │   └── image_separate_objects_main.cpp
   │   │   │   │   │   ├── metadata_convert_to_spider
   │   │   │   │   │   │   └── metadata_convert_to_spider_main.cpp
   │   │   │   │   │   ├── mlf_refine3d
   │   │   │   │   │   │   └── mlf_refine3d_main.cpp
   │   │   │   │   │   ├── ml_refine3d
   │   │   │   │   │   │   └── ml_refine3d_main.cpp
   │   │   │   │   │   ├── ml_tomo
   │   │   │   │   │   │   └── ml_tomo_main.cpp
   │   │   │   │   │   ├── mpi_ctf_correct_idr
   │   │   │   │   │   │   └── mpi_ctf_correct_idr_main.cpp
   │   │   │   │   │   ├── mpi_mlf_refine3d
   │   │   │   │   │   │   └── mpi_mlf_refine3d_main.cpp
   │   │   │   │   │   ├── mpi_ml_refine3d
   │   │   │   │   │   │   └── mpi_ml_refine3d_main.cpp
   │   │   │   │   │   ├── mpi_ml_tomo
   │   │   │   │   │   │   └── mpi_ml_tomo_main.cpp
   │   │   │   │   │   ├── mpi_reconstruct_admm
   │   │   │   │   │   │   └── mpi_reconstruct_admm_main.cpp
   │   │   │   │   │   ├── mpi_tomo_extract_subvolume
   │   │   │   │   │   │   └── mpi_tomo_extract_subvolume.cpp
   │   │   │   │   │   ├── mpi_xray_project
   │   │   │   │   │   │   └── mpi_xray_project_main.cpp
   │   │   │   │   │   ├── mrc_create_metadata
   │   │   │   │   │   │   └── mrc_create_metadata_main.cpp
   │   │   │   │   │   ├── parallel_forward_art_zernike3d
   │   │   │   │   │   │   └── parallel_forward_art_zernike3d_main.cpp
   │   │   │   │   │   ├── parallel_forward_art_zernike3d_float
   │   │   │   │   │   │   └── parallel_forward_art_zernike3d_float_main.cpp
   │   │   │   │   │   ├── pdb_construct_dictionary
   │   │   │   │   │   │   └── pdb_construct_dictionary_main.cpp
   │   │   │   │   │   ├── pdb_restore_with_dictionary
   │   │   │   │   │   │   └── pdb_restore_with_dictionary_main.cpp
   │   │   │   │   │   ├── reconstruct_admm
   │   │   │   │   │   │   └── reconstruct_admm_main.cpp
   │   │   │   │   │   ├── reconstruct_art_pseudo
   │   │   │   │   │   │   └── reconstruct_art_pseudo_main.cpp
   │   │   │   │   │   ├── reconstruct_art_xray
   │   │   │   │   │   │   └── reconstruct_art_xray_main.cpp
   │   │   │   │   │   ├── resolution_ibw
   │   │   │   │   │   │   └── resolution_ibw_main.cpp
   │   │   │   │   │   ├── resolution_ssnr
   │   │   │   │   │   │   └── resolution_ssnr_main.cpp
   │   │   │   │   │   ├── score_micrograph
   │   │   │   │   │   │   └── score_micrograph_main.cpp
   │   │   │   │   │   ├── starpu_reconstruct_fourier
   │   │   │   │   │   │   └── starpu_reconstruct_fourier_main.cpp
   │   │   │   │   │   ├── tomo_align_dual_tilt_series
   │   │   │   │   │   │   └── tomo_align_dual_tilt_series_main.cpp
   │   │   │   │   │   ├── tomo_align_refinement
   │   │   │   │   │   │   └── tomo_align_refinement_main.cpp
   │   │   │   │   │   ├── tomo_align_tilt_series
   │   │   │   │   │   │   └── tomo_align_tilt_series_main.cpp
   │   │   │   │   │   ├── tomo_extract_subvolume
   │   │   │   │   │   │   └── tomo_extract_volume_main.cpp
   │   │   │   │   │   ├── tomo_remove_fluctuations
   │   │   │   │   │   │   └── tomo_remove_fluctuations_main.cpp
   │   │   │   │   │   ├── transform_range_adjust
   │   │   │   │   │   │   └── transform_range_adjust_main.cpp
   │   │   │   │   │   ├── validation_tilt_pairs
   │   │   │   │   │   │   └── validation_tilt_pairs_main.cpp
   │   │   │   │   │   ├── volume_enhance_contrast
   │   │   │   │   │   │   └── volume_enhance_contrast_main.cpp
   │   │   │   │   │   ├── volume_pca
   │   │   │   │   │   │   └── volume_pca_main.cpp
   │   │   │   │   │   ├── volume_reslice
   │   │   │   │   │   │   └── volume_reslice_main.cpp
   │   │   │   │   │   ├── volume_validate_pca
   │   │   │   │   │   │   └── volume_validate_pca_main.cpp
   │   │   │   │   │   ├── work_test
   │   │   │   │   │   │   └── work_test.cpp
   │   │   │   │   │   ├── xray_import
   │   │   │   │   │   │   └── xray_import_main.cpp
   │   │   │   │   │   ├── xray_project
   │   │   │   │   │   │   └── xray_project_main.cpp
   │   │   │   │   │   └── xray_psf_create
   │   │   │   │   │       └── xray_psf_create_main.cpp
   │   │   │   │   └── scripts
   │   │   │   │       ├── apropos
   │   │   │   │       │   └── batch_apropos.py
   │   │   │   │       ├── cone_deepalign
   │   │   │   │       │   └── batch_cone_deepalign.py
   │   │   │   │       ├── cone_deepalign_predict
   │   │   │   │       │   └── batch_cone_deepalign_predict.py
   │   │   │   │       ├── deep_denoising
   │   │   │   │       │   └── batch_deep_denoising.py
   │   │   │   │       └── particle_boxsize
   │   │   │   │           └── batch_particle_boxsize.py
   │   │   │   ├── install_cuda_github.sh
   │   │   │   ├── install_cuda_travis.sh
   │   │   │   └── libraries
   │   │   │       ├── data
   │   │   │       │   ├── psf_xr.cpp
   │   │   │       │   └── psf_xr.h
   │   │   │       ├── parallel
   │   │   │       │   ├── mpi_project_XR.cpp
   │   │   │       │   ├── mpi_project_XR.h
   │   │   │       │   ├── mpi_reconstruct_admm.cpp
   │   │   │       │   └── mpi_reconstruct_admm.h
   │   │   │       ├── reconstruction
   │   │   │       │   ├── angular_resolution_alignment.cpp
   │   │   │       │   ├── angular_resolution_alignment.h
   │   │   │       │   ├── art_xray.cpp
   │   │   │       │   ├── art_xray.h
   │   │   │       │   ├── classify_kmeans_2d.cpp
   │   │   │       │   ├── classify_kmeans_2d.h
   │   │   │       │   ├── classify_significant.cpp
   │   │   │       │   ├── classify_significant.h
   │   │   │       │   ├── common_lines.cpp
   │   │   │       │   ├── common_lines.h
   │   │   │       │   ├── ctf_correct_idr.cpp
   │   │   │       │   ├── ctf_correct_idr.h
   │   │   │       │   ├── ctf_create_ctfdat.cpp
   │   │   │       │   ├── ctf_show.cpp
   │   │   │       │   ├── ctf_show.h
   │   │   │       │   ├── evaluate_coordinates.cpp
   │   │   │       │   ├── evaluate_coordinates.h
   │   │   │       │   ├── extract_subset.cpp
   │   │   │       │   ├── extract_subset.h
   │   │   │       │   ├── forward_art_zernike3d.cpp
   │   │   │       │   ├── forward_art_zernike3d.h
   │   │   │       │   ├── idr_xray_tomo.cpp
   │   │   │       │   ├── idr_xray_tomo.h
   │   │   │       │   ├── image_rotational_spectra.cpp
   │   │   │       │   ├── image_rotational_spectra.h
   │   │   │       │   ├── image_separate_objects.cpp
   │   │   │       │   ├── metadata_convert_to_spider.cpp
   │   │   │       │   ├── ml_refine3d.cpp
   │   │   │       │   ├── ml_refine3d.h
   │   │   │       │   ├── ml_tomo.cpp
   │   │   │       │   ├── ml_tomo.h
   │   │   │       │   ├── parallel_forward_art_zernike3d.cpp
   │   │   │       │   ├── parallel_forward_art_zernike3d_floats.cpp
   │   │   │       │   ├── parallel_forward_art_zernike3d_floats.h
   │   │   │       │   ├── parallel_forward_art_zernike3d.h
   │   │   │       │   ├── pdb_construct_dictionary.cpp
   │   │   │       │   ├── pdb_construct_dictionary.h
   │   │   │       │   ├── pdb_restore_with_dictionary.cpp
   │   │   │       │   ├── pdb_restore_with_dictionary.h
   │   │   │       │   ├── project_xray.cpp
   │   │   │       │   ├── project_xray.h
   │   │   │       │   ├── reconstruct_ADMM.cpp
   │   │   │       │   ├── reconstruct_ADMM.h
   │   │   │       │   ├── reconstruct_art_pseudo.cpp
   │   │   │       │   ├── reconstruct_art_pseudo.h
   │   │   │       │   ├── reconstruct_art_xray.cpp
   │   │   │       │   ├── reconstruct_art_xray.h
   │   │   │       │   ├── resolution_ibw.cpp
   │   │   │       │   ├── resolution_ibw.h
   │   │   │       │   ├── resolution_ssnr.cpp
   │   │   │       │   ├── resolution_ssnr.h
   │   │   │       │   ├── score_micrograph.cpp
   │   │   │       │   ├── score_micrograph.h
   │   │   │       │   ├── tomo_align_dual_tilt_series.cpp
   │   │   │       │   ├── tomo_align_dual_tilt_series.h
   │   │   │       │   ├── tomo_align_refinement.cpp
   │   │   │       │   ├── tomo_align_refinement.h
   │   │   │       │   ├── tomo_align_tilt_series.cpp
   │   │   │       │   ├── tomo_align_tilt_series.h
   │   │   │       │   ├── tomo_extract_subvolume.cpp
   │   │   │       │   ├── tomo_extract_subvolume.h
   │   │   │       │   ├── tomo_remove_fluctuations.cpp
   │   │   │       │   ├── tomo_remove_fluctuations.h
   │   │   │       │   ├── transform_range_adjust.cpp
   │   │   │       │   ├── validation_tilt_pairs.cpp
   │   │   │       │   ├── validation_tilt_pairs.h
   │   │   │       │   ├── volume_enhance_contrast.cpp
   │   │   │       │   ├── volume_enhance_contrast.h
   │   │   │       │   ├── volume_pca.cpp
   │   │   │       │   ├── volume_pca.h
   │   │   │       │   ├── volume_reslice.cpp
   │   │   │       │   ├── volume_validate_pca.cpp
   │   │   │       │   ├── volume_validate_pca.h
   │   │   │       │   ├── xray_import.cpp
   │   │   │       │   ├── xray_import.h
   │   │   │       │   └── xray_psf_create.cpp
   │   │   │       ├── reconstruction_adapt_cuda
   │   │   │       │   ├── xmipp_gpu_correlation.cpp
   │   │   │       │   ├── xmipp_gpu_correlation.h
   │   │   │       │   ├── xmipp_gpu_utils.cpp
   │   │   │       │   └── xmipp_gpu_utils.h
   │   │   │       ├── reconstruction_starpu
   │   │   │       │   ├── mpi
   │   │   │       │   │   ├── mpi_reconstruct_fourier_starpu.cpp
   │   │   │       │   │   └── mpi_reconstruct_fourier_starpu.h
   │   │   │       │   ├── reconstruct_fourier_codelet_load_projections.cpp
   │   │   │       │   ├── reconstruct_fourier_codelet_padded_image_to_fft.cpp
   │   │   │       │   ├── reconstruct_fourier_codelet_reconstruct.cpp
   │   │   │       │   ├── reconstruct_fourier_codelet_redux.cpp
   │   │   │       │   ├── reconstruct_fourier_codelets.cpp
   │   │   │       │   ├── reconstruct_fourier_codelets.h
   │   │   │       │   ├── reconstruct_fourier_defines.h
   │   │   │       │   ├── reconstruct_fourier_scheduler.cpp
   │   │   │       │   ├── reconstruct_fourier_scheduler.h
   │   │   │       │   ├── reconstruct_fourier_timing.cpp
   │   │   │       │   ├── reconstruct_fourier_timing.h
   │   │   │       │   ├── reconstruct_fourier_util.h
   │   │   │       │   └── util
   │   │   │       │       └── queue_bag.h
   │   │   │       └── tomo
   │   │   │           ├── resolution_monotomo.cpp
   │   │   │           └── resolution_monotomo.h
   │   │   ├── libraries
   │   │   │   ├── classification
   │   │   │   │   ├── ahc_classifier.cpp
   │   │   │   │   ├── ahc_classifier.h
   │   │   │   │   ├── analyze_cluster.cpp
   │   │   │   │   ├── analyze_cluster.h
   │   │   │   │   ├── base_algorithm.h
   │   │   │   │   ├── batch_som.cpp
   │   │   │   │   ├── batch_som.h
   │   │   │   │   ├── code_book.cpp
   │   │   │   │   ├── code_book.h
   │   │   │   │   ├── data_set.h
   │   │   │   │   ├── data_types.h
   │   │   │   │   ├── fcmeans.cpp
   │   │   │   │   ├── fcmeans.h
   │   │   │   │   ├── fkcn.cpp
   │   │   │   │   ├── fkcn.h
   │   │   │   │   ├── fuzzy_code_book.cpp
   │   │   │   │   ├── fuzzy_code_book.h
   │   │   │   │   ├── fuzzy_som.cpp
   │   │   │   │   ├── fuzzy_som.h
   │   │   │   │   ├── gaussian_kerdensom.cpp
   │   │   │   │   ├── gaussian_kerdensom.h
   │   │   │   │   ├── kerdensom.cpp
   │   │   │   │   ├── kerdensom.h
   │   │   │   │   ├── knn_classifier.cpp
   │   │   │   │   ├── knn_classifier.h
   │   │   │   │   ├── kSVD.cpp
   │   │   │   │   ├── kSVD.h
   │   │   │   │   ├── map.cpp
   │   │   │   │   ├── map.h
   │   │   │   │   ├── naive_bayes.cpp
   │   │   │   │   ├── naive_bayes.h
   │   │   │   │   ├── pca.cpp
   │   │   │   │   ├── pca.h
   │   │   │   │   ├── sammon.cpp
   │   │   │   │   ├── sammon.h
   │   │   │   │   ├── som.cpp
   │   │   │   │   ├── som.h
   │   │   │   │   ├── svm_classifier.cpp
   │   │   │   │   ├── svm_classifier.h
   │   │   │   │   ├── svm.cpp
   │   │   │   │   ├── training_set.h
   │   │   │   │   ├── training_vector.cpp
   │   │   │   │   ├── training_vector.h
   │   │   │   │   └── vector_ops.h
   │   │   │   ├── data
   │   │   │   │   ├── aft.h
   │   │   │   │   ├── alignment_estimation.h
   │   │   │   │   ├── alignment_result.h
   │   │   │   │   ├── array_2D.h
   │   │   │   │   ├── basic_pca.cpp
   │   │   │   │   ├── basic_pca.h
   │   │   │   │   ├── basis.cpp
   │   │   │   │   ├── basis.h
   │   │   │   │   ├── blobs.cpp
   │   │   │   │   ├── blobs.h
   │   │   │   │   ├── bspline_grid.h
   │   │   │   │   ├── chimeraTesterC.txt
   │   │   │   │   ├── chimeraTesterD.txt
   │   │   │   │   ├── chimeraTesterI2.txt
   │   │   │   │   ├── chimeraTesterO.txt
   │   │   │   │   ├── chimeraTesterT.txt
   │   │   │   │   ├── cpu.cpp
   │   │   │   │   ├── cpu.h
   │   │   │   │   ├── ctf.cpp
   │   │   │   │   ├── ctf.h
   │   │   │   │   ├── cuda_compatibility.h
   │   │   │   │   ├── dimensions.h
   │   │   │   │   ├── euler.cpp
   │   │   │   │   ├── euler.h
   │   │   │   │   ├── fft_settings.cpp
   │   │   │   │   ├── fft_settings.h
   │   │   │   │   ├── fftwT.cpp
   │   │   │   │   ├── fftwT.h
   │   │   │   │   ├── filters.cpp
   │   │   │   │   ├── filters.h
   │   │   │   │   ├── fourier_filter.cpp
   │   │   │   │   ├── fourier_filter.h
   │   │   │   │   ├── fourier_projection.cpp
   │   │   │   │   ├── fourier_projection.h
   │   │   │   │   ├── grids.cpp
   │   │   │   │   ├── grids.h
   │   │   │   │   ├── hw.h
   │   │   │   │   ├── image_operate.cpp
   │   │   │   │   ├── image_operate.h
   │   │   │   │   ├── image_resize.cpp
   │   │   │   │   ├── image_resize.h
   │   │   │   │   ├── integration.cpp
   │   │   │   │   ├── integration.h
   │   │   │   │   ├── local_alignment_result.h
   │   │   │   │   ├── mask.cpp
   │   │   │   │   ├── mask.h
   │   │   │   │   ├── micrograph.cpp
   │   │   │   │   ├── micrograph.h
   │   │   │   │   ├── monogenic_signal.cpp
   │   │   │   │   ├── monogenic_signal.h
   │   │   │   │   ├── morphology.cpp
   │   │   │   │   ├── morphology.h
   │   │   │   │   ├── normalize.cpp
   │   │   │   │   ├── normalize.h
   │   │   │   │   ├── numerical_tools.cpp
   │   │   │   │   ├── numerical_tools.h
   │   │   │   │   ├── pdb.cpp
   │   │   │   │   ├── pdb.h
   │   │   │   │   ├── phantom.cpp
   │   │   │   │   ├── phantom.h
   │   │   │   │   ├── point2D.h
   │   │   │   │   ├── point3D.h
   │   │   │   │   ├── point.h
   │   │   │   │   ├── polar.cpp
   │   │   │   │   ├── polar.h
   │   │   │   │   ├── projection.cpp
   │   │   │   │   ├── projection.h
   │   │   │   │   ├── rectangle.h
   │   │   │   │   ├── rotational_spectrum.cpp
   │   │   │   │   ├── rotational_spectrum.h
   │   │   │   │   ├── sampling.cpp
   │   │   │   │   ├── sampling.h
   │   │   │   │   ├── sparse_matrix2d.cpp
   │   │   │   │   ├── sparse_matrix2d.h
   │   │   │   │   ├── spherical_harmonics.cpp
   │   │   │   │   ├── spherical_harmonics.h
   │   │   │   │   ├── splines.cpp
   │   │   │   │   ├── splines.h
   │   │   │   │   ├── steerable.cpp
   │   │   │   │   ├── steerable.h
   │   │   │   │   ├── symmetries.cpp
   │   │   │   │   ├── symmetries.h
   │   │   │   │   ├── transform_downsample.cpp
   │   │   │   │   ├── transform_downsample.h
   │   │   │   │   ├── transform_geometry.cpp
   │   │   │   │   ├── transform_geometry.h
   │   │   │   │   ├── unitCell.cpp
   │   │   │   │   ├── unitCell.h
   │   │   │   │   ├── vectorial.h
   │   │   │   │   ├── wavelet.cpp
   │   │   │   │   ├── wavelet.h
   │   │   │   │   ├── wiener2d.cpp
   │   │   │   │   ├── wiener2d.h
   │   │   │   │   ├── xmipp_image_convert.cpp
   │   │   │   │   ├── xmipp_image_convert.h
   │   │   │   │   ├── xmipp_image_over.cpp
   │   │   │   │   ├── xmipp_image_over.h
   │   │   │   │   ├── xmipp_polynomials.cpp
   │   │   │   │   └── xmipp_polynomials.h
   │   │   │   ├── dimred
   │   │   │   │   ├── diffusionMaps.cpp
   │   │   │   │   ├── diffusionMaps.h
   │   │   │   │   ├── dimred_tools.cpp
   │   │   │   │   ├── dimred_tools.h
   │   │   │   │   ├── gplvm.cpp
   │   │   │   │   ├── gplvm.h
   │   │   │   │   ├── hessianLLE.cpp
   │   │   │   │   ├── hessianLLE.h
   │   │   │   │   ├── kernelPCA.cpp
   │   │   │   │   ├── kernelPCA.h
   │   │   │   │   ├── laplacianEigenmaps.cpp
   │   │   │   │   ├── laplacianEigenmaps.h
   │   │   │   │   ├── lltsa.cpp
   │   │   │   │   ├── lltsa.h
   │   │   │   │   ├── lpp.cpp
   │   │   │   │   ├── lpp.h
   │   │   │   │   ├── ltsa.cpp
   │   │   │   │   ├── ltsa.h
   │   │   │   │   ├── matrix_dimred.cpp
   │   │   │   │   ├── matrix_dimred.h
   │   │   │   │   ├── nca.cpp
   │   │   │   │   ├── nca.h
   │   │   │   │   ├── npe.cpp
   │   │   │   │   ├── npe.h
   │   │   │   │   ├── pca.cpp
   │   │   │   │   ├── pca.h
   │   │   │   │   ├── probabilisticPCA.cpp
   │   │   │   │   ├── probabilisticPCA.h
   │   │   │   │   ├── spe.cpp
   │   │   │   │   ├── spe.h
   │   │   │   │   ├── transform_dimred.cpp
   │   │   │   │   └── transform_dimred.h
   │   │   │   ├── interface
   │   │   │   │   ├── docfile.cpp
   │   │   │   │   ├── docfile.h
   │   │   │   │   ├── frm.cpp
   │   │   │   │   ├── frm.h
   │   │   │   │   ├── python_utils.cpp
   │   │   │   │   ├── python_utils.h
   │   │   │   │   ├── selfile.cpp
   │   │   │   │   ├── selfile.h
   │   │   │   │   ├── spider.cpp
   │   │   │   │   ├── spider.h
   │   │   │   │   └── virus.h
   │   │   │   ├── parallel
   │   │   │   │   ├── mpi_angular_accuracy_pca.cpp
   │   │   │   │   ├── mpi_angular_accuracy_pca.h
   │   │   │   │   ├── mpi_angular_assignment_mag.cpp
   │   │   │   │   ├── mpi_angular_assignment_mag.h
   │   │   │   │   ├── mpi_angular_class_average.cpp
   │   │   │   │   ├── mpi_angular_class_average.h
   │   │   │   │   ├── mpi_angular_continuous_assign.cpp
   │   │   │   │   ├── mpi_angular_projection_matching.cpp
   │   │   │   │   ├── mpi_angular_projection_matching.h
   │   │   │   │   ├── mpi_angular_project_library.cpp
   │   │   │   │   ├── mpi_angular_sph_alignment.cpp
   │   │   │   │   ├── mpi_classify_CL2D_core_analysis.cpp
   │   │   │   │   ├── mpi_classify_CL2D_core_analysis.h
   │   │   │   │   ├── mpi_classify_CL2D.cpp
   │   │   │   │   ├── mpi_classify_CL2D.h
   │   │   │   │   ├── mpi_classify_CLTomo.h
   │   │   │   │   ├── mpi_classify_CLTomo_prog.cpp
   │   │   │   │   ├── mpi_classify_FTTRI.cpp
   │   │   │   │   ├── mpi_classify_FTTRI.h
   │   │   │   │   ├── mpi_forward_zernike_images.cpp
   │   │   │   │   ├── mpi_forward_zernike_images_priors.cpp
   │   │   │   │   ├── mpi_forward_zernike_subtomos.cpp
   │   │   │   │   ├── mpi_image_rotational_pca.cpp
   │   │   │   │   ├── mpi_image_rotational_pca.h
   │   │   │   │   ├── mpi_image_sort.cpp
   │   │   │   │   ├── mpi_ml_align2d.cpp
   │   │   │   │   ├── mpi_ml_align2d.h
   │   │   │   │   ├── mpi_multireference_aligneability.cpp
   │   │   │   │   ├── mpi_multireference_aligneability.h
   │   │   │   │   ├── mpi_nma_alignment.cpp
   │   │   │   │   ├── mpi_nma_alignment_vol.cpp
   │   │   │   │   ├── mpi_nma_alignment_vol.h
   │   │   │   │   ├── mpi_performance_test.cpp
   │   │   │   │   ├── mpi_performance_test.h
   │   │   │   │   ├── mpi_reconstruct_art.cpp
   │   │   │   │   ├── mpi_reconstruct_art.h
   │   │   │   │   ├── mpi_reconstruct_fourier_accel.cpp
   │   │   │   │   ├── mpi_reconstruct_fourier_accel.h
   │   │   │   │   ├── mpi_reconstruct_fourier.cpp
   │   │   │   │   ├── mpi_reconstruct_fourier.h
   │   │   │   │   ├── mpi_reconstruct_significant.cpp
   │   │   │   │   ├── mpi_reconstruct_significant.h
   │   │   │   │   ├── mpi_reconstruct_wbp.cpp
   │   │   │   │   ├── mpi_reconstruct_wbp.h
   │   │   │   │   ├── mpi_run.cpp
   │   │   │   │   ├── mpi_subtomo_subtraction.cpp
   │   │   │   │   ├── mpi_subtomo_subtraction.h
   │   │   │   │   ├── mpi_subtract_projection.cpp
   │   │   │   │   ├── mpi_subtract_projection.h
   │   │   │   │   ├── mpi_transform_adjust_image_grey_levels.cpp
   │   │   │   │   ├── mpi_validation_nontilt.cpp
   │   │   │   │   ├── mpi_validation_nontilt.h
   │   │   │   │   ├── mpi_volumeset_align.cpp
   │   │   │   │   ├── mpi_volumeset_align.h
   │   │   │   │   ├── xmipp_mpi.cpp
   │   │   │   │   └── xmipp_mpi.h
   │   │   │   ├── parallel_adapt_cuda
   │   │   │   │   ├── mpi_reconstruct_fourier_gpu.cpp
   │   │   │   │   └── mpi_reconstruct_fourier_gpu.h
   │   │   │   ├── parallel_adapt_cuda11
   │   │   │   ├── py_xmipp
   │   │   │   │   ├── classifyPcaFuntion
   │   │   │   │   │   ├── assessment.py
   │   │   │   │   │   ├── bnb_gpu.py
   │   │   │   │   │   ├── __init__.py
   │   │   │   │   │   └── pca_gpu.py
   │   │   │   │   ├── coordinatesTools
   │   │   │   │   │   ├── coordinatesTools.py
   │   │   │   │   │   └── __init__.py
   │   │   │   │   ├── deepConsensusWorkers
   │   │   │   │   │   ├── deepConsensus_deepLearning1.py
   │   │   │   │   │   ├── deepConsensus_networkDef.py
   │   │   │   │   │   ├── __init__.py
   │   │   │   │   │   └── updateModels.py
   │   │   │   │   ├── deepDenoising
   │   │   │   │   │   ├── augmentators.py
   │   │   │   │   │   ├── dataGenerator.py
   │   │   │   │   │   ├── DeepLearningGeneric.py
   │   │   │   │   │   ├── gan.py
   │   │   │   │   │   ├── __init__.py
   │   │   │   │   │   └── unet.py
   │   │   │   │   ├── deepLearningToolkitUtils
   │   │   │   │   │   ├── __init__.py
   │   │   │   │   │   └── utils.py
   │   │   │   │   ├── deepResLearner
   │   │   │   │   │   ├── cnn_deepRes_1_7.py
   │   │   │   │   │   ├── cnn_deepRes_2_13.py
   │   │   │   │   │   └── __init__.py
   │   │   │   │   ├── example_module2
   │   │   │   │   │   ├── example_inmodule2.py
   │   │   │   │   │   └── __init__.py
   │   │   │   │   ├── example_module.py
   │   │   │   │   └── swiftalign
   │   │   │   │       ├── alignment
   │   │   │   │       │   ├── __init__.py
   │   │   │   │       │   └── InPlaneTransformCorrector.py
   │   │   │   │       ├── classification
   │   │   │   │       │   ├── aligned_2d_classficiation.py
   │   │   │   │       │   └── __init__.py
   │   │   │   │       ├── image
   │   │   │   │       │   ├── __init__.py
   │   │   │   │       │   ├── Path.py
   │   │   │   │       │   ├── read.py
   │   │   │   │       │   ├── torch_utils
   │   │   │   │       │   │   ├── Dataset.py
   │   │   │   │       │   │   └── __init__.py
   │   │   │   │       │   ├── utils.py
   │   │   │   │       │   └── write.py
   │   │   │   │       ├── __init__.py
   │   │   │   │       ├── metadata
   │   │   │   │       │   ├── __init__.py
   │   │   │   │       │   ├── labels.py
   │   │   │   │       │   ├── read.py
   │   │   │   │       │   ├── utils.py
   │   │   │   │       │   └── write.py
   │   │   │   │       ├── operators
   │   │   │   │       │   ├── __init__.py
   │   │   │   │       │   └── MaskFlattener.py
   │   │   │   │       ├── transform
   │   │   │   │       │   ├── affine_2d.py
   │   │   │   │       │   ├── affine_matrix_2d.py
   │   │   │   │       │   ├── euler_to_matrix.py
   │   │   │   │       │   ├── euler_to_quaternion.py
   │   │   │   │       │   ├── __init__.py
   │   │   │   │       │   ├── matrix_to_euler.py
   │   │   │   │       │   ├── quaternion_arithmetic.py
   │   │   │   │       │   ├── quaternion_to_matrix.py
   │   │   │   │       │   ├── rotation_matrix_2d.py
   │   │   │   │       │   └── twist_swing_decomposition.py
   │   │   │   │       └── utils
   │   │   │   │           ├── __init__.py
   │   │   │   │           ├── LruCache.py
   │   │   │   │           └── progress_bar.py
   │   │   │   ├── reconstruction
   │   │   │   │   ├── aalign_significant.cpp
   │   │   │   │   ├── aalign_significant.h
   │   │   │   │   ├── adjust_volume_grey_levels.cpp
   │   │   │   │   ├── adjust_volume_grey_levels.h
   │   │   │   │   ├── aextrema_finder.cpp
   │   │   │   │   ├── aextrema_finder.h
   │   │   │   │   ├── ageo_transformer.h
   │   │   │   │   ├── align2d.cpp
   │   │   │   │   ├── align2d.h
   │   │   │   │   ├── align_tilt_pairs.cpp
   │   │   │   │   ├── align_tilt_pairs.h
   │   │   │   │   ├── align_type.h
   │   │   │   │   ├── amerit_computer.h
   │   │   │   │   ├── angular_accuracy_pca.cpp
   │   │   │   │   ├── angular_accuracy_pca.h
   │   │   │   │   ├── angular_assignment_mag.cpp
   │   │   │   │   ├── angular_assignment_mag.h
   │   │   │   │   ├── angular_break_symmetry.cpp
   │   │   │   │   ├── angular_break_symmetry.h
   │   │   │   │   ├── angular_commonline.cpp
   │   │   │   │   ├── angular_commonline.h
   │   │   │   │   ├── angular_continuous_assign2.cpp
   │   │   │   │   ├── angular_continuous_assign2.h
   │   │   │   │   ├── angular_continuous_assign.cpp
   │   │   │   │   ├── angular_continuous_assign.h
   │   │   │   │   ├── angular_discrete_assign.cpp
   │   │   │   │   ├── angular_discrete_assign.h
   │   │   │   │   ├── angular_distance.cpp
   │   │   │   │   ├── angular_distance.h
   │   │   │   │   ├── angular_distribution_show.cpp
   │   │   │   │   ├── angular_estimate_tilt_axis.cpp
   │   │   │   │   ├── angular_estimate_tilt_axis.h
   │   │   │   │   ├── angular_neighbourhood.cpp
   │   │   │   │   ├── angular_neighbourhood.h
   │   │   │   │   ├── angular_projection_matching.cpp
   │   │   │   │   ├── angular_projection_matching.h
   │   │   │   │   ├── angular_project_library.cpp
   │   │   │   │   ├── angular_project_library.h
   │   │   │   │   ├── angular_rotate.cpp
   │   │   │   │   ├── angular_sph_alignment.cpp
   │   │   │   │   ├── angular_sph_alignment.h
   │   │   │   │   ├── arotation_estimator.cpp
   │   │   │   │   ├── arotation_estimator.h
   │   │   │   │   ├── art_crystal.cpp
   │   │   │   │   ├── art_crystal.h
   │   │   │   │   ├── art_zernike3d.cpp
   │   │   │   │   ├── art_zernike3d.h
   │   │   │   │   ├── ashift_corr_estimator.cpp
   │   │   │   │   ├── ashift_corr_estimator.h
   │   │   │   │   ├── ashift_estimator.cpp
   │   │   │   │   ├── ashift_estimator.h
   │   │   │   │   ├── base_art_recons.cpp
   │   │   │   │   ├── base_art_recons.h
   │   │   │   │   ├── basic_art.cpp
   │   │   │   │   ├── basic_art.h
   │   │   │   │   ├── bspline_geo_transformer.cpp
   │   │   │   │   ├── bspline_geo_transformer.h
   │   │   │   │   ├── bspline_helper.cpp
   │   │   │   │   ├── bspline_helper.h
   │   │   │   │   ├── classify_compare_classes.cpp
   │   │   │   │   ├── classify_compare_classes.h
   │   │   │   │   ├── classify_evaluate_classes.cpp
   │   │   │   │   ├── classify_evaluate_classes.h
   │   │   │   │   ├── classify_extract_features.cpp
   │   │   │   │   ├── classify_extract_features.h
   │   │   │   │   ├── classify_first_split3.cpp
   │   │   │   │   ├── classify_first_split3.h
   │   │   │   │   ├── classify_first_split.cpp
   │   │   │   │   ├── classify_first_split.h
   │   │   │   │   ├── classify_kerdensom.cpp
   │   │   │   │   ├── compare_density.cpp
   │   │   │   │   ├── compare_density.h
   │   │   │   │   ├── compare_views.cpp
   │   │   │   │   ├── compare_views.h
   │   │   │   │   ├── coordinates_noisy_zones_filter.cpp
   │   │   │   │   ├── coordinates_noisy_zones_filter.h
   │   │   │   │   ├── correlation_computer.cpp
   │   │   │   │   ├── correlation_computer.h
   │   │   │   │   ├── ctf_correct_phase.cpp
   │   │   │   │   ├── ctf_correct_phase.h
   │   │   │   │   ├── ctf_correct_wiener2d.cpp
   │   │   │   │   ├── ctf_correct_wiener2d.h
   │   │   │   │   ├── ctf_correct_wiener3d.cpp
   │   │   │   │   ├── ctf_correct_wiener3d.h
   │   │   │   │   ├── ctf_enhance_psd.cpp
   │   │   │   │   ├── ctf_enhance_psd.h
   │   │   │   │   ├── ctf_estimate_from_micrograph.cpp
   │   │   │   │   ├── ctf_estimate_from_micrograph.h
   │   │   │   │   ├── ctf_estimate_from_psd_base.cpp
   │   │   │   │   ├── ctf_estimate_from_psd_base.h
   │   │   │   │   ├── ctf_estimate_from_psd.cpp
   │   │   │   │   ├── ctf_estimate_from_psd_fast.cpp
   │   │   │   │   ├── ctf_estimate_from_psd_fast.h
   │   │   │   │   ├── ctf_estimate_from_psd.h
   │   │   │   │   ├── ctf_estimate_psd_with_arma.cpp
   │   │   │   │   ├── ctf_estimate_psd_with_arma.h
   │   │   │   │   ├── ctf_group.cpp
   │   │   │   │   ├── ctf_group.h
   │   │   │   │   ├── ctf_phase_flip.cpp
   │   │   │   │   ├── ctf_phase_flip.h
   │   │   │   │   ├── ctf_sort_psds.cpp
   │   │   │   │   ├── ctf_sort_psds.h
   │   │   │   │   ├── denoise.cpp
   │   │   │   │   ├── denoise.h
   │   │   │   │   ├── directions.cpp
   │   │   │   │   ├── directions.h
   │   │   │   │   ├── eq_system_solver.cpp
   │   │   │   │   ├── eq_system_solver.h
   │   │   │   │   ├── flexible_alignment.cpp
   │   │   │   │   ├── flexible_alignment.h
   │   │   │   │   ├── forward_art_zernike3d_subtomos.cpp
   │   │   │   │   ├── forward_art_zernike3d_subtomos.h
   │   │   │   │   ├── forward_zernike_images.cpp
   │   │   │   │   ├── forward_zernike_images.h
   │   │   │   │   ├── forward_zernike_images_priors.cpp
   │   │   │   │   ├── forward_zernike_images_priors.h
   │   │   │   │   ├── forward_zernike_subtomos.cpp
   │   │   │   │   ├── forward_zernike_subtomos.h
   │   │   │   │   ├── forward_zernike_volume.cpp
   │   │   │   │   ├── forward_zernike_volume.h
   │   │   │   │   ├── fringe_processing.cpp
   │   │   │   │   ├── fringe_processing.h
   │   │   │   │   ├── gpu_geo_transformer_defines.h
   │   │   │   │   ├── image_assignment_tilt_pair.cpp
   │   │   │   │   ├── image_assignment_tilt_pair.h
   │   │   │   │   ├── image_eliminate_byEnergy.cpp
   │   │   │   │   ├── image_eliminate_byEnergy.h
   │   │   │   │   ├── image_eliminate_empty_particles.cpp
   │   │   │   │   ├── image_eliminate_empty_particles.h
   │   │   │   │   ├── image_find_center.cpp
   │   │   │   │   ├── image_header.cpp
   │   │   │   │   ├── image_histogram.cpp
   │   │   │   │   ├── image_odd_even.cpp
   │   │   │   │   ├── image_odd_even.h
   │   │   │   │   ├── image_peak_high_contrast.cpp
   │   │   │   │   ├── image_peak_high_contrast.h
   │   │   │   │   ├── image_rotational_pca.cpp
   │   │   │   │   ├── image_rotational_pca.h
   │   │   │   │   ├── image_sort_by_statistics.cpp
   │   │   │   │   ├── image_sort_by_statistics.h
   │   │   │   │   ├── image_statistics.cpp
   │   │   │   │   ├── image_vectorize.cpp
   │   │   │   │   ├── iterative_alignment_estimator.cpp
   │   │   │   │   ├── iterative_alignment_estimator.h
   │   │   │   │   ├── local_volume_adjust.cpp
   │   │   │   │   ├── local_volume_adjust.h
   │   │   │   │   ├── mean_shift.cpp
   │   │   │   │   ├── mean_shift.h
   │   │   │   │   ├── metadata_histogram.cpp
   │   │   │   │   ├── metadata_split_3D.cpp
   │   │   │   │   ├── metadata_split_3D.h
   │   │   │   │   ├── metadata_split.cpp
   │   │   │   │   ├── metadata_utilities.cpp
   │   │   │   │   ├── metadata_xml.cpp
   │   │   │   │   ├── micrograph_automatic_picking2.cpp
   │   │   │   │   ├── micrograph_automatic_picking2.h
   │   │   │   │   ├── micrograph_scissor.cpp
   │   │   │   │   ├── ml2d.cpp
   │   │   │   │   ├── ml2d.h
   │   │   │   │   ├── ml_align2d.cpp
   │   │   │   │   ├── ml_align2d.h
   │   │   │   │   ├── mlf_align2d.cpp
   │   │   │   │   ├── mlf_align2d.h
   │   │   │   │   ├── movie_alignment_correlation_base.cpp
   │   │   │   │   ├── movie_alignment_correlation_base.h
   │   │   │   │   ├── movie_alignment_correlation.cpp
   │   │   │   │   ├── movie_alignment_correlation.h
   │   │   │   │   ├── movie_alignment_gpu_defines.h
   │   │   │   │   ├── movie_estimate_gain.cpp
   │   │   │   │   ├── movie_estimate_gain.h
   │   │   │   │   ├── movie_filter_dose.cpp
   │   │   │   │   ├── movie_filter_dose.h
   │   │   │   │   ├── multireference_aligneability.cpp
   │   │   │   │   ├── multireference_aligneability.h
   │   │   │   │   ├── nma_alignment.cpp
   │   │   │   │   ├── nma_alignment.h
   │   │   │   │   ├── nma_alignment_vol.cpp
   │   │   │   │   ├── nma_alignment_vol.h
   │   │   │   │   ├── pdb_analysis.cpp
   │   │   │   │   ├── pdb_analysis.h
   │   │   │   │   ├── pdb_label_from_volume.cpp
   │   │   │   │   ├── pdb_label_from_volume.h
   │   │   │   │   ├── pdb_nma_deform.cpp
   │   │   │   │   ├── pdb_nma_deform.h
   │   │   │   │   ├── pdb_reduce_pseudoatoms.cpp
   │   │   │   │   ├── pdb_reduce_pseudoatoms.h
   │   │   │   │   ├── pdb_sph_deform.cpp
   │   │   │   │   ├── pdb_sph_deform.h
   │   │   │   │   ├── phantom_movie.cpp
   │   │   │   │   ├── phantom_movie.h
   │   │   │   │   ├── phantom_movie_param_estimator.m
   │   │   │   │   ├── phantom_simulate_microscope.cpp
   │   │   │   │   ├── phantom_simulate_microscope.h
   │   │   │   │   ├── phantom_transform.cpp
   │   │   │   │   ├── polar_rotation_estimator.cpp
   │   │   │   │   ├── polar_rotation_estimator.h
   │   │   │   │   ├── precompute_sampling.cpp
   │   │   │   │   ├── precompute_sampling.h
   │   │   │   │   ├── program_extension.cpp
   │   │   │   │   ├── program_extension.h
   │   │   │   │   ├── program_filter.cpp
   │   │   │   │   ├── program_filter.h
   │   │   │   │   ├── program_image_residuals.cpp
   │   │   │   │   ├── program_image_residuals.h
   │   │   │   │   ├── program_image_ssnr.cpp
   │   │   │   │   ├── program_image_ssnr.h
   │   │   │   │   ├── project.cpp
   │   │   │   │   ├── project_crystal.cpp
   │   │   │   │   ├── project_crystal.h
   │   │   │   │   ├── project.h
   │   │   │   │   ├── project_real_shears.cpp
   │   │   │   │   ├── project_real_shears.h
   │   │   │   │   ├── project_tomography.cpp
   │   │   │   │   ├── project_tomography.h
   │   │   │   │   ├── psd_estimator.cpp
   │   │   │   │   ├── psd_estimator.h
   │   │   │   │   ├── radon.cpp
   │   │   │   │   ├── radon.h
   │   │   │   │   ├── recons.h
   │   │   │   │   ├── recons_misc.cpp
   │   │   │   │   ├── recons_misc.h
   │   │   │   │   ├── reconstruct_art.cpp
   │   │   │   │   ├── reconstruct_art.h
   │   │   │   │   ├── reconstruct_fourier_accel.cpp
   │   │   │   │   ├── reconstruct_fourier_accel.h
   │   │   │   │   ├── reconstruct_fourier_buffer_data.h
   │   │   │   │   ├── reconstruct_fourier.cpp
   │   │   │   │   ├── reconstruct_fourier_defines.h
   │   │   │   │   ├── reconstruct_fourier.h
   │   │   │   │   ├── reconstruct_fourier_projection_traverse_space.h
   │   │   │   │   ├── reconstruct_significant.cpp
   │   │   │   │   ├── reconstruct_significant.h
   │   │   │   │   ├── reconstruct_wbp.cpp
   │   │   │   │   ├── reconstruct_wbp.h
   │   │   │   │   ├── refinement.cpp
   │   │   │   │   ├── refinement.h
   │   │   │   │   ├── resolution_directional.cpp
   │   │   │   │   ├── resolution_directional.h
   │   │   │   │   ├── resolution_fsc.cpp
   │   │   │   │   ├── resolution_fsc.h
   │   │   │   │   ├── resolution_fso.cpp
   │   │   │   │   ├── resolution_fso.h
   │   │   │   │   ├── resolution_localfilter.cpp
   │   │   │   │   ├── resolution_localfilter.h
   │   │   │   │   ├── resolution_monogenic_signal.cpp
   │   │   │   │   ├── resolution_monogenic_signal.h
   │   │   │   │   ├── resolution_pdb_bfactor.cpp
   │   │   │   │   ├── resolution_pdb_bfactor.h
   │   │   │   │   ├── shift_corr_estimator.cpp
   │   │   │   │   ├── shift_corr_estimator.h
   │   │   │   │   ├── single_extrema_finder.cpp
   │   │   │   │   ├── single_extrema_finder.h
   │   │   │   │   ├── subtomo_subtraction.cpp
   │   │   │   │   ├── subtomo_subtraction.h
   │   │   │   │   ├── subtract_projection.cpp
   │   │   │   │   ├── subtract_projection.h
   │   │   │   │   ├── symmetrize.cpp
   │   │   │   │   ├── symmetrize.h
   │   │   │   │   ├── threshold.cpp
   │   │   │   │   ├── threshold.h
   │   │   │   │   ├── transform_add_noise.cpp
   │   │   │   │   ├── transform_adjust_image_grey_levels.cpp
   │   │   │   │   ├── transform_adjust_image_grey_levels.h
   │   │   │   │   ├── transform_center_image.cpp
   │   │   │   │   ├── transform_morphology.cpp
   │   │   │   │   ├── transform_window.cpp
   │   │   │   │   ├── validation_nontilt.cpp
   │   │   │   │   ├── validation_nontilt.h
   │   │   │   │   ├── volume_align_prog.cpp
   │   │   │   │   ├── volume_apply_coefficient_zernike3d.cpp
   │   │   │   │   ├── volume_apply_coefficient_zernike3d.h
   │   │   │   │   ├── volume_apply_deform_sph.cpp
   │   │   │   │   ├── volume_apply_deform_sph.h
   │   │   │   │   ├── volume_correct_bfactor.cpp
   │   │   │   │   ├── volume_correct_bfactor.h
   │   │   │   │   ├── volume_deform_sph.cpp
   │   │   │   │   ├── volume_deform_sph.h
   │   │   │   │   ├── volume_find_symmetry.cpp
   │   │   │   │   ├── volume_from_pdb.cpp
   │   │   │   │   ├── volume_from_pdb.h
   │   │   │   │   ├── volume_halves_restoration.cpp
   │   │   │   │   ├── volume_halves_restoration.h
   │   │   │   │   ├── volume_initial_simulated_annealing.cpp
   │   │   │   │   ├── volume_initial_simulated_annealing.h
   │   │   │   │   ├── volume_local_sharpening.cpp
   │   │   │   │   ├── volume_local_sharpening.h
   │   │   │   │   ├── volume_segment.cpp
   │   │   │   │   ├── volume_segment.h
   │   │   │   │   ├── volumeset_align.cpp
   │   │   │   │   ├── volumeset_align.h
   │   │   │   │   ├── volume_structure_factor.cpp
   │   │   │   │   ├── volume_subtraction.cpp
   │   │   │   │   ├── volume_subtraction.h
   │   │   │   │   ├── volume_to_pseudoatoms.cpp
   │   │   │   │   ├── volume_to_pseudoatoms.h
   │   │   │   │   └── volume_to_web.cpp
   │   │   │   ├── reconstruction_adapt_cuda
   │   │   │   │   ├── align_significant_gpu.cpp
   │   │   │   │   ├── align_significant_gpu.h
   │   │   │   │   ├── angular_continuous_assign2_gpu.cpp
   │   │   │   │   ├── angular_continuous_assign2_gpu.h
   │   │   │   │   ├── angular_sph_alignment_gpu.cpp
   │   │   │   │   ├── angular_sph_alignment_gpu.h
   │   │   │   │   ├── basic_mem_manager.h
   │   │   │   │   ├── movie_alignment_correlation_gpu.cpp
   │   │   │   │   ├── movie_alignment_correlation_gpu.h
   │   │   │   │   ├── reconstruct_fourier_gpu.cpp
   │   │   │   │   ├── reconstruct_fourier_gpu.h
   │   │   │   │   ├── volume_deform_sph_gpu.cpp
   │   │   │   │   ├── volume_deform_sph_gpu.h
   │   │   │   │   ├── volume_halves_restoration_gpu.cpp
   │   │   │   │   └── volume_halves_restoration_gpu.h
   │   │   │   ├── reconstruction_adapt_cuda11
   │   │   │   │   ├── forward_art_zernike3d_gpu.cpp
   │   │   │   │   └── forward_art_zernike3d_gpu.h
   │   │   │   ├── reconstruction_cuda
   │   │   │   │   ├── basic_mem_manager.cpp
   │   │   │   │   ├── cuda_all.cpp
   │   │   │   │   ├── cuda_angular_sph_alignment.cpp
   │   │   │   │   ├── cuda_angular_sph_alignment.cu
   │   │   │   │   ├── cuda_angular_sph_alignment.h
   │   │   │   │   ├── cuda_asserts.h
   │   │   │   │   ├── cuda_basic_math.h
   │   │   │   │   ├── cuda_bspline_geo_transformer.cpp
   │   │   │   │   ├── cuda_bspline_geo_transformer.h
   │   │   │   │   ├── cuda_cdf.cpp
   │   │   │   │   ├── cuda_cdf.cu
   │   │   │   │   ├── cuda_cdf.h
   │   │   │   │   ├── cuda_compatibility.cu
   │   │   │   │   ├── cuda_compatibility.h
   │   │   │   │   ├── cuda_correlation_computer.cpp
   │   │   │   │   ├── cuda_correlation_computer.h
   │   │   │   │   ├── cuda_correlation.cu
   │   │   │   │   ├── cuda_fft.cpp
   │   │   │   │   ├── cuda_fft.h
   │   │   │   │   ├── cuda_flexalign_correlate.cpp
   │   │   │   │   ├── cuda_flexalign_correlate.h
   │   │   │   │   ├── cuda_flexalign_scale.cpp
   │   │   │   │   ├── cuda_flexalign_scale.h
   │   │   │   │   ├── cuda_fourier_projection.cpp
   │   │   │   │   ├── cuda_fourier_projection.cu
   │   │   │   │   ├── cuda_fourier_projection.h
   │   │   │   │   ├── cuda_geo_linear_interpolator.cu
   │   │   │   │   ├── cuda_gpu_bilib.cu
   │   │   │   │   ├── cuda_gpu_correlation.cpp
   │   │   │   │   ├── cuda_gpu_correlation.h
   │   │   │   │   ├── cuda_gpu_geo_shift_transformer.cpp
   │   │   │   │   ├── cuda_gpu_geo_shift_transformer.cu
   │   │   │   │   ├── cuda_gpu_geo_shift_transformer.h
   │   │   │   │   ├── cuda_gpu_geo_transformer.cpp
   │   │   │   │   ├── cuda_gpu_geo_transformer.cu
   │   │   │   │   ├── cuda_gpu_geo_transformer.h
   │   │   │   │   ├── cuda_gpu_iirconvolve.cu
   │   │   │   │   ├── cuda_gpu_movie_alignment_correlation_kernels.cu
   │   │   │   │   ├── cuda_gpu_multidim_array.cu
   │   │   │   │   ├── cuda_gpu_polar.cu
   │   │   │   │   ├── cuda_gpu_reconstruct_fourier.cpp
   │   │   │   │   ├── cuda_gpu_reconstruct_fourier.h
   │   │   │   │   ├── cuda_rot_polar_estimator.cpp
   │   │   │   │   ├── cuda_rot_polar_estimator.h
   │   │   │   │   ├── cuda_scaleFFT.h
   │   │   │   │   ├── cuda_scaleFFT_kernels.cu
   │   │   │   │   ├── cuda_shift_corr_estimator.cpp
   │   │   │   │   ├── cuda_shift_corr_estimator.h
   │   │   │   │   ├── cuda_single_extrema_finder.cpp
   │   │   │   │   ├── cuda_single_extrema_finder.cu
   │   │   │   │   ├── cuda_single_extrema_finder.h
   │   │   │   │   ├── cuda_vec2.h
   │   │   │   │   ├── cuda_volume_deform_sph.cpp
   │   │   │   │   ├── cuda_volume_deform_sph.cu
   │   │   │   │   ├── cuda_volume_deform_sph_defines.h
   │   │   │   │   ├── cuda_volume_deform_sph.h
   │   │   │   │   ├── cuda_volume_halves_restorator.cpp
   │   │   │   │   ├── cuda_volume_halves_restorator.h
   │   │   │   │   ├── cuda_volume_restoration_kernels.cpp
   │   │   │   │   ├── cuda_volume_restoration_kernels.cu
   │   │   │   │   ├── cuda_volume_restoration_kernels.h
   │   │   │   │   ├── cuda_xmipp_utils.cpp
   │   │   │   │   ├── cuda_xmipp_utils.h
   │   │   │   │   ├── gpu.cpp
   │   │   │   │   └── gpu.h
   │   │   │   ├── reconstruction_cuda11
   │   │   │   │   ├── cuda_forward_art_zernike3d.cpp
   │   │   │   │   ├── cuda_forward_art_zernike3d.cu
   │   │   │   │   ├── cuda_forward_art_zernike3d_defines.h
   │   │   │   │   └── cuda_forward_art_zernike3d.h
   │   │   │   └── tomo
   │   │   │       ├── resolution_monotomo.cpp
   │   │   │       ├── resolution_monotomo.h
   │   │   │       ├── tomo_average_subtomos.cpp
   │   │   │       ├── tomo_average_subtomos.h
   │   │   │       ├── tomo_ctf_wiener2d_correction.cpp
   │   │   │       ├── tomo_ctf_wiener2d_correction.h
   │   │   │       ├── tomo_detect_missing_wedge.cpp
   │   │   │       ├── tomo_detect_missing_wedge.h
   │   │   │       ├── tomo_extract_particlestacks.cpp
   │   │   │       ├── tomo_extract_particlestacks.h
   │   │   │       ├── tomo_extract_subtomograms.cpp
   │   │   │       ├── tomo_extract_subtomograms.h
   │   │   │       ├── tomo_filter_coordinates.cpp
   │   │   │       ├── tomo_filter_coordinates.h
   │   │   │       ├── tomo_map_back.cpp
   │   │   │       ├── tomo_map_back.h
   │   │   │       ├── tomo_simulate_tilt_series.cpp
   │   │   │       ├── tomo_simulate_tilt_series.h
   │   │   │       ├── tomo_tiltseries_dose_filter.cpp
   │   │   │       └── tomo_tiltseries_dose_filter.h
   │   │   ├── resources
   │   │   │   └── test
   │   │   │       ├── dimred
   │   │   │       │   ├── clusters.txt
   │   │   │       │   ├── diffusionMaps.txt
   │   │   │       │   ├── gplvm.txt
   │   │   │       │   ├── helix.txt
   │   │   │       │   ├── hessianlle.txt
   │   │   │       │   ├── intersect.txt
   │   │   │       │   ├── kernelPCA.txt
   │   │   │       │   ├── laplacianEigenmap.txt
   │   │   │       │   ├── lltsaSCG.txt
   │   │   │       │   ├── lltsa.txt
   │   │   │       │   ├── lpp.txt
   │   │   │       │   ├── ltsa.txt
   │   │   │       │   ├── nca.txt
   │   │   │       │   ├── npe.txt
   │   │   │       │   ├── probabilisticPCA.txt
   │   │   │       │   ├── spe.txt
   │   │   │       │   ├── swiss.txt
   │   │   │       │   └── twinpeaks.txt
   │   │   │       ├── EMX
   │   │   │       │   ├── EMXread.emx
   │   │   │       │   ├── EMXwrite_badly_formed_assert.emx
   │   │   │       │   ├── EMXwrite_badly_formed.emx
   │   │   │       │   ├── EMXwrite.emx
   │   │   │       │   └── emx.xsd
   │   │   │       ├── filters
   │   │   │       │   ├── KLH.tif
   │   │   │       │   └── test2.spi
   │   │   │       ├── funcs
   │   │   │       │   ├── singleImage.mrc
   │   │   │       │   └── singleImage.spi
   │   │   │       ├── image
   │   │   │       │   ├── mappedFile.vol
   │   │   │       │   ├── progVol.vol
   │   │   │       │   ├── singleImage.hed
   │   │   │       │   ├── singleImage.img
   │   │   │       │   ├── singleImage.inf
   │   │   │       │   ├── singleImage.mrc
   │   │   │       │   ├── singleImage.raw
   │   │   │       │   ├── singleImage.raw.inf
   │   │   │       │   ├── singleImage.spi
   │   │   │       │   ├── singleImage_swap.spi
   │   │   │       │   ├── singleImage.tif
   │   │   │       │   ├── smallStack.hed
   │   │   │       │   ├── smallStack.img
   │   │   │       │   ├── smallStack.mrcs
   │   │   │       │   ├── smallStack.stk
   │   │   │       │   ├── smallVolumeStackCorrupted.stk
   │   │   │       │   ├── smallVolumeStack.stk
   │   │   │       │   ├── smallVolume.vol
   │   │   │       │   ├── sum.spi
   │   │   │       │   ├── test2.spi
   │   │   │       │   ├── test2_wrap_false.spi
   │   │   │       │   └── test2_wrap_true.spi
   │   │   │       ├── metadata
   │   │   │       │   ├── mDsource.sqlite
   │   │   │       │   ├── mDsource.xmd
   │   │   │       │   ├── mDsource.xml
   │   │   │       │   ├── noXmipp.xmd
   │   │   │       │   ├── ReadWriteAppendBlock.xmd
   │   │   │       │   ├── smallStack.stk
   │   │   │       │   ├── symop.star
   │   │   │       │   ├── WriteIntermediateBlock2.xmd
   │   │   │       │   └── WriteIntermediateBlock.xmd
   │   │   │       ├── polynomials
   │   │   │       │   └── down1_42_Periodogramavg.psd
   │   │   │       ├── pythoninterface
   │   │   │       │   ├── Bsoft
   │   │   │       │   │   └── symop.star
   │   │   │       │   ├── importObject.xmd
   │   │   │       │   ├── progVol.vol
   │   │   │       │   ├── singleImage.spi
   │   │   │       │   ├── smallStack.stk
   │   │   │       │   ├── sum.spi
   │   │   │       │   ├── testBlock.xmd
   │   │   │       │   ├── test_row.xmd
   │   │   │       │   ├── test.xmd
   │   │   │       │   ├── tinyImage.spi
   │   │   │       │   └── tinyRotated.spi
   │   │   │       └── sampling
   │   │   │           ├── experimental_images.xmd
   │   │   │           ├── neigh_ref_c1_exp_sampling.xmd
   │   │   │           ├── neigh_ref_i3h_exp_sampling.xmd
   │   │   │           ├── ref_c1_exp_sampling.xmd
   │   │   │           ├── ref_c1_sampling.xmd
   │   │   │           ├── ref_i3h_exp_sampling.xmd
   │   │   │           ├── ref_i3h_sampling.xmd
   │   │   │           ├── refkk_sampling.xmd
   │   │   │           ├── ref_sampling.xmd
   │   │   │           └── test_sampling.xmd
   │   │   └── tests
   │   │       ├── all_tests.py
   │   │       ├── __init__.py
   │   │       ├── test_binding.py
   │   │       ├── test_programs.py
   │   │       └── test.py

scipion-em-xmipp
--------------------------
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
--------------------------
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
--------------------------
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