> [!IMPORTANT]
> AI-trash PRs will be closed immediately.

## Comitting & PRs

Please [create a new PR](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-a-pull-request) (pull request) if you want to make a change.

### 1. Prefix your commits with a commit type

Use these prefixes on commits when applicable, as they will be used to generate change logs on release.

- `fix:` **_must_** be used if the commit _fixes_ a known issue or if _fixes_ a bug.
- `feat:` **_must_** be used for the commit that introduces a new feature.
- `refactor:` **_must_** be used when existing code is reworked without changing functionality.
- `build:`: **_must_** be used for changes in project (CMake) or build files.
- `ci:` **_must_** be used for commits that modify CI.
- `chore:` **_should_** be used when removed unused code and for most anything else.

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


### 3. Open PRs must be tested and must compile

Before asking a maintainer to review your PR, you must keep the PR in draft mode. Before switching to open, you must:
- For new features, the feature must be tested and working
- For bug fixes, you should be confident the bug fix works
- Code must compile on Linux, macOS, and Windows

Once all of the above conditions are met, then set your PR to open and request a review from one maintainer. If you do not have access to an OS (e.g., macOS), please let us know if it might not compile successfully on that OS before we approve and run the workflows.

### 4. Update File License info

To remain reuse compliant its important contributors add proper license info when creating new files or editing existing ones. 

 - All Files **_shall_** include copyright info. (In file or in REUSE.toml)
 - Copyright **_must_** be in order from newest to oldest
 - You **_must_** preform action one of the actions below when you have made non trivial changes to the file. Sub year and info 
    - Add `(C) YEAR Your Name <youremail>` to the list of copyright holders.
    - Use `(C) YEAR Deskflow Developers` if you do not want to add your name.
    - Update the Copyright year if already on the list. Years needs to be
       - `20XX` Changes by Author just in that year
       - `200X - 20XX` Changes ever year in this range
       - `20XX, 20XY` Changes in these non constitutive years

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

The following changes are considered to be trivial
 - Moving files from one path to another
 - Removing unused variables
 - Changing spacing or indenting
 - Moving a function to a new file with little to no changes

### 5. Update documentation

Since documentation can become stale quickly we must do our best to keep it updated.

 - You **_must_** update the documentation within the same Pull Request where you invalidate the document's contents.
 - This **_shall_** include Creating or updating [Doxygen comments](https://www.doxygen.nl/manual/docblocks.html) for methods.
 - This **_should_** include also updating any relevant wiki pages.

### 6. No rage caps in comments/logs

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