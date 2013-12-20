##### Guide Information
This guide was created to help you set up a basic PEQ server with the current database and quests. My system is Windows 7 x64 with XAMPP. I use XAMPP because it is a good all-in-one package which includes MySQL, Apache, PHP, and Perl. This was compiled as 32-bit using Microsoft Visual Studio Express 2013 for Windows Desktop. In addition to the server, we will also set up the PEQ Database Editor. The guide is generic enough so you can tweak the steps to fit your specific requirements/system.

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

##### The Walk-Thru
1. Get the server source.
2. Configure the source with CMake.
3. Build the source.
4. Get the database.
5. Get the database editor.
6. Configure the server settings.
7. Take it for a test run.