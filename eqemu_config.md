
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
| tcp

### Server -> World -> Loginserver