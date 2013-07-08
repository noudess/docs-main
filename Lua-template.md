e.self:Say(string.format(" %s ",e.other:GetName())); -- to use player name in place of %s in the text.

local fac = e.other:GetFaction(e.self); -- to use for faction condition in an if statement.

function event_say(e)
	if(e.message:findi("")) then
		e.self:Say("");
	elseif(e.message:findi("")) then
		e.self:Say("");
	elseif(e.message:findi("")) then
		e.self:Say("");
	elseif(e.message:findi("")) then
		e.self:Say("");
	end
end

e.self:Say(string.format("",e.other:GetName()));

local fac = e.other:GetFaction(e.self);

function event_trade(e)
	local item_lib = require("items");
	if(item_lib.check_turn_in(e.trade, {item1 = 0})) then
		e.self:Say("");
		e.other:SummonItem(0);
		e.other:Ding();
		e.other:Faction(0,0,0);
		e.other:Faction(0,0,0);
		e.other:Faction(0,0,0);
		e.other:Faction(0,0,0);
		e.other:Faction(0,0,0);
		e.other:AddEXP(0);
		e.other:GiveCash(0,0,0,0);
	end
	item_lib.return_items(e.self, e.other, e.trade)
end

function event_waypoint_arrive(e)
	if(e.wp == 0) then
		e.self:Say("");
	elseif(e.wp == 0) then
		e.self:Say("");
	end
end