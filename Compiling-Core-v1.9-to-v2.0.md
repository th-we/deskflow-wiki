# Dependencies

## Windows

1. Install [Visual Studio Professional 2015 with Updates](https://my.visualstudio.com/Downloads?q=Visual%20Studio%202015%20Update%203)
   1. Select Custom
   1. Deselect all
   1. Within `Programming Languages`, select `Visual C++`
   1. Within `Windows and Web Development > Universal... >`, select `Windows 10 SDK (...86)`
1. Install [Windows 10 SDK](https://developer.microsoft.com/en-US/windows/downloads/windows-10-sdk)
1. Install [Qt](https://www1.qt.io/download-open-source/)
1. Install [CMake](https://cmake.org/files/v3.9/cmake-3.9.2-win64-x64.msi)
1. If using command line, set `CMAKE_PREFIX_PATH` environment variable to `\path\to\qt\qt_version\msvc2015_64`


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
1. Install cmake, openssl using Homebrew:
    1. `$ brew install cmake openssl`

## Ubuntu 16.04 and up
1. Install packages: `sudo apt-get install cmake make g++ xorg-dev libssl-dev libx11-dev libsodium-dev libgl1-mesa-glx libegl1-mesa libcurl3-dev`
1. Install [Qt](https://www1.qt.io/download-open-source/)

## CentOS 7
```
sudo yum groupinstall "Development Tools"
sudo yum -y install epel-release cmake3 git libXtst-devel qt5-qtbase-devel qt5-qtdeclarative-devel libcurl-devel openssl-devel
```

# Compile Steps

First, follow the [[Checkout Code]] guide.

## IDE Compile

Compiling from the IDE (e.g. Qt Creator).

### All OSes

1. Open Qt Creator
2. Open Project
3. Open CMakeLists.txt
4. Untick "Imported Kit"
5. Expand "Desktop Qt..."
6. Untick all except Debug and Release
7. If macOS, follow *macOS Only* steps

### macOS Only

TODO

## CLI Compile

Compiling from the command line.

### Windows
```
cd Projects\synergy
mkdir build
cd build
call "C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\vcvarsall.bat"
cmake -G "Visual Studio 14 2015 Win64" -DCMAKE_BUILD_TYPE=%CMAKE_BUILD_TYPE% ..
msbuild synergy.sln /p:Platform="x64" /p:Configuration=%CMAKE_BUILD_TYPE% /m
```

### macOS
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

### Linux
```
cd Projects/synergy
mkdir build
cd build
cmake ..
make
```