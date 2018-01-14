Perl general functions are wrapped within the quest type.

```perl
quest::activespeakactivity() # int
quest::activespeaktask() # int
quest::activetasksinset() # int
quest::addldonloss(long losses, int theme_id) # void
quest::addldonpoints(long points, int theme_id) # void
quest::addldonwin(long wins, int theme_id) # void
quest::addloot(int item_id, int charges) # void
quest::AddNode(float x, float y, float z, float best_z, int requested_id) # void
quest::addskill(int skill_id, int int_value) # void
quest::AssignGroupToInstance() # void
quest::AssignRaidToInstance() # void
quest::assigntask(uint task_id, bool enforce_level_requirement) # void
quest::AssignToInstance() # void
quest::attack() # void
quest::attacknpc() # void
quest::attacknpctype() # void
quest::buryplayercorpse() # uint
quest::castspell(int spell_id, int target_id) # void
quest::changedeity() # void
quest::checktitle() # bool
quest::ChooseRandom() # void
quest::clear_npctype_cache() # void
quest::clear_proximity() # void
quest::clear_zone_flag() # void
quest::clearspawntimers() # void
quest::Client::new() # void
quest::collectitems(int item_id, bool remove_item) # void
quest::completedtasksinset() # int
quest::ConnectNodeToNode(int node1, int node2, int teleport, uint doorid) # void
quest::createBot(string firstname, string lastname, int level, int race_id, int class_id, int gender_id) # uint
quest::createdoor(string modelname, float x, float y, float z, float heading, int object_type, int size) # void
quest::creategroundobject(int item_id, float x, float y, float z, float heading, int decay_time) # void
quest::creategroundobjectfrommodel(string modelname, float x, float y, float z, float heading, int object_type, int decay_time) # void
quest::createguild(string guild_name, string leader_name) # void
quest::CreateInstance(string zone_name, int version, int duration) # void
quest::crosszonemessageplayerbyname(int channel_id, string name, string message) # void
quest::crosszonemessageplayerbyname(int channel_id, string name, string message) # void
quest::crosszonesetentityvariablebyclient_name(string client_name, string key, string str_value) # void
quest::crosszonesetentityvariablebynpctypeid(int npc_type_id, string key, string str_value) # void
quest::crosszonesignalclientbychar_id(int char_id, int int_value) # void
quest::crosszonesignalclientbychar_id(int char_id, int int_value) # void
quest::crosszonesignalclientbychar_id(string name, int int_value) # void
quest::crosszonesignalclientbychar_id(string name, int int_value) # void
quest::crosszonesignalnpcbynpctypeid(int npc_type_id, int int_value) # void
quest::debug(string message, int debug_level) # void
quest::delglobal() # void
quest::depop() # void
quest::depop_withtimer() # void
quest::depopall() # void
quest::depopzone() # void
quest::DestroyInstance() # void
quest::ding() # void
quest::disable_proximity_say() # void
quest::disable_spawn2() # void
quest::disablerecipe() # void
quest::disabletask(int task_id1, int task_id2, int task_id10) # void
quest::doanim() # void
quest::echo(int color_id, string message) # void
quest::emote() # void
quest::enable_proximity_say() # void
quest::enable_spawn2() # void
quest::enabledtaskcount() # int
quest::enablerecipe() # void
quest::enabletask(int task_id1, int task_id2, int task_id10) # void
quest::enabletitle() # void
quest::EntityList::new() # void
quest::exp() # void
quest::faction(int faction_id, int int_value, int temp) # void
quest::factionvalue() # void
quest::failtask() # void
quest::firsttaskinset() # int
quest::FlagInstanceByGroupLeader(uint zone, int version) # void
quest::FlagInstanceByRaidLeader(uint zone, int version) # void
quest::FlyMode() # void
quest::follow(int entity_id, int distance) # void
quest::forcedoorclose(int door_id, bool alt_mode) # void
quest::forcedooropen(int door_id, bool alt_mode) # void
quest::get_spawn_condition(string zone_short, int instance_id, int condition_id) # uint
quest::GetCharactersInInstance() # string
quest::getguildnamebyid() # string
quest::GetInstanceID(string zone_name, int version) # void
quest::GetInstanceTimer() # void
quest::GetInstanceTimerByID() # void
quest::getlevel() # uint
quest::getplayerburiedcorpsecount() # uint
quest::GetSpellResistType() # void
quest::GetSpellTargetType() # void
quest::gettaskactivitydonecount(uint task_id, uint activity_id) # void
quest::GetTimeSeconds() # void
quest::GetZoneID() # void
quest::GetZoneLongName() # string
quest::givecash(int copper, int silver, int gold, int platinum) # void
quest::gmmove(float x, float y, float z) # void
quest::gmsay(string message, int color_id, bool send_to_world) # void
quest::has_zone_flag() # uint
quest::incstat(int stat_id, int int_value) # void
quest::IsBeneficialSpell() # uint
quest::isdisctome() # bool
quest::isdooropen() # uint
quest::IsEffectInSpell(int spell_id, int effect_id) # uint
quest::IsRunning() # uint
quest::istaskaappropriate() # uint
quest::istaskactive() # uint
quest::istaskactivityactive(uint task_id, uint activity_id) # uint
quest::istaskcompleted() # int
quest::istaskenabled() # uint
quest::itemlink() # void
quest::lasttaskinset() # int
quest::LearnRecipe() # void
quest::level() # void
quest::MerchantCountItem(int npc_id, int item_id) # void
quest::MerchantSetItem(int npc_id, int item_id, int quantity) # void
quest::MobList::new() # void
quest::ModifyNPCStat(int stat_id, string str_value) # void
quest::movegrp(int zone_id, float x, float y, float z) # void
quest::movepc(int zone_id, float x, float y, float z, float heading) # void
quest::MovePCInstance(int zone_id, int instance_id, float x, float y, float z, float heading) # void
quest::moveto(float x, float y, float z, float heading, bool saveguard) # void
quest::nexttaskinset(int task_set, uint task_id) # int
quest::NPC::new() # void
quest::npcfeature(string str_value, int int_value) # uint
quest::npcgender() # void
quest::npcrace() # void
quest::npcsize() # void
quest::npctexture() # void
quest::pause() # void
quest::permaclass() # void
quest::permagender() # void
quest::permarace() # void
quest::playerfeature(string str_value, int int_value) # void
quest::playergender() # void
quest::playerrace() # void
quest::playersize() # void
quest::playertexture() # void
quest::popup(string window_title, string message, int popup_id, int buttons, int duration) # void
quest::pvp() # void
quest::qs_player_event(int char_id, string message) # void
quest::qs_send_query() # void
quest::QuestItem::new() # void
quest::rain() # void
quest::rebind(int zone_id, float x, float y, float z) # void
quest::RemoveAllFromInstance() # void
quest::RemoveFromInstance() # void
quest::removetitle() # void
quest::repopzone() # void
quest::resettaskactivity(uint task_id, uint activity_id) # void
quest::respawn(int npc_type_id, int grid_id) # void
quest::resume() # void
quest::safemove() # void
quest::save() # void
quest::say(string message, int language_id) # void
quest::saylink(string message, bool silent, string link_name) # string
quest::scribespells(int max_level, int min_level) # uint
quest::selfcast() # void
quest::SendMail(string to, string from, string subject, string message) # void
quest::set_proximity(float min_x, float max_x, float min_y, float max_y, float min_z, float max_z) # void
quest::set_zone_flag() # void
quest::setallskill() # void
quest::setanim(int npc_type_id, int anim_num) # void
quest::setglobal(string key, string str_value, int options, int duration) # void
quest::setguild(unsigned long new_guild_id, int guild_rank_id) # void
quest::sethp() # void
quest::setlanguage(int skill_id, int int_value) # void
quest::setnexthpevent() # void
quest::setnextinchpevent() # void
quest::SetRunning() # void
quest::setskill(int skill_id, int int_value) # void
quest::setsky() # void
quest::setstat(int stat_id, int int_value) # void
quest::settarget(string target_enum, int target_id) # void
quest::settime(int new_hour, int new_min, int update_world) # void
quest::settimer(string timer_name, int seconds) # void
quest::settimerMS(string timer_name, int milliseconds) # void
quest::sfollow() # void
quest::shout() # void
quest::shout2() # void
quest::showgrid() # void
quest::signal(int npc_id, int wait_ms) # void
quest::signalwith(int npc_id, int signal_id, int wait_ms) # void
quest::snow() # void
quest::spawn(int npc_type_id, int grid_id, int int_unused, float x, float y, float z) # uint
quest::spawn2(int npc_type_id, int grid_id, int int_unused, float x, float y, float z, float heading) # uint
quest::spawn_condition(string zone_short, int instance_id, int condition_id, int int_value) # void
quest::spawn_from_spawn2() # uint
quest::start() # void
quest::stop() # void
quest::stopalltimers() # void
quest::stoptimer() # void
quest::summonallplayercorpses(int char_id, float dest_x, float dest_y, float dest_z, float dest_heading) # bool
quest::summonburiedplayercorpse(int char_id, float dest_x, float dest_y, float dest_z, float dest_heading) # bool
quest::summonitem(int item_id, int charges) # void
quest::surname() # void
quest::targlobal(string key, string str_value, int duration, int npc_id, int char_id, int zone_id) # void
quest::task_setselector() # void
quest::taskexplorearea() # void
quest::taskselector(int task_id1, int task_id2, int task_id%i) # void
quest::tasktimeleft() # int
quest::toggle_spawn_event(uint event_id, bool is_enabled, bool is_strict, bool reset_base) # void
quest::toggledoorstate() # void
quest::traindisc() # void
quest::traindiscs(int max_level, int min_level) # uint
quest::unique_spawn(int npc_type_id, int grid_id, int int_unused, float x, float y, float z, float heading) # uint
quest::unscribespells() # void
quest::untraindiscs() # void
quest::UpdateInstanceTimer(int instance_id, int duration) # void
quest::UpdateSpawnTimer(uint spawn2_id, uint updated_time_till_repop) # void
quest::updatetaskactivity(uint task_id, uint activity_id, int count, bool ignore_quest_update) # void
quest::varlink() # string
quest::voicetell(string client_name, int macro_id, int race_id, int gender_id) # void
quest::we(int channel_id, string message) # void
quest::wearchange(uint slot, int texture_id, int hero_forge_model_id, int elite_material_id) # void
quest::worldwidemarquee(int color_id, int priority, int fade_in, int fade_out, int duration, string message) # void
quest::write(string file, string message) # void
quest::ze(int channel_id, string message) # void
quest::zone() # void

```