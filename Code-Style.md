Our code style is enforced via CI. It runs the `scripts/lint_cmake.py` and `script/lint_clang.py` scripts to ensure that all files match our code style.

- CLang (C/C++/Objective-C): `.clang-format`
- CMake: `cmake-format.yaml`
- Python: Use [black](https://github.com/psf/black)