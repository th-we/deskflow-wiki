Before you can compile, you'll need the source code. Follow the [[Getting Started]] guide for help with this. 

Also, this guide is for compiling Synergy Core v1.9 and up (including v2.0). If using v1.3.5 to v1.8, follow the [[Compiling Legacy|Compiling-Legacy-v1.3.5-to-v1.8]] guide.

# Dependencies

**Important:** Please also reflect changes in the [Core Compiling](https://github.com/symless/synergy-core/wiki/Compiling-Core-v1.9-to-v2.0) guide.

## Windows

1. Install [Git for Windows](https://gitforwindows.org/)
1. Install [Visual Studio Professional 2015 with Updates](https://go.microsoft.com/fwlink/?LinkId=532606&clcid=0x409)
   1. Select Custom
   1. Deselect all
   1. Within `Programming Languages`, select `Visual C++`
   1. Git for Windows should already be installed
1. Download the [Windows 10 SDK Web Installer](https://developer.microsoft.com/en-US/windows/downloads/windows-10-sdk)
   1. Click **Download the installer** (not the iso)
   1. Use default options for first 2 screens 
   1. On the feature screen, untick everything except **Debugging Tools for Windows**
1. Install Bonjour
   1. Download: [Bonjour SDK for Windows v3.0](https://binaries.symless.com/bonjour/bonjoursdksetup.exe)
1. Install [Qt](https://www1.qt.io/download-open-source/)
   1. Install to C:\Qt
   1. Select Qt 5.9.5
1. Add 'C:\Qt\Tools\QtCreator\bin' to the system PATH 
1. Install [CMake](https://cmake.org/)
   1. Add CMake to PATH for all users
1. Restart Qt
1. Set `CMAKE_PREFIX_PATH` environment variable to `\path\to\qt\qt_version\msvc2015_64`
1. Now follow the compile steps below

## macOS
1. Install [Homebrew](http://brew.sh/)
1. Install [XCode](https://developer.apple.com/xcode/download/) (also available via the Mac App Store)
    1. Update the command line tools setting - Preferences -> Locations
    1. In the Command Line Tools drop down, select "Xcode 9.4"
1. Install the latest version of Qt 5.9 [Qt](https://www1.qt.io/download-open-source/) (5.9.6 as of Jun 11/18)
    1. Choose open source option
    1. Run package manager
    1. Select Qt 5.9.x and unselect everything other than macOS
    1. At bottom of list ensure Qt Creator is selected under "Tools"
    1. Select Continue and agree to terms
1. Install cmake, openssl, libsodium using Homebrew: `brew install cmake openssl libsodium`
1. Now follow the compile steps below

## Ubuntu 16.04 and up
1. $ `sudo apt install qtcreator qtbase5-dev cmake make g++ xorg-dev libssl-dev libx11-dev libsodium-dev libgl1-mesa-glx libegl1-mesa libcurl4-openssl-dev libavahi-compat-libdnssd-dev qtdeclarative5-dev libqt5svg5-dev libsystemd-dev`
1. Edit the Qt kit environment field (*Manage Kits* in *Projects*) and add `BOOST_ROOT=/home/<user>/boost`

## CentOS 7
```
sudo yum groupinstall "Development Tools"
sudo yum -y install epel-release cmake3 boost-static git libXtst-devel qt5-qtbase-devel qt5-qtdeclarative-devel libcurl-devel openssl-devel
```
## Fedora 28 (may work for earlier releases)
```
sudo yum groupinstall "Development Tools"
sudo yum -y install libavahi-compat-libdnssd-devel avahi-compat-libdns_sd cmake3 boost-static git libXtst-devel qt5-qtbase-devel qt5-qtdeclarative-devel libcurl-devel openssl-devel
```
# Compile Steps

Make sure you have completed the steps at [[Getting Started]].

## IDE Compile

Compiling from the IDE (e.g. Qt Creator).

### macOS Only

Do this first on macOS.

1. Qt Creator > Preferences > Build & Run > CMake
1. Click Add, set Path to: `/usr/local/bin/cmake`
1. Go to the Kits tab
1. Set the C compiler to Clang 64-bit
1. Restart Qt Creator

### All OSes

1. Open Qt Creator
1. If macOS, follow *macOS Only* steps
1. Open Project
1. Navigate to the project directory (from git clone)
1. Open CMakeLists.txt
1. Untick "Imported Kit"
1. Expand "Desktop Qt..."
1. Untick all except Debug and Release
1. Right-click project and select Run CMake
1. If macOS, follow *macOS Post-CMake* steps
1. Right-click project and select Build

### macOS Post-CMake

1. Open Projects
1. Select Build
1. Find `CMAKE_OSX_DEPLOYMENT_TARGET`
1. Set value to `10.10`
1. Find `CMAKE_OSX_SYSROOT`
1. Set value to `/Applications/Xcode.app/Contents/Developer/Platforms/MacOSX.platform/Developer/SDKs/MacOSX.sdk/`
1. Click *Apply Configuration Changes*
1. Go back to the *All OSes* steps (above)

## CLI Compile

Compiling from the command line.

## Windows
```
cd Projects\synergy
mkdir build
cd build
call "C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\vcvarsall.bat"
cmake -G "Visual Studio 14 2015 Win64" -DCMAKE_BUILD_TYPE=%CMAKE_BUILD_TYPE% ..
msbuild synergy-core.sln /p:Platform="x64" /p:Configuration=%CMAKE_BUILD_TYPE% /m
```

## macOS
```
cd Projects/synergy
mkdir build
cd build
QT_PATH=$HOME/Qt/5.9.3/clang_64
export PATH=$PATH:/usr/local/bin:$QT_PATH/bin
#cmake -DCMAKE_OSX_SYSROOT=/Applications/Xcode.app/Contents/Developer/Platforms/MacOSX.platform/Developer/SDKs/MacOSX10.12.sdk -DOSX_TARGET_MAJOR=10 -DOSX_TARGET_MINOR=12 -DCMAKE_OSX_ARCHITECTURES=x86_64 ..
cmake  -DCMAKE_OSX_DEPLOYMENT_TARGET=10.10 -DCMAKE_OSX_ARCHITECTURES=x86_64 -DCMAKE_BUILD_TYPE=$CMAKE_BUILD_TYPE -DCMAKE_CONFIGURATION_TYPES=$CMAKE_BUILD_TYPE ..
make
```

## Linux
```
cd Projects/synergy
mkdir build
cd build
cmake ..
make
```