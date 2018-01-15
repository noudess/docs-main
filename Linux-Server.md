
### Starting the Linux Installer

* First you will need to kick off the installer using the single line command line also referenced on the README in the EQEmu/Server repository

### > Debian/Ubuntu/CentOS/Fedora

* You can use curl or wget to kick off the installer (whichever your OS has)
> curl -O https://raw.githubusercontent.com/EQEmu/Server/master/utils/scripts/linux_installer/install.sh install.sh && chmod 755 install.sh && ./install.sh

> wget --no-check-certificate https://raw.githubusercontent.com/EQEmu/Server/master/utils/scripts/linux_installer/install.sh -O install.sh && chmod 755 install.sh && ./install.sh

### Enter Environment Parameters

* The Linux installer has configurable options
  * EQEmu User: eqemu - set password
  * MySQL root password
  * MySQL database name
  * MySQL new user name and password

```
root@debian:/home/eqemu# wget --no-check-certificate https://raw.githubusercontent.com/EQEmu/Server/master/utils/scripts/linux_installer/install.sh -O install.sh && chmod 755 install.sh && ./install.sh
--2018-01-15 11:34:02--  https://raw.githubusercontent.com/EQEmu/Server/master/utils/scripts/linux_installer/install.sh
Resolving raw.githubusercontent.com (raw.githubusercontent.com)... 151.101.148.133
Connecting to raw.githubusercontent.com (raw.githubusercontent.com)|151.101.148.133|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 10617 (10K) [text/plain]
Saving to: ‘install.sh’

install.sh                           100%[========================================================================>]  10.37K  --.-KB/s   in 0s

2018-01-15 11:34:03 (122 MB/s) - ‘install.sh’ saved [10617/10617]

#########################################################
#::: EverQuest Emulator Modular Installer
#::: Installer Author: Akkadius
#::: Installer Co-Author(s): N0ctrnl
#:::
#::: EQEmulator Server Software is developed and maintained
#:::    by the EQEmulator Developement team
#:::
#::: Everquest is a registered trademark
#::: Daybreak Game Company LLC.
#:::
#::: EQEmulator is not associated or
#::: affiliated in any way with Daybreak Game Company LLC.
#########################################################
#:
#########################################################
#::: To be installed:
#########################################################
- Server running folder - Will be installed to the folder you ran this script
- MariaDB (MySQL) - Database engine
- Perl 5.X :: Scripting language for quest engines
- LUA Configured :: Scripting language for quest engines
- Latest PEQ Database
- Latest PEQ Quests
- Latest Plugins repository
- Maps (Latest V2) formats are loaded
- New Path files are loaded
- Optimized server binaries
#########################################################
Press any key to continue...
First, we need to set your passwords...
Make sure that you remember these and keep them somewhere


Enter new UNIX password:
Retype new UNIX password:
passwd: password updated successfully
mkdir: cannot create directory ‘/home/eqemu’: File exists
Enter MySQL root (Database) password: eqemu
Enter Database Name (single word, no special characters, lower case):eqemu
Enter (Database) MySQL EQEmu Server username: eqemu
Enter (Database) MySQL EQEmu Server password: eqemu
```
* Once complete, the installer will take off and do the rest, and you can just sit back and wait for it to complete! 
* Note: Compiling takes a little while because of compiling happening on a single core, this is because not all servers that the installer runs on has proper memory configured for the amount of processor jobs that could be ran to speed up this process

### Starting the Server

* Once the installation is complete, you will have the following directory structure in /home/eqemu
```
root@debian:/home/eqemu# ls -l
total 24
-rwxr-xr-x 1 eqemu eqemu 10617 Jan 15 11:34 install.sh
drwxr-xr-x 9 eqemu eqemu  4096 Jan 15 11:46 server
drwxr-xr-x 3 eqemu eqemu  4096 Jan 15 11:34 server_source
drwxr-xr-x 2 eqemu eqemu  4096 Jan 15 11:34 source
root@debian:/home/eqemu# cd server
```
* Once in the server you can use either of the start scripts to start your server, and the stop script of course to stop the server

```

 - server_start.sh        Starts EQEmu server (Quiet) with 30 dynamic zones, UCS & Queryserv, dynamic zones
 - server_start_dev.sh    Starts EQEmu server with 10 dynamic zones, UCS & Queryserv, dynamic zones all verbose
 - server_stop.sh         Stops EQEmu Server (No warning)
 - server_status.sh       Prints the status of the EQEmu Server processes
```
* Startup example
```
root@debian:/home/eqemu/server# ./server_start.sh
[Status] Loading items...
[Status] Loading factions...
[Status] Loading loot...
[Status] Loading skill caps...
[Status] Loading spells...
[Status] Loading base data...
Server started - use server_status.sh to check server status

root@debian:/home/eqemu/server#
Akka's Linux Server Launcher
Zones to launch: 30
Launcher already running... Exiting...

root@debian:/home/eqemu/server# ./server_status.sh

Akka's Linux Server Launcher
World: UP Zones: (30/30) UCS: UP Queryserv: UP
```
### Basic Server Configuration

* To configure your server name, shortname and other parameters, you can visit [[eqemu_config]]
* To configure additional zones to boot, those options can be set in the startup script

That's it! You should be set!