Client is a class exported to Perl that represent the Client object from EQEmu. All Client are also [Mob](Perl-Mob).

### Properties
```
client.null -- Returns true if this object is null
client.valid -- Returns true if this object is not null
```

### Member Functions
```perl
$client->AccountID() # uint
$client->AccountName() # string
$client->AddAAPoints(number) # void
$client->AddAlternateCurrencyValue(uint32 currency_id, int32 amount) # void
$client->AddCrystals(RadiantCount, EbonCount) # void
$client->AddEXP(add_exp, conlevel) # void
$client->AddLevelBasedExp(exp_percentage, int max_level) # void
$client->AddMoneyToPP(int copper, int silver, int gold, int platinum, updateclient) # void
$client->AddPVPPoints(Points) # void
$client->AddSkill(skillid, int value) # void
$client->Admin() # int
$client->AssignTask(TaskID, NPCID, bool enforce_level_requirement) # void
$client->AssignToInstance(int instance_id) # void
$client->AutoSplitEnabled() # bool
$client->BreakInvis() # void
$client->CalcPriceMod(other) # double
$client->CanHaveSkill(skill_id) # bool
$client->ChangeLastName(string in_lastname) # void
$client->CharacterID() # uint
$client->CheckIncreaseSkill(skillid, chancemodi) # bool
$client->CheckSpecializeIncrease(int spell_id) # void
$client->ClearCompassMark() # void
$client->ClearZoneFlag(int zone_id) # void
$client->Connected() # bool
$client->DecreaseByID(int type, amt) # bool
$client->DeleteItemInInventory(slot_id, int quantity) # void
$client->Disconnect() # void
$client->DropItem(slot_id) # void
$client->Duck() # void
$client->Escape() # void
$client->ExpeditionMessage(ExpdID, Message) # void
$client->FailTask(TaskID) # void
$client->ForageItem() # void
$client->GetAAExp() # uint
$client->GetAALevel(aaskillid) # uint
$client->GetAAPercent() # uint
$client->GetAAPoints() # uint
$client->GetAccountFlag(flag) # string
$client->GetAggroCount() # int
$client->GetAllMoney() # int
$client->GetAnon() # uint
$client->GetAugmentAt(int slot, aug_slot) # void
$client->GetAugmentIDAt(slot_id, augslot) # int
$client->GetBaseAGI() # uint
$client->GetBaseCHA() # uint
$client->GetBaseDEX() # uint
$client->GetBaseFace() # uint
$client->GetBaseINT() # uint
$client->GetBaseSTA() # uint
$client->GetBaseSTR() # uint
$client->GetBaseWIS() # uint
$client->GetBecomeNPCLevel() # uint
$client->GetBindHeading(index) # double
$client->GetBindX(index) # double
$client->GetBindY(index) # double
$client->GetBindZ(index) # double
$client->GetBindZoneID(index) # uint
$client->GetCarriedMoney() # int
$client->GetCharacterFactionLevel(faction_id) # int
$client->GetClientVersion() # uint
$client->GetClientVersionBit() # uint
$client->GetCorpseCount() # int
$client->GetCorpseID(corpse) # int
$client->GetCorpseItemAt(corpse_id, slotid) # int
$client->GetCustomItemData(slot_id, identifier) # string
$client->GetDiscSlotBySpellID(int spell_id) # int
$client->GetDuelTarget() # uint
$client->GetEbonCrystals() # uint
$client->GetEndurance() # uint
$client->GetEnduranceRatio() # uint
$client->GetEXP() # uint
$client->GetFace() # uint
$client->GetFactionLevel(int char_id, int npc_id, p_race, p_class, p_deity, pFaction, tnpc) # int
$client->GetFeigned() # bool
$client->GetFreeSpellBookSlot(start_slot) # int
$client->GetGM() # bool
$client->GetGroup() # void
$client->GetGroupPoints() # uint
$client->GetHorseId() # uint
$client->GetHunger() # int
$client->GetInstanceID() # uint
$client->GetInstrumentMod(int spell_id) # uint
$client->GetIP() # uint
$client->GetItemAt(int slot) # void
$client->GetItemIDAt(slot_id) # int
$client->GetItemInInventory(slot_id) # void
$client->GetLanguageSkill(n) # uint
$client->GetLastName() # string
$client->GetLDoNLosses() # uint
$client->GetLDoNLossesTheme(theme) # uint
$client->GetLDoNPointsTheme(theme) # uint
$client->GetLDoNWins() # uint
$client->GetLDoNWinsTheme(theme) # uint
$client->GetMaxEndurance() # uint
$client->GetModCharacterFactionLevel(faction_id) # int
$client->GetPVP() # bool
$client->GetPVPPoints() # uint
$client->GetRadiantCrystals() # uint
$client->GetRaid() # void
$client->GetRaidPoints() # uint
$client->GetRawItemAC() # int
$client->GetRawSkill(skill_id) # uint
$client->GetSkill(skill_id) # uint
$client->GetSkillPoints() # uint
$client->GetSpellBookSlotBySpellID(int spell_id) # int
$client->GetSpentAA() # uint
$client->GetStartZone() # uint
$client->GetTargetRingX() # double
$client->GetTargetRingY() # double
$client->GetTargetRingZ() # double
$client->GetTaskActivityDoneCount(TaskID, ActivityID) # int
$client->GetThirst() # int
$client->GetTotalSecondsPlayed() # uint
$client->GetWeight() # uint
$client->GMKill() # void
$client->GoFish() # void
$client->GrantAlternateAdvancementAbility(aa_id, points, ignore_cost) # bool
$client->GuildID() # uint
$client->GuildRank() # uint
$client->HasSkill(skill_id) # bool
$client->HasSpellScribed(int spell_id) # bool
$client->HasZoneFlag(int zone_id) # bool
$client->Hungry() # bool
$client->IncreaseLanguageSkill(skill_id, int value) # void
$client->IncreaseSkill(skill_id, int value) # void
$client->IncrementAA(aaskillid) # void
$client->IncStats(int type, increase_val) # void
$client->InZone() # bool
$client->IsBecomeNPC() # bool
$client->IsDueling() # bool
$client->IsGrouped() # bool
$client->IsLD() # bool
$client->IsMedding() # bool
$client->IsRaidGrouped() # bool
$client->IsSitting() # bool
$client->IsTaskActive(TaskID) # bool
$client->IsTaskActivityActive(TaskID, ActivityID) # bool
$client->IsTaskCompleted(TaskID) # bool
$client->KeyRingAdd(int item_id) # void
$client->KeyRingCheck(int item_id) # bool
$client->Kick() # void
$client->LearnRecipe(recipe_id) # void
$client->LeaveGroup() # void
$client->LoadZoneFlags() # void
$client->MarkCompassLoc(float x, float y, float z) # void
$client->MaxSkill(skillid, class, int level) # uint
$client->MemSpell(int spell_id, int slot, update_client) # void
$client->MovePC(zoneID, float x, float y, float z, float heading) # void
$client->MovePCInstance(zoneID, instanceID, float x, float y, float z, float heading) # void
$client->NPCSpawn(target_npc, option, respawntime) # void
$client->NukeItem(itemnum, where_to_check) # uint
$client->OpenLFGuildWindow() # void
$client->PlayMP3(fname) # void
$client->QuestReward(mob, int copper, int silver, int gold, int platinum, itemid, exp, faction) # void
$client->ReadBook(Book Text, Type) # void
$client->RefundAA() # void
$client->RemoveFromInstance(int instance_id) # void
$client->RemoveNoRent() # void
$client->ResetAA() # void
$client->ResetTrade() # void
$client->Save(iCommitNow) # bool
$client->SaveBackup() # void
$client->ScribeSpell(int spell_id, int slot, update_client) # void
$client->SendColoredText(int color, string message) # void
$client->SendMarqueeMessage(int type, int priority, int fade_in, int fade_out, int duration, msg) # void
$client->SendOPTranslocateConfirm(Caster, SpellID) # void
$client->SendSound() # void
$client->SendTargetCommand(in_entid) # void
$client->SendWebLink(website) # void
$client->SendZoneFlagInfo(to) # void
$client->SetAAPoints(points) # void
$client->SetAATitle(txt, save) # void
$client->SetAccountFlag(flag, int value) # void
$client->SetBaseClass(i) # void
$client->SetBaseGender(i) # void
$client->SetBaseRace(i) # void
$client->SetBecomeNPC(flag) # void
$client->SetBecomeNPCLevel(int level) # void
$client->SetBindPoint(to_zone) # void
$client->SetCustomItemData(slot_id, identifier, int value) # void
$client->SetDeity(i) # void
$client->SetDueling(duel) # void
$client->SetDuelTarget(set_id) # void
$client->SetEndurance(Endurance) # void
$client->SetEXP(set_exp, set_aaxp, resexp) # void
$client->SetFactionLevel(int char_id, int npc_id, char_class, char_race, char_deity) # void
$client->SetFactionLevel2(int char_id, faction_id, char_class, char_race, char_deity, int value, int temp) # void
$client->SetFeigned(in_feigned) # void
$client->SetGM(toggle) # void
$client->SetHorseId(horseid_in) # void
$client->SetHunger(in_hunger) # void
$client->SetHunger(in_hunger, in_thirst) # void
$client->SetLanguageSkill(langid, int value) # void
$client->SetMaterial(slot_id, int item_id) # void
$client->SetPVP(toggle) # void
$client->SetSkill(skill_num, int value) # void
$client->SetSkillPoints(inp) # void
$client->SetStartZone(zoneid , float x, float y, float z) # void
$client->SetStats(int type, increase_val) # void
$client->SetThirst(in_thirst) # void
$client->SetTint(slot_id, int color) # void
$client->SetTitleSuffix(txt, save) # void
$client->SetZoneFlag(int zone_id) # void
$client->SignalClient(data) # void
$client->SilentMessage(Message) # void
$client->SlotConvert2(int slot) # uint
$client->Stand() # void
$client->SummonItem(int item_id, int charges) # void
$client->TakeMoneyFromPP(int copper, updateclient) # bool
$client->TGB() # bool
$client->Thirsty() # bool
$client->TrainDiscBySpellID(int spell_id) # void
$client->Undye() # void
$client->UnmemSpell(int slot, update_client) # void
$client->UnmemSpellAll(update_client) # void
$client->UnmemSpellBySpellID(int spell_id) # void
$client->UnscribeSpell(int slot, update_client) # void
$client->UnscribeSpellAll(update_client) # void
$client->UntrainDisc(int slot, update_client) # void
$client->UntrainDiscAll(update_client) # void
$client->UpdateAdmin(bool iFromDB) # void
$client->UpdateGroupAAs(points, int type) # void
$client->UpdateLDoNPoints(points, theme) # bool
$client->UpdateTaskActivity(TaskID, ActivityID, Count, bool ignore_quest_update) # void
$client->UpdateWho(remove) # void
$client->UseDiscipline(int spell_id, target) # bool
$client->WorldKick() # void
```