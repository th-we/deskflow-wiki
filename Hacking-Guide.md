## Comitting & PRs

### 1. Prefix your commits with a commit type

Use these prefixes on commits when applicable, as they will be used to generate change logs on release.

- `fix:` **must** be used if the commit _fixes_ a known issue or if _fixes_ a bug.
- `feat:` **must** be used for the commit that introduces a new feature.
- `refactor:` **must** be used when existing code is reworked without changing functionality.
- `build:`: **must** be used for changes in project (CMake) or build files.
- `ci:` **must** be used for commits that modify CI.
- `chore:` **may** be used for most anything else.

#### Example of a good commit message

Issue number (e.g. #3393) is optional:
```
fix: #3393 Crash on startup 

  Additional commit info can be helpful 
```

### 2. PRs are not squashed, so make each commit sane

- Use `git commit --amend` to fix a previous commit rather than a follow-up commit.
  See: [[PR Review]]
- Each commit must build; no broken commits.

### 3. Update Documentation

Since documentation can become stale quickly we must do our best to keep it updated.

 - You **must** update the documentation within the same Pull Request where you invalidate the document's contents.
 - This **shall** include Creating or updating [Doxygen comments](https://www.doxygen.nl/manual/docblocks.html) for methods.
 - This **should** include also updating any relevant wiki pages.

### 4. No rage caps

Rage caps erode SNR (signal-to-noise). Don't shout in your comments or log messages. This rule applies to:
- Program code
- Build config
- Documentation

What is important to one developer is usually not as important to another. Prioritizing your message over everyone else's is not collaborative. If you want to find something, use a text search tool. Be respectful of other developers and do not cause unnecessary distractions.

Example:
```
# This is a polite and respectful comment.
# THIS IS A SHOUTY AND DISTRACTING COMMENT

message(VERBOSE "This is a polite and respectful log line.")
message(STATUS "THIS IS AN SHOUTY AND DISTRACTING LOG LINE")
```