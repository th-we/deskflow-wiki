> [!WARNING]
> **WIP:** These instructions are a work in progress. [[Building (legacy)]]

Deskflow is free and open source software, and anyone is welcome to build it,
run it, tinker with it, fork it, redistribute it as part of their own app, etc.

- [Getting Started](#getting-started)
- [Dependencies](#dependencies)
- [Configure](#configure)
- [Build](#build)

# Getting Started

Before we can begin building, we need to set up the development environment.



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

 Tip: Initial configuration using vcpkg can take awhile since it will checkout and build all dependencies this is the easiest way to configure the project on windows. If you do not want to build a dependency (or any of them) You must
  1. Edit the `vcpkg.config` file to remove the items you do will install manually, This must happen before you attempt to configure the project. OR when configuring the project without CMAKE_TOOLCHAIN_FILE set to the vcpkg toolchain.
  1. Install the item manually and make sure that cmake can find it, usually this involves adding the path where the projects *.cmake file is located to your PATH
  1. In the case of Qt also add the path of the qt tools to your PATH

## macOS
 Getting started on macOS you will need to have the following tools
  1. [XCode](https://apps.apple.com/us/app/xcode/id497799835) - App Store
    - You must open it after installing and install the SDK for the version of macOS you have.
  1. [Homebrew](https://www.brew.sh)
  1. Git
  1. CMake 3.24
  1. Qt 6

Tip: The Brew version of Qt can crash when it should show a dialog, For this reason its recommended to use [aqtinstall](https://github.com/miurahr/aqtinstall) or the [Official Qt Installer](https://www.qt.io/download-qt-installer-oss).

Tip: Once you have installed `brew`, run this command
```
brew install git cmake
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
 - Qt 6.7+
 - OpenSSL 3.0
 - Google Test**
 - libportal 0.8+ (Linux only)
 - libei 1.3+ (Linux only)

** These dependencies will be downloaded automatically at build time if they are not found on your system, Google Test is only needed to build tests.

## Windows

If you have installed `vcpkg` when using either Qt Creator or Visual Studio Code it should automatically detect your vcpkg info. If it does not you will need to [set your `CMAKE_TOOLCHAIN_FILE`](https://learn.microsoft.com/en-us/vcpkg/get_started/get-started?pivots=shell-powershell#4---build-and-run-the-project). Once `vcpkg` has been setup it will download and build the needed dependencies when you run the configuration command. It will take a while to build things the first time, which is normal.

The following items will be installed by vcpkg: `qt`, `openssl`, and `gtest`.

## macOS

  1. Qt 6.7+ 
    - You should not use the `brew` version of Qt if you plan to distribute the build (it targets only the current system).
    - If you want to distribute your builds you need to get Qt from the [Qt Online Installer](https://doc.qt.io/qt-6/qt-online-installation.html)
  1. openssl 3.0+
  1. googletest (optional)       

## Linux
  If your disto has `dev` or `devel` package be sure to install those.
  - libei 1.3
  - libportal 0.8 
  - qt 6.7+
  - google test (optional)

**Debian/Ubuntu:**
```
  apt install cmake build-essential ninja-build \
              xorg-dev libx11-dev libxtst-dev libssl-dev \
              libglib2.0-dev libxkbfile-dev qt6-base-dev qt6-tools-dev \
              libgtk-3-dev libgtest-dev libgmock-dev libei-dev libportal-dev
```

**Fedora:**
```
  dnf install cmake make ninja-build gcc-c++ rpm-build \
              openssl-devel glib2-devel libXtst-devel libxkbfile-devel \
              qt6-qtbase-devel qt6-qttools-devel gtk3-devel \
              gtest-devel gmock-devel libei-devel libportal-devel
```

**RHEL**
```
  dnf install epel-release
  dnf config-manager --set-enabled crb
  dnf install cmake make ninja-build gcc-c++ rpm-build \
              openssl-devel glib2-devel libXtst-devel libxkbfile-devel \
              qt6-qtbase-devel qt6-qttools-devel gtk3-devel \
              gtest-devel gmock-devel libei-devel libportal-devel

```

**SUSE/openSUSE:**
```
  zypper install cmake make ninja gcc-c++ rpm-build libopenssl-devel \
                 glib2-devel libXtst-devel libxkbfile-devel qt6-base-devel \
                 qt6-tools-devel gtk3-devel googletest-devel googlemock-devel 
                 libei-devel libportal-devel
```

**Arch Linux:**
```
  pacman -S base-devel cmake ninja gcc openssl \
            glib2 libxtst libxkbfile gtest libei libportal \
            qt6-base qt6-tools gtk3
```

**FreeBSD:**
```
  pkg install cmake ninja gmake gcc12 openssl glib \
              libX11 libXtst libxkbfile qt6-base qt6-tools \
              gtk3 googletest pkgconf libei libportal
```


# Configure

CMake options:

|         Option           |            Description                  |   Default Value    | Additional requirements |
:-------------------------:|:---------------------------------------:|:------------------:|:-----------------------:|
| BUILD_GUI                | Build GUI                               | ON                 | `Qt`|
| BUILD_DOCS               | Build User Documentation                | ON                 | `Doxygen` |
| BUILD_INSTALLER          | Build installers/packages               | ON                 | |
| BUILD_TESTS              | Build unit tests and legacy tests       | ON                 | `gtest`|
| BUILD_UNIFIED            | Build unified binary (client+server)    | OFF                | |
| ENABLE_COVERAGE          | Enable test coverage                    | OFF                | `gcov` |
| SKIP_BUILD_TESTS         | Skip running of tests at build time     | OFF                | |

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

## Missing icon or symbolic not recoloring on linux 

Icons must be installed to work correctly on linux

copy `deploy/linux/org.deskflow.deskflow.png` -> `/usr/share/icons/hicolor/512x512/apps/org.deskflow.deskflow.png`

copy `src/apps/res/icons/deskflow-light/apps/64/org.deskflow.deskflow-symbolic.svg` -> `/usr/share/icons/hicolor/symbolic/apps/org.deskflow.deskflow-symbolic.svg`

you may need to update your icon cache with a command like `gtk-update-icon-cache` after copying them over