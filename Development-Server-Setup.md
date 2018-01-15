# Standing Up a Dev Server
* As a developer - you may find the necessity to build a clean server/folder with the latest PEQ database without messing up an existing folder - today this is easy to do and applies for either Linux or Windows

### Using eqemu_server.pl

* First, create your server folder that you wish use, the examples are going to be used with Linux, but the command line is almost identical for Windows

* In Linux - the base installer uses /home/eqemu/ - so let's use that directory as our base

```
mkdir eqemu_test
cd eqemu_test
```
* Now that we are in our server folder, we can either copy the eqemu_server.pl from another server folder, or we can pull down a fresh copy from Github

* You can use curl, wget or manually create the file
> curl -O https://raw.githubusercontent.com/EQEmu/Server/master/utils/scripts/eqemu_server.pl eqemu_server.pl && chmod 755 eqemu_server.pl && ./eqemu_server.pl new_server

> wget --no-check-certificate https://raw.githubusercontent.com/EQEmu/Server/master/utils/scripts/eqemu_server.pl  -O eqemu_server.pl && chmod 755 eqemu_server.pl && ./eqemu_server.pl new_server

* Next, this is going to kick off installer routines - and build the source in
  * /home/eqemu/eqemu_test_source/Server/build
  * When this is done compiling, the folder you created will by symlinked to this custom build directory
* 