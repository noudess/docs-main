* As a developer - you may find the necessity to build a clean server/folder with the latest PEQ database without messing up an existing folder - today this is easy to do and applies for either Linux or Windows

### Creating a New Folder

* First, create your server folder that you wish use, the examples are going to be used with Linux, but the command line is almost identical for Windows

* In Linux - the base installer uses /home/eqemu/ - so let's use that directory as our base

```
mkdir eqemu_test
cd eqemu_test
```

### Using eqemu_server.pl

* Now that we are in our server folder, we can either copy the eqemu_server.pl from another server folder, or we can pull down a fresh copy from Github

* You can use curl, wget or manually create the file
> curl -O https://raw.githubusercontent.com/EQEmu/Server/master/utils/scripts/eqemu_server.pl eqemu_server.pl && chmod 755 eqemu_server.pl && ./eqemu_server.pl new_server

> wget --no-check-certificate https://raw.githubusercontent.com/EQEmu/Server/master/utils/scripts/eqemu_server.pl  -O eqemu_server.pl && chmod 755 eqemu_server.pl && ./eqemu_server.pl new_server

### Setting Environment Parameters

* The script will prompt for a few questions, this is to ask for a valid MySQL user/password so the script can install a new environment properly, it is also going to ask for your new database name so it can associate the new folder with that database

```
[New Server] For a new server folder install, we assume Perl and MySQL are configured
[New Server] This will install a fresh PEQ Database, with all server assets
[New Server] You will need to supply database credentials to get started...

[Input] MySQL User: eqemu
[Input] MySQL Password: eqemu
[New Server] Success! We have a database connection
[Input] Specify a NEW database name that PEQ will be installed to: peq_new
```
* Note: If you do not supply valid MySQL credentials - the command will halt and not continue. Make sure to also use a simple database name to prevent issues

### Waiting for Installation

* Next, this is going to kick off installer routines - and build the source in the following directory:
  * **/home/eqemu/eqemu_test**_source/Server/build
  * When this is done compiling, the folder you created will by symlinked to this custom build directory