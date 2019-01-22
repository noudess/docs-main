# Project-PEQ-Expansions

This document describes the challenges and solutions to creating a dynamic-expansion supported PEQ baseline.

## Areas of Concern
- Load data based on expansion: Add a new expansion TINYINT(4)? to many tables to allow dynamic loading.
  - aa tables: This is handled I believe with db_string? Verify
  - account: This has an expansion field however it used to limit a specific account with a lesser-version expansion. Rule should be honored for the global expansion version
  - adventure_template: add expansions field
  - char_create_combinations: expansions_req contains this data
  - doors: add expansions field
  - fishing: add expansions field
  - forage: add expansions field
  - global_loot: add expansions field
  - ground_spawns: add expansions field
  - loottable: add expansions field
  - lootdrop: add expansions field
  - merchantlist: add expansions field
  - object: add expansions field
  - spawn2: add expansions field
  - spells_new: due to general nature of spells, and simplicity to simply replace, no expansions field.
  - starting_items - add expansions field
  - start_zones: add expansions field
  - titles: add expansions field
  - tradeskill_recipe: add expansions field
  - traps: add expansions field
  - tributes: add expansions field
  - zone: add expansions field
- Quests
  - Perhaps add a feature to prefix a quest file with an expansion to enable/disable it? Especially useful for things like player.pl/player.lua.
### Legacy Zones
```
[7:25 PM] Shin Noir: zone points may need expansions.. well, and zones in general.
What I would love to do personally, is add to PEQ "legacy" versions of zones, that are entirely new/unique inserts into zones. Maybe even a new shortname.

legacylavastorm
legacyecommons
legacywcommons
legacynektulous
and so on.
give them new unique zone id's and zone id numbers. They'll be disabled by default on PEQ, but perhaps if your expansion is less than when the revamps happen, it will attempt to load you into these legacy versions, the client will error about the zone not being found, but the server can be responsible with providing their player base with the old versions.
[7:25 PM] Shin Noir: doing the above means we can add npc_types, spawn2, and all other field data without touching the revamped ones.
[7:26 PM] Uleat: have to be careful using old as a prefix..there are valid names like oldcommonlands
[7:26 PM] Shin Noir: whatever we decide, it's just a generic example
```

### Combat
  - https://github.com/mackal/EQMechanics/wiki
```[PM] mackal: they used to have hardcaps on mitigation
[6:55 PM] mackal: which was easy to hit during kunark as a plat toon
[6:55 PM] mackal: plate
[6:56 PM] mackal: they added a softcap, then shield going over
[6:53 PM] mackal: combat system is basically the same
[6:53 PM] mackal: mostly just a change in mitigation calcs
[6:56 PM] mackal: then it basically stayed the same
```

```cpp
if IsClient():
  softcap = 350
  if GetClass() == WARRIOR and GetLevel() > 50:
    softcap = 430
  if (GetClass() == PALADIN or GetClass() == SHADOWKNIGHT or GetClass() == BARD) and GetLevel() > 50
    softcap = 403
  if (GetClass() == RANGER or GetClass() == ROGUE or GetClass() == MONK or GetClass() == BEASTLORD) and GetLevel() > 50
    softcap = 375

  cs_mod = 0
  cs_rank = GetAA(ComabtStability)
  if cs_rank == 1:
    cs_mod = 2
  elif cs_rank == 2:
    cs_mod = 5
  elif cs_rank == 3:
    cs_mod = 10

  softcap = softcap + (softcap * cs_mod / 100)

  if GetAA(PhysicalEnhancement):
    softcap = softcap + (2 * softcap / 100)

  if bonus <= softcap:
    return bonus

  if IsWarrior(): # melee, not priest/casters
    return (bonus - softcap) / 12 + softcap

  return softcap # hardcapped for everyone else
```