## During Development

1. Ensure version number in `Version.cmake` and `Build.properties` is correct
1. Ensure stage name in `Version.cmake` and `Build.properties` is correct
1. Create release branch (e.g. v1.2)
1. Make code changes (do not commit to master)

## Beta & RC Release Process

1. Tidy up issue titles (these will be shared publicly with users)
1. Update ChangeLog file (use [github-query](https://github.com/symless/github-query))
1. Test new bug fixes and features
1. Share RC snapshot links with the testing community 
1. Test internally for 1 week at the Symless office
1. Fix any new urgent issues and repeat from step 1
1. Go to [[Public Release]]