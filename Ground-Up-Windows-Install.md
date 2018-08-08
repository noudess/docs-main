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
* Once installed, Open up Visual Studio and select New Project -> Visual C++ (MFC). If it lets you select this option without an optional download, you should be good to go. If it does ask you to install the C++ essential files, yes say. You can cancel out without creating a project at this time.

### Run Cmake & Build

* Download and Run Cmake 3.12.0 [link](https://cmake.org/download/)
* Set the "Where is the source code" directory to the root of your eqemu\server directory.
* Set the "Where to build the binaries" directory to eqemu\server\build, or you can customize this if preferred.
* Press Configure. You may get warnings in the output on bottom, and the debug list may turn red, but as long as no errors are hit, you should be fine.
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
* *Option 2* Use docker-compose to dockerize your MySQL installation [link](https://gist.github.com/xackery/d93e05825b2db74425086bde617ac635). 
* *If Option 2*, download and run the docker-compose.yml file in a location of your choice. Create a sub directory called db. type in the command line `docker-compose up`, and it will spin up the container for you.

### Inject Your Database, Finalize preparation

* TODO: Finish writing this, and find a baseline schema to inject
* TODO: download eqemu_config.json steps
* TODO: run shared_memory.exe
* TODO: run world or zone.
* TODO: Optional stuff like start.bat scripts etc

