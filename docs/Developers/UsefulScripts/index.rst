Useful Tricks and Scripts
----------------------------

This a list of commonly used scripts for processing of electron
microscopy images. Please feel free to share your own.

Rafa’s tricks
^^^^^^^^^^^^^^^^

-  [[BoxerToXmippMark]] - translate the coordinates of EMAN’s Boxer to
   Xmipp_Mark
-  [[CorrectCoordinates]] - correct the coordinates too near to the
   border of the image
-  [[CreateMaskFromMap]] - using a binarized, thresholded map
-  [[RunKerdenSOM]] - apply kerdensom to a set of 2D images or to a set
   of rotational power spectra
-  [[SubmitMpiJobOnJumilla]] - run parallel jobs using our Alpha queues.
-  [[ConvertXmdfileToRelionPosFile]] - After a classfication in Xmipp3,
   generate Pos file to extract particles in Relion

Sjors’ tricks
^^^^^^^^^^^^^^^^

-  [[FromXmippToVariance3D]] - use Pawel Penzeck’s Spider scripts after
   an Xmipp alignment
-  [[SelectionFileSpidertoXmipp]] - convert Spider selection file (with
   numbers only) to an Xmipp selfile
-  [[XmippPreprocessing]] - Tiff2raw, CTF-estimation, extraction,
   normalization, phase correction etc.
-  [[MovingParticles]] - analyze the behaviour of your particles in a ML
   classification experiment.
-  [[SortImagesBasedOnDocfile]] - Make a sorted selfile from a newxmipp
   style docfile (e.g. sort by CC).
-  [[CtffindToXmippCtfParam]] - convert the .ctf file from CTFFIND to an
   XMIPP CTF-parameter file
-  [[CompareClassAveragesWithReprojections]] - Align reference-free
   class averages with projections of a 3D model and visualize

Roberto’s tricks
^^^^^^^^^^^^^^^^

-  [[OpenDX]] - visualize Xmipp volumes in opendx
-  [[CompareVolumeT]] using python (Note volumeT is the base clase of
   [[VolumeXmipp]])
-  
-  
-  
-  [[CTFParamOldNew]] Convert ctf from old to new (metadata
-  [[ExportPos]]
-  [[CtfFindToXmippThree]]

Coss’ tricks
^^^^^^^^^^^^^^^^

-  [[WebToXmippMark]] - How to convert coordinates of particles picked
   with Web (Spider) into a set of particles picked with Xmipp
-  [[EstimatingNoisePowerForAGivenSNR]] - How to estimate how much noise
   to add to a set of phantom projections to have a given average SNR
-  [[CoSSSmallTricks]] - How to generate an empty image, compute a
   radial average, …
-  [[EstimateTheCTF]] - How to estimate the CTF
-  [[RunMpiProgramsWithoutRepeatingThePassword]] - How to run MPI
   programs without having to repeat the password for each process
   (depends on the UNIX distribution)
-  [[CorrectingMisalignmentOfPDB]] - How to look for a misaligned
   rotational symmetry axis in a PDB and correct it
-  [[HowManyReferenceProjections]] - What is the number of reference
   projections given an angular step
-  [[EquivalentEulerAngles]] - Given an Euler angle, what are the Euler
   angles of its X, Y and XY mirrors and how are they expressed with
   another set of angles
-  [[ConvertImagesToXmipp]] - Given images in EMAN, CCP4, Spider, … How
   to convert them to Xmipp
-  [[RemoveOpenMPIWarnings]] - Remove [[OpenMPI]] warning about openib
   and udapl
-  [[EulerAngles]] - What is the interpretation of Euler angles in Xmipp
-  [[HexDumpF]] - Hexdump of float numbers considering endianness
-  [[ConvertingFrealignXmipp]] - Conversion of Euler angles from
   FRealign to Xmipp
-  [[ConvertingLstXmipp]] - Conversion of Eman lst files to Xmipp
-  [[DefinedMacros]] - How to know the macros defined by a compiler in a
   given system
-  [[ConvertDownsamplePos]] - Convert and downsample posfiles of Xmipp
   3.0 to Xmipp 2.4
-  [[ImportPosFromEmanAndSpider]] - Import coordinates from Eman and
   Spider into Xmipp 3.0
-  [[ApplyGeoInReconstructionMetadata]] - Given a metadata for
   reconstruction, generate the aligned images needed for reconstructing
   without shifts and mirrors
-  [[GenerateTiltPairs]] - Generate untilted and tilted images for a
   given volume



Carmen’s scripts
^^^^^^^^^^^^^^^^

-  If you have performed a projection matching after downsampling the
   micrographs by a certain factor, and now want to proceed with a
   different downsampling factor (eg to use a finer pixel size), you may
   find the next two shell scripts useful:

   -  [[ScalePos]] - to write new .pos files according to the new
      downsampling (so you do not have to pick particles again)
   -  [[ScaleShifts]] - to reuse angles and shifts found in the previous
      projection matching run
