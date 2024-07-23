The quick start instructions in the [README](/symless/synergy-core/blob/master/README.md) are simplified and should work in the ideal development environment. However, some developers will likely need to make changes to their environment to build Synergy Core. This guide aims to help with common development environment issues.

## IDE

We suggest using [VS Code](https://code.visualstudio.com/) with our recommended workspace extensions (`.vscode/extensions.json`), especially the [CMake Tools](https://marketplace.visualstudio.com/items?itemName=ms-vscode.cmake-tools) extension (`ms-vscode.cmake-tools`).

## Common problems

- [Dependencies](#dependencies)
- [Configure step](#configure-step)

### Dependencies

Problems running the dependencies script (`python scripts/install_deps.py`)

#### There is no `python3` command

You'll need to install Python if you don't have it installed.

Examples:
- Windows: `winget install Python.Python.3.12`
- macOS: `brew install python`

If you do have it installed, then you may need to use `python3` (instead of `python`). 

Tip: If you need the `python` command to run Python 3, you can use `python-is-python3` on Linux or create a symlink/alias.

#### On Windows: Stuck at `Starting package install`

The Visual Studio installer takes a while. If this takes longer than 5-10 minutes, the Visual Studio installer may be stuck. Kill the command, completely remove Visual Studio, reboot your computer, and try again.

#### On Windows: Visual Studio is installed but the VC++ tools are not

If the Visual Studio Build Tools are already installed then it might not be possible for the script to modify the existing install. You'll need to manually modify the Visual Studio installation and add the C++ workload. Failing that, completely remove Visual Studio and re-run the dependencies script.

#### On Linux: Error related to `pip` or `venv`

On some Linux distros, `pip` and `venv` are not included with Python by default. The dependencies script will try to resolve this, but if this fails you'll need to install these to use the dependencies script. 

If you're still having problems running the dependencies script, you can get the packages command from `config.yml` file and run it manually.

### Configure step

Problems running `cmake` in configure mode.

#### Error: `cmake : The term 'cmake' is not recognized`

The dependencies script should set the `PATH` environment variable on Windows and macOS, but you may need to do this manually if you're still having problems. 

On Windows, you will probably need to run `refreshenv` or restart your IDE to use the new environment variable values.

#### The same `cmake` error persists even after trying solutions

CMake caches configuration but doesn't invalidate the cache when the environment changes. Delete the `build` directory and re-run the configure step to create a fresh configuration.

For example, a common CMake error solved by removing the `build` dir is: `The C compiler [...] is not able to compile a simple test program`

#### CMake cannot find Qt: `CMake Warning at src/gui/CMakeLists.txt`

On Windows and macOS, the dependencies script should set the `CMAKE_PREFIX_PATH` environment variables with the Qt path, for example:
- Windows: `C:\Qt\5.15.2\msvc2019_64`
- macOS: `$(brew --prefix qt@5)`

This is not normally required on Linux.

On Windows, you will probably need to run `refreshenv` or restart your IDE to use the new environment variable values.

After environment variables change, you may need to delete the `build` directory and re-run the configure step to create a fresh configuration.

#### Windows error: `The CXX compiler identification is unknown`

This error may occur for a few reasons assuming the Visual Studio C++ tools are installed correctly. 

If the CMake configure command was run before Visual Studio was properly installed, the cached CMake configuration may be incorrect. Delete the `build` directory and re-run the configure step to create a fresh configuration.

If you're using VS Code, the easiest way to fix this is to use the recommended extension, [CMake Tools](https://marketplace.visualstudio.com/items?itemName=ms-vscode.cmake-tools) which automatically sets up the Visual Studio developer tools environment for you.

When running the CMake configure command from a regular terminal, most likely, you're not running from the Visual Studio developer tools environment (i.e. `vcvarsall.bat` was not run). Microsoft provides a start menu entry to a special terminal which they call 'Developer PowerShell for VS 2022'.

Alternatively, if you're using VS Code but don't want to use the CMake Tools extension, you could add the 'Developer PowerShell for VS 2022' terminal to `settings.json`:
```
  "terminal.integrated.profiles.windows": {
    "Developer PowerShell for VS 2022": {
      "source": "PowerShell",
      "icon": "terminal-powershell",
      "args": [
        "-NoExit",
        "-Command",
        "$vsWhere = \"${Env:ProgramFiles(x86)}\\Microsoft Visual Studio\\Installer\\vswhere.exe\"; $vsInstallationPath = & $vsWhere -products * -latest -property installationPath; & \"${vsInstallationPath}\\Common7\\Tools\\Launch-VsDevShell.ps1\" -Arch amd64 -SkipAutomaticLocation"
      ]
    }
  }
```

#### Linix error: `gcovr not found! Aborting`

When building with `-DENABLE_COVERAGE=ON`, gcovr is required. This is not satisfied by the dependencies script, since it's not a normal dependency. We could install this with the OS package manager (e.g. `apt`) but usually, it's an older version that gets installed. To install the latest version, you could use pipx:
```
sudo apt install pipx
pipx install gcovr
```