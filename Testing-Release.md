## During Development

1. Ensure version number in `Version.cmake` is correct
1. Ensure stage name in `Version.cmake` is `snapshot`
1. Develop on feature branches based on `v1-dev`

## Beta & RC Release Process

1. Tidy up issue titles (these will be shared publicly with users)
1. Update ChangeLog file (use [github-query](https://github.com/symless/github-query))
1. Test new bug fixes and features
1. Create a release branch based on `v1-dev` (e.g. `v1.2.3`)
1. Update stage name in `Version.cmake` (e.g. `rc1`, `beta1`, etc)
1. Tag version from release branch (e.g. `v1.2.3`)
1. Wait for build and share RC snapshot links with the testing community
1. If issues** found, fix in release branch (e.g. `v1.2.3`) then repeat from step 1
1. Finally, go to [[Public Release]]

** An issue that is a direct result of fixes in the release candidate.