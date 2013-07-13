Packet is a class exported to Lua that represents the EQApplicationPacket object from EQEmu.

[Return to the Lua API](Lua-API)

### Properties
```
packet.null -- Returns true if this object is null
packet.valid -- Returns true if this object is not null
```

### Member Functions
```
Packet() -- Creates a null spell
Packet(Integer opcode, Integer size)
Integer GetSize();
Integer GetOpcode();
void SetOpcode(Integer op);
void WriteInteger8(Integer offset, Integer value);
void WriteInteger16(Integer offset, Integer value);
void WriteInteger32(Integer offset, Integer value);
void WriteInteger64(Integer offset, Integer value);
void WriteFloat(Integer offset, Real value);
void WriteDouble(Integer offset, Real value);
void WriteString(Integer offset, String value);
void WriteFixedLengthString(Integer offset, String value, Integer string_length);
Integer ReadInteger8(Integer offset);
Integer ReadInteger16(Integer offset);
Integer ReadInteger32(Integer offset);
Integer ReadInteger64(Integer offset);
Real ReadFloat(Integer offset);
Real ReadDouble(Integer offset);
String ReadString(Integer offset);
String ReadFixedLengthString(Integer offset, Integer string_length);
```