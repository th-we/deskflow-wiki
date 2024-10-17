## Comitting & PRs

### 1. Prefix your commits with a commit type
Use on the these prefixes on commits when applicable, as they will be used to generate change logs on release.

- `fix:` MUST be used if the commit "fixes" a known issue or if Fixes a Bug.
- `feat:` MUST be used for the commit that introduces a new feature
- `refactor:` MUST be used when existing code is reworked
- `build:`: MUST be used for changes in project (CMake) or build files.
- `ci:` MUST be used for commits that modify ci 
- `chore:` MAYBE used for most anything else.

#### Example of a good commit message
```
fix: #3393 Crash on startup 

  Additional commit info can be helpful 
```
where #3393 is the Issue Number of the reported issue.


### 2. PRs are not squashed, so make each commit sane

- Use `git commit --amend` to fix a previous commit rather than a follow-up commit.
  See: [[PR Review]]
- Each commit must build; no broken commits.

### 3. Update Documentation

Since documentation can become stale quickly its important we do our best to keep it updated.

 - You **must** update the documentation within the same Pull Request where you invalidate the document's contents.
 - This **shall** include Creating or updating [Doxygen comments](https://www.doxygen.nl/manual/docblocks.html) for methods.
 - This **should** includes also updating any relevant wiki pages.

### 4. No rage caps in comments/logs

Rage caps erode SNR (signal-to-noise). Do not shout in your comments or log messages. This rule applies to both the program code and the build config.

What is important to one developer is usually not as important to another. Prioritizing your message over everyone else's is not a polite thing to do. If you want to find something, use a text search tool. Be respectful of other developers and do not cause unnecessary distractions.

Example:
```
# This is a polite and respectful comment.
# THIS IS AN SHOUTY AND DISTRACTING COMMENT

message(VERBOSE "This is a polite and respectful log line.")
message(STATUS "THIS IS AN SHOUTY AND DISTRACTING LOG LINE")
```