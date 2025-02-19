> [!WARNING]
> **WIP:** These instructions are a work in progress.

Deskflow is free and open source software, and anyone is welcome to build it,
run it, tinker with it, fork it, redistribute it as part of their own app, etc.

- [Getting Started](#getting-started)
- [Dependencies](#dependencies)
- [Configure](#configure)
- [Build](#build)

# Getting Started

Before we can begin building, we need to set up the development environment.

Legacy instructions: [[Building (legacy)]]

## Windows

 Getting started on Windows requires you first have the following tools installed and in your `PATH`
   1. [Visual Studio Community](https://visualstudio.microsoft.com/vs/community/) or [Visual Studio 2022](https://visualstudio.microsoft.com/vs/)
      - Install at least the following VS components:
         - MSVC v143 - VS 2022 C++ x64 / x86 build tools
         - A Windows SDK for example I am using  `Windows 10 SDK (10.0.18362.0)`
   1. [cmake](https://cmake.org/download/) - CMake v3.24 or higher is needed
   1. [ninja](https://github.com/ninja-build/ninja/releases)
   1. [git](https://github.com/git-for-windows/git/releases)
   1. [vcpkg](https://learn.microsoft.com/en-us/vcpkg/get_started/get-started) - Recommended for dependency management:
      - Clone `vcpkg` to `C:\vcpkg` (names can get long and Windows has a path limit)
      - After you have `vcpkg.exe` in `C:\vcpkg` be sure to run `vcpkg integrate install`
      - Note the "toolchain" it tells you to use for CMake; we will need this to configure.
      - Be sure to add `%VCPKG_ROOT%` to your `PATH` env var.
   1. [WiX](https://github.com/wixtoolset/wix/releases)

## macOS
 Getting started on macOS you will need to have the following tools
  1. [XCode](https://apps.apple.com/us/app/xcode/id497799835) - App Store
    - You must open it after installing and install the SDK for the version of macOS you have.
  1. [Homebrew](https://www.brew.sh)
  1. Git
  1. CMake 3.24
  1. Qt 6

Tip: Once you have installed `brew`, run this command
```
brew install git cmake qt
```

## Linux

You should have at lest the basic items to build C++ code:
   - gcc or clang
   - cmake 3.24+
   - git
   - ninja build tool (recommended)

Use your package manager to install these.

# Dependencies

Deskflow requires the following to build:
 - CMake 3.24+
 - Qt 6.5+
 - OpenSSL 3.0
 - TOML++**
 - CLI11**
 - Google Test**
 - libportal 0.8+ (Linux only)
 - libei 1.3+ (Linux only)
 - WinToast (Windows only)

** These dependencies will be downloaded automatically at build time if they are not found on your system, Google Test is only needed to build tests.

## Windows
If you have installed `vcpkg` when using either Qt Creator or Visual Studio Code it should automatically detect your vcpkg info. If it does not you will need to [set your `CMAKE_TOOLCHAIN_FILE`](https://learn.microsoft.com/en-us/vcpkg/get_started/get-started?pivots=shell-powershell#4---build-and-run-the-project). Once `vcpkg` has been setup it will download and build the needed dependencies when you run the configuration command. It will take a while to build things the first time, which is normal.

The following items will be installed by vcpkg: `qt`, `openssl`, `gtest`, and `wintoast`.
Both `tomlplusplus` and `cli11` will be embedded by CMake.

## macOS
  1. Qt 6.5+ 
    - You should not use the `brew` version of Qt if you plan to distribute the build (it targets only the current system).
    - If you want to distribute your builds you need to get Qt from the [Qt Online Installer](https://doc.qt.io/qt-6/qt-online-installation.html)
  1. openssl 3.0+
  1. tomlplusplus (optional)
  1. cli11 (optional)
  1. googletest (optional)       

## Linux
  If your disto has `dev` or `devel` package be sure to install those.
  - libei 1.3
  - libportal 0.8 
  - qt 6.5+
  - tomlplusplus (optional)
  - cli11(optional)
  - google test (optional)

**Debian/Ubuntu:**
```
  apt install cmake build-essential ninja-build \
              xorg-dev libx11-dev libxtst-dev libssl-dev \
              libglib2.0-dev libgdk-pixbuf-2.0-dev libnotify-dev \
              libxkbfile-dev qt6-base-dev qt6-tools-dev \
              libgtk-3-dev libgtest-dev libgmock-dev libpugixml-dev \
              libei-dev libportal-dev libtomlplusplus-dev libcli11-dev
```

**Fedora:**
```
  dnf install cmake make ninja-build gcc-c++ rpm-build \
              openssl-devel glib2-devel gdk-pixbuf2-devel \
              libXtst-devel libnotify-devel libxkbfile-devel \
              qt6-qtbase-devel qt6-qttools-devel gtk3-devel \
              gtest-devel gmock-devel pugixml-devel libei-devel \
              libportal-devel tomlplusplus-devel cli11-devel
```

**RHEL**
```
  dnf install epel-release
  dnf config-manager --set-enabled crb
  dnf install cmake make ninja-build gcc-c++ rpm-build \
              openssl-devel glib2-devel gdk-pixbuf2-devel \
              libXtst-devel libnotify-devel libxkbfile-devel \
              qt6-qtbase-devel qt6-qttools-devel gtk3-devel \
              gtest-devel gmock-devel pugixml-devel libei-devel \
              libportal-devel tomlplusplus-devel cli11-devel

```

**SUSE/openSUSE:**
```
  zypper install cmake make ninja gcc-c++ rpm-build libopenssl-devel \
                 glib2-devel gdk-pixbuf-devel libXtst-devel libnotify-devel \
                 libxkbfile-devel qt6-base-devel qt6-tools-devel gtk3-devel \
                 googletest-devel googlemock-devel pugixml-devel libei-devel \
                 libportal-devel tomlplusplus-devel cli11-devel
```

**Arch Linux:**
```
  pacman -S base-devel cmake ninja gcc openssl \
            glib2 gdk-pixbuf2 libxtst libnotify \
            libxkbfile gtest pugixml libei libportal \
            qt6-base qt6-tools gtk3 tomlplusplus cli11
```

# Configure

CMake options:

|         Option           |            Description                  |   Default Value    | Additional requirements |
:-------------------------:|:---------------------------------------:|:------------------:|:-----------------------:|
| BUILD_GUI                | Build GUI                               | ON                 | `Qt`|
| BUILD_DOCS               | Build User Documentation                | ON                 | `Doxygen` |
| BUILD_INSTALLER          | Build installers/packages               | ON                 | |
| BUILD_TESTS              | Build unit tests and integration tests  | ON                 | `gtest`|
| BUILD_UNIFIED            | Build unified binary (client+server)    | OFF                | |
| ENABLE_COVERAGE          | Enable test coverage                    | OFF                | `gcov` |

To configure you use CMake.

> [!TIP]
> You could create a [`CMakeUserPresets.json`](https://gist.github.com/nbolton/1a6c59b576528f20f76ae2e3fd0c72d5) file.

**Configure command example:**
```
cmake -S . -B build -DCMAKE_BUILD_TYPE=Release
```

# Build

**Build command example:**
```
cmake --build build -j8
```

# Gotchas

## Error: `qt.qpa.plugin: Could not find the Qt platform plugin "windows" in ""`

Attempted fix: https://github.com/deskflow/deskflow/pull/8057

Create a `qt.conf` file in `bin`:
```
[Paths]
Plugins = C:\vcpkg...debug\Qt6\plugins
```