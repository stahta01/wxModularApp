wxModularApp
============

Cross-Platform Modular Application (Main app + plugins) example for C++/wxWidgets

Requirements
------------
* Compiled shared (DLL Debug/DLL Release) version of wxWidgets. [SVN HEAD](http://svn.wxwidgets.org/svn/wx/wxWidgets/trunk) or official [3.0.x](http://svn.wxwidgets.org/svn/wx/wxWidgets/tags/WX_3_0_2/) release should work fine. Ensure that you have only `vc_dll` subfolder in `%WXWIN%/libs`. If you have `vc_lib*` folders then rename them temporary.
* [CMake](http://www.cmake.org/) - required on all platforms. It is used for creating 
  * Visual Studio projects under Windows
  * Makefiles under Linux
  * XCode projects under OS X
* Under Windows `%WXWIN%` environment variable is required. Should point to wxWidgets source folder (e.g. `C:\libs\wxWidgets-svn`)

wxWidgets Build Commands for Linux and OS X
-------------------------------------------
<strong>Debug:</strong>

`configure --enable-shared --disable-static --enable-unicode --disable-compat28 --disable-final --enable-debug`

<strong>Release:</strong>

`configure --enable-shared --disable-static --enable-unicode --disable-compat28 --enable-final --disable-debug`

Compilation under Windows
-------------------------
* Open Visual Studio console ("Start menu -> VS2012 x86 Native Tools Command Prompt" or x64 native tools for x64 build)
* Navigate to `<DEMO_SOURCE_ROOT>/build` folder
* Execute `cm86.bat` (or `cm64.bat` for x64 build, or `cm.bat` which auto-detects the platform)
* The batch file will execute CMake and after that you will get Visual Studio project files in <DEMO_SOURCE_ROOT>/build/Win folder
* Build the solution in Visual Studio or using msbuild

Compilation under Linux
-----------------------
* Open `<DEMO_SOURCE_ROOT>/build` folder in console
* Execute `cmLinux.sh` script
* The script will create LinuxDebug and LinuxRelease folders with Makefiles.
* Go to LinuxRelease (or to LinuxDebug for debug build)
* Execute `make`

Compilation under OS X
----------------------
* Open `<DEMO_SOURCE_ROOT>/build` folder in terminal
* Execute `cm.sh` script
* The script will create XCode project in Mac subfolder
* Go to Mac subfolder
* Execute `xcodebuild build` command or build the project from XCode
