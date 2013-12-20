##### Guide Information
This guide was created to help you set up a basic PEQ server with the current database and quests. My system is Windows 7 x64 with XAMPP. I use XAMPP because it is a good all-in-one package which includes MySQL, Apache, PHP, and Perl. This was compiled as 32-bit using Microsoft Visual Studio 2013 Express for Desktop. In addition to the server, we will also set up the PEQ Database Editor. The guide is generic enough so you can tweak the steps to fit your specific requirements/system.

##### Required Programs
* [[XAMPP|XAMPP-for-Windows]]
* [[Microsoft VC++ Runtime Libraries|Microsoft-Visual-C---Runtime-Libraries]]
* [[Perl 5.12|ActivePerl-5.12]]
* [[Visual Studio Express 2013 for Windows Desktop|Visual-Studio-Express-2013-for-Windows-Desktop]]
* [[TortoiseGit|TortoiseGit]]
* [[TortoiseSVN|TortoiseSVN]]
* [[Boost 1.55|boost]]
* [[Lua 5.1|lua-windows]]
* [[CMake 2.8|cmake-windows]]

##### Recommended Programs
* [[Notepad++|notepad-plusplus]]
* [[WinRAR|winrar]]

##### The Walk-Thru
1. Get the server source.
2. Configure the source with CMake.
3. Build the source.
4. Get the database.
5. Get the database editor.
6. Configure the server settings.
7. Take it for a test run.