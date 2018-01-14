```perl
$mob->AddFeignMemory(attacker) # void
$mob->AddToHateList(other, hate) # void
$mob->Attack(other, Hand) # bool
$mob->BehindMob(other) # bool
$mob->BuffFadeAll() # void
$mob->BuffFadeByEffect(effectid, skipslot) # void
$mob->BuffFadeBySlot(slot, iRecalcBonuses) # void
$mob->BuffFadeBySpellID(int spell_id) # void
$mob->CalculateDistance(float x, float y, float z) # double
$mob->CalculateHeadingToTarget(in_x, in_y) # int
$mob->CalculateNewPosition(float x, float y, float z, speed, checkZ) # bool
$mob->CalculateNewPosition2(float x, float y, float z, speed, checkZ) # bool
$mob->CameraEffect(int duration, intensity, singleclient, global) # void
$mob->CanBuffStack(spellid, caster_level, iFailIfOverwrite) # int
$mob->CanClassEquipItem(int item_id) # bool
$mob->CanThisClassDodge() # bool
$mob->CanThisClassDoubleAttack() # bool
$mob->CanThisClassDualWield() # bool
$mob->CanThisClassParry() # bool
$mob->CanThisClassRiposte() # bool
$mob->CastingSpellID() # uint
$mob->CastSpell(int spell_id, int target_id, slot) # void
$mob->CastToClient() # void
$mob->CastToCorpse() # void
$mob->CastToMob() # void
$mob->CastToNPC() # void
$mob->changelastname->(string name) # void
$mob->ChangeSize(in_size, bNoRestriction) # void
$mob->Charmed() # bool
$mob->CheckAggro(other) # bool
$mob->CheckAggroAmount(spellid) # uint
$mob->CheckHealAggroAmount(spellid, possible_heal_amt) # uint
$mob->CheckLoS(mob) # bool
$mob->CheckLoSToLoc(loc_x, loc_y, loc_z, mob_size) # bool
$mob->ClearFeignMemory() # void
$mob->clearlastname->() # void
$mob->ClearSpecialAbilities() # void
$mob->CombatRange(target) # bool
$mob->Damage(string from, damage, int spell_id, attack_skill, avoidable) # void
$mob->Depop(StartSpawnTimer) # void
$mob->DivineAura() # bool
$mob->DoAnim(animnum, type) # void
$mob->DoArcheryAttackDmg(target, RangeWeapon) # void
$mob->DoKnockback(caster, pushback, pushup) # void
$mob->DoMeleeSkillAttackDmg(target, weapon_damage, skill, chance_mod, focus, CanRiposte) # void
$mob->DontBuffMeBefore() # uint
$mob->DontDotMeBefore() # uint
$mob->DontHealMeBefore() # uint
$mob->DontRootMeBefore() # uint
$mob->DontSnareMeBefore() # uint
$mob->DoSpecialAttackDamage(target, skill, max_damage, min_damage) # void
$mob->DoThrowingAttackDmg(target, RangeWeapon) # void
$mob->DoubleAggro(other) # void
$mob->Emote(format) # void
$mob->EntityVariableExists(id) # bool
$mob->FaceTarget(MobToFace) # void
$mob->FindBuff(spellid) # bool
$mob->FindGroundZ(new_x, new_y, z_offset) # double
$mob->FindType(type, bOffensive) # bool
$mob->Gate() # void
$mob->GetAA(rank_id) # uint
$mob->GetAAByAAID(aa_id) # uint
$mob->GetAC() # uint
$mob->GetActSpellCasttime(int spell_id, casttime) # int
$mob->GetActSpellCost(int spell_id, cost) # int
$mob->GetActSpellDamage(int spell_id, value) # int
$mob->GetActSpellDuration(int spell_id, int duration) # int
$mob->GetActSpellHealing(int spell_id, value) # int
$mob->GetActSpellRange(int spell_id, range) # double
$mob->GetAggroRange() # double
$mob->GetAGI() # int
$mob->GetAllowBeneficial() # bool
$mob->GetAppearance() # uint
$mob->GetArmorTint(material_slot) # int
$mob->GetAssistRange() # double
$mob->GetATK() # uint
$mob->GetBaseGender() # uint
$mob->GetBaseRace() # uint
$mob->GetBaseSize() # double
$mob->GetBeard() # uint
$mob->GetBeardColor() # uint
$mob->GetBodyType() # uint
$mob->GetBuffSlotFromType(type) # int
$mob->GetCasterLevel(int spell_id) # int
$mob->GetCHA() # int
$mob->GetClass() # uint
$mob->GetClassLevelFactor() # uint
$mob->GetCleanName() # string
$mob->GetCorruption() # int
$mob->GetCR() # int
$mob->GetDamageAmount(tmob) # uint
$mob->GetDeity() # uint
$mob->GetDEX() # int
$mob->GetDR() # int
$mob->GetDrakkinDetails() # uint
$mob->GetDrakkinHeritage() # uint
$mob->GetDrakkinTattoo() # uint
$mob->GetEntityVariable(id) # string
$mob->GetEquipment(material_slot) # int
$mob->GetEquipmentColor(material_slot) # int
$mob->GetEquipmentMaterial(material_slot) # int
$mob->GetEyeColor1() # uint
$mob->GetEyeColor2() # uint
$mob->GetFlurryChance() # uint
$mob->GetFollowID() # uint
$mob->GetFR() # int
$mob->GetGender() # uint
$mob->GetHairColor() # uint
$mob->GetHairStyle() # uint
$mob->GetHandToHandDamage() # int
$mob->GetHandToHandDelay() # int
$mob->GetHaste() # int
$mob->GetHateAmount(tmob, is_dam) # uint
$mob->GetHateDamageTop(other) # void
$mob->GetHateList() # void
$mob->GetHateRandom() # void
$mob->GetHateTop() # void
$mob->GetHeading() # double
$mob->GetHelmTexture() # uint
$mob->GetHerosForgeModel(material_slot) # int
$mob->GetHP() # int
$mob->GetHPRatio() # double
$mob->GetID() # uint
$mob->GetINT() # int
$mob->GetInvul() # bool
$mob->GetItemHPBonuses() # int
$mob->GetItemStat(itemid, stat) # int
$mob->GetLevel() # uint
$mob->GetLevelCon(iOtherLevel) # uint
$mob->GetLevelHP(tlevel) # uint
$mob->GetLuclinFace() # uint
$mob->GetMana() # int
$mob->GetManaRatio() # double
$mob->GetMaxAGI() # int
$mob->GetMaxCHA() # int
$mob->GetMaxDEX() # int
$mob->GetMaxHP() # int
$mob->GetMaxINT() # int
$mob->GetMaxMana() # int
$mob->GetMaxSTA() # int
$mob->GetMaxSTR() # int
$mob->GetMaxWIS() # int
$mob->GetModSkillDmgTaken(skill_num) # int
$mob->GetModVulnerability(resist) # int
$mob->GetMR() # int
$mob->GetName() # string
$mob->GetNimbusEffect1() # uint
$mob->GetNimbusEffect2() # uint
$mob->GetNimbusEffect3() # uint
$mob->GetNPCTypeID() # uint
$mob->GetOwnerID() # uint
$mob->GetPetID() # uint
$mob->GetPetOrder() # int
$mob->GetPetType() # uint
$mob->GetPhR() # int
$mob->GetPR() # int
$mob->GetRace() # uint
$mob->GetResist(type) # int
$mob->GetReverseFactionCon(iOther) # int
$mob->GetRunAnimSpeed() # uint
$mob->GetRunspeed() # double
$mob->GetShieldTarget() # void
$mob->GetSize() # double
$mob->GetSkill(skill_num) # uint
$mob->GetSkillDmgTaken(skill_num) # uint
$mob->GetSpecialAbility(special_ability) # int
$mob->GetSpecialAbilityParam(special_ability, param) # int
$mob->GetSpecializeSkillValue(int spell_id) # uint
$mob->GetSpellHPBonuses() # int
$mob->GetSpellIDFromSlot(slot) # int
$mob->GetSpellStat(itemid, stat, slot) # int
$mob->GetSTA() # int
$mob->GetSTR() # int
$mob->GetTarget() # void
$mob->GetTexture() # uint
$mob->GetWalkspeed() # double
$mob->GetWaypointH() # double
$mob->GetWaypointID() # uint
$mob->GetWaypointPause() # uint
$mob->GetWaypointX() # double
$mob->GetWaypointY() # double
$mob->GetWaypointZ() # double
$mob->GetWIS() # int
$mob->GetX() # double
$mob->GetY() # double
$mob->GetZ() # double
$mob->GetZoneID() # uint
$mob->GMMove(float x, float y, float z, float heading) # void
$mob->GoToBind() # void
$mob->HalveAggro(other) # void
$mob->HasNPCSpecialAtk(parse) # bool
$mob->HasOwner() # bool
$mob->HasPet() # bool
$mob->HasProcs() # bool
$mob->HasShieldEquiped() # bool
$mob->HasTwoHandBluntEquiped() # bool
$mob->HasTwoHanderEquipped() # bool
$mob->HateSummon() # bool
$mob->Heal() # void
$mob->HealDamage(amount, caster) # void
$mob->InterruptSpell(spellid) # void
$mob->IsAIControlled() # bool
$mob->IsAmnesiad() # bool
$mob->IsBeacon() # bool
$mob->IsBeneficialAllowed(target) # bool
$mob->IsBlind() # bool
$mob->IsCasting() # bool
$mob->IsClient() # bool
$mob->IsCorpse() # bool
$mob->IsDoor() # bool
$mob->IsEliteMaterialItem(material_slot) # uint
$mob->IsEngaged() # bool
$mob->IsEnraged() # bool
$mob->IsFeared() # bool
$mob->IsImmuneToSpell(int spell_id, caster) # bool
$mob->IsInvisible(other) # bool
$mob->IsMeleeDisabled() # bool
$mob->IsMezzed() # bool
$mob->IsMob() # bool
$mob->IsMoving() # bool
$mob->IsNPC() # bool
$mob->IsNPCCorpse() # bool
$mob->IsObject() # bool
$mob->IsPet() # bool
$mob->IsPlayerCorpse() # bool
$mob->IsRoamer() # bool
$mob->IsRooted() # bool
$mob->IsRunning() # bool
$mob->IsSilenced() # bool
$mob->IsStunned() # bool
$mob->IsTargetable() # bool
$mob->IsTargeted() # bool
$mob->IsTrap() # bool
$mob->IsWarriorClass() # bool
$mob->Kill() # void
$mob->MakePet(int spell_id, pettype, string name) # void
$mob->MakeTempPet(int spell_id, string name) # void
$mob->Mesmerize() # void
$mob->Message(type, string message) # void
$mob->Message_StringID(type, string_id, int distance) # void
$mob->ModSkillDmgTaken(skill, value) # void
$mob->ModVulnerability(resist, value) # void
$mob->NPCSpecialAttacks(parse, permtag, reset, remove) # void
$mob->ProcessSpecialAbilities(str) # void
$mob->ProjectileAnim(mob, int item_id, IsArrow, speed, angle, tilt, arc) # void
$mob->RangedAttack(other) # void
$mob->RemoveFromFeignMemory(attacker) # void
$mob->RemoveNimbusEffect(effectid) # void
$mob->ResistSpell(ressit_type, int spell_id, caster) # double
$mob->RogueAssassinate(other) # void
$mob->Say(format) # void
$mob->SeeHide() # bool
$mob->SeeImprovedHide() # bool
$mob->SeeInvisible() # uint
$mob->SeeInvisibleUndead() # bool
$mob->SendAppearanceEffect(parm1, parm2, parm3, parm4, parm5, singleclient) # void
$mob->SendIllusion(race, gender, texture, helmtexture, face, hairstyle, haircolor, beard, beardcolor, drakkin_heritage, drakkin_tattoo, drakkin_details, int size) # void
$mob->SendPosition() # void
$mob->SendPosUpdate(iSendToSelf) # void
$mob->SendTo(new_x, new_y, new_z) # void
$mob->SendToFixZ(new_x, new_y, new_z) # void
$mob->SendWearChange(material_slot) # void
$mob->SetAA(aa_id, points, int charges) # bool
$mob->SetAllowBeneficial(value) # void
$mob->SetAppearance(app, iIgnoreSelf) # void
$mob->SetBodyType(type, overwrite_orig) # void
$mob->SetCurrentWP(waypoint) # void
$mob->SetDeltas(delta_x, delta_y, delta_z, delta_h) # void
$mob->SetDisableMelee(value) # void
$mob->SetEntityVariable(id, var) # void
$mob->SetExtraHaste(Haste) # void
$mob->SetFlurryChance(value) # void
$mob->SetFlyMode(0|1|2|3) # void
$mob->SetFollowID(id) # void
$mob->SetGender(gender) # void
$mob->SetHate(other, hate) # void
$mob->SetHeading(iHeading) # void
$mob->SetHP(hp) # void
$mob->SetInvisible(state) # void
$mob->SetInvul(invul) # void
$mob->SetLD(value) # void
$mob->SetLevel(in_level, command) # void
$mob->SetMana(amount) # void
$mob->SetMaxHP() # void
$mob->SetOOCRegen(newoocregen) # void
$mob->SetOwnerID(NewOwnerID) # void
$mob->SetPetID(NewPetID) # void
$mob->SetPetOrder(i) # void
$mob->SetRace(race) # void
$mob->SetRunAnimSpeed(in) # void
$mob->SetRunning(value) # void
$mob->SetShieldTarget(mob) # void
$mob->SetSlotTint(material_slot, red_tint, green_tint, blue_tint) # void
$mob->SetSpecialAbility(ability, value) # void
$mob->SetSpecialAbilityParam(ability, param, value) # void
$mob->SetTarget(mob) # void
$mob->SetTargetable(on) # void
$mob->SetTargetDestSteps(target_steps) # void
$mob->SetTexture(texture) # void
$mob->Shout(format) # void
$mob->SignalClient(client, data) # void
$mob->SpellEffect(effect, int duration, finish_delay, zone_wide, unk20, perm_effect, client) # void
$mob->SpellFinished(int spell_id, spell_target) # void
$mob->Spin() # void
$mob->StartEnrage() # void
$mob->Stun(int duration) # void
$mob->TempName(string name) # void
$mob->ThrowingAttack(other) # void
$mob->TypesTempPet(typesid, string name) # void
$mob->WearChange(material_slot, texture, int color, hero_forge_model) # void
$mob->WipeHateList() # void
```