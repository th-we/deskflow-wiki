# Common problems

## Dependencies

Problems running the dependencies script (`python scripts/install_deps.py`)

### There is no `python` or `pip` command

If you don't have Python installed, you'll need to install it.

If you do have it installed, then you may need to use `python3` or `pip3` respectively.

### Unable to install `pyyaml` on macOS

Try using `brew install pyyaml` instead of using `pip`.

### Stuck at 'Starting package install' on Windows

The Visual Studio installer may be stuck. Reboot your computer and try again.

## Configure step

### Error: `The CXX compiler identification is unknown`

If the dependencies script was successful and Visual Studio was installed, try restarting your IDE.