
Logging categories have their settings stored in the [logsys_categories](/database/logsys_categories) table, but the categories are defined in [common/eqemu_logsys.h](https://github.com/EQEmu/Server/blob/master/common/eqemu_logsys.h)

```
select * from logsys_categories;
+-----------------+------------------------------------+----------------+-------------+--------------+
| log_category_id | log_category_description           | log_to_console | log_to_file | log_to_gmsay |
+-----------------+------------------------------------+----------------+-------------+--------------+
|               1 | AA                                 |              0 |           0 |            0 |
|               2 | AI                                 |              0 |           0 |            0 |
|               3 | Aggro                              |              0 |           0 |            0 |
|               4 | Attack                             |              0 |           0 |            0 |
|               5 | Packet: Client -> Server           |              0 |           0 |            0 |
|               6 | Combat                             |              0 |           0 |            0 |
|               7 | Commands                           |              0 |           0 |            0 |
|               8 | Crash                              |              1 |           1 |            0 |
|               9 | Debug                              |              0 |           0 |            0 |
|              10 | Doors                              |              0 |           0 |            0 |
|              11 | Error                              |              1 |           1 |            0 |
|              12 | Guilds                             |              0 |           0 |            0 |
|              13 | Inventory                          |              0 |           0 |            0 |
|              14 | Launcher                           |              1 |           1 |            0 |
|              15 | Netcode                            |              0 |           0 |            0 |
|              16 | Normal                             |              1 |           1 |            0 |
|              17 | Object                             |              0 |           0 |            0 |
|              18 | Pathing                            |              0 |           0 |            0 |
|              19 | QS_Server                          |              0 |           0 |            0 |
|              20 | Quests                             |              0 |           0 |            0 |
|              21 | Rules                              |              0 |           0 |            0 |
|              22 | Skills                             |              0 |           0 |            0 |
|              23 | Spawns                             |              0 |           0 |            0 |
|              24 | Spells                             |              0 |           0 |            0 |
|              25 | Status                             |              1 |           1 |            0 |
|              26 | TCP_Connection                     |              0 |           0 |            0 |
|              27 | Tasks                              |              0 |           0 |            0 |
|              28 | Tradeskills                        |              0 |           0 |            0 |
|              29 | Trading                            |              0 |           0 |            0 |
|              30 | Tribute                            |              0 |           0 |            0 |
|              31 | UCS_Server                         |              1 |           1 |            0 |
|              32 | WebInterface_Server                |              1 |           1 |            0 |
|              33 | World_Server                       |              1 |           1 |            0 |
|              34 | Zone Server                        |              1 |           1 |            0 |
|              35 | MySQL Error                        |              1 |           1 |            1 |
|              36 | MySQL Queries                      |              0 |           0 |            0 |
|              37 | Mercenaries                        |              0 |           0 |            0 |
|              38 | Quest Debug                        |              0 |           0 |            1 |
|              39 | Packet: Server -> Client           |              0 |           0 |            0 |
|              40 | Packet: Client -> Server Unhandled |              0 |           0 |            0 |
|              41 | Packet: Server -> Client With Dump |              0 |           0 |            0 |
|              42 | Packet: Server -> Client With Dump |              0 |           0 |            0 |
|              43 | Loginserver                        |              1 |           0 |            0 |
|              44 | Client Login                       |              1 |           1 |            1 |
+-----------------+------------------------------------+----------------+-------------+--------------+
44 rows in set (0.05 sec)
```
