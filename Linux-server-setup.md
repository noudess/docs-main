Prerequisites
-------------

* Some knowledge of the terminal
* Some knowledge of mysql
* A compatible installation of the Everquest client.

Note:  If you are using CentOS Enterprise or any other *nix package with a GCC version lower than 4.6, you should read this article: [[GCC below 4.6]]

Steps
-----

* Open a terminal window.
* First make sure you have dependencies installed. On Ubuntu this is done with: `sudo apt-get install subversion mysql-server libmysqlclient-dev libboost-dev build-essential git liburi-escape-xs-perl`.
* Additional optional dependencies: `sudo apt-get install phpmyadmin`
* Clone the repository from github: `git clone git://github.com/EQEmu/Server.git eqemu` 
   OR if behind a firewall/proxy `git https://://github.com/EQEmu/Server.git eqemu`
* `cd eqemu`
* If you do not have make or cmake installed already, `sudo apt-get install cmake make`
* `cmake -G "Unix Makefiles" -Wno-dev -i .`  build types are "Debug Release RelWithDebInfo MinSizeRel"
* `make`
* If you get errors about CMake Error: your CXX compiler: "CMAKE_CXX_COMPILER-NOTFOUND" was not found, then try  `sudo apt-get install build-essential`
* If you get errors about Could NOT find PerlLibs (missing: PERL_LIBRARY), then try running ``cmake . -DPERL_LIBRARY=`locate -n 1 libperl.so` ``
* If you get errors about missing lua.h try `sudo apt-get install liblua5.1-0-dev`
* Go to http://peqtgc.com/releases and download the peqbeta_ and quests_ files.
* The peqbeta archive contains SQL data that needs to be loaded into your database.
* The quests archive contains a quests folder that should be copied to your eqemu directory.
* Inside the quest folder are two folders called `lua_modules` and `plugins`. Move these to the root of your eqemu directory.
* Download the maps from Google Code. From your eqemu directory: `svn checkout http://eqemumaps.googlecode.com/svn/trunk/ .`
* Copy the default config file to eqemu root directory: `cp utils/defaults/eqemu_config.xml.full ./eqemu_config.xml`
* Create a database named `eq` and load the .sql files from the peqbeta_ archive into it. 
* Create a user with privileges on `eq` and add the credentials to `eqemu_config.xml`.
* Copy `eqtime.cfg` from the peqbeta_ archive into the eqemu root directory.
* Copy `spells_us.txt` from your Everquest installation into the eqemu root directory.
* Create the logs directory: `mkdir logs`. 
    Copy default log.ini to eqemu root `cp utils/defaults/log.ini ./`
* Create the shared memory directory: `mkdir shared`.
* Run `Bin/shared_memory` to populate the shared directory
* Create symlinks to needed configs
~~~ 
ln -s utils/patches/patch_RoF.conf patch_RoF.conf
ln -s utils/patches/patch_SoD.conf patch_SoD.conf
ln -s utils/patches/patch_SoF.conf patch_SoF.conf
ln -s utils/patches/patch_Titanium.conf patch_Titanium.conf
ln -s utils/patches/patch_UF.conf patch_UF.conf
ln -s utils/patches/patch_RoF2.conf patch_RoF2.conf
ln -s utils/patches/opcodes.conf opcodes.conf
ln -s utils/patches/mail_opcodes.conf mail_opcodes.conf
ln -s utils/defaults/mime.types mime.types
ln -s utils/defaults/worldui.pl worldui.pl
ln -s utils/defaults/plugin.pl plugin.pl
ln -s utils/defaults/commands.pl commands.pl
ln -s loginserver/login_util/login_opcodes.conf login_opcodes.conf
ln -s loginserver/login_util/login_opcodes_sod.conf login_opcodes_sod.conf
~~~

* Run `ln -s utils/defaults/templates/ templates` in the eqemu root directory.  This is the magic that makes the HTTP service(default port 9080) work.
* To log into the HTTP service, you'll need to add an entry to tblServerAdminRegistration and account
~~~
insert into tblServerAdminRegistration (Accountname,AccountPassword,FirstName,LastName,Email,RegistrationDate,RegistrationIPAddr)
values ('webguiacct','RandomPassword','Web','Gui','webgui.acct@dev.null',now(),'127.0.0.1');

insert into account (name,password,status,lsaccount_id,time_creation)
values ('webguiacct','RandomPassword',250,1,now());
~~~
* NOTE: account.lsaccount_id equals tblServerAdminRegistration.ServerAdminID
* Run `Bin/world` and wait for it to finish initializing.
* Once the world server is running, open a new terminal window and run `Bin/eqlaunch zone`. If Bin/zone is not in your path, you can edit your eqemu_config.xml to include:<br />
\<launcher><br />
\<exe>Bin/zone\</exe><br />
\</launcher><br />

If you find your characters are unable to move, try applying utils/sql/git/required/2015_02_12_zone_gravity.sql .  It'll fix a bug with the gravity.
~~~
mysql -u eqdbuser -p -D eq < utils/sql/git/required/2015_02_12_zone_gravity.sql
~~~
Found that solution at -> http://www.eqemulator.org/forums/showthread.php?p=239737
