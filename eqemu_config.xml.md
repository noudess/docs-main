This file has the configuration setup for your server. It is a text file located in your server root folder.

***

Sample file contents:
```
<?xml version="1.0"?>
<server>
	<world>
		<shortname>MyPEQ</shortname>
		<longname>My PEQ Testbed</longname>

		<!-- Only specify these two if you really think you need to.  (read: You don't) -->
		<!-- <address>example.dyndns.org</address> -->
		<!-- <localaddress>192.168.0.100</localaddress> -->

		<!-- Loginserver information.  Defaults shown -->
		<loginserver>
			<host>localhost</host>
			<port>5998</port>
			<account>world_username</account>
			<password>world_password</password>
		</loginserver>

		<!-- Server status.  Default is unlocked -->
		<!--<locked/>-->
		<!-- <unlocked/> -->

		<!-- Sets the ip/port for the tcp connections.  Both zones and console (if enabled).  Defaults are shown -->
		<tcp ip="localhost" port="9000" telnet="disable"/>

		<!-- Sets the shared key used by zone/launcher to connect to world -->
		<key>MySpecialLongKey</key>
		
		<!-- Enable and set the port for the HTTP service.  Defaults are shown -->
		<http port="9080" enabled="false" mimefile="mime.types"/>
	</world>

	<!-- Chatserver (channels) information.  Defaults shown -->
	<chatserver>
		<host>localhost</host>
		<port>7778</port>
	</chatserver>

	<!-- Mailserver (in-game mail) information.  Defaults shown -->
	<mailserver>
		<host>localhost</host>
		<port>7778</port>
	</mailserver>

	<zones>
		<defaultstatus>0</defaultstatus>

		<!-- Sets port range for world to use to auto configure zones -->
		<ports low="7000" high="7005"/>
	</zones>

	<!-- Database configuration, replaces db.ini.  Defaults shown -->
	<database>
		<host>localhost</host>
		<port>3306</port>
		<username>db_username</username>
		<password>db_password</password>
		<db>peq</db>
	</database>

	<!-- Queryserv Database configuration -->
	<qsdatabase>
		<host>localhost</host>
		<port>3306</port>
		<username>db_username</username>
		<password>db_password</password>
		<db>peq_qs</db>
	</qsdatabase>
 
	<!-- Launcher Configuration -->
	<launcher>
		<!-- <logprefix>logs/zone-</logprefix> -->
		<!-- <logsuffix>.log</logsuffix> -->
		<!-- <exe>zone.exe or ./zone</exe> -->
		<!-- <timers restart="10000" reterminate="10000"> -->
	</launcher>

	<!-- File locations.  Defaults shown -->
	<files>
		<!-- <spells>spells_us.txt</spells> -->
		<!-- <opcodes>opcodes.conf</opcodes> -->
		<!-- <logsettings>log.ini</logsettings> -->
		<!-- <eqtime>eqtime.cfg</eqtime> -->
	</files>
	<!-- Directory locations.  Defaults shown -->
	<directories>
		<!-- <maps>Maps</maps> -->
		<!-- <quests>quests</quests> -->
		<!-- <plugins>plugins</plugins> -->
	</directories>
</server>
```