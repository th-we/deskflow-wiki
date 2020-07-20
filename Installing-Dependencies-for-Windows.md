You will need to following tools to compile on a windows system
* Qt
* MSBuild Tools
* Bonjour
* Git (Unless you download source as a zip)
* CMake

# Qt
There is 2 options for downloading Qt
* [Qt Online installer](https://www.qt.io/download-open-source)
* [aqtinstaller](https://pypi.org/project/aqtinstall/)

The online installer pulls in a lot of extra thing you might not want, and is not strictly required to build Synergy-Core where as aqtinstaller require python and is command line based but will pull down a lot less 

### Qt Online installer
1. Download the [online installer](https://www.qt.io/download-open-source)
1. Run the installer Creating/logging into you account as needed
1. Select the version of Qt you wish to build against (Current is 5.12.6)
1. Set install location to `C:/Qt`
1. Wait for the install to finish

### aqtinstaller
1. [Install Python 3](https://www.python.org/downloads/) if you don't already have it
1. [Install pip](https://pip.pypa.io/en/stable/installing/) if you haven't already
1. Install aqtinstall
    1. `pip install aqtinstall` or `python -m pip install aqtinstall`
1. Install Qt
    * `aqt install --outputdir c:\Qt 5.12.6 windows desktop win64_msvc2017_64`
    * or 
    * `python -m aqt install --outputdir c:\Qt 5.12.6 windows desktop win64_msvc2017_64`
1. If you want the 32 bit binaries use the following command replace `win64_msvc2017_64` with `win32_msvc2017`

# MS Build tools
You have 2 options here depending on if you want just compile synergy or you wish to develop
* [Visual studio](https://visualstudio.microsoft.com/vs/) if you would like the develop 
* [MS Build tools](https://visualstudio.microsoft.com/downloads/) for just compiling (Command line based only)
    * Scroll down, and expand `Tools for Visual Studio 2019`

When installing Visual Studio, ensure you select the Visual C++ environment 

# Bonjour 

For windows the [Bonjour SDK](https://binaries.symless.com/bonjour/bonjoursdksetup.exe) is needed.

Install to the default location.

# Cmake

1. [Download Cmake](https://cmake.org/download/)
1. Follow the wizard to install 
    * Adding cmake to you PATH will make compiling simpler

# Git (Optional)

1. [Download Git](https://git-scm.com/downloads) for windows
1. Follow the wizard to install
