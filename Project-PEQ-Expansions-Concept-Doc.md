# Project-PEQ-Expansions

This document describes the challenges and solutions to creating a dynamic-expansion supported PEQ baseline.

## Areas of Concern
- Load data based on expansion: Add a new expansion TINYINT(4)? to many tables to allow dynamic loading.
  - aa tables: This is handled I believe with db_string? Verify
  - account: This has an expansion field however it used to limit a specific account with a lesser-version expansion. Rule should be honored for the global expansion version
  - adventure_template: Since multiple expansions add different styles of adventures, add support for this.
  - char_create_combinations: expansions_req contains this data
  - doors: Does this need expansion? I'm leaning no, zone will determine
  - items: may need expansion to ensure merchants, global_loot are not populated with out of era items
  - spawn2: need expansion to disable spawning of certain npcs
  - spells_new: needs a way to discern expansion for allowing certain spells.
  - starting_items: perhaps just honor if an item is of a proper expansion or not?
  - titles: may need expansion?
  - tradeskill_recipe: needs expansion
  - zone: will not be able to zone into an area unless you are GM status or have the expansion enabled.
- Quests
  - Perhaps add a feature to prefix a quest file with an expansion to enable/disable it? Especially useful for things like player.pl/player.lua.
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