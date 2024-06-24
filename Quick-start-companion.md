The quick start instructions on the README are an oversimplification of the steps required to build Synergy Core. You'll almost always have to do at least a few of the steps in this companion. Because developer environments vary, it's difficult to know exactly what every developer will need to do.

- [Dependencies](#dependencies)
- [Configure step](#configure-step)

## Dependencies

Problems running the dependencies script (`python scripts/install_deps.py`)

### There is no `python` or `pip` command

You'll need to install Python if you don't have it installed.

If you do have it installed, then you may need to use `python3` or `pip3` respectively.

### On macOS: The dependencies script loops with `brew install pyyaml`

This can happen when brew is installing `pyyaml` to a different version than you're using, e.g. if you have `python@3.11` and `python@3.12` installed. Try removing the older version, e.g.: `brew remove python@3.11`

### On Windows: Stuck at `Starting package install`

The Visual Studio installer takes a while. If this takes longer than 5-10 mins, the Visual Studio installer may be stuck. Kill the command, completely remove Visual Studio, reboot your computer, and try again.

### On Windows: Visual Studio is installed but the VC++ tools are not

If the Visual Studio Build Tools are already installed then it might not be possible for the script to modify the existing install. You'll need to manually modify the Visual Studio installation and add the C++ workload. Failing that, completely remove Visual Studio and re-run the dependencies script.

### On Linux: Error related to `pip` or `venv`

On some Linux distros, `pip` and `venv` are not included with Python by default. The dependencies will try to resolve this, but if this fails you'll need to install these to use the dependencies script. Alternatively, get the packages command from `config.yml` file and run it manually.

## Configure step

Problems running `cmake` in configure mode.

### Error: `cmake : The term 'cmake' is not recognized`

The dependencies script should set the `PATH` environment variable on Windows and macOS, but you may need to do this manually if you're still having problems. 

On Windows, you will probably need to restart your IDE to use the new environment variable values.

### The same `cmake` error persists even after trying solutions

CMake caches configuration but doesn't invalidate the cache when the environment changes. Delete the `build` directory and re-run the configure step to create a fresh configuration.

For example, a common CMake error solved by removing the `build` dir is: `The C compiler [...] is not able to compile a simple test program`

### CMake cannot find Qt: `CMake Warning at src/gui/CMakeLists.txt`

On Windows and macOS, the dependencies script should set the `CMAKE_PREFIX_PATH` environment variables with the Qt path, for example:
- Windows: `C:\Qt\5.15.2\msvc2019_64`
- macOS: `$(brew --prefix qt@5)`

This is not normally required on Linux.

On Windows, you will probably need to restart your IDE to use the new environment variable values.

After environment variables change, you may need to delete the `build` directory and re-run the configure step to create a fresh configuration.

### Windows error: `The CXX compiler identification is unknown`

Assuming the Visual Studio C++ tools are installed correctly, this error may occur for a few reasons. Most likely is that you're not running from the Visual Studio developer tools environment (i.e. `vcvarsall.bat` was not run). If you're using VS Code, a recommended extension is [CMake Tools](https://marketplace.visualstudio.com/items?itemName=ms-vscode.cmake-tools) by Microsoft which automatically sets up the Visual Studio developer tools environment for you. Failing that, if the configure command was run previously before Visual Studio was properly installed, the cached CMake configuration may be incorrect. Delete the `build` directory and re-run the configure step to create a fresh configuration.