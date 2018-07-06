**Download**
* [https://ci.appveyor.com/api/projects/KimLS/zone-utilities/artifacts/build_x64.zip](https://ci.appveyor.com/api/projects/KimLS/zone-utilities/artifacts/build_x64.zip)

**Source** 
* [https://github.com/EQEmu/zone-utilities](https://github.com/EQEmu/zone-utilities)

**Contents**
```
➜ find *.exe
awater.exe
azone.exe
map_edit.exe
pfs.exe
```
# Azone

* Azone is a binary responsible for generating our .map files by reading geometry files, for more information on these see [[Maps Introduction]]

* Azone will look within the current directory for each zone_name you pass it and attempt to open the files with one of three loaders in the following order:
  * EQG Standard
  * EQG Terrain (v4)
  * S3D

**Usage**

```
./azone nektulos tutorialb qeytoqrg
```

This will load and output the following files

* nektulos.eqg -> nektulos.map
* tutorialb.eqg -> tutorialb.map
* qeytoqrg.s3d -> qeytoqrg.map

# Awater

* Awater reads in a geometry file and outputs a water map file that can be loaded by the EQEmu server software and is then used for area detection purposes.

* Water maps are a bit of a misnomer as they handle more than water volume data but rather all marked area volumes

**Usage**

```
./awater nektulos tutorialb qeytoqrg
```

* This will load and output the following files
  * nektulos.eqg -> nektulos.wtr
  * tutorialb.eqg -> tutorialb.wtr
  * qeytoqrg.s3d -> qeytoqrg.wtr

Each of these **.wtr** files may then be copied to the server's maps directory to be used by the server.
