Player Housing was introduced in the House of Thule expansion. It can be accessed from the Guild Lobby and allows for players to purchase houses and place items in their houses. Houses do require upkeep to maintain.

There is a single zone for all neighborhood instances (Sunrise Hills). House zones are separate and appear to be spread across a variety of .zon files (e.g. phinterior1a1.zon) based on the type of home purchased.

To my knowledge, no work has been done to add player housing to EQEMU. If it has, it hasn't been made public as no emu server has this capability as far as I am aware.

This page has packet information from Live as of 12/28/2018. While it is likely that the OpCodes have changed since House of Thule was released, my hope is that the structure of each packet has remained largely unchanged.

[TODO: Add image of neighborhood search window]

## Click on door to view Neighborhood List (Client -> Server)

| Name                   | Number of Bytes | Description                             |
|------------------------|-----------------|-----------------------------------------|
| Network OpCode         | 2               | 0x09                                    |
| Packet Sequence Number | 2               |                                         |
| Application OpCode     | 2               | OP_ClickDoor<br/>- Live: 0x2254<br/>- RoF2: 0x3A8F |
| Unknown                | 12              | Live: 38,0,0,0,0,0,0,0,255,255,255,255<br/>RoF2: 77,0,0,0,0,0,0,0,255,255,255,255 |
| Unknown                | 4               | Varies                                  |

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

TODO: In-zone clicks for the spring, purchasing a property, placing items in a property, identifying RoF opcodes, etc.