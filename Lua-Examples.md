Various Lua Quest examples to give a feel for how the code works:

### NPC
```
-- Nerissa_Clothspinner
-- Makes use of the item_turnin module, string_ext module for findi and client_ext module for Client:GiveCash() and Client:Faction()
function event_waypoint_arrive(e)
	if(e.wp == 17) then
		e.self:Say("When will my sister show up? I need her!");
	elseif(e.wp == 43) then
		e.self:Say("Bartender! Some water, please.");
	end
end

function event_say(e)
	if(e.message:findi("hail")) then
		e.self:QuestSay(e.other, "Good day to you! Be careful in the city of Qeynos. [Rumors] of corruption may be true. Believe me. I wish my [sister] were here to help.");
	elseif(e.message:findi("sister")) then
		e.self:QuestSay(e.other, "My sister is in the Karanas. She is a warrior. Her name is Milea. I really need her. Would you please deliver a note to her? You look able-bodied enough for the job.");
	elseif(e.message:findi("deliver a note")) then
		if(e.other:GetLevel() < 4) then
			e.self:Say("I cannot discuss such things with a person as young to the world as you are.");
		elseif(e.other:GetLevel() > 65) then
			e.self:Say("I cannot trouble a person of your stature with such trivial talk.");
		else
			e.self:QuestSay(e.other, "Here you go then, brave adventurer. Godspeed to you.");
			e.other:SummonItem(18801);
		end
	elseif(e.message:findi("rumors")) then
		e.self:QuestSay(e.other, "I have heard that a few of the Qeynos merchants and guards are not very happy with the current state of the city. Taxes are too high and many of the guards have been sent to the outlands, leaving Qeynos vulnerable to attack. I do not feel the same way, but I fear these few may become many. I [fear for my life].");
	elseif(e.message:findi("fear for your life")) then
		e.self:QuestSay(e.other, "During a late night stroll by the pond in north Qeynos I spied a guard carrying a very large carpet on his shoulders. He approached the pond's edge and unrolled the carpet, the body of another guard rolled out and began to moan. The other guard grabbed for a long spear like weapon from his back. He drove the weapon into the man and pushed him into the pond. I screamed. He turned to me and I ran. I do not think he gave chase, too bad, he would not like to run into my [guardian] at home. I told my guardian and we both went to the pond and saw no body. He believes I was drinking too much wine. I do not drink. Now I fear for my life when I am in the streets of Qeynos.");
	elseif(e.message:findi("guardian")) then
		e.self:QuestSay(e.other, "When my big sister left Qeynos for adventure, she left me in the hands of her old time friend Kane Bayle. Yes, the commander of the Qeynos Guards is my guardian. You would think I would be safe. Every time I tell him the rumors I hear he just ignores me. He is too busy I guess.");
	end
end

function event_trade(e)
	local item_lib = require("item_turnin");
	
	if(item_lib.check_turn_in(e.trade, {item1 = 13302})) then
		e.self:QuestSay(e.other, "Thank you my friend. I understand that Astaed Wemor of the Temple of Life has been concerned for my well being. Take him this note. I am sure he will reward you for easing my troubled mind.. If you are a respected member.");
		e.other:SummonItem(18862);
		e.other:GiveCash(0, 10, 0, 0);
		e.other:Faction(217, 1, 0);
		e.other:Faction(33, -1, 0);
		e.other:Faction(9, 1, 0);
		e.other:Faction(47, 1, 0);
		e.other:Faction(135, 1, 0);
		e.other:AddEXP(3000);
	end
	
	if(item_lib.return_items(e.self, e.other, e.trade)) then
		e.other:Message(0, e.self:GetCleanName() .. " does not need this.");
	end
end
```

