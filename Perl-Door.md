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
void Doors::GetNoKeyring( THIS,  type)
void Doors::GetIncline()
void Doors::GetIncline()
void Doors::SetOpenType( THIS,  type)
void Doors::SetLockpick( THIS,  type)
void Doors::SetKeyItem( THIS,  type)
void Doors::SetNoKeyring( THIS,  type)
void Doors::SetIncline( THIS,  type)
void Doors::SetSize( THIS, int size)
void Doors::SetLocation( THIS, float x, float y, float z)
void Doors::SetX( THIS,  XPos)
void Doors::SetY( THIS,  YPos)
void Doors::SetZ( THIS,  ZPos)
void Doors::SetHeading( THIS, float heading)
void Doors::SetModelName( THIS, string name)
void Doors::GetModelName()
void Doors::InsertDoor()
```