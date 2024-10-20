Deskflow is free and open source software, and anyone is welcome to build it,
run it, tinker with it, redistribute it as part of their own app, etc.

These instructions are A WIP
- [Getting Started](#getting-started)
- [Dependencies](#dependencies)

# Getting Started

Before we can begin building we will need to make sure we correctly set up our system 

## Windows
 Getting started on windows requires you first have the following tools installed and in your `PATH`
   1. [Visual Studio 2022](https://visualstudio.microsoft.com/vs/) 
      - Install at least the following
         -  MSVC v143 - VS 2022 C++ x64 / x86 build tools
         - A Windows SDK for example I am using  `Windows 10 SDK (10.0.18362.0)`
   1. [cmake](https://cmake.org/download/) v3.24+
      - Version 3.24 or higher is needed
   1. [ninja](https://github.com/ninja-build/ninja/releases)
   1. [git](https://github.com/git-for-windows/git/releases/tag/v2.47.0.windows.1)
   1. [vcpkg](https://learn.microsoft.com/en-us/vcpkg/get_started/get-started?pivots=shell-powershell#1---set-up-vcpkg) Recommended for dependency management
      - Check out vcpkg to C:\vcpkg (names can get long and windows has a path limit)
      - After you have vcpkg.exe in C:\vcpkg be sure to run `vcpkg integrate install`
      - Note the "toolchain" it tells you to use for cmake we will need this to configure.
      - Be SURE TO add %VCPKG_ROOT% to your PATH 

## Mac os 
 Getting started on mac os you will need to have the following tools
  1. XCode - Appstore
    - You must open it after installing and install the sdk for the version of mac os you have
  1. [homebrew] (https://www.brew.sh)
    - Use homebrew to instal both git and cmake  `brew install git cmake qt`
  1. git
  1. cmake 3.24

 Once you have installed brew run this command to get the others 

 ```
  brew install cmake git
 ```

## Linux

You should have at lest the basic items to build c++ code at this time 
   - gcc or clang 
   - cmake 3.24 +
   - git
   - ninja build tool (recommended)

Use your package manager to install these

# Dependencies

Deskflow requires the following items to build
 - cmake 3.24+
 - Qt 6.5 +
 - openssl 3.0
 - tomlplusplus**
 - cli11**
 - google test**
 - libportal 0.8+ (linux wayland)
 - libei 1.3+ (linux wayland)
 - wintoast (windows)

** These dependencies will be downloaded automatically at build time if they are not found on your system, Google Test Is only needed for build tests

## Windows
 If you have installed vcpkg when using either Qt Creator or Visual Studio Code it should automatically detect your vcpkg info if it does not you will need to set your `CMAKE_TOOLCHAIN_FILE` as described [here](https://learn.microsoft.com/en-us/vcpkg/get_started/get-started?pivots=shell-powershell#4---build-and-run-the-project). Once vcpkg has been setup it will download and build the needed item when you run the configuration command It will take a while to build things the first time that is normal.

the following items will be installed by vcpkg
 qt, openssl, gtest, and wintoast. both `tomlplusplus` and `cli11` will be embedded by cmake.

## Mac os
  1. Qt 6.5+ 
    - You Can not use the brew version of Qt if you plan to distribute the build
    - If you want to distribute your builds you need to get Qt from the [Qt-Online-Installer](https://doc.qt.io/qt-6/qt-online-installation.html)
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


# Configuration

CMake options:

|         Option           |            Description                  |   Default Value    | Additional requirements |
:-------------------------:|:---------------------------------------:|:------------------:|:-----------------------:|
| BUILD_GUI                | Build GUI                               | ON                 | `Qt`|
| BUILD_INSTALLER          | Build installers/packages               | ON                 | |
| BUILD_TESTS              | Build unit tests and integration tests  | ON                 | `gtest`|
| BUILD_UNIFIED            | Build unified binary (client+server)    | OFF                | |
| ENABLE_COVERAGE          | Enable test coverage                    | OFF                | `gcov` |
| SYSTEM_LIBEI             | Use system libei (use local dep)        | ON                 | |
| SYSTEM_LIBPORTAL         | Use system libportal (or local dep)     | ON                 | |
| LIBPORTAL_STATIC         | Use static libportal (hacky)            | OFF                | `subprojects/packagefiles/libportal/static-lib.diff` |

To configure you use cmake 
example command 

```
cmake -S . -B build -DCMAKE_BUILD_TYPE=Release
```

# Build
For most you can use 
```
cmake --build build
```

