We have an automated way for pulling down certain assets and maintaining parts of the server

The main script we use for this is **eqemu_server.pl** in the server folder

**eqemu_server.pl** is a required part of the server binary set. 

World will download a fresh copy on bootup and then run the script to make sure no database schema updates need to be ran, it also does a handful of other very powerful things

## EQEmu Server Menu

* First start by going to your server directory and either running the script and going into the interactive prompt, or you can run commands to do things that you would like the script to do

```C:\EQEmu\servers\peq_server>perl eqemu_server.pl
[Update] No script update necessary...

>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
>>> EQEmu Server Main Menu >>>>>>>>>>>>
>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>

 [database]     Enter database management menu
 [assets]       Manage server assets
 [new_server]   New folder EQEmu/PEQ install - Assumes MySQL/Perl installed
 [setup_bots]   Enables bots on server - builds code and database requirements

 exit

Enter a command #>
```

## Assets Menu

* The assets menu will show a variety of options depending on what OS you are running the script on (Windows or Linux)

Example: perl eqemu_server.pl maps

```>>> Server Assets Menu

 [maps]                 Download latest maps
 [opcodes]              Download opcodes (Patches for eq clients)
 [quests]               Download latest quests
 [plugins]              Download latest plugins
 [lua_modules]          Download latest lua_modules
 [utility_scripts]      Download utility scripts to run and operate the EQEmu Server
>>> Windows
 [windows_server_download]      Updates server via latest 'stable' code
 [windows_server_latest]        Updates server via latest commit 'unstable'
 [windows_server_download_bots] Updates server (bots) from latest 'stable'
 [fetch_dlls]                   Grabs dll's needed to run windows binaries
 [setup_loginserver]            Sets up loginserver for Windows
```
### Asset Commands

| Command        | Action  |
| ------------- |-------------|
|  maps| Download latest maps |
|  opcodes| Download latest opcodes (Patches for eq clients) |
|  quests| Download latest quests  |
|  plugins| Download latest plugins  |
|  lua_modules| Download latest lua_modules  |
|  utility_scripts| Download utility scripts|
|  setup_loginserver | Windows Loginserver setup |
|  linux_login_server_setup | Loginserver setup for Linux |

### Database Maintenance Commands

| Command        | Action  |
| ------------- |-------------|
|  backup_database| Back up database to backups/ |
|  backup_database_compressed| Back up database (zip/tar) to backups/ |
|  backup_player_tables| Backs up only player tables to backsup/ |
|  check_db_updates| Checks for database updates manually (should not be needed) |
|  check_bot_db_updates| Checks for bot database updates manually (should not be needed) |
|  remove_duplicate_rules| Older databases used to have tons of duplicate rules - this can be ran to purge them for the new inheritance rules|
|  drop_db_bots_schema| Removes bot database schema|

### Updating Windows Binaries - Stable

* **perl eqemu_server.pl windows_server_download** will download EQEmu development team approved 'stable' binaries - you can check the date on the files as to when they were built

Example:

```perl eqemu_server.pl windows_server_download
[Copy] folder doesn't exist, creating 'updates_staged/'
[Update] No script update necessary...
[Update] Fetching Latest Windows Binaries...
[Download] Saved: (updates_staged/master_windows_build.zip) from https://raw.githubusercontent.com/Akkadius/EQEmuInstall/master/master_windows_build.zip
[Update] Fetched Latest Windows Binaries...
[Update] Extracting... ---
[Unzip] Extracting...
[Update] Installing :: common.lib
[Update] Installing :: eqlaunch.exe
[Update] Installing :: eqlaunch.ilk
[Update] Installing :: eqlaunch.pdb
[Update] Installing :: export_client_files.exe
[Update] Installing :: export_client_files.ilk
[Update] Installing :: export_client_files.pdb
[Update] Installing :: import_client_files.exe
[Update] Installing :: import_client_files.ilk
[Update] Installing :: import_client_files.pdb
[Update] Installing :: libeay32.dll
[Update] Installing :: libsodium.dll
[Update] Installing :: loginserver.exe
[Update] Installing :: loginserver.ilk
[Update] Installing :: loginserver.pdb
[Update] Installing :: luabind.lib
[Update] Installing :: queryserv.exe
[Update] Installing :: queryserv.ilk
[Update] Installing :: queryserv.pdb
[Update] Installing :: shared_memory.exe
[Update] Installing :: shared_memory.ilk
[Update] Installing :: shared_memory.pdb
[Update] Installing :: ucs.exe
[Update] Installing :: ucs.ilk
[Update] Installing :: ucs.pdb
[Update] Installing :: world.exe
[Update] Installing :: world.ilk
[Update] Installing :: world.pdb
[Update] Installing :: zone.exe
[Update] Installing :: zone.ilk
[Update] Installing :: zone.pdb
[Update] Done
```

### Updating Windows Binaries - Unstable - Latest

* **perl eqemu_server.pl windows_server_latest** - will download the latest compiled binaries from our **AppVeyor CI integration**

Example:

```perl eqemu_server.pl windows_server_latest
[Update] No script update necessary...
[Update] Fetching Latest Windows Binaries (unstable) from Appveyor...
[Download] Saved: (updates_staged/master_windows_build_pdb.zip) from https://ci.appveyor.com/api/projects/KimLS/server/artifacts/build_x86_pdb.zip
[Download] Saved: (updates_staged/master_windows_build.zip) from https://ci.appveyor.com/api/projects/KimLS/server/artifacts/build_x86.zip
[Update] Fetched Latest Windows Binaries (unstable) from Appveyor...
[Update] Extracting... ---
[Unzip] Extracting...
[Unzip] Extracting...
[Update] Installing :: eqlaunch.exe
[Update] Installing :: eqlaunch.pdb
[Update] Installing :: export_client_files.exe
[Update] Installing :: export_client_files.pdb
[Update] Installing :: import_client_files.exe
[Update] Installing :: import_client_files.pdb
[Update] Installing :: loginserver.exe
[Update] Installing :: loginserver.pdb
[Update] Installing :: queryserv.exe
[Update] Installing :: queryserv.pdb
[Update] Installing :: shared_memory.exe
[Update] Installing :: shared_memory.pdb
[Update] Installing :: tests.exe
[Update] Installing :: tests.pdb
[Update] Installing :: ucs.exe
[Update] Installing :: ucs.pdb
[Update] Installing :: world.exe
[Update] Installing :: world.pdb
[Update] Installing :: zone.exe
[Update] Installing :: zone.pdb
[Update] Done
```

### New Server Option

* This command is detailed and used in [[Development Server Setup]]