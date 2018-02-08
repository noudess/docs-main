We have an automated way for pulling down certain assets and maintaining parts of the server

The main script we use for this is **eqemu_server.pl** in the server folder

**eqemu_server.pl** is a required part of the server binary set. 

World will download a fresh copy on bootup and then run the script to make sure no database schema updates need to be ran, it also does a handful of other very powerful things

### Looking at the eqemu_server menu

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

### The Assets Menu

* The assets menu will show a variety of options depending on what OS you are running the script on (Windows or Linux)

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

* You can type 'maps' to interactively download maps in the script, or you can also just run:

```perl eqemu_server.pl maps```

Same thing goes for **perl eqemu_server.pl opcodes** or any other command

### Updating Windows Binaries - Stable

* **perl eqemu_server.pl windows_server_download** will download EQEmu development team approved 'stable' binaries - you can check the date on the files as to when they were built

### Updating Windows Binaries - Unstable - Latest

* **perl eqemu_server.pl windows_server_latest** - will download the latest compiled binaries from our **AppVeyor CI integration**

### New Server Option

* This command is detailed and used in [[Development Server Setup]]