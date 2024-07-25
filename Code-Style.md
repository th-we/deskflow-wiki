# Formatting
Our code formatting is enforced via CI which runs the `scripts/lint_cmake.py` and `script/lint_clang.py` scripts to ensure that all files match our code style. If your IDE doesn't support formatting, you can use `--format` on either of those scripts to format your code.

- CLang (C/C++/Objective-C): `.clang-format` - LLVM with a few minor tweaks.
- CMake: `cmake-format.yaml` - Standard with a few minor tweaks.
- Python: Use [black](https://github.com/psf/black)

# Naming

- Member variables should be prefixed with `m_helloWorld`
- Pointers should begin with a lower case `p`, e.g. `m_pHelloWorld`
- Getters _should not_ have `get` prefixed, e.g. `helloWorld()`
- Setters should have `set` prefixed, e.g. `setHelloWorld(...)`

## Qt naming
- Qt slots should always begin with `on_`, e.g. `on_foo_bar`
- Qt slots should include both the signal origin and signal name, e.g. on_signalOrigin_somethingHappened
- Qt signals should indicate that something happened, e.g. `somethingHappened`

# Organization

- Getters should be grouped together
- Setters should be grouped together
- Getters and setters should not be paired
