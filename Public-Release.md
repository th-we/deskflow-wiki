## GA Release Process

1. First, follow [[Testing Release]]
1. Ensure that `ChangeLog` file is up to date
1. Ensure version number in `Version.cmake` and `Build.properties` is correct
1. Ensure stage name in `Version.cmake` and `Build.properties` is correct
1. Test snapshot on all operating systems
1. Close the release milestone
1. Tag the version branch
1. Merge version branch into master
1. Upload to the public website and test links
1. Set current version in website settings
1. Test all download links
1. Install the previous version and test update check feature
1. Set next version in `Version.cmake` and `Build.properties` (master branch)