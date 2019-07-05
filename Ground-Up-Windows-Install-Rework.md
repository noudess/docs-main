**This guide provides instructions for compiling 32-bit Windows server binaries and setting up a local development server.**

**Read through this guide before starting to ensure an understanding of the process.**

**Please direct any questions to our server support channel in 
[[discord](https://discord.gg/QHsm7CD)].**


---

## Compiler Setup

The current c/c++ support standard of the EQEmulator server code base mandates the use of Visual Studio 2013 or later compilers.

Visual Studio 2017 is the current EQEmulator standard for binary compilation. Please ensure that your system meets the [[Visual Studio 2017 Minimum System Requirements](https://docs.microsoft.com/en-us/visualstudio/productinfo/vs2017-system-requirements-vs#visual-studio-2017-system-requirements)].

If your system does not meet the above requirements, or you are/would like to use an older version of Visual Studio, check the minimum system requirements for the version you plan to use. (It must still meet the Visual Studio 2013 or later requirement of the code base.)

This setup assumes an install on a 64-bit Windows operating system with 32-bit target binaries.

* ### Verify System Environment Variable %Path% Length

  Sometimes an automated server installation will fail due to the %Path% variable being full. This can happen with a manual installation as well.

  Since this guide installs more programs than are required for server operation alone, verifying the length of %Path% is critical before we start.

  The easiest way to find it is to:

  * Click on your `Start` button

  * Type "environment variable" into your search programs and files text box

  * Click on `Edit system environment variables`

  * Click the `Environment Variables` button on the window that pops up

  * Ensure the variable `Path` is selected in the system variables section (bottom text box)	
	
  * Click the `Edit` button

  You may check the length of your %Path% variable by copying the `Variable value` contents and pasting them into a text editor that supports "selection" count.

  ![](https://user-images.githubusercontent.com/3311166/60465078-3b56b180-9c1e-11e9-89c5-0137a6ed84ba.png)

  Registry values are only allocated 1024 bytes of storage. However, environmental variables may contain up to 2048 bytes through the use of an alias.

  If your selection count is greater than 768 characters, you may need to setup an alias to prevent corruption of the %Path% variable.

* ### Required Programs

  Some of the pre-requisites for compiling binaries are the same as running a server.

  If you have already installed any of the following, the download and installation requirement should be omitted:

  * Visual Studio 2017 Community Edition [[select Visual Studio 2017 Community Edition](https://visualstudio.microsoft.com/vs/older-downloads/)]

    _Note: Microsoft now requires a user account to download Visual Studio. Clicking the Visual Studio link above will take you to the "older versions" page. Clicking the_ `Download` _button on that page will prompt you to log in or create an account._

  * MariaDB (64-bit) [[download](https://downloads.mariadb.org/interstitial/mariadb-10.4.6/winx64-packages/mariadb-10.4.6-winx64.msi/from/http%3A//mirror.nodesdirect.com/mariadb/)]

  * Perl v5.12.3.1204 (32-bit) [[download](https://github.com/EQEmu/eqemu.github.com/raw/master/downloads/ActivePerl-5.12.3.1204-MSWin32-x86-294330.msi)]

  * CMake (64-bit) [[download](https://github.com/Kitware/CMake/releases/download/v3.14.5/cmake-3.14.5-win64-x64.msi)] 

  [](#back-git)
  * Git (64-bit - see [[note](Ground-Up-Windows-Install-Rework#note-git)] under install) [[download](https://git-scm.com/download/win)]

  [](#back-tgit)
  * TortoiseGit (64-bit - optional - see [[note](Ground-Up-Windows-Install-Rework#note-tgit)] under install [[download](https://download.tortoisegit.org/tgit/2.8.0.0/TortoiseGit-2.8.0.0-64bit.msi)]

    _Note: TortoiseGit is a menu-driven, add-on gui interface for Git. Though optional, this instructional provides for its use._

  Some programs may be able to use newer versions, or even their lastest releases, without issue. But, this is not the case with Perl and (later) dependencies.

  The above list of programs is known to work for compiling working server binaries.

* ### Install Visual Studio

  During the install process, ensure the option for `Desktop development with C++` is checked.

  This package is required by Visual Studio to compile c/c++ code and by CMake to determine available compiler options. It will cause CMake file generation to fail, if not enabled.

  ![](https://user-images.githubusercontent.com/3311166/60468475-b40e3b80-9c27-11e9-8b2b-462bd0f22165.png)

* ### Install MariaDB

  This installation is self-explanatory.

  _Note: You will need to keep track of your username and password. They will be needed anytime that you access the database as well as for setting up the server configuration files._

  At the end of the installation process, you will be prompted to install HeidiSQL. It is **HIGHLY** recommended that you install this program.

* ### Install Perl 5.12.3 (32-bit)

  This installation is self-explanatory.

  _Note: It is recommended that you install in the root directory (_`c:\`_) to avoid possible issues._

* ### Install CMake

  This installation is self-explanatory.

* ### Install Git

  This installation is self-explanatory.

  [](#note-git)
  _Note: Should you wish to download the repository code with no further chance of updating or restoration, this requirement may be omitted._ [[back](Ground-Up-Windows-Install-Rework#back-git)]

* ### Install TortoiseGit (optional)

  This installation is self-explanatory.

  [](#note-tgit)
  _Note: If Git is not installed, this installation should be omitted._ [[back](Ground-Up-Windows-Install-Rework#back-tgit)]

* ### Restart Computer

  You will need to restart your computer to ensure that all of the %Path% additions are loaded into memory.

* ### Acquiring the Code

  At this point, you will need to make a decision on how you want to manage your code.

  There are three options:

  * Option 1 - Retrieve the code as a one-time download (unmanaged - not recommended)

  * Option 2 - Create a local repository from the parent EQEmulator project that can be updated, managed and maintained (recommended)

  * Option 3 - Create a local repository from a fork of the EQEmulator project that you manage (optional - select only if you want to contribute back to the parent project)

  _Note: If you choose to create a fork of the EQEmulator repository, you will need to create a_ [[github.com](https://github.com/)] _account._

  If you chose options 1 or 2, create a sub-directory called `git-eqemulator` in the root directory of c: drive.

  If you chose option 3, create a sub-directory called `git-<git-username>` in the root directory of c: drive. (example: git username is `Pavlov`, directory name would be `git-pavlov`)

  The purpose of this directory is to facilitate code management. We'll refer to this as the `account` directory.

  For option 1:

  * Download [[Server-master.zip](https://github.com/EQEmu/Server/archive/master.zip)]

  * Place it inside of the `account` directory

  * Unpack its contents

  * Rename the local code directory from `Server-master` to `Server`

  * Move on to [[Download Dependencies](Ground-Up-Windows-Install-Rework#step-dependencies)]

  For options 2 & 3, go to the EQEmulator server code repository web page at [https://github.com/EQEmu/Server](https://github.com/EQEmu/Server)

  If you chose option 3 and are creating a fork, click on the fork button to add the repository to your github account. You should be redirected to your fork's main repository page.

  ![](https://user-images.githubusercontent.com/3311166/60550151-0e290280-9cf5-11e9-966e-e8d1fec1c80e.png)

  Finally, click the `Clone or download` button, then `Open in Desktop` button to create a local code repository on your computer. When prompted for where to create it, select the `account` directory created above.

  ![](https://user-images.githubusercontent.com/3311166/60550164-21d46900-9cf5-11e9-882b-439dea49c8e8.png)

  You should now have a managed local code repository on your computer.

  _Note: It is helpful to create a shortcut to the_ `account` _directory and place it on your desktop._

[](#step-dependencies)
* ### Download Dependencies

  Library dependencies can be downloaded from [[here](https://github.com/EQEmu/eqemu.github.com/raw/master/downloads/WindowsDependencies_x86.zip)].

  Inside of your local code directory, you will find a sub-directory called `dependencies`.

  Just place this download inside of the `dependencies` folder and unpack its contents.

* ### Running CMake

  CMake's default options are adequate to configure and generate the files needed for Visual Studio.

  There are two directory locations that you will need to provide:

  * `Where is the source code:`

  * `Where to build the binaries:`

  For the source code, type-in or navigate to your `c:/<account>/Server` directory.

  The easiest way to define the build directory is to copy the source path and paste it in. Then, add `/build` to the end of the path so that you have `c:/<account>/Server/build`.

  Once CMake knows where to look, click the `Configure` button. You will get a pop-up window stating that the `build` directory does not exist. Click `OK` to create it.

  The next window will be for compiler selection. Ensure that `Visual Studio 15 2017` is selected, then click `Finish` to proceed.

  ![](https://user-images.githubusercontent.com/3311166/60629799-3b44e600-9dc5-11e9-996a-df781b021d5c.png)

  You should now have a list of unconfigured options (in red) displayed in the main window of CMake:

  ![](https://user-images.githubusercontent.com/3311166/60629816-54e62d80-9dc5-11e9-89ab-8961e94c9491.png)

  The following list contains the most common options of interest to the majority of users:

  * `EQEMU_BUILD_CLIENT_FILES` [_enabled_] Builds binaries used to import/export client support files

  * `EQEMU_BUILD_LOGIN` [_disabled_] Builds the login server (this guide makes use of the login server - change this option to _enabled_)

  * `EQEMU_BUILD_LUA` [_enabled_] Compiles server code with Lua support

  * `EQEMU_BUILD_PERL` [_enabled_] Compiles server code with Perl support

  * `EQEMU_DEBUG_LEVEL` [_5_] Determines what additional messaging and debugging code is enabled/disabled (_12_ is max)

  * `EQEMU_ENABLE_BOTS` [_disabled_] Compiles server code with Bot support (user choice)

  _Note: Ensure that you set_ `EQEMU_BUILD_LOGIN` _to **enabled**_.

  Once you have set the options that you would like for your server, click `Configure` again.

  Since we set an option (login server) that requires additional settings, more unconfigured options have appeared. In this case, the open ssl library:

  ![](https://user-images.githubusercontent.com/3311166/60629837-67606700-9dc5-11e9-8b8c-560e629eae27.png)

  These new options are only file path definitions. No additional changes need to be made. Click `Configure` one last time.

  ![](https://user-images.githubusercontent.com/3311166/60629846-76471980-9dc5-11e9-9b30-d7059103ed89.png)

  _Note: Regardless of option settings, anytime that you have red (unconfigured) entries in your options list, you will need to click_ `Configure` _to ensure that the settings are applied to the current CMake file generation template._

  You can now click the `Generate` button.

  If file generation was successful, you should see "Generating done" at the bottom of the CMake window.

  You are now ready to open Visual Studio and compile your code!

* ### Compiling Code

  navigate through desktop shortcut to `c:\<account>\Server\build`

  right-click on `EQEmu.sln` and select `Open with` >> `Microsoft Visual Studio 2017`

  upon loading, Intellisense will begin mapping out the entire project. allow a few seconds for this process to finish. the lower left-hand corner will display "Ready" when this process has completed.

  Visual Studio does not honor CMake's `CMAKE_BUILD_TYPE` variable. You will need to manually set this to the desired build type before compiling your code.

  <!-- image of build type drop-down box -->

  There are 4 options:

  * `Debug` - not recommended for production servers unless conditions warrant its use (i.e., load testing and trouble-shooting)

  * `RelWithDebugInfo` - standard compile for production servers (provides debug symbols without the added overhead of extra code, memory buffers and stl assertions)

  * `Release` - similar to `RelWithDebugInfo`..but, without access to debug symbols (not recommended)

  * `MinSizeRel` - probably not a good selection (due to over optimization?)

  you may now click `compile`

  <!-- image of menu bar build option drop-down box -->

  the compiled code will be located in the `c:\<account>\Server\build\bin\<build_type>` directory

  [walk-through]

* ### Code Maintenance

  [final thoughts...]

---

## Local Server Setup


