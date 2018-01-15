### Compatibility:

* Windows 7 - x64
* Windows 8 - x64
* Windows 10 - x64
* Windows Server 2012 - x64

### Requirements

*   This installer assumes you have a clean install of Windows
*   Internet Connection

### Runtime
*   2-10 minute install depending on your connection

## What's in the Installer

*   **Perl 5.12.3**
    *   Perl DBI (Database Integration)
*   **MariaDB x64 10.0.0** \- Optimized MySQL configuration
    *   Heidi SQL (Comes with MariaDB)
*   **Latest PEQ Database** and automatically updated with the installer
*   **Latest PEQ Quests**
*   **Latest Plugins repository**
*   **Visual Studio** runtimes
*   **Automatically added firewall rules**
*   **V2 Server Side Maps**
*   **Path Files**
*   **LUA**
*   **Optimized and latest server binaries (Stable)**
*   **Loginserver:**
    *   The server is configured to use the **EQEmu Public Loginserver**
    *   You can also install a local loginserver for **LAN play**

## Server Installation

 1. First you will need to download the starter files that will kick off the installation process

*   [EQEmu Server Installer Files](http://wiki.eqemulator.org/eqemu_installer_files.zip)

![image](https://user-images.githubusercontent.com/3319450/34912524-61f9eff6-f8a9-11e7-8028-2283d0347167.png)


2\. Once you have the files downloaded, you need to make a folder somewhere that you would like your server to reside, the place I chose is **C:\\EQEmuServer**

3\. Extract the files inside **eqemu\_installer\_files.zip** to this folder

4\. Once extracted, right click **eqemu_install.bat** and **"Run as Administrator"**, from this point on the entire install will be automated and run on its own, this is assuming you have an internet connection so the installer can pull down all of the necessary server assets

![image](https://user-images.githubusercontent.com/3319450/34912527-6e97d462-f8a9-11e7-981f-6a60ba0fbdea.png)


## Installation Details

*   **MariaDB installed**
    *   **User**: root (Doesn't allow remote connections)
    *   **Password:** eqemu
*   **Folders created:**
    *   logs
    *   updates_staged
    *   shared
*   **Map files (maps/)**
*   **Opcode files (patch_*.conf)**
*   **Plugins (plugins/)**
*   **Quests (quests/)**
*   **LUA Modules (lua_modules/)**
*   **Pre-requisite .dll files (lua511.dll, zlib1.dll, libmysql.dll)**
*   **Server Scripts**
    *   t\_database\_backup.bat
    *   t\_server\_crash_report.pl
    *   t\_start\_server.bat
    *   t\_start\_server\_with\_login_server.bat
    *   t\_stop\_server.bat
*   **PEQ Database Downloaded and automatically updated, database created as name: "peq"**
*   **Windows Firewall rules added**
    *   **Ports 9000, 7000-7500**

![image](https://user-images.githubusercontent.com/3319450/34912555-f02fc548-f8a9-11e7-928a-172977e140d3.png)


When the installation process is done running, you will see **"press any key to continue"** once the final step of adding firewall rules has been complete that's when everything should be installed and ready to go.

Change your server name in **eqemu_config.json**, **shortname/longname** is currently set to:

*   **Akka's Server Installer (Change Name)**

At this point you can use:

*   **t\_start\_server.bat** to start the server
*   **t\_stop\_server.bat** to stop the server

You are good to go!

## Loginserver Installation

* The windows installer already pulls down pre-compiled Loginserver binaries, but if you need to download them again for any reason, you can issue the following command:
```
perl eqemu_server.pl setup_loginserver

[Install] Fetching Loginserver...
[Copy] folder doesn't exist, creating 'updates_staged/'
[Download] Saved: (updates_staged/login_server.zip) from https://raw.githubusercontent.com/Akkadius/EQEmuInstall/master/login_server.zip
[Install] Extracting...
[Unzip] Extracting...
[Install] Installing :: EQEmuAuthCrypto.dll
[Install] Installing :: login.ini
[Install] Installing :: loginserver.exe
[Install] Installing :: loginserver.ilk
[Install] Installing :: loginserver.pdb
[Install] Installing :: login_opcodes.conf
[Install] Installing :: login_opcodes_sod.conf
[Install] Done...
[Install] Pulling down Loginserver database tables...
[Download] Saved: (db_update/login_server_tables.sql) from https://raw.githubusercontent.com/Akkadius/EQEmuInstall/master/login_server_tables.sql
[Install] Installing Loginserver tables...
[Install] Done...
[Install] Found existing rule :: EQEmu Loginserver (SOD+) (5999) UDP
[Install] Found existing rule :: EQEmu Loginserver (SOD+) (5999) TCP
[Install] Found existing rule :: EQEmu Loginserver (Titanium) (5998) UDP
[Install] Found existing rule :: EQEmu Loginserver (Titanium) (5998) TCP
If firewall rules don't add you must run this script (eqemu_server.pl) as administrator

[Install] Instructions
[Install] In order to connect your server to the loginserver you must point your eqemu_config.json to your local server similar to the following:

"loginserver2" : {
	"account" : "",
	"host" : "192.168.197.129",
	"password" : "",
	"port" : "5998"
},

[Install] When done, make sure your EverQuest client points to your loginserver's IP (In this case it would be 127.0.0.1) in the eqhosts.txt file
[Install] Press any key to continue...
```

#### Loginserver Settings

*   Keep in mind, that the loginserver is setup for convenient **LAN purposes**, so that you can use your **EverQuest client to login to the Loginserver**, if you don't have a **Loginserver account created**, it will use the username and password you typed in trying to login and automatically create an account which you can use from then on out via the **login.ini** option **"auto\_create\_accounts"**

`auto_create_accounts = TRUE`

*   The installer is configured to connect to the **EQEmu Public loginserver** and the **local loginserver** that you may or may not use, so you can use both methods of logging into your server that way as you choose. How you use your server is up to you and your desires

#### Setting up the Loginserver for Local LAN

*   Now, assuming you've had all of the above done, you may need to do a little manual work to configure some of your network settings to get your server to properly show up.
*   First you will need to get your local LAN IP
    *   Open up 'cmd' by going to Start and typing in 'cmd'
    *   Type the command:
        *   ipconfig

![image](https://user-images.githubusercontent.com/3319450/34912564-330bc466-f8aa-11e7-9f97-c73049af2268.png)

*   You will need to use this address in all of the following files

**EQEmuServer: (login.ini)**

![image](https://user-images.githubusercontent.com/3319450/34912567-4100373c-f8aa-11e7-95c8-309e4da03a37.png)

**EQEmuServer: (eqemu_config.json)**
```               
"loginserver2" : {
	"account" : "",
	"host" : "192.168.197.129",
	"password" : "",
	"port" : "5998"
},
```
**Uncomment the address tag and put the local LAN IP**

**All EverQuest Clients on the local network will need this entry: (eqhost.txt)**

![image](https://user-images.githubusercontent.com/3319450/34912578-95aa7a86-f8aa-11e7-9354-7288b512d8d4.png)

Restart your server using **t\_start\_server\_with\_login_server** and you should be good to go!

**Connect using your game client and you should see:**

![image](https://user-images.githubusercontent.com/3319450/34912582-a025e892-f8aa-11e7-8676-2cdd98f6592c.png)
