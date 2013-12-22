##### Guide Information
This guide (still in progress) was created to help you set up a basic PEQ server with the current database and quests. My system is Windows 7 x64 with XAMPP. I use XAMPP because it is a good all-in-one package which includes MySQL, Apache, PHP, and Perl. This was compiled as 32-bit using Microsoft Visual Studio Express 2013 for Windows Desktop. In addition to the server, we will also set up the PEQ Database Editor. The guide should be broad enough so you can tweak the steps to fit your specific requirements/system.

***

##### Required Programs, Libraries, and Dependencies
* [[XAMPP|XAMPP-for-Windows]]
* [[Microsoft VC++ Runtime Libraries|Microsoft-Visual-C-Plus-Plus-Runtime-Libraries]]
* [[Perl 5.12|ActivePerl-5.12]]
* [[VS Express 2013 for Desktop|Visual-Studio-Express-2013-for-Windows-Desktop]]
* [[TortoiseGit|TortoiseGit]]
* [[TortoiseSVN|TortoiseSVN]]
* [[Boost 1.55|Boost]]
* [[Lua 5.1|Lua-for-Windows]]
* [[CMake 2.8|CMake-for-Windows]]
* [[MySQL and ZLIB Dependencies|MySQL-and-ZLIB-Dependencies]]

##### Recommended Programs
* [[Notepad++|Notepad-Plus-Plus]]
* [[WinRAR|winrar]]

***

##### The Walk-Thru
* **Get the server source.** In your XAMPP directory, create a folder to store your EQEmu files. I've selected c:\xampp\eqemu (from here on out identified as \eqemu or server folder). Within that folder (or other folder if you choose), create a source folder to store the EQEmu source code. Using TortoiseGit, clone the source files from https://github.com/EQEmu/Server.git into c:\xampp\eqemu\source\Server\. To do this, you can right-click inside your source folder and select "Git Clone...".
* **Get the dependencies.** In your \source\Server folder, you will find a folder named "dependencies". Inside, put in your boost, mysql_x86, and zlib_x86 folders/files.
* **Configure the source with CMake.** The first time you run CMake, you will need to specify where the source code is located and where to build the binaries. Use the "Browse Source" button to locate your \source\Server folder. Use the "Browse Build" button to create a \source\Build folder. It will ask you to identify your default compiler. If you installed VC++ correctly, it will identify Visual Studio 12 (confusing, but VC 2013 is VS12) as the default native compiler. Select "Finish" to start the intial check by CMake. It will check your compiler identification and search for existing dependencies. The output should look something like this:
```
The C compiler identification is MSVC 18.0.21005.1
The CXX compiler identification is MSVC 18.0.21005.1
Check for working C compiler using: Visual Studio 12
Check for working C compiler using: Visual Studio 12 -- works
Detecting C compiler ABI info
Detecting C compiler ABI info - done
Check for working CXX compiler using: Visual Studio 12
Check for working CXX compiler using: Visual Studio 12 -- works
Detecting CXX compiler ABI info
Detecting CXX compiler ABI info - done
Looking for include file stdint.h
Looking for include file stdint.h - found
Found ZLIB: C:/xampp/eqemu/source/Server/dependencies/zlib_x86/lib/zdll.lib (found version "1.2.3") 
Found MySQL: c:/xampp/eqemu/source/Server/dependencies/mysql_x86/lib/mysqlclient.lib  
Found Perl: C:/xampp/perl/bin/perl.exe (found version "5.12.3") 
Found PerlLibs: C:/xampp/perl/lib/CORE/perl512.lib (found version "5.12.3") 
Configuring done
```
**Note:** If it identifies your MySQL dependencies in \xampp\mysql folder, you will need to manually change the location. To do this, select the Advanced checkbox to expand the configuration options in CMake. Scroll to the bottom and find the 3 entries for MySQL_INCLUDE_DIR, MySQL_LIBRARY_DEBUG, and MySQL_LIBRARY_RELEASE. Change the INCLUDE line to **C:/xampp/eqemu/source/Server/dependencies/mysql_x86/include/** and the two LIBRARY lines to **C:/xampp/eqemu/source/Server/dependencies/mysql_x86/lib/mysqlclient.lib**. Uncheck the Advanced checkbox to finish configuring CMake.

  Now that CMake has done the initial check, you will need to configure a few more options so it can generate your build files. You should change/update these options:
  * CMAKE_BUILD_TYPE - RelWithDebInfo
  * CMAKE_INSTALL_PREFIX - C:/xampp/eqemu
  * EQEMU_BUILD_LUA - Checked
  * EQEMU_BUILD_PERL - Checked

* **Build the source.**
* **Get the database.** PEQ conducts a backup every day. The most up-to-date version can be found at http://peqtgc.com/releases. The file you need is peqbeta_(date-time).tar.gz. This database is usually synced with the most current EQEmu source.
* **Get the quests.** PEQ uses [Google Code] (http://code.google.com/p/projecteqquests) to store their quests. Currently, there is a mix and match of Perl and Lua quests. Using TortosieSVN, checkout the quests folder into your \eqemu\quests folder. Copy the plugins and lua_modules folders into your \eqemu folder. If you do not want to keep an SVN, you can download the daily quest dump from PEQ at http://peqtgc.com/releases.
* **Get the maps.** Your server will use the map files from EQ for in-game calculations. Currently, maps are stored at [Google Code] (http://code.google.com/p/eqemumaps). Using TortoiseSVN, checkout the maps folder to your \eqemu\Maps folder (yes, capital "M").
* **Get the database editor.** PEQ uses [Google Code] (http://code.google.com/p/peqphpeditor/) to store the PEQ Database Editor. Using TortoiseSVN, checkout the editor into your xampp\htdocs\peqedit folder (or whatever you wish to call it).
* **Get the .conf files.** In your source, you need to copy/move the .conf files to your \eqemu root folder. They are located at \source\Server\utils\patches. These files contain specific OPCODES your server needs to communicate with the clients.
* **Configure the server settings.** You will need to have the [[eqemu_config.xml]] file in your \eqemu root folder. Also, you can edit your server variables using the database editor.
* **Take it for a test run.** It is a good idea to run each command one at a time the first time you launch your server to ensure you don't have any errors. Once you are sure everything works correctly, you can use [[start.bat]] to automate your server startup.