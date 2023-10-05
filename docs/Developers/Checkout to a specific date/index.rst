Since Xmipp consists of several repositories, it might be rather complicated to return to a specific version based on the date. A typical example would be the situation in which you encounter a new bug, which has not been present here some time ago, or you have a long-lived branch in Xmipp (without a matching branch in XmippCore), but XmippCore has been changed so it's no longer compatible with your branch.

You can use Git to get the latest commit before some date on a specific branch like this:

.. code-block:: shell

   git checkout `git rev-list -n 1 --first-parent --before="2020-09-27 08:57:42" devel`

If you repeat this process for all repositories that you are interested in, you should get the exact same state as back then.

For additional details, see `this Stack Overflow answer <https://stackoverflow.com/a/6990682/5484355>`_.
