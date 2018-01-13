**Field**|**Type**|**Null**|**Key**|**Default**|**Notes**
-----|-----|-----|-----|-----|-----
bot\_id|int(11) unsigned|NO|PRI| |auto\_increment
owner\_id|int(11) unsigned|NO| | | 
spells\_id|int(11) unsigned|NO| |0| 
name|varchar(64)|NO| | | 
last\_name|varchar(64)|NO| | | 
title|varchar(32)|NO| | | 
suffix|varchar(32)|NO| | | 
zone\_id|smallint(6)|NO| |0| 
gender|tinyint(2)|NO| |0| 
race|smallint(5)|NO| |0| 
class|tinyint(2)|NO| |0| 
level|tinyint(2) unsigned|NO| |0| 
deity|int(11) unsigned|NO| |0| 
creation\_day|int(11) unsigned|NO| |0| 
last\_spawn|int(11) unsigned|NO| |0| 
time\_spawned|int(11) unsigned|NO| |0| 
size|float|NO| |0| 
face|int(10)|NO| |1| 
hair\_color|int(10)|NO| |1| 
hair\_style|int(10)|NO| |1| 
beard|int(10)|NO| |0| 
beard\_color|int(10)|NO| |1| 
eye\_color\_1|int(10)|NO| |1| 
eye\_color\_2|int(10)|NO| |1| 
drakkin\_heritage|int(10)|NO| |0| 
drakkin\_tattoo|int(10)|NO| |0| 
drakkin\_details|int(10)|NO| |0| 
ac|smallint(5)|NO| |0| 
atk|mediumint(9)|NO| |0| 
hp|int(11)|NO| |0| 
mana|int(11)|NO| |0| 
str|mediumint(8)|NO| |75| 
sta|mediumint(8)|NO| |75| 
cha|mediumint(8)|NO| |75| 
dex|mediumint(8)|NO| |75| 
int|mediumint(8)|NO| |75| 
agi|mediumint(8)|NO| |75| 
wis|mediumint(8)|NO| |75| 
fire|smallint(5)|NO| |0| 
cold|smallint(5)|NO| |0| 
magic|smallint(5)|NO| |0| 
poison|smallint(5)|NO| |0| 
disease|smallint(5)|NO| |0| 
corruption|smallint(5)|NO| |0| 
show\_helm|int(11) unsigned|NO| |0| 
follow\_distance|int(11) unsigned|NO| |200| 