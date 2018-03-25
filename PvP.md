Note: PVP Is currently a work in progress.

To emulate the original Everquest PVP servers, the only rule you have to adjust is the PVPSettings one.

## World:PVPSettings

|Value|Name|Desc|
|:--|:--|:--|
|0|Disabled|Default, No PVP Enabled|
|1|Rallos Zek|Not yet supported|
|2|TZ/VZ|Partial Support|
|4|Sullon Zek|Partial support|
|6|Discord|Partial Support|
|7+|Discord+ (Any value above 6)|Discord without the no-drop restrictions removed|

Rules from this point onward are optional, and allow you the ability to customize your PVP server beyond the classic PVP rules. If you enable PVPSettings then adjust the below, most values will override defaults. Some exceptions include PVPLootCoin (once true by above PVPSettings, it cannot be turned off without setting PVPSettings to 0).

### World:PVPMinLevel
Default|RZ|TV/VZ|SZ|Description
:--|:--|:--|:--|:--|
0|1|?|6|minimum level pvp is enabled



### World:PVPUseDeityBasedPVP
Default|RZ|TV/VZ|SZ|Description
:--|:--|:--|:--|:--|
false|false|false|true|use deity based pvp alignment (agnostic is neutral)


### World:PVPUseTeamsBySizeBasedPVP
Default|RZ|TV/VZ|SZ|Description
:--|:--|:--|:--|:--|
false|false|true|false|use racial size based pvp alignment (drakkin is human group)

The teams are as follows:
* Team 1: Human, Barbarian, Erudite, Drakkin
* Team 2: Gnome, Halfling, Dwarf, Froglok
* Team 3: High Elf, Wood Elf, Half Elf, Vahshir
* Team 4: Dark Elf, Ogre, Troll, Iksar
* **Note: The above teams may be inaccurate. If you can source a reference to correct this, please let Shin know**

### World:PVPLevelDifference
Default|RZ|TV/VZ|SZ|Description
:--|:--|:--|:--|:--|
0|4|?|6|players with a difference greater than value will not be attackable

### World:PVPLoseExperienceLevelDifference
Default|RZ|TV/VZ|SZ|Description
:--|:--|:--|:--|:--|
0|0|?|5|players lose experience if killed by a player within level difference

### World:PVPPetDamageMitigation
Default|RZ|TV/VZ|SZ|Description
:--|:--|:--|:--|:--|
50|100|?|?|pet damage is mitigated by this amount

### World:PVPMeleeMitigation
Default|RZ|TV/VZ|SZ|Description
:--|:--|:--|:--|:--|
67|100|?|?|melee is mitigated by this amount

### World:PVPSpellMitigation
Default|RZ|TV/VZ|SZ|Description
:--|:--|:--|:--|:--|
67|67|?|?|spells are mitigated by this amount

### World:PVPRangedMitigation
Default|RZ|TV/VZ|SZ|Description
:--|:--|:--|:--|:--|
80|100|?|?|ranged attacks are mitigated by this amount

### World:PVPCanLootCoin
Default|RZ|TV/VZ|SZ|Description
:--|:--|:--|:--|:--|
false|true|true|true|Can players loot coin from player corpses?

### Spells:PVPRootBreakFromSpells
Default|RZ|TV/VZ|SZ|Description
:--|:--|:--|:--|:--|
75|75|75|75|Chance for root to break when cast on by a client (20% more than native root)

### Character:PVPRespawnManaPercent
Default|RZ|TV/VZ|SZ|Description
:--|:--|:--|:--|:--|
100|0|0|0|Percent of mana to respawn with

### Inventory:PVPCanLootNoTrade
Default|RZ|TV/VZ|SZ|Description
:--|:--|:--|:--|:--|
false|false|false|false|Can players loot no trade items from player corpses?

### Inventory:PVPCanLootContainer
Default|RZ|TV/VZ|SZ|Description
:--|:--|:--|:--|:--|
false|false|false|false|Can players loot bags/containers from player corpses?

### Inventory:PVPLootableEquipSlots
Default|RZ|TV/VZ|SZ|Description
:--|:--|:--|:--|:--|
0|0|0|0|When looting a player's corpse, equipped items in slots listed here are lootable. 0 means all slots are lootable
