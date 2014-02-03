Prerequisites
-------------

* Some knowledge of the terminal
* Some knowledge of mysql
* A compatible installation of the Everquest client.

Note:  If you are using CentOS Enterprise or any other *nix package with a GCC version lower than 4.6, you should read this article: [[GCC below 4.6]]

Steps
-----

1. Open a terminal window.
2. First make sure you have dependencies installed. On Ubuntu this is done with: `sudo apt-get install subversion mysql-server libmysqlclient-dev`.
3. Additional optional dependencies: `sudo apt-get install phpmyadmin`
4. Clone the repository from github: `git clone git@github.com:EQEmu/Server.git eqemu`
5. `cd eqemu`
6. If you do not have make or cmake installed already, `sudo apt-get install cmake make`
7. `cmake .`
8. `make`
9. If you get errors about CMake Error: your CXX compiler: "CMAKE_CXX_COMPILER-NOTFOUND" was not found, then try  `sudo apt-get install build-essential`
10 If you get errors about Could NOT find PerlLibs (missing: PERL_LIBRARY), then try running `cmake . -DPERL_LIBRARY=`locate -n 1 libperl.so``
11. Go to http://peqtgc.com/releases and download the peqbeta_ and quests_ files.
12. The peqbeta archive contains SQL data that needs to be loaded into your database.
13. The quests archive contains a quests folder that should be copied to your eqemu directory.
14. Inside the quest folder are two folders called `lua_modules` and `plugins`. Move these to the root of your eqemu directory.
15. Download the maps from Google Code. From your eqemu directory: `svn checkout http://eqemumaps.googlecode.com/svn/trunk/ .`
16. Copy the default config file: `cp utils/defaults/eqemu_config.xml.full ./eqemu_config.xml`
17. Create a database named `eq` and load the .sql files from the peqbeta_ archive into it. 
18. Create a user with privileges on `eq` and add the credentials to `eqemu_config.xml`.
19. Copy `eqtime.cfg` from the peqbeta_ archive into the eqemu root directory.
20. Copy `spells_us.txt` from your Everquest installation into the eqemu root directory.
21. Create the logs directory: `mkdir logs`.
22. Create the shared memory directory: `mkdir shared`.
23. Run `Bin/world` and wait for it to finish initializing.
24. Once the world server is running, open a new terminal window and run `Bin/eqlaunch <name of your server>`.