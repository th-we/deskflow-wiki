## GA Release Process

1. First, follow [[Testing Release]]
1. Ensure that `ChangeLog` file is up to date
    * Change stage to `stable` in `ChangeLog`
1. Ensure version number in `Version.cmake` is correct
1. Change stage name in `Version.cmake` to `stable`
1. Merge release branch (e.g. `v1.2.3`) into `master`
1. Manually build from `master`
1. Test master build on all operating systems
    * This is a cursory test to ensure build is as expected
    * This not full QA as that was done in [[Testing Release]]
1. Tag version from `master` branch
1. Close the release milestone
1. Upload installers to the public website:
    * Test all download links on the website
1. Set current version in website settings
    * Older versions will now show as out of date in the config app
    * This prompts users to download the new update
1. Test update check feature by installing the previous version