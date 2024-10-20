Deskflow is free and open source software, and anyone is welcome to build it,
run it, tinker with it, redistribute it as part of their own app, etc.

These instructions will build Deskflow
 We are working on a newer guide for now the legacy guide will be kept and linked here


- [Legacy Guide](#legacy-guide)
- [Getting Started](#getting-started)

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
  1. Qt 6.5+ 
    - You Can not use the brew version of Qt if you plan to distribute the build
    - If you want to distribute your builds you need to get Qt from the [Qt-Online-Installer](https://doc.qt.io/qt-6/qt-online-installation.html)

 Once you have installed brew run this command to get the rest 
 ```
  brew install qt cmake git
 ```

## Linux

You should have at lest the basic items to build c++ code at this time 
   - gcc or clang 
   - cmake 3.24 +
   - git

Use your package manager to install these

          
