Player Housing was introduced in the House of Thule expansion. It can be accessed from the Guild Lobby and allows for players to purchase houses and place items in their houses. Houses do require upkeep to maintain.

There is a single zone for all neighborhood instances (Sunrise Hills). House zones are separate and appear to be spread across a variety of .zon files (e.g. phinterior1a1.zon) based on the type of home purchased.

The Place button in the Real Estate Items window is enabled on a zone-by-zone basis (probably). It is likely part of one of the zoning packets. For example, if you have the window open and click on a placeable item, the button remains disabled in the Guild Lobby. Repeat the process in a neighborhood or inside a residence and the button becomes enabled.

To my knowledge, no work has been done to add player housing to EQEMU. If it has, it hasn't been made public as no emu server has this capability as far as I am aware.

This page has packet information from Live as of 12/28/2018. While it is likely that the OpCodes have changed since House of Thule was released, my hope is that the structure of each packet has remained largely unchanged.

[TODO: Add image of neighborhood search window]

## Click on door to view Neighborhood List (Client -> Server)

| Name                   | Number of Bytes | Description                             |
|------------------------|-----------------|-----------------------------------------|
| Network OpCode         | 2               | 0x09                                    |
| Packet Sequence Number | 2               |                                         |
| Application OpCode     | 2               | OP_ClickDoor<br/>- Live: 0x2254<br/>- RoF2: 0x3A8F |
| Door Id                | 1               | 77 for the neighborhood "door" gate in Guild Lobby |
| Unknown                | 1               | 0 |
| Unknown                | 1               | 0 |
| Unknown                | 1               | 0 |
| picklockskill          | 1               | 0 |
| Unknown5               | 3               | 0 |
| Item Id                | 4               | 255,255,255,255 |
| Player Id              | 2               |                                         |
| Unknown                | 2               |                                         |

## Neighborhood List (Server -> Client)

| Name                               | Number of Bytes          | Description                                                              |
|------------------------------------|--------------------------|--------------------------------------------------------------------------|
| Network OpCode                     | 2                        | 0x0D                                                                     |
| Packet Sequence Number             | 2                        | Identifies order of fragments                                            |
| Total length of combined fragments | 3                        | Total size of all fragments. This is only present in the first fragment. |
| Application OpCode                 | 2                        | 0x125C (Possibly?)                                                       |
| Unknown                            | 4                        | An id? Different across servers                                          |
| Unknown                            | 5                        | Always 6,0,0,0,0                                                         |
| Total # of Neighborhoods           | 2                        |                                                                          |
| Unknown                            | 5                        | Always 1,1,0,0,0                                                         |
| Neighborhood ID                    | 4                        |                                                                          |
| Neighborhood Name Length           | 4                        |                                                                          |
| Neighborhood Name                  | Neighborhood Name Length | Not null terminated                                                      |
| Guild ID                           | 4                        | 0 if no guild is associated with this neighborhood, otherwise it is the Guild ID           |
| Unknown                            | 4                        | If Guild ID is 0, this is also 0. If Guild ID is not 0, this is always 147,0,0,0                 |
| Max Player Plots                   | 4                        | Always 71                                                                       |
| Used Player Plots                  | 4                        |                                                                          |
| Max Guild Plots                    | 4                        | Always 4                                                                        |
| Used Guild Plots                   | 4                        |                                                                          |

Once the first neighborhood is parsed, the format repeats for the next Neighborhood ID -> Used Guild Plots. This continues until the last neighborhood is parsed.

## Searching for neighborhoods (or clicking on a specific one) (Client -> Server)

| Name                     | Number of Bytes          | Description                                                    |
|--------------------------|--------------------------|----------------------------------------------------------------|
| Network OpCode           | 2                        | 0x09                                                           |
| Packet Sequence Number   | 2                        |                                                                |
| Application OpCode       | 2                        | 0x125C (Possibly?)                                             |
| Search Type              | 4                        | 0 when searching for a player or guild.<br/>2 when clicking to view details of a specific neighborhood.<br/>4 when inside a neighborhood and searching specific addresses. |
| Neighborhood ID          | 4                        | 1 if searching for a player. The Neighborhood ID if clicking on a neighborhood entry. |
| Unknown                  | 4                        | 0s
| Neighborhood Search Criteria | 80                   | A neighborhood's name. 79 bytes plus 1 for the null terminator. |
| Player Search Criteria   | 64                       | A player's name. 63 bytes plus 1 for the null terminator. |
| Guild Search Criteria    | 64                       | A guild's name. 63 bytes plus 1 for the null terminator. |
| Unknown                  | 2                        | Always 1,1                                  |

## Response to click to get neighborhood details (Server -> Client)

| Name                   | Number of Bytes    | Description         |
|------------------------|--------------------|---------------------|
| Network OpCode         | 2                  | 0x09                |
| Packet Sequence Number | 2                  |                     |
| Application OpCode     | 2                  | 0x125C (Possibly?)  |
| Unknown                | 4                  | 173,153,9,0         |
| Unknown                | 1                  | 10                  |
| Unknown                | 4                  | 2,0,0,0             |
| # of Players           | 2                  |                     |
| Player Name Length     | 4                  |                     |
| Player Name            | Player Name Length | Not null terminated |
| # of Guilds            | 2                  |                     |
| Guild ID               | 4                  |                     |
| Guild Terminator       | 4                  | 147,0,0,0           |

If # of Players is greater than 0, the fields Player Name Length and Player Name repeat. The same is true for # of Guilds.

## Click on a property marker (Server -> Client) (this is not fully identified yet)

| Name                   | Number of Bytes | Description                      |
|------------------------|-----------------|----------------------------------|
| Network OpCode         | 2               | 0x09                             |
| Packet Sequence Number | 2               |                                  |
| Application OpCode     | 2               | 0x2254                           |
| Neighborhood Id        | 4               | Need to confirm                  |
| Unknown                | 7               |                                  |
| Unknown                | 4               | Not sure yet                     |
| Unknown                | 4               | Not sure yet                     |
| Unknown                | 4               | 123,0,0,0 (may not be constant)  |
| Unknown                | 4               | 107,0,0,0                        |
| Unknown                | 21              | 0                                |
| Unknown                | 4               | 45,0,0,0                         |
| Neighborhood Name      | 45              | At least 45, not null terminated |
| Unknown                | 8               | 0                                |
| Unknown                | 4               | 105,0,0,0                        |
| Unknown                | 4               | 0                                |
| Unknown                | 7               | 5,0,0,0,0,0,0                    |

## Real Estate Items window, Click on Trophies button (Client -> Server)
Possible new opcode: 0xA02F
Length: 342 bytes

| Name                   | Number of Bytes | Description                      |
|------------------------|-----------------|----------------------------------|
| Network OpCode         | 2               | 0x09                             |
| Packet Sequence Number | 2               |                                  |
| Application OpCode     | 2               | 0xA02F                           |
| Unknown                | 4               | 0                    |
| Unknown                | 4               | 1                    |
| Unknown                | 328             | 0                    |

TODO: In-zone clicks for the spring, purchasing a property, placing items in a property, identifying RoF opcodes, updating with additional vendors, fixing Z for existing vendors (some are floating), adding house interior zones (first attempt results in a client crash), etc.