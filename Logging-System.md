### Preface

* EQEmu used to have many different logging systems in its past. They all were configured differently, all had different configuration formats. In 2015 - a much needed massive overhaul to our logging was made and it has been one of the most valuable things to our project to date.

### Features

* Log levels
* Hot-Reload of log settings
* In game, real time server logs
* Debug levels
* Categories (Spells, Merchants, Loot etc.)

### Output formats

* Console
* File
* In game (gmsay)
* Can easily be extended to be implemented with other output sinks

### Debug Levels

**Level**||**Description**
-----|-----|-----
General|1|Low-Level general debugging, useful info on single line|
Moderate|2|Informational based - used in functions|
Detail|3|Use this for extreme detail in logging, usually in extreme debugging in the stack or interprocess communication|

*   Debug levels are PER category, so if you wanted to set for example, level 3 debugging enabled to gmsay (In Game) but only 1 to your console, you put respectively 1 in your console field and 3 in gmsay for whatever category it is your enable

### Settings

*   All settings are managed in **logsys_categories** database table
*   When a process boots up, such as **zone/world/ucs/queryserv/etc**. \- These settings will load and whatever applies to the server category wise is what it will use as **'rules'** to understand where to send output, as well as what level of information (high or low) to display
    *   Please note that **log\_to\_gmsay** is only available for **Zone level debugging.**

## In-Game Commands

**Command**|**Description**|
-----|-----
#logs | Displays usage menu
#logs reload_all | Reload all settings in world and all zone processes with what is defined in the database
#logs list_settings | Shows current log settings and categories loaded into the current process' memory
#logs set \[console\|file\|gmsay\] | Sets log settings during the lifetime of the zone

```
#logs set [gmsay|file|console] [category_id] [log_level]
```

## File Logs

*   All **zone logs** go underneath a respective **logs/zone/**
    *   All zones, once booted up, will have a name that actually means something to a server administrator:
        *   nexus\_version\_0\_inst\_id\_0\_port\_7000\_20084.log
        *   nexus\_version\_0\_inst\_id\_0\_port\_7000\_24356.log
        *   zone_20084.log \- A zone that has been booted up as a dynamic, but not assigned to any logical zone yet
*   Crash Logs will make their way underneath `logs/crash`
*   All other process logs go to the top level of logs, this may change
*   Naming Convention:
    *   Unless a zone is using zone properties for the file name, most processes will look like the following convention
        *   process\_name\_process_id.log

## Example Output Screenshots

### GM-Say

<p align="center">
<img src="/EQEmu/Server/wiki/images/FaWAgAq.gif?raw=true">
</p>

### Windows Console of Zone

![](https://i.imgur.com/okWg2y8.png)

## Linux Console

ANSI Color support

![](https://i.imgur.com/SC9lO4N.png)

