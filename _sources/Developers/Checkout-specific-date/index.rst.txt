Checkout to a Specific Version
------------------------------------------

If you need to revert to a specific version of Xmipp or its associated repositories based on a particular date, you can achieve this using Git. This is useful, for example, when you encounter a new bug that was not present in an earlier version or when you have a long-lived branch in Xmipp that needs to be synchronized with a specific historical state.

Here is a step-by-step guide on how to accomplish this:

1. **Identify the Date**: Determine the date of the version you want to revert to. In the following example, we'll use "2020-09-27 08:57:42" as an example date.

2. **Checkout a Specific Commit**: Use the following command to checkout the latest commit on the "devel" branch before the specified date:

   ```bash
   git checkout `git rev-list -n 1 --first-parent --before="2020-09-27 08:57:42" devel`
