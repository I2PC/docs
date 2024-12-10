How to release
----------------

Let’s assume that we want to make a new Xmipp version from the ‘devel’
branch with a version name **X.YY.ZZ** where **X=3** (to keep the main
version number to be able to sort the version as usual. Also to keep the
name *xmipp3*), **YY=Year** of the release, **ZZ=Month** of release.
Also, we name the version following Greek gods/goddess (`Apollo,
Boreas… <https://www.gods-and-monsters.com/list-of-greek-gods-goddesses.html>`__),
see the `TAGging section
below <https://github.com/I2PC/scipion-em-xmipp/wiki/How-to-release-a-new-Xmipp-version#making-a-git-tag-and-promoting-the-code-to-master>`__.

**Create the release notes**

Add all the information about the release
`here <https://github.com/I2PC/xmipp/blob/devel/CHANGELOG.md>`__

**Schedule the releasing**

Prepare everything, but post the release at the beginning of your
workday.

Make release branches
^^^^^^^^^^^^^^^^^^^^^

Create a branch where freeze the code and fix some minor bug before to
upgrade the version for all Xmipp repositories. The usual name for that
branch is ``release-X.YY.ZZ``. > Branches with ‘release’ word are
protected, to unprotect it create a PR from an other branch and get the
aprove from other developer

   If some Xmipp repository has not to be uploaded (scipion-em-xmipp,
   xmipp, xmippViz, xmippCore), please make this ``release-X.YY.ZZ``
   branch from the ``master`` one in order to make sure that the update
   from other repos is compatible. In this way, we will also be able to
   include some bug fixing during the release procedure.

**Set the version to the code**

There are three types of version tags. One is the plugin version (in
sync with pypi), other is the software version (related with the name of
the tgz hosted in the Scipion web) and, finally, the third is the
linking from the plugin to the software.

-  **Software version**: It must be set at ``$XMIPP_BUNDLE/xmipp`` –>
   `XMIPP_VERSION=X.YY.ZZ <https://github.com/I2PC/xmipp/blob/f152af31ff8ab6400b77c7fb513aa3319901b3a3/xmipp#L41>`__.
   This version is used when the software is compiled and the
   ``xmipp_version`` is done, to create the end-of-installation token
   (``$XMIPP_HOME/vX.YY.ZZ``) and when the bundle is created using
   ``./xmipp tar ...`` with an automatic version.

-  **Linking version**:It must be set at
   ``$XMIPP_BUNDLE/src/scipion-em-xmipp/xmipp3/__init__.py`` –>
   `\_currentVersion =
   ‘X.YY.ZZ’ <https://github.com/I2PC/scipion-em-xmipp/blob/c12a1115f268ec77edd34bf5c84e6ffad256a818/xmipp3/__init__.py#L41>`__.
   This is used to find the binaries to install. This is also in sync
   with `the pypi
   versions <https://pypi.org/project/scipion-em-xmipp/#history>`__
   since this version is used when the pypi module is created and
   uploaded.

-  **XMIPP_VERNAME** Replace devel for the name of the release
   `here <https://github.com/I2PC/xmipp/blob/7e5aea662c93bbfbb6bcd3729850b95914a722f4/xmipp#L38>`__

-  Replace the type_of_version at <https://github.com/I2PC/scipion-em-xmipp/blob/da42ebc37f85c1c39fcd7f6f2f9d1af1b9424c7a/xmipp3/__init__.py#L40>`__

-  Review the status of each protocol (_devStatus), maybe some change
   from New to Production, or production to updated…

Creating the Xmipp software bundle
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

When the ``release-X.YY.ZZ`` branch is ready and all bugs seem fixed,
**we must do a Pull Request** for each Xmipp repository from
``release-X.YY.ZZ`` to ``master``. Once approved but **not merged yet**,
we can start with the release procedure.

   If the Pull Request contain conflicts, merge Master into your release
   branch and resolve it. If the release only contain changes in the
   plugin (not in the rest of the Xmipp repositories), you can go to the
   next section below.

Make sure that all is self-contained (keep in mind the rest of the
Xmipp’s repositories) and compatible with the current Scipion version.
To do that, go for a fresh compilation as follow

(*We assume that the current version of Scipion is installed in
``$scipionMASTER``.*)

::

   git clone git@github.com:I2PC/xmipp.git xmipp2release
   cd xmipp2release

   $scipionMASTER/scipion3 run ./xmipp all br=release-X.YY.ZZ N=8

   $scipionMASTER/scipion3 uninstallp -p scipion-em-xmipp
   git checkout release-X.YY.ZZ
   $scipionMASTER/scipion3 installp -p ./xmipp2release/src/scipion-em-xmipp --devel

   rm -rf $scipionMASTER/software/em/xmipp
   ln -s ~/xmipp2release/build $scipionMASTER/software/em/xmipp

   $scipionMASTER scipion3 test --grep xmipp 
   $scipionMASTER scipion3 test xmipp3.tests.XXX
   $scipionMASTER scipion3 test xmipp3.tests.XXY