```
-- this is an example of how to track time on an NPC.
-- time_a is declared local outside of a function to be available later.
local time_a = os.time();

function event_spawn(e)
	-- os.time(); returns an integer value in seconds.
	e.self:Shout("The time is now: "..time_a);
end

function event_say(e)
	-- time_b is local because we have no need for it to be global, though the script would work both ways
	local time_b = os.time();
	if(e.message:findi("hail")) then
		e.self:Say("The time is now: "..time_b);
		-- os.difftime(t2,t1) returns an integer value in seconds t2-t1
		local time_diff = os.difftime(time_b,time_a);
		e.self:Say("It has been "..time_diff.." seconds since I spawned");
	end
end
```

```
--An example of using PEQ's thread_manager to make scripts with lots of timers easier to write
local ThreadManager = require("thread_manager");
local evt;

function ability_one()
	evt.self:Emote("begins to cast something electrical");
	ThreadManager:Wait(2.5);
	evt.self:Shout("Feel the thunder!");
end

function ability_two()
	evt.self:Emote("begins to cast something fiery");
	ThreadManager:Wait(2.5);
	evt.self:Shout("Feel the fire!");
end

function ability_three()
	evt.self:Emote("begins to cast something cold");
	ThreadManager:Wait(2.5);
	evt.self:Shout("Feel the freeze!");
end

function swapped_abilities()
	local i = 0;
	while true do
		if(i == 0) then
			ability_one();
			i = 1;
		elseif(i == 1)
			ability_two();
			i = 2;
		else
			ability_three();
			i = 0;
		end
		ThreadManager:Wait(15.0);
	end
end

function predictable()
	while true do
		ThreadManager:Wait(10.0);
		evt.self:Emote("begins to cast something predictable");
		ThreadManager:Wait(2.5);
		evt.self:Shout("Feel the Predictableness!");
	end
end

function event_combat(e)
	if(e.joined) then
		eq.set_timer("heartbeat", 500);
		ThreadManager:Clear();
		ThreadManager:Create("Predictable", predictable);
		ThreadManager:Create("Swapping", swapped_abilities);
	else
		eq.stop_timer("heartbeat");
		ThreadManager:Clear();
	end
end

function event_timer(e)
	evt = e;
	ThreadManager:Resume("Predictable");
	ThreadManager:Resume("Swapping");
end
```

### Player
```
-- player.lua example of access and changing the lockpick value of a door.
function event_click_door(e)
	local door_id = e.door:GetDoorID();
	local entity_list = eq.get_entity_list();
	e.self:Message(15,"You clicked on door: "..door_id);
	local door = entity_list:FindDoor(door_id);
	e.self:Message(15,"GetLockPick was: "..door:GetLockPick());
	if (entity_list:FindDoor(DoorID):GetLockPick() == 0) then
		door:SetLockPick(-1);
	else
		door:SetLockPick(0);
	end
	e.self:Message(15,"GetLockPick is now: "..door:GetLockPick());
end
```

```
-- This is an example of how to use get_characters_in_instance
function event_death_complete(e)
	-- get the zone instance id
	local instance_id = eq.get_zone_instance_id();
	local charid_list = eq.get_characters_in_instance(instance_id);
	-- Lua loop basics:
	-- k = key which is generally the current index of the array, not used in this example
	-- v = value for the current key, in this example it would be the character ID
	for k,v in pairs(charid_list) do
		eq.target_global("lockout_ikky_g1", "1", "H17", 0,v, 0);
	end
end
```

```
--- using event command and lua packets to send both a static and raw opcode packet to the client
function event_command(e)
	if(e.command:findi("test_raw_packet")) then
		local pack = Packet(0x624c, 8, true);
		pack:WriteInt32(0, 1);
		pack:WriteInt32(4, 125);
		e.self:QueuePacket(pack);
		return 1;
	end
	
	if(e.command:findi("test_packet")) then
		local pack = Packet(Opcode.AdventureFinish, 8);
		pack:WriteInt32(0, 1);
		pack:WriteInt32(4, 125);
		e.self:QueuePacket(pack);
		return 1;
	end
end
```

### Item

### Spell

### Encounter