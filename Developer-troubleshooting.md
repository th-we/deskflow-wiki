# Common problems

- [Dependencies](#dependencies)
- [Configure step](#configure-step)

## Dependencies

Problems running the dependencies script (`python scripts/install_deps.py`)

### There is no `python` or `pip` command

If you don't have Python installed, you'll need to install it.

If you do have it installed, then you may need to use `python3` or `pip3` respectively.

### Unable to install `pyyaml` on macOS

Try using `brew install pyyaml` instead of using `pip`.

### On Windows: Stuck at `Starting package install`

The Visual Studio installer takes a while. If this takes longer than 5-10 mins, the Visual Studio installer may be stuck. Kill the command, completely remove Visual Studio, reboot your computer and try again.

### On Windows: Visual Studio is installed but the VC++ tools are not

If the Visual Studio Build Tools are already installed then it will not be modified. You'll need to manually modify the Visual Studio installation and add the C++ workload. Failing that, completely remove Visual Studio and re-run the dependencies script.

## Configure step

Problems running `cmake` in configure mode.

### Error: `cmake : The term 'cmake' is not recognized`

Depending onyour OS, the CMake directory is not always added to your path during installation. For example on Windows, you may need to edit your `PATH` environment variable to include the CMake directory (e.g. `C:\Program Files\CMake\bin`). After changing your environment variables, you may need to restart your IDE.

### CMake cannot find Qt: `CMake Warning at src/gui/CMakeLists.txt`

You may need to add the `CMAKE_PREFIX_PATH` environment variable with the path to the Qt library dir (e.g. on Windows, `C:\Qt\5.15.2\msvc2019_64`).

### The same error persists even after trying solutions

CMake caches configuration but doesn't invalidate the cache when the environment changes. Delete the `build` directory and re-run the configure step to create a fresh configuration.

### Windows error: `The CXX compiler identification is unknown`

If the configure command was run previously before Visual Studio was properly installed, the cached CMake configuration may be incorrect. Delete the `build` directory and re-run the configure step to create a fresh configuration. Failing that, you may not be running from the Visual Studio developer tools environment, in which case run `vcvarsall.bat`.