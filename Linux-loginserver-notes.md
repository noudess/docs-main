these are my chicken scratches of me trying to get the loginserver running

Need libcryptopp.a  libEQEmuAuthCrypto.a to compile it
these can be found at
http://projecteqemu.googlecode.com/svn/trunk/EQEmuServer/EQEmuLoginServer/login_util/linux/

Optionally can use subversion to pull down the whole "EQEmuLoginServer"
`svn checkout http://projecteqemu.googlecode.com/svn/trunk/EQEmuServer/EQEmuLoginServer`
but so far I just need the zip file with the two *.a files

Copy them to the dependencies directory in your eqemu root directory

Now prep the database
~~~
mysql -u eq -p -D eq < loginserver/login_util/EQEmuLoginServerDBInstall.sql
mysql -u eq -p -D eq < loginserver/login_util/tblLoginServerAccounts.sql
mysql -u eq -p -D eq < loginserver/login_util/tblServerAdminRegistration.sql
mysql -u eq -p -D eq < loginserver/login_util/tblServerListType.sql
mysql -u eq -p -D eq < loginserver/login_util/tblWorldServerRegistration.sql
~~~

copy the login.ini to the eqemu root directory
`cp loginserver/login_util/login.ini ./`
Edit login.ini, set the database info(user,passwd, etc)
not sure what "local_network" under [options] is used for

symlink the opcodes to the eqemu root directory
~~~
ln -s loginserver/login_util/login_opcodes.conf login_opcodes.conf
ln -s loginserver/login_util/login_opcodes_sod.conf login_opcodes_sod.conf
~~~

Update the tblWorldServerRegistration table
`mysql -u eq -p -D eq < ALTER TABLE tblWorldServerRegistration ADD ServerTrusted int(11);`

Add your server to the tblWorldServerRegistration table
http://www.eqemulator.org/forums/showpost.php?p=174840&postcount=41
~~~
insert into tblWorldServerRegistration
(ServerID,ServerLongName,ServerTagDescription,ServerShortName,ServerListTypeID,ServerLastLoginDate,ServerLastIPAddr,ServerAdminID,Note)
values
('1','LongNameFromConfig','Blah','ShortNameFromConfig','3',now(),'192.168.1.105','1','');
~~~

And now should be able to start the loginserver via `Bin/loginserver`

