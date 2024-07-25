# Formatting
Our code formatting is enforced via CI which runs the `scripts/lint_cmake.py` and `script/lint_clang.py` scripts to ensure that all files match our code style. If your IDE doesn't support formatting, you can use `--format` on either of those scripts to format your code.

- CLang (C/C++/Objective-C): `.clang-format` - LLVM with a few minor tweaks.
- CMake: `cmake-format.yaml` - Standard with a few minor tweaks.
- Python: Use [black](https://github.com/psf/black)

# Naming

1. Member variables should be prefixed with `m_helloWorld`
1. Pointers should begin with a lower case `p`, e.g. `m_pHelloWorld`
1. Getters _should not_ have `get` prefixed, e.g. `helloWorld()`
1. Setters should have `set` prefixed, e.g. `setHelloWorld(...)`

## Qt naming

1. Qt signals should indicate that something happened, e.g. `somethingHappened`
1. Qt slots should not follow the autoconnection convention (`on_foo_bar`) to demonstrate use of manual slots
1. Qt slots should always begin with `on`, e.g. `onFooBar`
1. Qt slots should include both the signal origin and signal name, e.g. `onOriginSomethingHappened`

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
    - For Qt, the `_ui.h` file
    - Project header files
    - 3rd party lib and system headers
1. Getters should be grouped together
1. Setters should be grouped together
1. Getters and setters should not be paired
