
| Legend  |
|--|
| *Required |
| Not required |


### Server -> World

| Variable | Default Value | Description |
|--|--|--|
| *shortname |  | This is the short name of your server, this shows up in a client's .ini file eg: servername_charactername.ini |
| *longname |  | This is the long name of your server, this shows up in a on the Loginserver |
| address | | Not required, but binds the server to this address, default is to listen on all addresses
| localaddress | | Not required, but recommended to set for LAN setups so other local clients can connect properly
| maxclients | -1 | This sets the max amount of clients that can connect to your server, -1 is unlimited
| locked | false | This determines whether the server starts up locked or not, it takes a minimum status of 20 to get through locked state |

### Server -> World -> Loginserver

* Subsection: loginserver

| Variable | Default Value | Description |
|--|--|--|
| *host | login.eqemulator.net | This is the hostname of the loginserver endpoint |
| *port | 5998 | Loginserver endpoint port |
| legacy | 0 | When set to 1, will connect to old netcode (IE current public LS) |
| account |  | Account forum username for public EQEmu authentication, this is used with worldserver registration
| password | | Account forum password  | 

* Note: Multiple Loginserver endpoints can be established by using the same configuration above, however declaring your loginserver subsections with a number, below is an example

```
  "world" : {
	   "loginserver1" : {
			"account" : "",
			"host" : "login.eqemulator.net",
			"legacy" : "1",
			"password" : "",
			"port" : "5998"
	   },
	   "loginserver2" : {
			"account" : "",
			"host" : "myloginserver.net",
			"password" : "",
			"port" : "5998"
	   },
  },
```