This guide details how to setup a public Windows server using 32-bit versions of MySQL and Perl. If you feel you are special and want to use 64-bit MySQL and Perl, then this guide is NOT for you. If you want to setup a private server, using a Private login server, you are strongly advised to follow this guide to setup a public server first before attempting to setup a private login server (see the post linked at the bottom of this article for extra steps required to setup a private login server)


### WARNING - PLEASE READ FIRST

> One of the biggest reasons some people end up with problems is because they missed something in the guide they are following, we have all done it at one time or another. _Please make sure you're not just skimming over the text written here._ If you read each and every single line in the following steps before moving on to the next one, you will end up with a working server. If you get an error in your setup, you missed something or changed something you weren't supposed to. Go back and retrace your steps. One single mis-typed character can cause your server not to start, run, or connect to the public server list.

### Step 1: Gather the programs you will need to compile and run the server

There are specific instructions to installing and configuring Perl, MySQL and Visual Studio Express 2013 in this guide. Read each section completely prior to installing everything.

These instructions are using 32-bit versions of Perl and MySQL because the method is tried and works without errors. You can compile a 64-bit server, but that is not part of this guide at this time.
Some parts of this process require you to open tar/gzip files. Windows can not extract these files natively, so you will have to install a 3rd party program to extract these files. 7-Zip is free (not trial-ware like WinRAR) and works for everything you need and it is available here∞. Feel free to use whatever application you are comfortable with.

**Make the necessary folders**

1. Make a folder on your C drive called EQ.<br />`C:\EQ`
1. Make a folder inside the EQ Folder called Installs, this folder will have all the files you need to install to compile and run the server.<br />`C:\EQ\Installs`
1. Make a folder inside the EQ Folder called EQEmuServer, this folder will be where the actual game server runs from.<br />`C:\EQ\EQEmuServer`
1. Make a folder inside the EQ\EQEmuServer Folder called shared, this folder is required for "shared memory"<br />`C:\EQ\EQEmuServer\shared`
1. Make a folder inside the EQ Folder called SQL, this folder will be where you save database files and scripts to be sourced in to the database.<br />`C:\EQ\SQL`
1. Make a folder inside the EQ Folder called Source, this folder will be where you clone/download the C++ source code to.<br />`C:\EQ\Source`

**Download the required third-party applications**

