**Important:** Follow the [[Getting Started]] guide first to get the code. Before you can compile, you'll need the source code. Ensure you checkout the appropriate branch you wish to compile, e.g. if you wish to compile v1.13.1, `git checkout v1.13.1`.

Also, this guide is for compiling Synergy Core v1.9 and up (including v2.0). If using v1.3.5 to v1.8, follow the [[Compiling Legacy|Compiling v1.3.5 to v1.8 (legacy)]] guide.

# Table of Contents

- [Dependencies](#dependencies)
- [Compile Steps](#compile-steps)

# Dependencies

## Windows

1. Install [Git for Windows](https://yip.su/2FgCT4)
1. Install [Visual Studio Community 2019 with Updates](https://yip.su/2FgCT4)
   1. Select Custom
   1. Deselect all
   1. Within `Programming Languages`, select `Visual C++`
   1. Git for Windows should already be installed
1. Install [Windows 10 SDK](https://yip.su/2FgCT4)
   1. Select **Download the installer**, not the iso
   1. Use default options for first 2 screens 
   1. On the feature screen, unselect everything except **Debugging Tools for Windows**
1. Install [Bonjour SDK for Windows v3.0](https://binaries.symless.com/bonjour/bonjoursdksetup.exe)
1. Install [Qt](https://www1.qt.io/download-open-source/)
   1. Install to C:\Qt
   1. Select Qt 5.12.12
   1. After installation, add `C:\Qt\Tools\QtCreator\bin` to the system PATH 
7. Install OpenSSL either [directly](https://slproweb.com/products/Win32OpenSSL.html) or with [Chocolatey](https://chocolatey.org/)
   1. Remove(if exist) old OpenSSL from PATH in environment variables
   1. Remove(if exist) old OpenSSL folder from C:\Program Files\ and C:\Program Files (x86)
   1. Install new OpenSSL either [directly](https://slproweb.com/products/Win32OpenSSL.html) or with [Chocolatey](https://chocolatey.org/)
      1. `choco install openssl`
8. Install [CMake](https://cmake.org/)
   1. When prompted for PATH, select one of the options starting with "Add CMake to system PATH …" 
9. Restart Qt
10. Set `CMAKE_PREFIX_PATH` environment variable `C:\Qt\5.12.12\msvc2017_64`
11. Follow the compile steps below

## macOS
1. Install [Homebrew](http://brew.sh/)
1. Install [XCode](https://developer.apple.com/xcode/download/) (also available via the Mac App Store)
1. Install the latest version of Qt 5
    1. [Offline installer for Qt 5](https://www.qt.io/offline-installers)
        1. 5.12 is LTS until Dec 2021
        1. 5.12.12 is latest LTS release for Qt 5 as of November 26, 2021
        1. The Online Qt installer will install Qt 6 (not recommended)
1. Install CMake, libsodium using Homebrew:
    1. `brew install cmake libsodium`
1. Install OpenSSL
    1. `brew install openssl`
1. Now follow the compile steps below

## Linux
### Ubuntu 16.04 and up
```sh
sudo apt install -y \
  qtcreator \
  qtbase5-dev \
  qttools5-dev \
  cmake \
  make \
  g++ \
  xorg-dev \
  libssl-dev \
  libx11-dev \
  libsodium-dev \
  libgl1-mesa-glx \
  libegl1-mesa \
  libcurl4-openssl-dev \
  libavahi-compat-libdnssd-dev \
  qtdeclarative5-dev \
  libqt5svg5-dev \
  libsystemd-dev \
  libnotify-dev \
  libgdk-pixbuf2.0-dev \
  libglib2.0-dev

```

Edit the Qt kit _"Environment"_ field under _Tools -> Options -> Build & Run -> Kits_ and add `BOOST_ROOT=/home/<user>/boost`

### CentOS 7
```sh
sudo yum groupinstall "Development Tools"
sudo yum -y install epel-release cmake3 boost-static git libXtst-devel qt5-qtbase-devel qt5-qtdeclarative-devel libcurl-devel openssl-devel
```
### Fedora 28 (may work for earlier releases)
```sh
sudo yum groupinstall "Development Tools"
sudo yum -y install avahi-compat-libdns_sd-devel avahi-compat-libdns_sd cmake3 boost-static git libXtst-devel qt5-qtbase-devel qt5-qtdeclarative-devel libcurl-devel openssl-devel
```
### SUSE Linux 12 SP3 
```sh
sudo zypper install avahi-compat-mDNSResponder-devel libavahi-devel libqt5-qtbase-devel cmake libopenssl-devel libcurl-devel libXtst-devel
```
# Compile Steps

Make sure you have completed the steps at [[Getting Started]].

## IDE Compile

Compile instructions for Qt Creator.

### macOS

Do this first on macOS.

1. Qt Creator > Preferences > Kits > CMake
1. Click Add, set Path to: `/usr/local/bin/cmake`
1. Go to the Kits tab
1. Set the C compiler to Clang 64-bit
1. Restart Qt Creator

_Note:_ this may already be pre-configured for you.

### All OSes

1. Open Qt Creator
1. If macOS, follow *macOS Only* steps
1. Open Project
    1. Ctrl + O or File->Open File or Project
    1. Navigate to the project directory (from git clone)
    1. Open CMakeLists.txt
1. Untick "Imported Kit"
1. Expand "Desktop Qt 5.12.12 MSVC{VS version} {Prefered configuration}" e.g. Desktop Qt 5.12.12 MSVC2015 64bit
1. Untick all except Debug and Release and click Configure
1. Right-click on project and select Run CMake
1. If macOS, follow *macOS Post-CMake* steps
1. Build
    1. Check that selected mode is Release(bottom-left corner in QT CReator)
    1. Right-click project and select Build

### macOS Post-CMake

1. Open Projects
1. Select Build
1. Find `CMAKE_OSX_DEPLOYMENT_TARGET`
1. Set value to your version of OSX, e.g. `10.10`, `10.13`, etc. If you do not match the version of the OS SDK libraries you are linking against, there will be a lot of warnings during the build. By using the correct version, you will only receive deprecation warnings.
1. Find `CMAKE_OSX_SYSROOT`
1. Set value to `/Applications/Xcode.app/Contents/Developer/Platforms/MacOSX.platform/Developer/SDKs/MacOSX.sdk/`
1. Click *Apply Configuration Changes*
1. Go back to the *All OSes* steps (above)

### GUI standalone in Windows

These steps apply to 64-bit compilations.

In release and debug mode:
1. Copy all contents of `synergy-core/ext/openssl/windows/x64/bin/*` to `{build_folder}/bin/`
1. Copy the following files from `{QtInstallDir}/{QT Version}/{Compiler version}/bin/`(e.g. C:\Qt\5.12.12\msvc2015_64) to `{build_folder}/bin/`:
    - `Qt5Core.dll`
    - `Qt5Gui.dll`
    - `Qt5Network.dll`
    - `Qt5Widgets.dll`
1. Create folder `platforms` under `{build_folder}/bin/` 
1. Copy `{QtInstallDir}/{Version}/MSVC2019_64bit/plugins/platforms/qwindows.dll` in to `{build_folder}/bin/platforms`

To make possible debugging:
1. Copy all the files requested in release mode
1. Also from Qt installation directory, copy the following files (pay attention to the letter `d` in file names):
    - `Qt5Cored.dll`
    - `Qt5Guid.dll`
    - `Qt5Networkd.dll`
    - `Qt5Widgetsd.dll`

## CLI Compile

Compiling from the command line.

## Windows
```cmd
cd synergy-core
mkdir build
cd build
call "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\VC\Auxiliary\Build\vcvarsall.bat"
cmake -G "Visual Studio 16 2019" -DCMAKE_BUILD_TYPE=Debug ..
msbuild synergy-core.sln /p:Platform="x64" /p:Configuration=Debug /m
cd ..
copy ext\openssl\windows\x64\bin\* build\
```

### Example
- QT version is 5.12.12, and is installed at 'C:\Qt\5.12.12'
- Windows 10 SDK version is 10.0.19041.0
 - Open C:\Program Files (x86)\Windows Kits\10\SDKManifest.xml
 - Find 'PlatformIdentity = "UAP, Version=10.0.19041.0"'
- Visual studio 2019 community
- Your source path is "c:\<path>\synergy-core"
- Your host is x64
- Will build as x64 binary
```cmd
cd "c:\<path>\synergy-core"
mkdir build
cd build
call "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\VC\Auxiliary\Build\vcvarsall.bat" x64 10.0.19041.0
cmake -G "Visual Studio 16 2019"  -DCMAKE_BUILD_TYPE=Debug ..
msbuild synergy-core.sln /p:Platform="x64" /p:Configuration=Debug /m
cd ..
copy ext\openssl\windows\x64\bin\* build\
```

If you want to build the MSI package, see [Building the MSI Installer](https://github.com/symless/synergy-core/wiki/Building-the-Windows-MSI-Package) for details. 

## macOS

```sh
cd synergy-core
mkdir build
cd build
export  QT_PATH=$HOME/Qt/<qt version> ("ex:export  QT_PATH=/Users/user/Qt5.12.12/5.12.12/clang_64")
export PATH=$PATH:/usr/local/bin:$QT_PATH/bin
cmake -DOPENSSL_ROOT_DIR=/usr/local/opt/openssl -DOPENSSL_LIBRARIES=/usr/local/opt/openssl/lib -DCMAKE_OSX_DEPLOYMENT_TARGET=10.13 -DCMAKE_OSX_ARCHITECTURES=x86_64 -DCMAKE_BUILD_TYPE=$CMAKE_BUILD_TYPE ..
make
```
Go to build folder > bin copy all execs and place in bundler > Synergy.app (click left and Show package contents) > Contents and make a folder called MacOS and paste the execs there
## Linux

```sh
cd synergy-core
mkdir build
cd build
cmake ..
make
```