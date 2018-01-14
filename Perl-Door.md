Door is a class exported to Perl that represent the Door object from EQEmu. All Door are also [Entity](Perl-Entity).

### Properties
```
door.null -- Returns true if this object is null
door.valid -- Returns true if this object is not null
```

### Member Functions
```
void Doors::GetDoorDBID()
void Doors::GetDoorID()
void Doors::GetID()
void Doors::GetX()
void Doors::GetY()
void Doors::GetZ()
void Doors::GetHeading()
void Doors::GetOpenType()
void Doors::GetLockpick()
void Doors::GetKeyItem()
void Doors::GetNoKeyring( type)
void Doors::GetIncline()
void Doors::GetIncline()
void Doors::SetOpenType( type)
void Doors::SetLockpick( type)
void Doors::SetKeyItem( type)
void Doors::SetNoKeyring( type)
void Doors::SetIncline( type)
void Doors::SetSize(int size)
void Doors::SetLocation(float x, float y, float z)
void Doors::SetX( XPos)
void Doors::SetY( YPos)
void Doors::SetZ( ZPos)
void Doors::SetHeading(float heading)
void Doors::SetModelName(string name)
void Doors::GetModelName()
void Doors::InsertDoor()
```