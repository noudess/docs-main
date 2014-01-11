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
6. `cmake .`
7. `make`
8. Go to http://peqtgc.com/releases and download the peqbeta_ and quests_ files.
9. The peqbeta archive contains SQL data that needs to be loaded into your database.
10. The quests archive contains a quests folder that should be copied to your eqemu directory.
11. Inside the quest folder are two folders called `lua_modules` and `plugins`. Move these to the root of your eqemu directory.
12. Download the maps from Google Code. From your eqemu directory: `svn checkout http://eqemumaps.googlecode.com/svn/trunk/ .`
13. Copy the default config file: `cp utils/defaults/eqemu_config.xml.full ./eqemu_config.xml`
14. Create a database named `eq` and load the .sql files from the peqbeta_ archive into it. 
15. Create a user with privileges on `eq` and add the credentials to `eqemu_config.xml`.
16. Copy `eqtime.cfg` from the peqbeta_ archive into the eqemu root directory.
17. Copy `spells_us.txt` from your Everquest installation into the eqemu root directory.
14. Create the logs directory: `mkdir logs`.
19. Create the shared memory directory: `mkdir shared`.
20. Run `Bin/world` and wait for it to finish initializing.
21. Once the world server is running, open a new terminal window and run `Bin/eqlaunch <name of your server>`.