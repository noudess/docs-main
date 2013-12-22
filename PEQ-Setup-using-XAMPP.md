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
* **Create the initial directory structure.** You should use one base EQEmu folder. I've selected c:\xampp\eqemu (from here on out identified as eqemu or server root folder). In your eqemu root folder, you should create folders called "logs", "quests", "Maps" (yes, capital "M"), "shared", and "source".

* **Get the server source.** Within your \eqemu\source folder, use TortoiseGit to clone the source files from https://github.com/EQEmu/Server.git into \eqemu\source\Server\. To do this, you can right-click inside your source folder and select "Git Clone...".

* **Get the dependencies.** In your \source\Server folder, you will find a folder named "dependencies". Put your boost, mysql_x86, and zlib_x86 folders inside the dependencies folder.

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
**Note:** If it identifies your MySQL dependencies in \xampp\mysql folder, you will need to manually change the location. To do this, select the Advanced checkbox to expand the configuration options in CMake. Scroll to the bottom and find the 3 entries for MySQL_INCLUDE_DIR, MySQL_LIBRARY_DEBUG, and MySQL_LIBRARY_RELEASE. Change the INCLUDE line to C:/xampp/eqemu/source/Server/dependencies/mysql_x86/include/ and the two LIBRARY lines to C:/xampp/eqemu/source/Server/dependencies/mysql_x86/lib/mysqlclient.lib. Uncheck the Advanced checkbox to finish configuring CMake.

  Now that CMake has done the initial check, you will need to configure a few more options so it can generate your build files. You should change/update these options:
  * CMAKE_BUILD_TYPE -> RelWithDebInfo
  * CMAKE_INSTALL_PREFIX -> C:/xampp/eqemu
  * EQEMU_BUILD_LUA -> Checked
  * EQEMU_BUILD_PERL -> Checked
  * EQEMU_BUILD_LOGIN -> Checked

  The rest should default to the appropriate settings. Now you can select "Configure" to let it finish finding the appropriate dependencies which should result in something like this:
```
Found Lua51: C:/Program Files (x86)/Lua/5.1/lib/lua51.lib (found version "5.1.4")
Boost version: 1.55.0
Configuring done
```
  There should be a new red-colored line, EQEMU_SANITIZE_LUA_LIBS. Select configure once again to let it finish configuration.

  **Note:** If there are any red-colored lines, correct any errors before moving to the next step!

  Now you can select "Generate" to create the build files. If there are no errors, you will get a "Generating done" message.

* **Build the source.** CMake should have created your \eqemu\source\Build folder. Inside, you can open your EQEmu.sln file to open VC 2013. Let the program initialize your project (i.e. scan includes and parse include files). When the program is "Ready", change the build from "Debug" to "RelWithDebInfo". It will continue to initialize your project. Select "Configuration Manager" and verify that the "Active solution configuration" is "RelWithDebInfo" and the "Active solution platform" is "Win32". In the "Build" column, check the "INSTALL" box and select "Close" (INSTALL will copy the executables to your eqemu root folder upon successful build). From the Build menu, select "Clean Solution" and verify 13 succeeded messages. Now select "Build Solution" and get a cup of coffee (or beer if you like). Once the build is complete, you should see 13 succeeded messages.

* **Get the database.** PEQ conducts a backup every day. The most up-to-date version can be found at http://peqtgc.com/releases. The file you need is peqbeta_(date-time).tar.gz. This database is usually synced with the most current EQEmu source. Unzip these files into a temporary location of your choice. Move the [[eqtime.cfg]] file into your eqemu root folder. Open a command prompt at your temporary location (shift-right-click the folder and select "Open command window here". Start MySQL (mysql -uroot -p peq) and source in the user_tables, peq_beta, and source_views SQL files. Do not go any further if there are any sourcing errors!

* **Get the quests.** PEQ uses [Google Code] (http://code.google.com/p/projecteqquests) to store their quests. Currently, there is a mix and match of Perl and Lua quests. Using TortosieSVN, checkout the quests into your \eqemu\quests folder (make sure it isn't \eqemu\quests\quests). Copy the plugins and lua_modules folders into your eqemu root folder. If you do not want to keep an SVN, you can download the daily quest dump from PEQ at http://peqtgc.com/releases.

* **Get the maps.** Your server will use the map files from EQ for in-game calculations. Currently, maps are stored at [Google Code] (http://code.google.com/p/eqemumaps). Using TortoiseSVN, checkout the maps into your \eqemu\Maps folder.

* **Get the database editor.** PEQ uses [Google Code] (http://code.google.com/p/peqphpeditor/) to store the PEQ Database Editor. Using TortoiseSVN, checkout the editor into your \xampp\htdocs\ folder as peqedit or whatever you wish to call it. Open the readme file for instructions setting the configuration for your editor.

* **Move the .conf files.** In your source, you need to copy/move the .conf files to your eqemu root folder. They are located at \source\Server\utils\patches. These files contain specific OPCODES your server needs to communicate with the clients.

* **Configure the server settings.** You will need to have the [[eqemu_config.xml]] file in your eqemu root folder. Also, you can edit your server variables using the database editor.

* **Take it for a test run.** It is a good idea to run each command one at a time the first time you launch your server to ensure you don't have any errors. Once you are sure everything works correctly, you can use [[start.bat]] to automate your server startup.