Download the 32-bit version of [ActiveState Perl 5.12.3](http://eqemu.github.io/downloads/ActivePerl-5.12.3.1204-MSWin32-x86-294330.msi) and put it in the `C:\EQ\Installs` directory.
Note that it is vital you download 32-bit Activstate Perl version 5.12. No other version will work.

Download the Windows (x86, 32-bit), MSI Installer version of [MySQL Community Server](http://dev.mysql.com/downloads/mysql/5.1.html) and put it in the `C:\EQ\Installs` directory.
The current version as of January 11, 2014 is 5.1.73. DO NOT download the essentials version (it does not have the required developer components). Download the one called `mysql-5.1.73-win32.msi`.

Download [Visual Studio Express 2013 For Windows Desktop](http://www.visualstudio.com/downloads/download-visual-studio-vs) and put it in the `C:\EQ\Installs` directory. Download the installer by clicking on 'Install Now'. Note this one is only a simple web installer package. It will download more when you run it.

Download the current version of [TortoiseSVN](http://tortoisesvn.net/downloads). If you have a 64-bit OS, download the 64-bit version. Be careful that you don't click the Download button that is in an advertisement, as that will try and force you to install a crapware toolbar that you probably don't want. The correct download button should download an .msi file which you should place in your `C:\EQ\Installs` directory.

Download the current version of [GIT for Windows](http://git-scm.com/downloads). In the upper right of the download page there should be a picture of a monitor showing the latest stable release and a 'Download for Windows' button. Save it in your `C:\EQ\Installs` directory.

Download the current version of [Notepad++](http://notepad-plus-plus.org/download/) and save it in your `C:\EQ\Installs` directory.

Download the Windows (Win32 Installer) version of [CMake](http://www.cmake.org/cmake/resources/software.html) and place it in your `C:\EQ\Installs` directory.

Download a third party zip program such as [7-Zip](http://www.7-zip.org/download.html) because you will need to open .tar.gz files and the Windows compressed file utility does not know what to do with that file type.

**Optional Download** Get the current version of [HeidiSQL](http://www.heidisql.com/download.php) and save it in the `C:\EQ\Installs` directory.<br />_HeidiSQL is not required for this guide, however you may find it useful for editing the SQL database once you have the server up and running. If you are already comfortable using MySQL you can use HeidiSQL in place of the command line MySQL tool that is used throughout this guide_

### Step 2: Install the programs you will need to compile and run the server

The following steps install the programs that you downloaded and copied to your C:\EQ\Installs directory in the previous steps.

1. Install 7-Zip or your preferred file compression program using defaults (click yes, next, or allow to all prompts).
1. Install Notepad++ using defaults (click yes, next, or allow to all prompts).
1. Install GIT for Windows using defaults (click yes, next, or allow to all prompts).
1. Install CMake using defaults (click yes, next, or allow to all prompts).
1. Install Visual Studio Express 2013 For Windows Desktop using defaults (click yes, next, or allow to all prompts).
1. If you downloaded HeidiSQL, install HeidiSQL using defaults (click yes, next, or allow to all prompts).
1. Install TortoiseSVN using defaults (click yes, next, or allow to all prompts).<br />_The TortoiseSVN installation may say you need to reboot. **If it does then reboot before continuing.**_

**Now install the applications that require a specific configuration**

**Install ActiveState Perl** ensuring that the installation path shows as `C:\Perl` and if not, then change it to that.  Otherwise for all other prompts use the defaults (click yes, next, or allow to all prompts).<br />_When Perl is finished installing, you should either logoff/logon or reboot your PC to ensure the changes to the Windows PATH variable are updated **before proceeding further**_.

**Install MySQL 5.1** using the following instructions. If you miss a step you will have to completely uninstall MySQL and start this part all over again.

1. When you first start up the install, make sure you choose CUSTOM install.
1. On that same menu, make sure ALL options are installed. The developer components will probably have an X against it. Click it and select `This feature will be installed on local hard drive`. This is important, you will not be able to compile the EQEmu source code without the MySQL developer components.
1. After clicking "next", on that menu, click Install
1. If a Nag screen appears about MySQL Enterprise, click Next until a dialog appears with a box that says `Configure the MySQL Server now`. Ensure the box is ticked and click Finish.
1. The MySQL Server Instance Configuration Wizard should start. If you don't see it, make sure it is not hidden behind another window. Click Next.
1. Select `Detailed Configuration` and click Next.
1. Choose `Server Machine` and click Next.
1. Choose `Multifunctional Database` and click Next.
1. When the InnoDB settings dialogue appears, click Next.
1. Select `Online Transaction Processing (OLTP)` and click Next.
1. On the next screen,<br />
 ensure `Enable TCP/IP Networking` is ticked,<br />
the port number should be `3306`,<br />
and **untick** `Enable Strict Mode`. Then click Next.
1. On the next sceen, select `Best Support For Multilingualism` and click Next.
1. On the next screen, ensure `Install as a Windows Service` is ticked and, very important, tick the box to `Include Bin Directory in Windows PATH`. Then click Next.
1. You will be prompted for a root password (root is the default username). This will be known as your MySQL password. Make sure you remember it. Click Next.
1. Click Execute.
1. When the wizard has done it's thing, click Finish.

_When MySQL is finished installing, you should either logoff/logon or reboot your PC to ensure the changes to the Windows PATH variable are updated **before proceeding further**_.

### Step 3: Getting and compiling the C++ source code

These next steps will walk you through downloading the C++ source code and then compiling it into executable files.

1. Open the `C:\EQ` folder and then right click on the folder called Source.
1. From the menu that pops up, select 'GIT Bash'.
1. A command window should pop up (similar but not the same as the standard Windows command prompt).
1. Type: `git clone git://github.com/EQEmu/Server.git .`<br />Note the . at the end of the command, i.e. there is a space after Server.git and then a period/full-stop. This is important. It tells GIT to clone the source code into the current folder , i.e. C:\EQ\Source If you omitted the . it would create a new folder called C:\EQ\Source\Server and download the source into that.<br />The output of the git clone command should look similar to this:<br />
`Cloning into '.'... >a few lines of stuff of stuff< ... Checking out files: 100% (1181/1181), done.`<br />
1. Go to C:\EQ\Source in Windows Explorer, you should see a bunch of files and sub-folders have appeared, namely `CMakeLists.txt LICENSE.md cmake eqlaunch ucs zone shared_memory README.md common loginserver utils GPL.txt changelog.txt dependencies queryserv world`<br />Note that if you want to update your source code in the future to the latest version, follow the process above, but instead of typing `git clone ...` you would just type: `git pull` and that would check for updates to the source code and download the latest version if there have been any changes since you last did a git clone or git pull.

**Install some other required files**

Download the ""MySQL"" and zlib headers/libraries∞ and unzip them into C:\EQ\Source\dependencies
If you do it correctly, you should have two folders underneath C:\EQ\Source\dependencies, one called mysql_x86 and one called zlib_x86.

Use CMake to build the required Visual Studio Solution and Project files

Launch your CMake program, typically labeled CMake (cmake-gui). Eg: Start -> CMake 2.8 -> CMake

To the right of the 'Where is the source code' box, click 'Browse Source' and expand the tree, C:\EQ\, click once on Source and then click OK, so the entry in the 'Where is the source code' box should read C:/EQ/Source/

To the right of the 'Where to build the binaries box', click 'Browse Build', expand the tree down to C:\EQ\Source. With 'Source' highlighted, click 'Make New Folder'.
Name the new folder Build and click OK. The 'Where to build the binaries box' should now have C:/EQ/Source/Build in it.

Click on Configure.

In the next dialogue that says 'Specify the generator for this project', select 'Visual Studio 11'. Click on Finish.

Some messages should appear in the lower window with hopefully no errors. 

If you want to use 'Bots' on your server, click the box next to EQEMU_ENABLE_BOTS and then click Configure again.

Click on Generate and CMake should say 'Generating done' in the output window.

You can now close CMake. 

Build the executables using Visual Studio

In Windows explorer, navigate to C:\EQ\Source\Build and double-click on EQEmu.sln (if you don't see the .sln suffix, it is the file named EQEmu that has a Type of 'Microsoft Visual Studio Solution'.

Microsoft Visual Studio Express 2012 should open up. On the right hand side of the window you should see the 'solution explorer' with an entry called ALL_BUILD.

Right-click on ALL_BUILD and select Build.

This will take a while. When it is finished you should see a message saying:

========== Build: 9 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========


*WARNING*
If the build was successful, (9 succeeded), you DO NOT have to re-do that just because you have future problems. The rest of the setup is copying files, sourcing your database and configuring your server. The database and the server are two separate things. Your config files will help connect the two when your server is finally up and running.


Copying the executables to your server directory

First go into the C:\EQ\Source\Build\Bin\Debug folder and copy the following files:

shared_memory.exe, eqlaunch.exe, queryserv.exe, ucs.exe, world.exe and zone.exe


to your C:\EQ\EQEmuServer folder.

You may also copy all the .pdb files from C:\EQ\Source\Build\Bin\Debug to C:\EQ\EQEmuServer although this isn't strictly necessary. If EQEmu crashes and you have the .pdb files present in C:\EQ\EQEmuServer a crash report will be produced saying exactly whereabouts in the code the crash occurred. This can be useful when reporting crashes on the forums.

Next, go to your C:\EQ\Source\utils\patches folder and copy all the files from there to your C:\EQ\EQEmuServer folder.

Next, go to your C:\EQ\Source\utils\defaults folder and copy all the files and sub-folders from there to your C:\EQ\EQEmuServer folder.


Download maps and quests

In your C:\EQ\EQEMuServer server folder, right click on the quests folder and choose "SVN Checkout"

In the "URL of repository" line copy and paste the following:


http://projecteqquests.googlecode.com/svn/trunk/quests∞


Change the Checkout Directory to:

C:\EQ\EQEmuServer\quests

(Then click on OK)

Ignore the warning that pops up saying the quests folder is not empty (click Yes).

Let it download the quests. It will show "At Revision xx when done.

Next, in your server folder, right click on the Maps folder and choose "SVN Checkout"
In the "URL of repository" line copy and paste the following:

http://eqemu-maps.googlecode.com/svn/trunk/ 
 


Change the Checkout Directory to Change the Checkout Directory to:
C:\EQ\EQEmuServer\Maps


(then click OK)

Ignore the warning that pops up saying the Maps folder is not empty (click Yes).

This will take a while, have a coffee.

Copying quest plugins

Go to the C:\EQ\EQEmuServer\quests\plugins folder and copy all the files in there to the C:\EQ\EQEmuServer\plugins folder.

You will get a warning that the file check_handin.pl already exists. Select the option to overwrite the file.

Verifying that you have copied all the files into your server directory

In your eqemu (server folder) there should be 7 folders.

1. logs (this will be empty right now)

2. Maps (full of all the map files you downloaded)

3. plugins (has all the plugin files you copied from /quests/plugins folder)

4. quests (has all the quests you downloaded.)

5. templates

6. updated_templates

7. shared

Aside from those 7 folders, you should have 21 other files in your server folder.


Step 4: Downloading, installing and updating the PEQ database

First, go to your C:\EQ folder and right click on the folder you made called SQL and choose "SVN Checkout"

In the "URL of repository" line copy and paste the following:

http://projecteqdb.googlecode.com/svn/trunk/peqdatabase∞ (then click OK)


It will finish with "At Revision XX"

Next, go to the folder C:\EQ\SQL and unzip the file from peqdb_revNNNN.sql.gz
NNNN will be a four digit number that changes over time.

If double-clicking on peqdb_revNNNN.sql.gz does not launch 7-zip or your preferred unzipper, you may need to launch 7-manually (possibly using 'Run as Administrator' and go into the settings/options and tell it to associate it with .gz files).

Once you have the file opened with 7-zip, select extract and extract it to C:\EQ\SQL.

This file will be named peqdb_revNNNN.sql (without the .gz)

Now it is time to create the database.

Launch a command prompt window and navigate to your C:\EQ\SQL folder by typing:

cd c:\EQ\SQL


Then enter mysql -uroot -ppassword where password is the password you chose when installing MySQL.

You should be presented with a mysql> prompt.

Type: create database peq; and press enter.

Type: use peq; and press enter.

Note: Now that the database is created anytime you need to login to MySQL in the future, you can do it with a single line command.
mysql -uroot -pyourpassword peq


Type source peqdb_revNNNN.sql (replacing NNNN with the four digits depending on the latest version of the database that you downloads).

This may take a while to complete, depending on how powerful your PC is.

When the mysql> prompt returns:

Type: source load_player.sql and press enter.

If you plan on using Bots, also do the following:

Type: source load_bots.sql and press enter.

Type exit to return to the command prompt.

Applying SQL updates to your database so that it is compatible with your version of the EQEmu source code/executables

At the time of updating this guide, the source code has just been moved from Google code SVN to github, so there could be SQL updates in two places for a short time.

In Windows Explorer, navigate to the C:\EQ\Source\utils\sql\svn folder

This folder has a list of all SQL updates going back several years. You are going to need to 'source in' those that have a higher number than the NNNN of your peqdb_revNNNN.sql file
e.g. if your peq file was called peqdb_rev2294.sql, then you need to source in all those .sql files that have a number of 2295 or higher.

Make a note of the names of all the .sql files with a number higher than 2294.

As of the time of writing, the EQEmu source is at Revision 2501, so we need to source in any SQL updates with a number between 2295 and 2501 (there are 14 of them). 

Back in your command window, navigate to the C:\EQ\Source\utils\sql\svn folder, i.e. cd C:\EQ\Source\utils\sql\svn folder.

type mysql -uroot -p
Enter your MySQL password

When the mysql prompt appears:

type use peq; and press enter

Then, for each of the .sql files you made a note of, starting with the lowest numbered one and proceeding in sequence, enter:

source <filename> and press enter.

Eg. in the example I gave, i.e. using PEQ database rev 2294 and EQEmu Source rev 2501, you would type:

source 2299_required_inspectmessage_fields.sql
source 2300_optional_loot_changes.sql
source 2340_required_maxbuffslotspet.sql
source 2361_required_qs_rule_values.sql
source 2370_required_aa_updates.sql
source 2376_required_aa_updates.sql
source 2380_optional_merc_data.sql
source 2380_optional_merc_merchant_npctypes_update.sql
source 2380_optional_merc_rules.sql
source 2383_required_group_ismerc.sql
source 2428_optional_levelbasedexpmods.sql
source 2448_optional_stun_proc_aggro_rule.sql
source 2471_required_aa_updates.sql
source 2482_required_start_zones.sql (and press enter)


There may be further updates to apply in the following folder:
C:\EQ\Source\utils\sql\git folder


In this folder are two sub-folders, one called required, and one called optional. As the names suggest, any .sql files in the 'required' folder must be applied. The ones in the 'optional' folder are ... optional.

In each sub-folder, there may be .sql files with names like: 
YYYY_MM_DD_Desc.sql


Source these .sql files in in ascending date order in the same way you did with the updates in the utils\sql\svn folder.

When you are done you can type exit to exit mysql and then close the command window.

Optional - Backup your database

Once you have your database updated fully, BACK IT UP !!!
That is easily done without even logging in to your mysql.
Create a folder on your C-Drive (or wherever), called backup
Then in a command window, simply type the following:
mysqldump -uroot -ppassword peq > c:\EQ\peq_backup.sql


Then if you ever have to re-install everything, you can easily source your whole database
back in by typing the following: (make sure your in that same backup folder)

mysql -uroot -ppassword
drop database peq;
create database peq;
use peq
source C:\EQ\peq_backup.sql



Step 5: Editing your server configuration and launching your server

PORT FORWARDING ON YOUR ROUTER (if you're using one)

Port forwarding is required if you want to allow other people out on the Internet to play on your server. If you are only intending for yourself or other people on your local LAN to connect, then this step is not necessary.

Log in to your router and you need to forward the following ports to the internal ip of your server computer.

UDP 7000 to 7100 (Port Range Forwarding is essential for this)
UDP 9000


To find out the internal ip of your computer, at a command prompt type ipconfig. The 192.168.1.xxx number that is listed is the forwarding IP you need.
Every router is different, so if you don't know how to log in to it, then you will have some searching to do without the manual.

Most commonly, a web browser is used, typing in an address like 192.168.1.1


Editing your server configuration - eqemu_config.xml

In your C:\EQ\EQEmuServer folder, you will have two xml files in there, one called eqemu_config.xml and another called eqemu_config.xml.full
You don't need both of these. DELETE the eqemu_config.xml and keep the other one.
Rename eqemu_config.xml.full to eqemu_config.xml by REMOVING, the .full at the end of it. (The .full xml file is a more complete config)

*WARNING*WARNING*WARNING*

Editing this xml file is where a lot of people don't understand when someone trys to advise them NOT TO EDIT LINES, they don't listen and then get frustrated.

First of all when a line has these characters in front of it: <!--
That means it is commented out FOR A REASON. DO NOT REMOVE these characters from any of the lines that have them. Most of the configuration in this file and your server is already set to connect to the public eqemulator.net server list. The only changes you need to make are the shortname, longname and database info. NOTHING ELSE.

A sample of a eqemu_config.xml file is given below. Copy and and paste it in to Notepad++, then edit the items highlighted in red

Ensure you save it as C:\EQ\EQEmuServer\eqemu_config.xml

Note that the <defaultstatus> is currently set to 20 by default which means that anyone logging into your server will be given an admin status of 20 which will possibly allow them to use GM commands that you would rather they didn't. This is why it is set to 0 in the example below.


<?xml version="1.0">
<server>
<world>
<!-- Set the shortname to ONE word. The longname is what shows up on server list -->
<shortname>shortname</shortname> 
<longname>My Long Name</longname>

<!-- DO NOT EDIT ANY LINES BETWEEN HERE AND THE DATABASE SECTION -->
<!-- <address>do.not.edit</address> -->
<!-- <localaddress>do.not.edit</localaddress> -->

<!-- Loginserver information. DO NOT EDIT -->
<loginserver>
<host>eqemulator.net</host>
<port>5998</port>
<account></account>
<password></password>
</loginserver>

<!-- Server status. Default is unlocked DO NOT EDIT RIGHT NOW -->
<!--<locked/>-->
<!-- <unlocked/> -->

<!-- Sets the ip/port for the tcp connections. DO NOT EDIT -->
<tcp ip="127.0.0.1" port="9000" telnet="disable"/>

<!-- Sets the shared key used by zone/launcher to connect to world -->
<key>somelongrandomstring12345</key>

<!-- Enable and set the port for the HTTP service. Defaults are shown -->
<http port="9080" enabled="false" mimefile="mime.types" />
</world>

<!-- Chatserver (channels) information. DO NOT EDIT -->
<chatserver>
<host>192.168.1.x</host>
<port>7778</port>
</chatserver>

<!-- Mailserver (in-game mail) information. DO NOT EDIT -->
<mailserver>
<host>192.168.1.x</host>
<port>7778</port>
</mailserver>

<zones>
<!-- The defaultstatus is what status the new toons will have on your server -->
<defaultstatus>0</defaultstatus>

<!-- Sets port range for world to use to auto configure zones DO NOT EDIT RIGHT NOW-->
<ports low="7000" high="7100"/>
</zones>

<!-- Set username to root and password is your MySQL password and db to peq -->
<database>
<host>127.0.0.1</host>
<port>3306</port>
<username>root</username>
<password>xxxxx</password>
<db>peq</db>
</database>
<qsdatabase>
<host>127.0.0.1</host>
<port>3306</port>
<username>root</username>
<password>xxxxx</password>
<db>peq</db>
</qsdatabase>

<!-- Launcher Configuration DO NOT EDIT-->
<launcher>
<!-- <logprefix>logs/zone-</logprefix> -->
<!-- <logsuffix>.log</logsuffix> -->
<!-- <exe>zone.exe</exe> -->
<!-- <timers restart="10000" reterminate="10000"> -->
</launcher>

<!-- File locations. DO NOT EDIT -->
<files>
<!-- <spells>spells_us.txt</spells> -->
<!-- <opcodes>opcodes.conf</opcodes> -->
<!-- <logsettings>log.ini</logsettings> -->
<!-- <eqtime>eqtime.cfg</eqtime> -->
</files>
<!-- Directory locations. DO NOT EDIT -->
<directories>
<!-- <maps>Maps</maps> -->
<!-- <quests>quests</quests> -->
<!-- <plugins>plugins</plugins> -->
</directories>
</server>


Note that in this example, we are using the internal IP address of your server for the chatserver/mailserver (aka Universal Chat Server or UCS). This will allow PCs on your local LAN to connect to the UCS and use chat channels and in-game mail, but for people on the Internet to connect to your UCS, you will need to replace the IP address in the <chatserver> and <mailserver> blocks with a DNS name. If you are hosting the server on a residential broadband/cable connection you will typically need to use a service such as dyndns to get a DNS name. This is not within the scope of this guide and is not something you should worry about until you have your server running sucessfully.


Creating a batch file to launch the server

Now you can make a start.bat file to put in your server folder with the following lines:

@echo off
shared_memory.exe
start world.exe
echo waiting for the world to finish before starting zone...
ping -n 10 127.0.0.1 > nul
start queryserv.exe
start ucs.exe
start eqlaunch.exe zone
exit

Then create a shortcut on your desktop to run this file.


Launching your server for the first time

OK, If you've done all that, been there and back again, and your 300% sure that you followed these steps exactly, crossed all t's and dotted all i's - Your done.

Before you click on that Start.bat file, a couple things to know.

When you run start.bat, a new command window with the title C:\EQ\EQEmuServer\world.exe should appear.

After 10 seconds, three more command windows should appear with the following titles:

C:\EQ\EQEmuServer\eqlaunch.exe C:\EQ\EQEmuServer\queryserv.exe C:\EQ\EQEmuServer\ucs.exe


If one or all four of the windows does not appear then the corresponding program failed to launch for some reason. Launch a new command prompt window and navigate to C:\EQ\EQEmuServer
and run the command manually, e.g. world.exe

This will display any error messages that is causing the program to fail to start. You should look at the errors and go back over the guide to see if you can figure out what you did wrong. If all else fails, make a post on the EQEmu forums asking for assistance.

*NOTE* - Your server places it's log files in the logs folder. This is where you look for troubleshooting problems.

After you have run start.bat and you have the four windows displayed you can now log in the EQEmu public logon server, find your server in the list and login to it.


Giving yourself GM power

Assuming you are able to log in to your server successfully, you probably want to give yourself GM powers. The easiest way to do this is to open a command prompt, navigate to C:\EQ\EQEmuServer and then type:

world flag <your EQEmu loginserver account name> 250

e.g.
world flag Derision 250


This will flag your account with status 250.

At this point you can now lock your server so that nobody else can login to it. To do this, edit your eqemu_config.xml and change this line:

<!--<locked/>-->

to
<locked/>


This is removing the XML comments around that line.

Then restart your server, i.e. Ctrl-C all the running command windows and then run start.bat again.

When you login next, your server should have a status of 'Locked', but since you have GM status, it will let you login anyway.

Restricting Access to GM Commands

Besides the usual commands available in everquest that begin with a '/', e.g. /say, there are additional commands available in EQEmu that begin with a '#'.
These are mostly commands for GMs, e.g. #zone, #repop etc. although some are available to normal players, e.g. #undyeme

The access to these # commands is determined by 'account status' which is set as described above using the
world flag <Account> <Status>
command.

Each # command has a 'default' status that is required to use it which is set in the source code. This required status is overridden by the value assigned to the command in the commands table in the MySQL database. If you want to prevent normal players (who usually have a status of 0) from using a command, set the status for that command to > 0 in the commands table. Likewise, to give a player access to a command that they can't usually access (e.g. #zone), set the status for that command to 0 in the commands table.

Common Problems

Quest Problems

If quests don't work at all in game, make sure your quest files are in C:\EQ\EQEmuServer\quests and not C:\EQ\EQEmuServer\quests\quests

If hailing an NPC works but when you hand them an item they do nothing, then you missed the step where you must copy the contents of C:\EQ\EQEmuServer\quests\plugins into C:\EQ\EQEmuServer\plugins

Bot Problems

If bots don't work, ensure you ticked EQEMU_ENABLE_BOTS in the CMake step. If you forgot to do that, go back and run CMake again, followed by the step to compile the executables and copy the executables from the Build/Bin/Debug folder to your C:\EQ\EQEmuServer folder.

If you enabled bots in CMake but they still don't work, you may have missed the step to source load_bots.sql during the database setup.

shared_memory startup problems

If you click on your start.bat and receive a message along the lines that a shared memory file cannot be created, make sure you have a folder called shared in your C:\EQ\EQEmuServer folder, i.e. a folder called C:\EQ\EQEmuServer\shared

Any other problems ?

If you have any problems following this guide, read this thread to see if your question/problem has already been answered/solved:

http://www.eqemulator.org/forums/showthread.php?t=36481∞

If not, make a new post on that thread.

Using a Private Login Server

For tips on setting up a Private Login Server, refer to this post: 

http://www.eqemulator.org/forums/showpost.php?p=220659&postcount=14∞


Credits

This guide is an updated one based on previous work by Huppy and Sorvani.