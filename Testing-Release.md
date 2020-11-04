## During Development

1. Ensure version number in `Version.cmake` is correct
1. Ensure stage name in `Version.cmake` is `snapshot`
1. Develop on feature branches based on dev branch (e.g. `v1-dev`)

## Beta & RC Release Process

1. Create a release branch (e.g. `v1.2.3`) based on master branch
1. Update stage name in `Version.cmake` (e.g. `rc1`, `beta1`, etc)
1. Tag version (e.g. `v1.2.3-rc1`) from release branch (e.g. `v1.2.3`)
1. Trigger manual build using Azure Pipelines on the release branch (e.g. `v1.2.3`)
    * Do full QA internally
    * If issues** found from QA:
       * Fix in release branch (e.g. `v1.2.3`)
       * Repeat from step 1 (increment RC stage)
    * If ready for community testing, share RC links:
       * Wait for up to a week for issues to be reported
    * If issues** found from the community:
       * Fix in release branch (e.g. `v1.2.3`)
       * Repeat from step 1 (increment RC stage)
1. Post link to build on relevant:
    * GitHub issues
    * Forum threads
    * Support tickets
1. Go to [[Public Release]]

** An issue that is a direct result of fixes in the release candidate.