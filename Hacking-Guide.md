## Comitting & PRs

### 1. Prefix your commits with a commit type

Use these prefixes on commits when applicable, as they will be used to generate change logs on release.

- `fix:` **_must_** be used if the commit _fixes_ a known issue or if _fixes_ a bug.
- `feat:` **_must_** be used for the commit that introduces a new feature.
- `refactor:` **_must_** be used when existing code is reworked without changing functionality.
- `build:`: **_must_** be used for changes in project (CMake) or build files.
- `ci:` **_must_** be used for commits that modify CI.
- `chore:` **_may_** be used for most anything else.

#### Example of a good commit message
```
fix: Crash on startup 

   fixes #4444, #4323
   Additional commit info can be helpful 
```

### 2. PRs are not squashed, so make each commit sane

- Use `git commit --amend` to fix a previous commit rather than a follow-up commit.
  See: [[PR Review]]
- Each commit must build; no broken commits.


### 3. Update FileLicense info

To remain reuse compliant its important contributors add proper license info when creating new files or editing existing ones. 

You **_must_** include copyright info for **_all_** source files 
You **_may_** add your name to the list of copyright holders if you have made non trivial changes to the file.

The most basic form for code files is 
```
/*
 * Deskflow -- mouse and keyboard sharing utility
 * SPDX-FileCopyrightText: (C) YEAR Deskflow Developers
 * SPDX-License-Identifier: GPL-2.0-only WITH LicenseRef-OpenSSL-Exception
 */
```

Files that don't take comments well (ui, parsed files, icons, etc) **_must_** be added to the REUSE.toml file in the root of the project.

Our "General" licenses for our files are:
 - CMake and build / packaging related scripts `MIT`. As these files need to be accessible w/o restriction.
 - Source files `GPL-2.0-only WITH LicenseRef-OpenSSL-Exception`
 - Our icons are `GPL-2.0-only` (they don't need to link openssl)

See https://github.com/deskflow/deskflow/wiki/Code-Style#copyright for more details on the formatting

### 4. Update Documentation

Since documentation can become stale quickly we must do our best to keep it updated.

 - You **_must_** update the documentation within the same Pull Request where you invalidate the document's contents.
 - This **_shall_** include Creating or updating [Doxygen comments](https://www.doxygen.nl/manual/docblocks.html) for methods.
 - This **_should_** include also updating any relevant wiki pages.

### 5. No rage caps

Rage caps erode SNR (signal-to-noise). Don't shout in your comments or log messages. This rule applies to:
- Program code
- Build config
- Documentation

What is important to one developer is usually not as important to another. Prioritizing your message over everyone else's is not collaborative. If you want to find something, use a text search tool. Be respectful of other developers and do not cause unnecessary distractions.

Example:
```
# This is a polite and respectful comment.
# THIS IS A SHOUTY AND DISTRACTING COMMENT

message(STATUS "This is a polite and respectful log line.")
message(STATUS "THIS IS AN SHOUTY AND DISTRACTING LOG LINE")
```