# OpenCPN 5.10 Plugin build for Windows

- Download VS 2022 Community from https://visualstudio.microsoft.com
- Run the installer and select (at least) `Desktop development with C++`, then install
- Download Git from https://git-scm.com/download/win and install (all the defaults in the installer are OK to accept)
- Install Chocolatey
  - Run `Command Prompt` as Administrator
  - Run `powershell.exe`
  - Paste `Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))` and hit Enter
- Start `x86 Native Tools Command Prompt for VS 2022`
- Change directory to suitable choice, e.g. `C:\Projects`
- Clone the plugin source code `git clone --recurse-submodules https://github.com/bdbcat/vdr_pi.git`
- Close the command prompt
- Start `x86 Native Tools Command Prompt for VS 2022` as Administrator
- Run `choco install -y 7zip`
- Switch to the Plugin source folder `cd C:\Projects\vdr_pi`
- Run `buildwin\win_deps.bat`
- Close the command prompt
- Add `C:\Program Files (x86)\Poedit\GettextTools\bin` to your `PATH` environment variable  `set PATH=%PATH%;C:\Program Files (x86)\Poedit\GettextTools\bin`
- Start `x86 Native Tools Command Prompt for VS 2022`
- Switch to the Plugin source folder `cd C:\Projects\vdr_pi`
- Create the build folder `mkdir build`
- Switch to the build folder `cd build`
- Run `set "wxWidgets_ROOT_DIR=..\cache\wxWidgets"`
- Run `set "wxWidgets_LIB_DIR=..\cache\wxWidgets\lib\vc_dll"`
- Run `set "WXWIN=%wxWidgets_ROOT_DIR%"`
- Run `set PATH=%PATH%;C:\Program Files (x86)\Poedit\GettextTools\bin`
- Configure the build environment `cmake -A Win32 -G "Visual Studio 17 2022" -DCMAKE_GENERATOR_PLATFORM=Win32     ..`
- Build the plugin `cmake --build . --config Release`
- The plugin tarball should be successfully built
- The solution file `vdr_pi.sln` can be opened in Visual Studio and you can perform builds from within the IDE


