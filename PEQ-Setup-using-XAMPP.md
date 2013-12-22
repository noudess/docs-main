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
1. **Get the server source.** In your XAMPP directory, create a folder to store your EQEmu files. I've selected c:\xampp\eqemu (from here on out identified as \eqemu or server folder). Within that folder (or other folder if you choose), create a source folder to store the EQEmu source code. Using TortoiseGit, clone the source files from https://github.com/EQEmu/Server.git into c:\xampp\eqemu\source\Server\. To do this, you can right-click inside your source folder and select "Git Clone...".
2. **Configure the source with CMake.**
3. **Build the source.**
4. **Get the database.** PEQ conducts a backup every day. The most up-to-date version can be found at http://peqtgc.com/releases. The file you need is peqbeta_(date-time).tar.gz. This database is usually synced with the most current EQEmu source.
5. **Get the quests.** PEQ uses [Google Code] (http://code.google.com/p/projecteqquests) to store their quests. Currently, there is a mix and match of Perl and Lua quests. Using TortosieSVN, checkout the quests folder into your \eqemu\quests folder. Copy the plugins and lua_modules folders into your \eqemu folder. If you do not want to keep an SVN, you can download the daily quest dump from PEQ at http://peqtgc.com/releases.
6. **Get the maps.** Your server will use the map files from EQ for in-game calculations. Currently, maps are stored at [Google Code] (http://code.google.com/p/eqemumaps). Using TortoiseSVN, checkout the maps folder to your \eqemu\Maps folder (yes, capital "M").
7. **Get the database editor.** PEQ uses [Google Code] (http://code.google.com/p/peqphpeditor/) to store the PEQ Database Editor. Using TortoiseSVN, checkout the editor into your xampp\htdocs\peqedit folder (or whatever you wish to call it).
8. **Get the .conf files.** In your source, you need to copy/move the .conf files to your \eqemu root folder. They are located at \source\Server\utils\patches. These files contain specific OPCODES your server needs to communicate with the clients.
9. **Configure the server settings.** You will need to have the [eqemu_config.xml] file in your \eqemu root folder. Also, you can edit your server variables using the database editor.
10. **Take it for a test run.** It is a good idea to run each command one at a time the first time you launch your server to ensure you don't have any errors. Once you are sure everything works correctly, you can use [start.bat] to automate your server startup.