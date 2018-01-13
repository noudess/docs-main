**Field**|**Type**|**Null**|**Key**|**Default**|**Notes**
-----|-----|-----|-----|-----|-----
buffs\_index|int(11) unsigned|NO|PRI| |auto\_increment
bot\_id|int(11) unsigned|NO|MUL|0| 
spell\_id|int(10) unsigned|NO| |0| 
caster\_level|tinyint(3) unsigned|NO| |0| 
duration\_formula|int(10) unsigned|NO| |0| 
tics\_remaining|int(11) unsigned|NO| |0| 
poison\_counters|int(11) unsigned|NO| |0| 
disease\_counters|int(11) unsigned|NO| |0| 
curse\_counters|int(11) unsigned|NO| |0| 
corruption\_counters|int(11) unsigned|NO| |0| 
numhits|int(10) unsigned|NO| |0| 
melee\_rune|int(10) unsigned|NO| |0| 
magic\_rune|int(10) unsigned|NO| |0| 
dot\_rune|int(10) unsigned|NO| |0| 
persistent|tinyint(1)|NO| |0| 
caston\_x|int(10)|NO| |0| 
caston\_y|int(10)|NO| |0| 
caston\_z|int(10)|NO| |0| 
extra\_di\_chance|int(10) unsigned|NO| |0| 
instrument\_mod|int(10)|NO| |10| 