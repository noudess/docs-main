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


Add an admin for your server to tblServerAdminRegistration
~~~
insert into 
tblServerAdminRegistration (Accountname,AccountPassword,FirstName,LastName,Email,RegistrationDate,RegistrationIPAddr)
values ('srvadmin','DontUseThisPassword','Server','Admin','srvadmin@dev.null',now(),'127.0.0.1');
~~~

Get the ServerAdmin ID for recently added admin
~~~
select ServerAdminID from tblServerAdminRegistration where Accountname = 'srvadmin';
~~~

Add your server to the tblWorldServerRegistration table.  
Set ServerAdminID equal to the value from the query above.
~~~
insert into tblWorldServerRegistration
(ServerID,ServerLongName,ServerTagDescription,ServerShortName,ServerListTypeID,ServerLastLoginDate,ServerLastIPAddr,ServerAdminID,Note,ServerTrusted)
values
('1','LongNameFromConfig','Blah','ShortNameFromConfig','3',now(),'127.0.0.1','1','','1');
~~~

The above magic was found at -> http://www.eqemulator.org/forums/showpost.php?p=174840&postcount=41

And now should be able to start the loginserver via `Bin/loginserver`

To add a user account, you just need to add an entry to the _tblLoginServerAccounts_ table.  When the user successfully logs in for the first time, the server will take care of add them to the _accounts_ table
~~~
insert into tblLoginServerAccounts 
(AccountName,AccountPassword,AccountEmail) 
values('FirstUserID',sha('EasyToGuessPassword'),'spam.me@dev.null');
~~~
