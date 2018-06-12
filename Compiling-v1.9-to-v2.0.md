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
1. Install [Boost 1.65.1](https://sourceforge.net/projects/boost/files/boost-binaries/1.65.1/boost_1_65_1-msvc-14.0-64.exe/download) (from boost-binaries)
1. Set the `BOOST_ROOT` environment variable (pointing to `\path\to\boost`)
1. Set the `BOOST_LIBRARYDIR` environment variable (pointing to `\path\to\boost\lib64-msvc-14.0`)
1. Install [Git for Windows](https://git-scm.com/download/win)
1. Download [libsodium](https://download.libsodium.org/libsodium/releases/libsodium-1.0.14-msvc.zip)
1. Set the `LIBSODIUM_INCLUDE_DIR` environment variable to `\path\to\libsodium\include`
1. Set the `LIBSODIUM_LIBRARY_DIR` environment variable to `\path\to\libsodium\x64\Release\v140\dynamic`
1. Restart Qt
1. Set `CMAKE_PREFIX_PATH` environment variable to `\path\to\qt\qt_version\msvc2015_64`


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
1. Install boost 1.65.1 from https://dl.bintray.com/boostorg/release/1.65.1/source/
    1. `tar jxvf boost_1_65_1.tar.bz2`
    1. `./bootstrap.sh`
    1. `./b2`
    1. `sudo ./bjam install`

## Ubuntu 16.04 and up
1. Install packages: `sudo apt-get install cmake make g++ xorg-dev libssl-dev libx11-dev libsodium-dev libgl1-mesa-glx libegl1-mesa libcurl3-dev`
1. Install [Qt](https://www1.qt.io/download-open-source/)
1. Install [Boost 1.65.1](http://www.boost.org/doc/libs/1_65_1/more/getting_started/unix-variants.html)
1. Edit the Qt kit environment field (`Manage Kits` in `Projects`) and add `BOOST_ROOT=/path/to/boost_1_65_1`
1. Run `./bootstrap.sh --prefix=/path/to/boost_1_65_1` and `./b2 install`

## CentOS 7
```
sudo yum groupinstall "Development Tools"
sudo yum -y install epel-release cmake3 boost-static git libXtst-devel qt5-qtbase-devel qt5-qtdeclarative-devel libcurl-devel openssl-devel
```

# Compile

## Windows
```
cd Projects\synergy
mkdir build
cd build
call "C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\vcvarsall.bat"
cmake -G "Visual Studio 14 2015 Win64" -DCMAKE_BUILD_TYPE=%CMAKE_BUILD_TYPE% ..
msbuild synergy.sln /p:Platform="x64" /p:Configuration=%CMAKE_BUILD_TYPE% /m
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