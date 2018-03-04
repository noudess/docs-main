Note: PVP Is currently a work in progress.

To emulate the original Everquest PVP servers, change the World:PVPSettings to the following values:
```
1 = Rallos Zek RuleSet, (NOT SUPPORTED)
2 = Tallon/Vallon Zek Ruleset,  (NOT SUPPORTED)
4 = Sullon Zek Ruleset,  (PARTIALLY SUPPORTED)
6 = Discord Ruleset,  (PARTIALLY SUPPORTED)
anything above 6 is the Discord Ruleset without the no-drop restrictions removed.
```

You can customize beyond the original EQ PVP Rulesets using the following rules:
```
World:PVPMinLevel - default 0, minimum level to pvp
World:PVPUseDeityBasedPVPdeity default false, is used to determine if a player can attack another.
World:PVPLevelDifference default 0, if value is greater than 0, players with a difference greater than value will not be attackable
World:PVPLoseExperienceLevelDifference default 0, if value is greater than 0, players lose experience if killed by a player within level difference
World:PVPPetDamageMitigation default 50, pet damage is mitigated by this amount
World:PVPMeleeMitigation default 67, melee is mitigated by this amount
World:PVPSpellMitigation default 67, spells are mitigated by this amount
World:PVPRangedMitigation default 80, ranged attacks are mitigated by this amount
```
