How to release
---------------

Let's assume that we want to make a new Xmipp version from the 'devel' branch with a version name **X.YY.ZZ** where **X=3** (to keep the main version number to be able to sort the version as usual. Also to keep the name *xmipp3*), **YY=Year** of the release, **ZZ=Month** of release. Also, we name the version following Greek gods/goddess ([Apollo, Boreas...](https://www.gods-and-monsters.com/list-of-greek-gods-goddesses.html)), see the [TAGging section below](https://github.com/I2PC/scipion-em-xmipp/wiki/How-to-release-a-new-Xmipp-version#making-a-git-tag-and-promoting-the-code-to-master).

Create the release notes
^^^^^^^^^^^^^^^^^^^^
Add all the information about the release [here](https://github.com/I2PC/xmipp/blob/devel/CHANGELOG.md)

Schedule the releasing
^^^^^^^^^^^^^^^^^^^^
Prepare everything, but post the release at the beginning of your workday.

Make release branches
^^^^^^^^^^^^^^^^^^^^
Create a branch where freeze the code and fix some minor bug before to upgrade the version for all Xmipp repositories. The usual name for that branch is `release-X.YY.ZZ`.
 > Branches with 'release' word are protected, to unprotect it create a PR from an other branch and get the aprove from other developer

 > If some Xmipp repository has not to be uploaded (scipion-em-xmipp, xmipp, xmippViz, xmippCore), please make this `release-X.YY.ZZ` branch from the `master` one in order to make sure that the update from other repos is compatible. In this way, we will also be able to include some bug fixing during the release procedure.

Set the version to the code
^^^^^^^^^^^^^^^^^^^^
There are three types of version tags. One is the plugin version (in sync with pypi), other is the software version (related with the name of the tgz hosted in the Scipion web) and, finally, the third is the linking from the plugin to the software.

 * **Software version**: It must be set at `$XMIPP_BUNDLE/xmipp` --> [XMIPP_VERSION=X.YY.ZZ](https://github.com/I2PC/xmipp/blob/f152af31ff8ab6400b77c7fb513aa3319901b3a3/xmipp#L41). This version is used when the software is compiled and the `xmipp_version` is done, to create the end-of-installation token (`$XMIPP_HOME/vX.YY.ZZ`) and when the bundle is created using `./xmipp tar ...` with an automatic version.



 * **Linking version**:It must be set at `$XMIPP_BUNDLE/src/scipion-em-xmipp/xmipp3/__init__.py` --> [_currentVersion = 'X.YY.ZZ'](https://github.com/I2PC/scipion-em-xmipp/blob/c12a1115f268ec77edd34bf5c84e6ffad256a818/xmipp3/__init__.py#L41). This is used to find the binaries to install. This is also in sync with [the pypi versions](https://pypi.org/project/scipion-em-xmipp/#history) since this version is used when the pypi module is created and uploaded.

* **XMIPP_VERNAME** Replace devel for the name of the release [here](https://github.com/I2PC/xmipp/blob/7e5aea662c93bbfbb6bcd3729850b95914a722f4/xmipp#L38)

* Replace the logo for the protocols: replace [scipion-em-xmipp](https://github.com/I2PC/scipion-em-xmipp)/[xmipp3](https://github.com/I2PC/scipion-em-xmipp/tree/devel/xmipp3)/xmipp_logo.png (in devel is the devel version of the image) for xmipp_logo_original.png
* Review the status of each protocol (_devStatus), maybe some change from New to Production, or production to updated...

Creating the Xmipp software bundle
^^^^^^^^^^^^^^^^^^^^
When the `release-X.YY.ZZ` branch is ready and all bugs seem fixed, **we must do a Pull Request** for each Xmipp repository from `release-X.YY.ZZ` to `master`. Once approved but **not merged yet**, we can start with the release procedure.

 > If the Pull Request contain conflicts, merge Master into your release branch and resolve it.
 > If the release only contain changes in the plugin (not in the rest of the Xmipp repositories), you can go to the next section below.

Make sure that all is self-contained (keep in mind the rest of the Xmipp's repositories) and compatible with the current Scipion version. To do that, go for a fresh compilation as follow

(*We assume that the current version of Scipion is installed in `$scipionMASTER`.*)
