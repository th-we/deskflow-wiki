Create a new PR with a single commit:
1. Commit message: "Release [version]"
   - Do not use conventional commit style prefix
1. Set version in `CMakeLists.txt`
2. Update `deploy/linux/org.deskflow.deskflow.metainfo.xml`
   - Go to [Releases](https://github.com/deskflow/deskflow/releases) and compare continuous to the last release
   - Manually write an abridged list of bullet points based on commits
   - Target audience for the metainfo file is Linux users (condense Windows/macOS list items)
   - Add a new release to the `releases` section of metainfo file
   - Date format is: YYYY-MM-DD
3. After landing the PR, tag the release
   - Always use annotated tag like the example below
   - The tag must match the major, minor, patch from `CMakeLists.txt`
   - Example:
     - `git tag -a v1.2.3 -m "v1.2.3"`
     - `git push origin v1.2.3`
4. Watch CI to ensure the release builds
   - Once done, check the [latest release](https://github.com/deskflow/deskflow/releases/latest) page
5. Go grab yourself a nice cold brew 🍺 