If all goes well (no error should be in the tests, however we assume
some ones… (at least all those at Buildbot
`xmipp_bundle_devel <http://scipion-test.cnb.csic.es:9980/#/builders/50>`__
and
`xmipp_devel <http://scipion-test.cnb.csic.es:9980/#/builders/19>`__)
then, we can make the Xmipp bundle.

First ensures that the new version info is well set at the `Xmipp main
script <https://github.com/I2PC/xmipp/blob/45c18d3397bcf94581b7568ed583729dfa1cab9f/xmipp#L40-L43>`__.
If not, update it, commit the change and push it. **All should be pushed
to github since the bundle is done from the github/branch, instead of
you local version.**

Then, we are able to create the bundle

::

   ./xmipp tar Sources br=release-X.YY.ZZ

A ``xmippSrc-vX.YY.ZZ.tgz`` should be created, where ``YY.ZZ`` is
according to the version info set above.

Test the archive in the Scipion
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

To test the archive, install new Scipion without Xmipp following the
guide
`here <https://scipion-em.github.io/docs/release-3.0.0/docs/scipion-modes/how-to-install.html>`__:

::

   python3 -m scipioninstaller -conda -noXmipp -noAsk scipion2ReleaseXmipp

First thing that needs to be done is to install Xmipp plugin.

::

   ./scipion3 installp -p  path/of/xmipp2release/src/scipion-em-xmipp --devel

Once the plugin is installed, you should see Xmipp sources available for
installation:

::

   $ ./scipion3 installb
   ...
   xmippSrc                 3.YY.ZZ.0[ ]   

Copy (overwrite) the source file ``xmippSrc-vX.YY.ZZ.tgz`` to the
*/software/em* path of the Scipion installation. Now install the
binaries and run some test to verify that everything works. Typical
problem is not matching version number in the *scipion-em-xmipp* plugin.

::

   ./scipion3 installb xmippSrc -j 8

If all seems fine means that bundle ``xmippSrc-vX.YY.ZZ.tgz`` is
compatible to work with the Scipion under ``$scipionMASTER`` and under
the plugin at ``~/xmipp2release/src/scipion-em-xmipp``, thus upload the
``.tgz`` to Nolan to be able to get it remotely. If you don’t know how
to do it, please `ask Scipion’s people <mailto:scipion@cnb.csic.es>`__
(…/downloads/scipion/software/em)

Creating the PyPi module
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

**Testing the installation with source archive from Nolan**


Before creation the Pypi module, **it is worth it to start a testing
stage** to be sure that all is working well. Take into account that,
once the Pypi module is uploaded, the current available version will
automaticly be this.

Make sure that you remove existing Xmipp installation from the Scipion.
The easiest way is to do so via the Plugin manager. Make also sure that
there is no Xmipp archive in the ``software/em`` folder.

Install the Scipion-em-xmipp plugin directly from the Github:

::

   ./scipion3 run pip install git+https://github.com/I2PC/scipion-em-xmipp.git@release-X.YY.MM   # What is after '@' is the release branch.
   ./scipion3 installb xmippSrc -j 8

During the installation, the source file archive should be downloaded
from Nolan.

**Update PyPi module**

Ensures that the `release
information <https://github.com/I2PC/scipion-em-xmipp/blob/fa78fc12536b814275b9a1790e3570f69bf5f0fd/setup.py#L43>`__
is updated and match with those above.

- **New way:**

Merge in scipìon-em-xmipp the PR from release to master, one action will
manage the update to pypi, also will create a tag that we have to remove
(will be managed in the next step) ``git tag -d tagname``
``git push --delete origin tagname`` > If you have no permissions to
push, clone each repository with
``git clone git@github.com:I2PC/scipion-em-xmipp.git``
``git clone git@github.com:I2PC/xmippCore.git``

- **Old way:**

When all is checked, create and upload the Pypi module by (check
`this <https://scipion-em.github.io/docs/docs/developer/creating-a-plugin#create-and-upload-distribution>`__
for more information) Notice that you should have the Scipion virtual
environment active.

::

   cd src/scipion-em-xmipp
   rm -rf dist/*    # To clean the already uploaded modules
   python setup.py sdist
   twine upload dist/* -c "scipion-X.Y"

after **``-c`` flag have to be the lowest Scipion’s compatible version**
(e.g. ``"scipion-3.0"``).

Making a git-TAG and promoting the code to MASTER
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

After concluding the two section above, the new Xmipp version is already
released. Congrats! Publish it in mailing list, Twitter… but also we
want to keep this checkpoint in the git history by a TAG and we must
promote the code to the master branch:

::

   cd ~/xmipp2release
   ./xmipp git tag 'vX.YY.ZZ-GreekGod'   # replace GreekGod for one in the list below
   ./xmipp git push origin 'vX.YY.ZZ-GreekGod'

we name the version following Greek gods (`Apollo,
Boreas… <https://greekgodsandgoddesses.net/gods/>`__) > If you have no
permissions to push, clone each repository with
``git clone git@github.com:I2PC/scipion-em-xmipp.git``
``git clone git@github.com:I2PC/xmippCore.git``

Finally, **merge the rest 3 Pull Requests** to conclude the release!

XmippTomo wants a release
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

XmippTomo wants a release syncronized with the release of Xmipp. To do
that: 1. Create a branch (release_3….) from devel 2. Edit the
`xmipptomo/init.py <https://github.com/I2PC/scipion-em-xmipptomo/pull/118/files#diff-a2df3bcb36a6120ad93308737e1c6ff4200936396e7aedd5b0debc62752c03e2>`__
version number and writhe the same of the Xmipp, the last digit mst be
.0. 3. Be sure you have all the changes in your local path (git pull).
4. Create a PR from your branch to master. When it will be merged, the
action will create the tag and upload the version to pypi.

Final considerations
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Probably, you want all the bug fixings during the release procedure also
in the ``devel`` branch.

To do so, **make a Pull Request from ``release`` to ``devel``**. Also
replace the name of the version for devel
`here <https://github.com/I2PC/xmipp/blob/7e5aea662c93bbfbb6bcd3729850b95914a722f4/xmipp#L38>`__
