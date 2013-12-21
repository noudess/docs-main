1. Open a terminal window.
2. First make sure you have dependencies installed. On Ubuntu this is done with: `sudo apt-get install mysql-server libmysqlclient-dev`.
4. Clone the repository from github: `git clone git@github.com:EQEmu/Server.git eqemu`
5. `cd eqemu`
6. `cmake .`
7. `make`
8. Go to http://peqtgc.com/releases and download the peqbeta_ and quests_ files.
9. The peqbeta archive contains SQL data that needs to be loaded into your database.
10. The quests archive contains a quests folder that should be copied to your eqemu directory.
11. Inside the quest folder are two folders called `lua_modules` and `plugins`. Move these to the root of your eqemu directory.
