# Formatting
Our code formatting is enforced via CI which runs the `script/lint_clang.py` scripts to ensure that all files match our code style. If your IDE doesn't support formatting, you can use `--format` on either of those scripts to format your code.

> [!TIP]
> See our guide: [[Clang‐Format Tips & Tricks]]

- CLang (C/C++/Objective-C): `.clang-format` - LLVM with a few minor tweaks (80 column width).
- Python: Use [black](https://github.com/psf/black)
- JSON/YAML: Undefined (TBD)

# Copyright

Deskflow is reuse compliant and request reuse lint to pass in order to build
New files Must include license info. Either in a comment at the top of the file or in the REUSE.toml file

Examples:
```
/*
 * Deskflow -- mouse and keyboard sharing utility
 * SPDX-FileCopyrightText: (C) xxxx Deskflow Developers
 * SPDX-License-Identifier: GPL-2.0-only WITH LicenseRef-OpenSSL-Exception
 */
```

```
/*
 * Deskflow -- mouse and keyboard sharing utility
 * SPDX-FileCopyrightText: (C) xxxx - xxxx MY name <myemail>
 * SPDX-License-Identifier: GPL-2.0-only WITH LicenseRef-OpenSSL-Exception
 */
```

```
/*
 * Deskflow -- mouse and keyboard sharing utility
 * SPDX-FileCopyrightText: (C) xxxx - xxxx Deskflow Developers
 * SPDX-License-Identifier: GPL-2.0-only WITH LicenseRef-OpenSSL-Exception
 */
```
more info: https://spdx.dev/learn/handling-license-info/

# Naming

1. Function names should be `camelCase` (for both class member functions and free functions)
1. Namespaces should be all lower case and begin with `synergy`, e.g. `synergy::gui`
1. Member variables should be prefixed with `m_helloWorld`
1. Static variables should be prefixed with `s_`, e.g. `s_helloWorld`
1. Pointers should begin with a lower case `p`, e.g. `m_pHelloWorld`
1. Getters _should not_ have `get` prefixed, e.g. `helloWorld()`
1. Setters should have `set` prefixed, e.g. `setHelloWorld(...)`
1. Enum values and constants should be pascal case, e.g. `HelloWorld` (formerly enums began with `k`)
1. Class filenames should be pascal case, e.g. `HelloWorld.cpp`
1. Files with many classes or functions should be snake case, e.g. `hello_world.cpp`
1. Unit test names should follow the function-input-output pattern, e.g. `helloWorld_fooIn_barOut`
1. The word "deps" should be used to mean "dependencies"

## Qt naming
1. Qt Controls SHALL NOT use  a `p` to indicate they are a pointer.
1. Qt Controls SHALL be named `<type><Description>` (`lblShortName`) 
                                                    OR `<type>_<lenghtyDescription>`  (`lbl_longerNamesMayUseThisStyle`)
1. Qt signals should indicate that something happened, e.g. `nameChanged`

### UI Form Specific Rules
1. Members of UI forms SHALL NOT use the `m_` prefix (i.e lblError NOT m_lblError) 
1. Don't use the autoconnection conventions (`on_foo_bar`) or `onFooBar`.
1. Ui Forms should always be in the namespace `Ui`
    1. Always use `ui{std::make_unique<Ui::Type>()}` make the ui instance
    1. The Ui Form SHALL be a private member of the class using
    1. The variable name SHALL be `ui` 
1. Ui Forms should never have connections internally 
1. When editing ui files take extra care to not accidentally change item sizes
1.When editing ui files take extra care to not accidentally change the current item on container based widgets.

### Qt Type Prefix scheme
  - `label`  QLabels that are  a static label
  - `lbl`      QLabels you will be changing programmatically
  - `rb`      QRadioButton
  - `cb`      QCheckBoxe
  - `combo`  QComboBox
  -  `btn`    Buttons (Tool or Push)
  -  `action`  QAction
  - Others name without the Q 

# Organization

1. `.cpp` files should be ordered:
    - Copyright
    - Headers
    - `using`
    - Constants
    - Free functions
    - Class members
1. Headers should be ordered in separate groups of:
    - Header file for the `.cpp` file
    - For Qt, the `.ui` file
    - Project header files
    - 3rd party lib and system headers
1. Getters should be grouped together
1. Setters should be grouped together
1. Getters and setters should not be paired

# Unit tests

1. Use ctor dependency injection (e.g. `std::function` or a `Deps` struct)
1. A unit test body should follow the AAA (arrange-act-assert) pattern, e.g.:
    ```
    auto foo = "hello";
    auto bar = "world";

    auto baz = combine(foo, bar);

    EXPECT_EQ(baz, "hello world");
    ```
1. A unit test should test only one scenario and expectation
    - Split test scenarios into separate test functions

# Exceptions

1. Do not allow exceptions to propagate to Qt (instead, use `qFatal()`)
    - Remember: `qFatal` can be ignored on Windows, but not on macOS/Linux
1. Do use exceptions for exceptional situations (things that should not happen)
1. Do not use exceptions for validation (e.g. if a user input value is unexpected)

# Logging

1. Use `DEBUG` for debug messages that do not occur frequently.
1. Use `DEBUG1` for debug for high-frequency messages.
1. Use `DEBUG2` for debug messages that are very high frequency (e.g. events system).
1. Omit function names from log strings because (it's impractical to keep them consistent long-term).
1. Use lower case for our log lines, instead of sentence case.
1. End log messages with numeric data if possible.
1. Wrap inserted strings with single quotes.
1. Do not end log messages with a period character.
1. A comma can be used to make the log line read easier.