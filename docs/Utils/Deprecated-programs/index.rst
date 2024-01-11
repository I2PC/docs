Programs deprecated
=====================

Deprecating programs
-----------------------

We have a "legacy" folder with programs and code that is outdated. Some of the reasons we did this are uninteresting code, programs that do not have a protocol and are not used, and programs that are not used and are difficult to maintain. You can `visit the issue <https://github.com/I2PC/xmipp/issues/681>`_ with more information and the list of deprecated programs and protocols can be found `here <https://github.com/I2PC/xmipp/wiki/List-of-deprecated-programs-and-protocols>`_.

We managed to speed up the installation time by 25%, and we were also able to reduce the lines of code to maintain and the number of code smells that were reported by `SonarCloud <https://sonarcloud.io/projects>`_.

However, it is possible to recover a program if anyone needs it. If you are an external user, please contact us (opening an issue is a good way, `see here <https://github.com/I2PC/xmipp/issues/new>`_).  If you are part of the Xmipp team: Each deprecated program has an associated `commit <https://github.com/I2PC/xmipp/pull/685>`_.  Visit it and review all the changes the program needs to be recovered. Here are some clues:

- Go to the legacy folder and
- Search in the applications/programs folder for the folder of your program.
- Search in the libraries folder for the script of your program.
- Most of the deprecated programs had a test; go to the commit and search in tests_programs_xmipp.py for the test of your program.
- The last step is to remove the program that has been recovered from this list (see listDeprecatedFiles() in utils.py).

List of deprecated programs
---------------------------

