The quick start instructions in the [README](/symless/synergy-core/blob/master/README.md) are simplified and should work in the ideal development environment. However, some developers will likely need to make changes to their environment to build Synergy Core. This guide aims to help with common development environment issues.

- [Tools](#tools)
- [Dependencies](#dependencies)
- [Configure step](#configure-step)
- [Development](#development)

## Tools

We suggest using [VS Code](https://code.visualstudio.com/) with our recommended workspace extensions (`.vscode/extensions.json`), especially the [CMake Tools](https://marketplace.visualstudio.com/items?itemName=ms-vscode.cmake-tools) extension (`ms-vscode.cmake-tools`).

For developing the GUI, we recommend using Qt Creator. This can be installed in two ways:

1. [Qt Creator package](https://github.com/qt-creator/qt-creator/releases) from their GitHub project (recommended)
2. [Qt Online Installer](https://www.qt.io/download-open-source) (not recommended as it's quite bloated)

We don't recommend using your favorite package manager, because it's often harder to install the same version on all computers (which is important).

If you choose to use the Qt Online Installer, then you'll only need to install Qt Creator (and not Qt itself, as this dependency is managed by the dependencies script).

## Dependencies

Problems running the dependencies script (`python scripts/install_deps.py`)

### On Linux: `ERROR: File "setup.py" not found.`

This happens on older Linux distros such as Ubuntu 20, as they come with an older version of Python. Try upgrading `pip` to solve this.

```
pip install --upgrade pip
```

### There is no `python3` command

You'll need to install Python if you don't have it installed.

Examples:
- Windows: `winget install Python.Python.3.12`
- macOS: `brew install python`

If you do have it installed, then you may need to use `python3` (instead of `python`). 

Tip: If you need the `python` command to run Python 3, you can use `python-is-python3` on Linux or create a symlink/alias.

### On Windows: Stuck at `Starting package install`

The Visual Studio installer takes a while. If this takes longer than 5-10 minutes, the Visual Studio installer may be stuck. Kill the command, completely remove Visual Studio, reboot your computer, and try again.

### On Windows: Visual Studio is installed but the VC++ tools are not

If the Visual Studio Build Tools are already installed then it might not be possible for the script to modify the existing install. You'll need to manually modify the Visual Studio installation and add the C++ workload. Failing that, completely remove Visual Studio and re-run the dependencies script.

### On Linux: Error related to `pip` or `venv`

On some Linux distros, `pip` and `venv` are not included with Python by default. The dependencies script will try to resolve this, but if this fails you'll need to install these to use the dependencies script. 

If you're still having problems running the dependencies script, you can get the packages command from `config.yml` file and run it manually.

## Configure step

Problems running `cmake` in configure mode.

### Error: `cmake : The term 'cmake' is not recognized`

The dependencies script should set the `PATH` environment variable on Windows and macOS, but you may need to do this manually if you're still having problems. 

On Windows, you will probably need to run `refreshenv` or restart your IDE to use the new environment variable values.

### The same `cmake` error persists even after trying solutions

CMake caches configuration but doesn't invalidate the cache when the environment changes. Delete the `build` directory and re-run the configure step to create a fresh configuration.

For example, a common CMake error solved by removing the `build` dir is: `The C compiler [...] is not able to compile a simple test program`

### CMake cannot find Qt: `CMake Warning at src/gui/CMakeLists.txt`

On Windows and macOS, the dependencies script should set the `CMAKE_PREFIX_PATH` environment variables with the Qt path, for example:
- Windows: `C:\Qt\5.15.2\msvc2019_64`
- macOS: `$(brew --prefix qt@5)`

This is not normally required on Linux.

On Windows, you will probably need to run `refreshenv` or restart your IDE to use the new environment variable values.

After environment variables change, you may need to delete the `build` directory and re-run the configure step to create a fresh configuration.

### Windows error: `The CXX compiler identification is unknown`

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

### Linux error: `gcovr not found! Aborting`

When building with `-DENABLE_COVERAGE=ON`, gcovr is required. This is not satisfied by the dependencies script, since it's not a normal dependency. We could install this with the OS package manager (e.g. `apt`) but usually, it's an older version that gets installed. To install the latest version, you could use pipx:
```
sudo apt install pipx
pipx install gcovr
```

### Windows error: `Could not find a configuration file for package "Qt6" that is compatible`

This may be because the wrong arch is being used to compile. Instead of using the default `Developer command prompt for VS 2022`, try using `x86_64 Cross Tools Command Prompt for VS 2022` instead.

If you're using VS Code, the easiest way to fix this is to use the recommended extension, [CMake Tools](https://marketplace.visualstudio.com/items?itemName=ms-vscode.cmake-tools) which automatically sets up the Visual Studio developer tools environment for you.

## Development

### Qt `.ui` files change radically between computers

Different versions of Qt Creator save `.ui` files differently. To ensure as much consistency as possible between each OS, use the same version of Qt Creator across Windows, macOS, and Linux. This ensures that `.ui` files are at least saved in the same way, which can help to prevent _some_ rendering issues. However, this won't fix runtime rendering issues in the built Linux app since it'll be built against a much older version of Qt.

### The GUI looks different compared to Qt Creator preview

Qt development with `.ui` files is tricky due to Linux package dependencies. We have limited control over the Qt version available on each distro. On Windows and macOS, we can bundle the specific Qt DLLs, giving us more control over the Qt version the app is rendered with. Unfortunately, we have to work around weird rendering issues on Linux because of the Qt versions available in the package repositories.

### VS Code uses wrong `clang-format` or `cmake-format`

You should use the same version of `clang-format` on all of your computers, and you should use the latest version. 

```
pipx install clang-format cmakelang
pipx inject clang-format pyyaml
pipx inject cmakelang pyyaml
```

For some reason `clang-format` does not try to resolve it's dependency on `pyyaml` which isn't always available (depending on the version of Python you have), so you'll sometimes need to use `pipx inject` to satisfy this dependency.