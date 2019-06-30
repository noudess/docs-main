#### This guide is intended for advanced users who want to configure EQEmu "from the ground up" for a windows server. It is not the recommended route, we suggest using the [[Windows-Server]] install instead for most cases.

* These steps assume you will be using a 64bit environment.

### Download Dependencies

* *Note:* Any "temp link" is hosted on a personal repository is not recommended as a primary source.
* ActivePerl 5.16.3. EQEmu hosts a copy [link](https://raw.githubusercontent.com/EQEmu/eqemu.github.com/master/downloads/ActivePerl-5.16.3.1604-MSWin32-x64-298023.msi)
* Boost 1.58 [link](https://sourceforge.net/projects/boost/files/boost/1.58.0/boost_1_58_0.zip/download)
* MySQL (version?) [temp link](https://github.com/xackery/eqemu/releases/download/v0.02/mysql_x64.zip)
* LuaJIT 2.0.1 [link](http://luajit.org/download.html)
* Zlib 1.2.5 [temp link](https://github.com/xackery/eqemu/releases/download/v0.02/zlib_x64.zip)
* LibSodium (version?) [temp link](https://github.com/xackery/eqemu/releases/download/v0.02/libsodium.zip)

### Extract Dependencies

* ActivePerl - will extract by default to c:\Perl64. Any directory is fine, it uses environment variables to help detect it's location during cmake steps. 
* Boost - extract to a temporary directory, and look inside the zip file for the boost subdirectory. (first folder listed should be accumulators). Copy this folder into your dependencies so it reads: \dependencies\boost\boost\<accumulators, etc>.
* MySQL - extract the folder into your dependencies so it reads: \dependencies\mysql_x64\<include, lib>

### Install Visual Studio

* Visual Studio 2017 Community Edition is free [link](https://visualstudio.microsoft.com/downloads/)
* Once installed, Open up Visual Studio and select New Project -> Visual C++ (MFC). If it lets you select this option without an optional download, you should be good to go. If it does ask you to install the C++ essential files, say yes. Wait for it to download, then you can cancel out of the new project steps.

### Run Cmake & Build

* Download and Run Cmake 3.12.0 [link](https://cmake.org/download/)
* Set the "Where is the source code" directory to the root of your eqemu\server directory.
* Set the "Where to build the binaries" directory to eqemu\server\build, or you can customize this if preferred.
* Press Configure. A dialog pops up, choose the `Visual Studio 15 2017 Win64` option. You may get warnings in the output on bottom, and the debug list may turn red, but as long as no errors are hit, you should be fine.
* Press Generate. If the generate button is disabled, review the output log when you hit configure to figure out why.
* Press Open Project. This should open Visual Studio.
* Press F6 or Build -> Build Solution to begin compiling. You'll see yellow text warnings but they can be ignored. Eventually, the output window should display all successful with no fails.

### Add Dependencies To Your Bin Directory

* Your bin directory by default is a subfolder of your build directory configured during cmake based on the compile type, e.g. \eqemu\server\build\debug\bin may be where it's at.
* MySQL - Copy \dependencies\mysql_x64\lib\libmysql.dll to your bin directory
* LibSodium - Copy \dependencies\libsodium\libsodium.dll to your bin directory

### Install MySQL

* You need a running instance of MySQL in order to connect your database. You have two options:
* *Option 1* Download MySQL and install to your computer [link](https://www.mysql.com/downloads/)
* *Option 2* Use docker-compose to dockerize your MySQL installation [link](https://gist.github.com/xackery/d93e05825b2db74425086bde617ac635). (Note: This requires Windows 10 Pro+ And [Docker](https://store.docker.com/editions/community/docker-ce-desktop-windows) installed so it may not be for every environment)
* *If Option 2*, download the docker-compose.yml file in a location of your choice. Create a sub directory called db. Go to a command line in this directory, and type `docker-compose up`, and it will spin up the container for you, exposing the ports to 127.0.0.1:3306 with credentials on the config file.

### Inject Your Database, Finalize preparation

* TODO: Finish writing this, and find a baseline schema to inject
* TODO: download eqemu_config.json steps
* TODO: run shared_memory.exe
* TODO: run world or zone.
* TODO: Optional stuff like start.bat scripts etc

[*end original*]

[*begin test*]

* This guide provides instructions for compiling 32-bit Windows server binaries and setting up a local development server *


*** Compile Setup ***


* Verify Environmental Variable %PATH% *

** need to develop criteria


* Required Programs *

Some of the pre-requisits for compiling binaries are the same as running a server.

If you have already installed any of the following, the download and installation requirement should be omitted:

- Visual Studio 2017 (Community Edition) [<a href="https://visualstudio.microsoft.com/vs/older-downloads/">select 2017 community edition</a>]

- MariaDB [<a href="https://downloads.mariadb.org/interstitial/mariadb-10.4.6/winx64-packages/mariadb-10.4.6-winx64.msi/from/http%3A//mirror.nodesdirect.com/mariadb/">download</a>]

- Perl [<a href="https://github.com/EQEmu/eqemu.github.com/raw/master/downloads/ActivePerl-5.12.3.1204-MSWin32-x86-294330.msi">download</a>]

- CMake [<a href="https://github.com/Kitware/CMake/releases/download/v3.14.5/cmake-3.14.5-win64-x64.msi">download</a>]

- Git (see notes under install) [<a href="https://git-scm.com/download/win">download</a>]

- TortoiseGit (optional - see notes under install) [<a href="https://download.tortoisegit.org/tgit/2.8.0.0/TortoiseGit-2.8.0.0-64bit.msi">download</a>]


* Install Visual Studio *

During the install process, double-check the option for c++ command-line compiler. This is required by CMake to determine available compiler options. CMake file generation will fail if this option is not enabled.

Microsoft allows Visual Studio use for a 30-day trial period without registration of the product. Simply create an account at [*process change*] and enter the credentials in Visual Studio when prompted. The account is free and the license is usually valid for 1-2 years.


* Install MariaDB *

** need specifics on what settings to use **

At the end of the installation process, you will be prompted to install HeidiSQL. It is HIGHLY recommended that you install this program.


* Install Perl 5.12.3 (32-bit) *

This installation is self-explanatory. It is recommended that you install in the root directory ("c:\") to avoid possible issues.


* Install CMake *

This installation is self-explanatory.


* Install Git *

This installation is self-explanatory.

Should you wish to download the repository code with no further chance of updating or restoration, this requirement may be omitted.


* Install TortoiseGit (optional) *

This installation is self-explanatory.

If Git is not installed, this installation should be omitted.


* Restart Computer *

At this point, you will want to restart your computer to ensure that all of the %PATH% additions are loaded into memory.


* Acquiring the Code *

At this point, you will need to make a decision on how you want to manage your code.

There are three options:

- Option 1, Retrieve the code as a one-time download (not recommended)

- Option 2, Create a local repository from the parent EQEmulator project that can be updated, managed and maintained (recommended)

- Option 3, Create a local repository from a fork of the EQEmulator project that you manage (recommended only if you want to contribute back to the parent project)

If you choose to create a fork of the EQEmulator repository, you will need to create a [<a href="https://github.com/">github.com</a>] account.

[walk-through for option 2]


* Download Dependencies *

Library dependencies can be downloaded directly from [<a href="https://github.com/EQEmu/eqemu.github.com/raw/master/downloads/WindowsDependencies_x86.zip">here</a>].

Inside of your local code directory, you will need to create a sub-directory called 'dependencies` and unzip the download's contents into it.


* Running CMake *

[walk-through]


* Compiling Code *

[walk-through]


*** Local Server Setup ***

[*end test*]