- `angular_distribution_show <https://github.com/I2PC/xmipp/pull/685/commits/a3e0e05a1cf38abe4a738f08e63d975044fcb647>`_
- `apropos <https://github.com/I2PC/xmipp/pull/685/commits/9abe9264682c38d19d3cf2d56cda5d78bca6e5d1>`_
- `classify_significant <https://github.com/I2PC/xmipp/pull/716/commits/1d8968268aa353a89d37bec1f5c3e23cf2bb1fa2>`_
- `ctf_correct_idr <https://github.com/I2PC/xmipp/pull/685/commits/0d5a5e64efb7fda5c238b896dcdf65f0f89ef700>`_
- `ctf_create_ctfdat <https://github.com/I2PC/xmipp/pull/685/commits/6ee3dbfabe4f4dfea6eb5607d132adafb9dbc868>`_
- `ctf_show <https://github.com/I2PC/xmipp/pull/685/commits/634a48ec7c4d9470b73c59ceedba9ee2de7c69fe>`_
- `DeepAlign <https://github.com/I2PC/xmipp/pull/721/commits/3864711d5e8aa8fb04e6285695c8d5a3f132927b>`_
- `idr_xray_tomo <https://github.com/I2PC/xmipp/pull/685/commits/ccdd7589347ba95de488d91a9db7df1806e8f241>`_
- `image_common_lines <https://github.com/I2PC/xmipp/pull/685/commits/b243f01522377e6364bea13df5295e886e15ec23>`_
- `metadata_convert_to_spider <https://github.com/I2PC/xmipp/pull/685/commits/235c9e934673bda81285cf3afc0fa260d6ed4cd2>`_
- `metadata_selfile_create <https://github.com/I2PC/xmipp/pull/685/commits/d959b36909aa39a98f57f8babc5bf9559cdea593>`_
- `mlf_refine_3d, ml_refine_3d, ml_tomo <https://github.com/I2PC/xmipp/pull/685/commits/b90374d715d995fb5b3068dc921f5b9db9ae379e>`_
- `mrc_create_metadata <https://github.com/I2PC/xmipp/pull/685/commits/0feae957729cacbe0e5c66cf786d32b1c712501b>`_
- `pdb_construct_dictionary, pdb_restore_with_dictionary <https://github.com/I2PC/xmipp/pull/685/commits/7ec25d023113771065bf189f5277ab5e730925e0>`_
- `reconstruct_admn <https://github.com/I2PC/xmipp/pull/685/commits/f228b698e48197a06529311749789e9dd03ec47b>`_
- `reconstruct_art_pseudo <https://github.com/I2PC/xmipp/pull/685/commits/8b1b338634b4301e6d51e42f8e1562bcb90a937f>`_
- `resolution_ibw <https://github.com/I2PC/xmipp/pull/685/commits/fd177252feb57bccdb7de2691eb0759f0e5b3f17>`_
- `resolution_ssnr <https://github.com/I2PC/xmipp/pull/685/commits/ca81ae3f3a3b62c38a11ff76e794a7ccef6545cc>`_
- `score_micrograph <https://github.com/I2PC/xmipp/pull/685/commits/cd0c5ab540ef996de3f4f01fab3f1a70cd39e82a>`_
- `reconstruct_fourier_starpu <https://github.com/I2PC/xmipp/pull/685/commits/8a762466adb01d50c854267d5ba48c0bb9466f75>`_
- `tomo_align_tilt_series, tomo_align_dual_tilt_series, tomo_align_refinement, tomo_align_refinement, tomo_extract_subvolume, tomo_project_main, tomo_remove_fluctuations <https://github.com/I2PC/xmipp/pull/685/commits/9f1335854eadadad2e111b8f0062e4cdf7e8d6c4>`_
- `tomo_align_tilt

List of deprecated protocols
-----------------------------
* :doc:`protocol_mltomo`
* :doc:`protocol_movie_average`
* :doc:`protocol_subtract_projection`
* :doc:`protocol_deep_align <https://github.com/I2PC/scipion-em-xmipp/pull/614/commits/497f1f3596a78a35d58c8b9baebc07e78f311e48>`
* :doc:`protocol_reconstruct_heterogeneous <https://github.com/I2PC/scipion-em-xmipp/pull/614/commits/f5844c0207d9f74a30f0e0afbbf0868207460836>`
* :doc:`protocol_metaprotocol_create_output <https://github.com/I2PC/scipion-em-xmipp/pull/614/commits/f5844c0207d9f74a30f0e0afbbf0868207460836>`
* :doc:`protocol_metaprotocol_discrete_heterogeneity_scheduler <https://github.com/I2PC/scipion-em-xmipp/pull/614/commits/f5844c0207d9f74a30f0e0afbbf0868207460836>`
* :doc:`apply_deformation_zernike3d <https://github.com/I2PC/scipion-em-xmipp/commit/278996293f685995370ec80be5046c05677bf6ca>`
* :doc:`classify_kmeans2d <https://github.com/I2PC/scipion-em-xmipp/commit/6378a4ef7c8457b86dc14223ef39eab3d503b4fc>`
* :doc:`kmeans_clustering <https://github.com/I2PC/scipion-em-xmipp/commit/3f9333f5b2c056b2abea8ad751b7f8e216bc113a>`
* :doc:`rotational_spectra <https://github.com/I2PC/scipion-em-xmipp/commit/d032963d8b003e0b3c4c5df6d4bd306e4b3dea6c>`
* :doc:`particle_boxSize <https://github.com/I2PC/scipion-em-xmipp/pull/636/commits/ad2fa0e670282e86aafab13c5b11a79d4bdc11e0>`
* :doc:`protocol_split_volume_hierarchical_cluster <https://github.com/I2PC/scipion-em-xmipp/pull/700/commits/9c4ac348585841aaaf3c44c0cef7982a3f10a8fc>`
* :doc:`deep_denoissing <https://github.com/I2PC/scipion-em-xmipp/commit/547a5fe1b49d58a32ea61091b7615c299d2ed377>`
* :doc:`metaprotocol_create_subset <https://github.com/I2PC/scipion-em-xmipp/commit/bca78f9c8ba48ca203d7b83c56b885cc55c9eba2>`
* :doc:`metaprotocol_golden_highres <https://github.com/I2PC/scipion-em-xmipp/commit/4bc23c0a47a0267da6046a1ee7179ec470aaa7f3>`
* :doc:`solid_angle <https://github.com/I2PC/scipion-em-xmipp/commit/086710d671b0bcb388c4b99d662991e761952a44>`
* :doc:`split_volume <https://github.com/I2PC/scipion-em-xmipp/commit/b297c596441df37a626ec97c4d7373d858364cb6>`
