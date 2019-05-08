## GA Release Process

1. First, follow [[Testing Release]]
1. Ensure that `ChangeLog` file is up to date
1. Ensure version number in `Version.cmake` is correct
1. Ensure stage name in `Version.cmake` is `stable`
1. Merge release branch (e.g. `1.2.3`) into `master`
1. Manually build from `master`
1. Test master build on all operating systems
1. Close the release milestone
1. Tag version from `master` branch
1. Do a cursory test of all builds in case of silent CI issue 
1. Upload to the public website and test links
1. Set current version in website settings
1. Test all download links
1. Install the previous version and test update check feature
1. Set next version in `Version.cmake` (in `v1-dev` branch)