Player Housing was introduced in the House of Thule expansion. It can be accessed from the Guild Lobby and allows for players to purchase houses and place items in their houses. Houses do require upkeep to maintain.

There is a single zone for all neighborhood instances (Sunrise Hills).

To my knowledge, no work has been done to add player housing to EQEMU. If it has, it hasn't been made public as no emu server has this capability as far as I am aware.

This page has packet information from Live as of 12/28/2018. While it is likely that the OpCodes have changed since House of Thule was released, my hope is that the structure of each packet has remained largely unchanged.

[TODO: Add image of neighborhood search window]

## Neighborhood List

| Name                               | Number of Bytes          | Description                                                              |
|------------------------------------|--------------------------|--------------------------------------------------------------------------|
| Network OpCode                     | 2                        | 0x0D                                                                     |
| Packet Sequence Number             | 2                        | Identifies order of fragments                                            |
| Total length of combined fragments | 3                        | Total size of all fragments. This is only present in the first fragment. |
| Application OpCode                 | 2                        | 0x125c (Possibly?)                                                       |
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

TODO: Document click event that retrieves list, click to get neighborhood entry details, response to click on neighborhood entry (have it, need to write it up), plus ALL of the rest. =P