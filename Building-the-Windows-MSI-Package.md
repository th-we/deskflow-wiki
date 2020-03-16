# Prerequsites

Before you begin, you need to have successfully built Synergy as described on in [Compiling](https://github.com/symless/synergy-core/wiki/Compiling). You will also need:

  1. [The Wix toolchain](https://wixtoolset.org/releases/) and the plugin for your version of Visual Studio.
  1. C++ Redistributable Merge Modules (MSMs). These may have been installed with Visual Studio. If you get an error that the system can't find file `Microsoft_VC142_CRT_x86.msm`, you're missing these. To install, run the Visual Studio Installer, click the button to modify an existing installation, navigate to the 'Individual Components' tab, and check the box for `C++ 2019 Redistributable MSMs.` 

*Note: If you installed QT5 via vcpkg, you will also need to install the Angle library (`vcpkg install angle`). If you installed QT from the QT website, it was included in the installation.*

# Building Using MSBuild

From a developer console (or after running `call "C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\vcvarsall.bat"`), run: `msbuild -p:Configuration:Debug` or `msbuild -p:Configuration:Release` from the `build/installer` folder, depending on your settings during compilation.

If the build is successful, it will generate `bin/Debug/Synergy.msi` or `bin/Release/Synergy.msi` in the installer folder. 

# Using Wix Manually

While MSBuild is likely easier, you can also build the MSI manually, using the Wix toolchain:

```cmd
'C:\Program Files (x86)\WiX Toolset v3.11\bin\candle.exe' .\Product.wxs -dConfiguration=Debug -dPlatform=x86 -ext WixUtilExtension -ext WixUIExtension -ext WixFirewallExtension

'C:\Program Files (x86)\WiX Toolset v3.11\bin\light.exe' .\Product.wixobj -ext WixUtilExtension -ext WixUIExtension -ext WixFirewallExtension
```

Adjust -dConfiguration and -dPlatform to match your configuration (Debug or Release) and your architecture (x86 or x64) chosen during compilation.

# Debugging Build Failures

CMake generates the file `build/installer/Include.wsi`, and populates it with file locations set during CMake generation. If your build fails with file path errors, you may need to modify the file paths in `Include.wsi` if they were not correctly set by CMake. 

Additionally, if you are using Visual Studio Enterprise, you may need to modify the paths to MSMs in `Product.wxs` - see [this issue](https://github.com/symless/synergy-core/issues/6642) for details. 



