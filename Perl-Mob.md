```perl
$mob->IsClient() #bool
$mob->IsNPC() #bool
$mob->IsMob() #bool
$mob->IsCorpse() #bool
$mob->IsPlayerCorpse() #bool
$mob->IsNPCCorpse() #bool
$mob->IsObject() #bool
$mob->IsDoor() #bool
$mob->IsTrap() #bool
$mob->IsBeacon() #bool
$mob->CastToClient() #void
$mob->CastToNPC() #void
$mob->CastToMob() #void
$mob->CastToCorpse() #void
$mob->GetID() #uint
$mob->GetName() #string
$mob->Depop( StartSpawnTimer) #void
$mob->RogueAssassinate( other) #void
$mob->BehindMob( other) #bool
$mob->SetLevel( in_level,  command) #void
$mob->GetSkill( skill_num) #uint
$mob->SendWearChange( material_slot) #void
$mob->GetEquipment( material_slot) #int
$mob->GetEquipmentMaterial( material_slot) #int
$mob->GetEquipmentColor( material_slot) #int
$mob->GetArmorTint( material_slot) #int
$mob->IsMoving() #bool
$mob->GoToBind() #void
$mob->Gate() #void
$mob->Attack( other,  Hand) #bool
$mob->Damage(string from,  damage, int spell_id,  attack_skill,  avoidable) #void
$mob->RangedAttack( other) #void
$mob->ThrowingAttack( other) #void
$mob->Heal() #void
$mob->HealDamage( amount,  caster) #void
$mob->SetMaxHP() #void
$mob->GetLevelCon( iOtherLevel) #uint
$mob->SetHP( hp) #void
$mob->DoAnim( animnum,  type) #void
$mob->ChangeSize( in_size,  bNoRestriction) #void
$mob->GMMove(float x, float y, float z, float heading) #void
$mob->SendPosUpdate( iSendToSelf) #void
$mob->SendPosition() #void
$mob->HasProcs() #bool
$mob->IsInvisible( other) #bool
$mob->SetInvisible( state) #void
$mob->FindBuff( spellid) #bool
$mob->FindType( type,  bOffensive) #bool
$mob->GetBuffSlotFromType( type) #int
$mob->MakePet(int spell_id,  pettype, string name) #void
$mob->MakeTempPet(int spell_id, string name) #void
$mob->TypesTempPet( typesid, string name) #void
$mob->GetBaseRace() #uint
$mob->GetBaseGender() #uint
$mob->GetDeity() #uint
$mob->GetRace() #uint
$mob->GetGender() #uint
$mob->GetTexture() #uint
$mob->GetHelmTexture() #uint
$mob->GetHairColor() #uint
$mob->GetBeardColor() #uint
$mob->GetEyeColor1() #uint
$mob->GetEyeColor2() #uint
$mob->GetHairStyle() #uint
$mob->GetLuclinFace() #uint
$mob->GetBeard() #uint
$mob->GetDrakkinHeritage() #uint
$mob->GetDrakkinTattoo() #uint
$mob->GetDrakkinDetails() #uint
$mob->GetClass() #uint
$mob->GetLevel() #uint
$mob->GetCleanName() #string
$mob->GetTarget() #void
$mob->SetTarget( mob) #void
$mob->GetHPRatio() #double
$mob->IsWarriorClass() #bool
$mob->GetHP() #int
$mob->GetMaxHP() #int
$mob->GetItemHPBonuses() #int
$mob->GetSpellHPBonuses() #int
$mob->GetSpellIDFromSlot( slot) #int
$mob->GetWalkspeed() #double
$mob->GetRunspeed() #double
$mob->GetCasterLevel(int spell_id) #int
$mob->GetMaxMana() #int
$mob->GetMana() #int
$mob->SetMana( amount) #void
$mob->GetManaRatio() #double
$mob->GetAC() #uint
$mob->GetATK() #uint
$mob->GetSTR() #int
$mob->GetSTA() #int
$mob->GetDEX() #int
$mob->GetAGI() #int
$mob->GetINT() #int
$mob->GetWIS() #int
$mob->GetCHA() #int
$mob->GetMR() #int
$mob->GetFR() #int
$mob->GetDR() #int
$mob->GetPR() #int
$mob->GetCR() #int
$mob->GetCorruption() #int
$mob->GetPhR() #int
$mob->GetMaxSTR() #int
$mob->GetMaxSTA() #int
$mob->GetMaxDEX() #int
$mob->GetMaxAGI() #int
$mob->GetMaxINT() #int
$mob->GetMaxWIS() #int
$mob->GetMaxCHA() #int
$mob->GetActSpellRange(int spell_id,  range) #double
$mob->GetActSpellDamage(int spell_id,  value) #int
$mob->GetActSpellHealing(int spell_id,  value) #int
$mob->GetActSpellCost(int spell_id,  cost) #int
$mob->GetActSpellDuration(int spell_id, int duration) #int
$mob->GetActSpellCasttime(int spell_id,  casttime) #int
$mob->ResistSpell( ressit_type, int spell_id,  caster) #double
$mob->GetSpecializeSkillValue(int spell_id) #uint
$mob->GetNPCTypeID() #uint
$mob->IsTargeted() #bool
$mob->GetX() #double
$mob->GetY() #double
$mob->GetZ() #double
$mob->GetHeading() #double
$mob->GetWaypointX() #double
$mob->GetWaypointY() #double
$mob->GetWaypointZ() #double
$mob->GetWaypointH() #double
$mob->GetWaypointPause() #uint
$mob->GetWaypointID() #uint
$mob->SetCurrentWP( waypoint) #void
$mob->GetSize() #double
$mob->SetFollowID( id) #void
$mob->GetFollowID() #uint
$mob->Message( type, string message) #void
$mob->Message_StringID( type,  string_id, int distance) #void
$mob->Say( format) #void
$mob->Shout( format) #void
$mob->Emote( format) #void
$mob->InterruptSpell( spellid) #void
$mob->CastSpell(int spell_id, int target_id,  slot) #void
$mob->SpellFinished(int spell_id,  spell_target) #void
$mob->IsImmuneToSpell(int spell_id,  caster) #bool
$mob->BuffFadeBySpellID(int spell_id) #void
$mob->BuffFadeByEffect( effectid,  skipslot) #void
$mob->BuffFadeAll() #void
$mob->BuffFadeBySlot( slot,  iRecalcBonuses) #void
$mob->CanBuffStack( spellid,  caster_level,  iFailIfOverwrite) #int
$mob->IsCasting() #bool
$mob->CastingSpellID() #uint
$mob->SetAppearance( app,  iIgnoreSelf) #void
$mob->GetAppearance() #uint
$mob->GetRunAnimSpeed() #uint
$mob->SetRunAnimSpeed( in) #void
$mob->SetPetID( NewPetID) #void
$mob->GetPetID() #uint
$mob->SetOwnerID( NewOwnerID) #void
$mob->GetOwnerID() #uint
$mob->GetPetType() #uint
$mob->GetBodyType() #uint
$mob->Stun(int duration) #void
$mob->Spin() #void
$mob->Kill() #void
$mob->SetInvul( invul) #void
$mob->GetInvul() #bool
$mob->SetExtraHaste( Haste) #void
$mob->GetHaste() #int
$mob->GetHandToHandDamage() #int
$mob->CanThisClassDoubleAttack() #bool
$mob->CanThisClassDualWield() #bool
$mob->CanThisClassRiposte() #bool
$mob->CanThisClassDodge() #bool
$mob->CanThisClassParry() #bool
$mob->GetHandToHandDelay() #int
$mob->GetClassLevelFactor() #uint
$mob->Mesmerize() #void
$mob->IsMezzed() #bool
$mob->IsStunned() #bool
$mob->StartEnrage() #void
$mob->IsEnraged() #bool
$mob->GetReverseFactionCon( iOther) #int
$mob->IsAIControlled() #bool
$mob->GetAggroRange() #double
$mob->GetAssistRange() #double
$mob->SetPetOrder( i) #void
$mob->GetPetOrder() #int
$mob->IsRoamer() #bool
$mob->IsRooted() #bool
$mob->AddToHateList( other,  hate) #void
$mob->SetHate( other,  hate) #void
$mob->HalveAggro( other) #void
$mob->DoubleAggro( other) #void
$mob->GetHateAmount( tmob,  is_dam) #uint
$mob->GetDamageAmount( tmob) #uint
$mob->GetHateTop() #void
$mob->GetHateDamageTop( other) #void
$mob->GetHateRandom() #void
$mob->IsEngaged() #bool
$mob->HateSummon() #bool
$mob->FaceTarget( MobToFace) #void
$mob->SetHeading( iHeading) #void
$mob->WipeHateList() #void
$mob->CheckAggro( other) #bool
$mob->CalculateHeadingToTarget( in_x,  in_y) #int
$mob->CalculateNewPosition(float x, float y, float z,  speed,  checkZ) #bool
$mob->CalculateNewPosition2(float x, float y, float z,  speed,  checkZ) #bool
$mob->CalculateDistance(float x, float y, float z) #double
$mob->SendTo( new_x,  new_y,  new_z) #void
$mob->SendToFixZ( new_x,  new_y,  new_z) #void
$mob->NPCSpecialAttacks( parse,  permtag,  reset,  remove) #void
$mob->DontHealMeBefore() #uint
$mob->DontBuffMeBefore() #uint
$mob->DontDotMeBefore() #uint
$mob->DontRootMeBefore() #uint
$mob->DontSnareMeBefore() #uint
$mob->GetResist( type) #int
$mob->GetShieldTarget() #void
$mob->SetShieldTarget( mob) #void
$mob->Charmed() #bool
$mob->GetLevelHP( tlevel) #uint
$mob->GetZoneID() #uint
$mob->CheckAggroAmount( spellid) #uint
$mob->CheckHealAggroAmount( spellid,  possible_heal_amt) #uint
$mob->GetAA( rank_id) #uint
$mob->GetAAByAAID( aa_id) #uint
$mob->SetAA( aa_id,  points, int charges) #bool
$mob->DivineAura() #bool
$mob->AddFeignMemory( attacker) #void
$mob->RemoveFromFeignMemory( attacker) #void
$mob->ClearFeignMemory() #void
$mob->SetOOCRegen( newoocregen) #void
$mob->GetEntityVariable( id) #string
$mob->EntityVariableExists( id) #bool
$mob->SetEntityVariable( id,  var) #void
$mob->GetHateList() #void
$mob->SignalClient( client,  data) #void
$mob->CombatRange( target) #bool
$mob->DoSpecialAttackDamage( target,  skill,  max_damage,  min_damage) #void
$mob->CheckLoS( mob) #bool
$mob->CheckLoSToLoc( loc_x,  loc_y,  loc_z,  mob_size) #bool
$mob->FindGroundZ( new_x,  new_y,  z_offset) #double
$mob->ProjectileAnim( mob, int item_id,  IsArrow,  speed,  angle,  tilt,  arc) #void
$mob->HasNPCSpecialAtk( parse) #bool
$mob->SendAppearanceEffect( parm1,  parm2,  parm3,  parm4,  parm5,  singleclient) #void
$mob->SetFlyMode( 0|1|2|3) #void
$mob->SetTexture( texture) #void
$mob->SetRace( race) #void
$mob->SetGender( gender) #void
$mob->SendIllusion( race,  gender,  texture,  helmtexture,  face,  hairstyle,  haircolor,  beard,  beardcolor,  drakkin_heritage,  drakkin_tattoo,  drakkin_details, int size) #void
$mob->CameraEffect(int duration,  intensity,  singleclient,  global) #void
$mob->SpellEffect( effect, int duration,  finish_delay,  zone_wide,  unk20,  perm_effect,  client) #void
$mob->TempName(string name) #void
$mob->GetItemStat( itemid,  stat) #int
$mob->SetSlotTint( material_slot,  red_tint,  green_tint,  blue_tint) #void
$mob->WearChange( material_slot,  texture, int color,  hero_forge_model) #void
$mob->DoKnockback( caster,  pushback,  pushup) #void
$mob->RemoveNimbusEffect( effectid) #void
$mob->SetRunning( value) #void
$mob->:IsRunning() #bool
$mob->SetBodyType( type,  overwrite_orig) #void
$mob->SetDeltas( delta_x,  delta_y,  delta_z,  delta_h) #void
$mob->SetLD( value) #void
$mob->SetTargetDestSteps( target_steps) #void
$mob->SetTargetable( on) #void
$mob->ModSkillDmgTaken( skill,  value) #void
$mob->GetModSkillDmgTaken( skill_num) #int
$mob->GetSkillDmgTaken( skill_num) #uint
$mob->SetAllowBeneficial( value) #void
$mob->GetAllowBeneficial() #bool
$mob->IsBeneficialAllowed( target) #bool
$mob->ModVulnerability( resist,  value) #void
$mob->GetModVulnerability( resist) #int
$mob->DoMeleeSkillAttackDmg( target,  weapon_damage,  skill,  chance_mod,  focus,  CanRiposte) #void
$mob->DoArcheryAttackDmg( target,  RangeWeapon) #void
$mob->DoThrowingAttackDmg( target,  RangeWeapon) #void
$mob->SetDisableMelee( value) #void
$mob->IsMeleeDisabled() #bool
$mob->SetFlurryChance( value) #void
$mob->GetFlurryChance() #uint
$mob->GetSpellStat( itemid,  stat,  slot) #int
$mob->GetSpecialAbility( special_ability) #int
$mob->GetSpecialAbilityParam( special_ability,  param) #int
$mob->SetSpecialAbility( ability,  value) #void
$mob->SetSpecialAbilityParam( ability,  param,  value) #void
$mob->ClearSpecialAbilities() #void
$mob->ProcessSpecialAbilities( str) #void
$mob->CanClassEquipItem(int item_id) #bool
$mob->IsFeared() #bool
$mob->IsBlind() #bool
$mob->SeeInvisible() #uint
$mob->SeeInvisibleUndead() #bool
$mob->SeeHide() #bool
$mob->SeeImprovedHide() #bool
$mob->GetNimbusEffect1() #uint
$mob->GetNimbusEffect2() #uint
$mob->GetNimbusEffect3() #uint
$mob->IsTargetable() #bool
$mob->HasShieldEquiped() #bool
$mob->HasTwoHandBluntEquiped() #bool
$mob->HasTwoHanderEquipped() #bool
$mob->GetHerosForgeModel( material_slot) #int
$mob->IsEliteMaterialItem( material_slot) #uint
$mob->GetBaseSize() #double
$mob->HasOwner() #bool
$mob->IsPet() #bool
$mob->HasPet() #bool
$mob->IsSilenced() #bool
$mob->IsAmnesiad() #bool
$mob->changelastname->(string name) #void
$mob->clearlastname->() #void

```