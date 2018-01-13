**Field**|**Type**|**Null**|**Key**|**Default**|**Notes**
-----|-----|-----|-----|-----|-----
id|int(11)|NO|PRI| |auto\_increment
zone|varchar(16)|NO|MUL| | 
version|smallint(5) unsigned|NO| |0| 
x|int(11)|NO| |0| 
y|int(11)|NO| |0| 
z|int(11)|NO| |0| 
chance|tinyint(4)|NO| |0| 
maxzdiff|float|NO| |0| 
radius|float|NO| |0| 
effect|int(11)|NO| |0| 
effectvalue|int(11)|NO| |0| 
effectvalue2|int(11)|NO| |0| 
message|varchar(200)|NO| | | 
skill|int(11)|NO| |0| 
level|mediumint(4) unsigned|NO| |1| 
respawn\_time|int(11) unsigned|NO| |60| 
respawn\_var|int(11) unsigned|NO| |0| 
triggered\_number|tinyint(4)|NO| |0| 
group|tinyint(4)|NO| |0| 
despawn\_when\_triggered|tinyint(4)|NO| |0| 
undetectable|tinyint(4)|NO| |0| 