# Common problems

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

If the Visual Studio Build Tools are already installed then it will not be modified. You'll need to manually modify the Visual Studio installation and add the C++ workload.

## Configure step

Problems running `cmake` in configure mode.

### The same error persists even after trying solutions

CMake caches configuration but doesn't invalidate the cache when the environment changes. Delete the `build` directory and re-run the configure step to create a fresh configuration.

### Windows error: `The CXX compiler identification is unknown`

If the dependencies script was successful and Visual Studio was installed, try restarting your IDE to use new environment variables.