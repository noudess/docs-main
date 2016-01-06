NPC is a class exported to Lua that represent the NPC object from EQEmu. All NPC are also [Mob](Lua-Mob).

[Return to the Lua API](Lua-API)

### Properties
```
npc.null -- Returns true if this object is null
npc.valid -- Returns true if this object is not null
```

### Member Functions
```
NPC() -- Creates a null NPC
Void Signal(Integer id);
Integer CheckNPCFactionAlly(Integer faction);
Void AddItem(Integer item_id, Integer charges);
Void AddItem(Integer item_id, Integer charges, Boolean equip);
Void AddLootTable();
Void AddLootTable(Integer id);
Void RemoveItem(Integer item_id);
Void RemoveItem(Integer item_id, Integer quantity);
Void RemoveItem(Integer item_id, Integer quantity, Integer slot);
Void ClearItemList();
Void AddCash(Integer copper, Integer silver, Integer gold, Integer platinum);
Void RemoveCash();
Integer CountLoot();
Integer GetLoottableID();
Integer GetCopper();
Integer GetSilver();
Integer GetGold();
Integer GetPlatinum();
Void SetCopper(Integer amt);
Void SetSilver(Integer amt);
Void SetGold(Integer amt);
Void SetPlatinum(Integer amt);
Void SetGrid(Integer grid);
Void SetSaveWaypoint(Integer wp);
Void SetSp2(Integer sg2);
Integer GetWaypointMax();
Integer GetGrid();
Integer GetSp2();
Integer GetNPCFactionID();
Integer GetPrimaryFaction();
Integer GetNPCHate(Mob ent);
Boolean IsOnHatelist(Mob ent);
Void SetNPCFactionID(Integer id);
Integer GetMaxDMG();
Integer GetMinDMG();
Boolean IsAnimal();
Integer GetPetSpellID();
Void SetPetSpellID(Integer id);
Integer GetMaxDamage(Integer level);
Void SetTaunting(Boolean t);
Void PickPocket(Client thief);
Void StartSwarmTimer(Integer duration);
Void DoClassAttacks(Mob target);
Integer GetMaxWp();
Void DisplayWaypointInfo(Client to);
Void CalculateNewWaypoint();
Void AssignWaypoints(Integer grid);
Void SetWaypointPause();
Void UpdateWaypoint(Integer wp);
Void StopWandering();
Void ResumeWandering();
Void PauseWandering(Integer pause_time);
Void MoveTo(Real x, Real y, Real z, Real h, Boolean save);
Void NextGuardPosition();
Void SaveGuardSpot();
Void SaveGuardSpot(Boolean clear);
Boolean IsGuarding();
Void AI_SetRoambox(Real dist, Real max_x, Real min_x, Real max_y, Real min_y);
Void AI_SetRoambox(Real dist, Real max_x, Real min_x, Real max_y, Real min_y, Integer delay);
Integer GetNPCSpellsID();
Integer GetSpawnPointID();
Real GetSpawnPointX();
Real GetSpawnPointY();
Real GetSpawnPointZ();
Real GetSpawnPointH();
Real GetGuardPointX();
Real GetGuardPointY();
Real GetGuardPointZ();
Void SetPrimSkill(Integer skill_id);
Void SetSecSkill(Integer skill_id);
Integer GetPrimSkill();
Integer GetSecSkill();
Integer GetSwarmOwner();
Integer GetSwarmTarget();
Void SetSwarmTarget(Integer target);
Void ModifyNPCStat(String stat, String value);
Void AddAISpell(Integer priority, Integer spell_id, Integer type, Integer mana_cost, Integer recast_delay, Integer resist_adjust);
Void RemoveAISpell(Integer spell_id);
Void SetSpellFocusDMG(Integer focus);
Void SetSpellFocusHeal(Integer focus);
Integer GetSpellFocusDMG();
Integer GetSpellFocusHeal();
Real GetSlowMitigation();
Real GetAttackSpeed();
Integer GetAttackDelay();
Integer GetAccuracyRating();
Integer GetSpawnKillCount();
Integer GetScore();
Void MerchantOpenShop();
Void MerchantCloseShop();
Integer GetMerchantProbability();
Void SetMerchantProbability(Integer new_item_spawn_probability);
```