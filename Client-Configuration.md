EQEmulator is a custom, completely from-scratch, open source server implementation for EverQuest, built mostly on C++.  EQEmulator is an open-source project, released under the GNU General Public License.

**EverQuest clients are the intellectual property of the Daybreak Game Company, LLC.**  Copies of Daybreak Game Company intellectual property are not sourced through the EQEmulator project, nor should you provide unlicensed copies through any EQEmulator asset.

This page is intended to assist you in configuring your client to connect to an EQEmu server.  

- [**All Operating Systems**](#all-operating-systems)
- [**Windows**](#windows)
- [**macOS Mojave**](#macos-mojave)
- [**macOS High Sierra**](#macos-high-sierra)
- [**Linux**](#linux)
- [**Troubleshooting**](#troubleshooting)

# All Operating Systems

* Navigate to your EverQuest directory and modify the eqhost file:

**Titanium** or **Secrets of Faydwer** Clients:

```
[LoginServer]
Host=login.eqemulator.net:5998
```

**Seeds of Destruction**, **Underfoot**, or **Rain of Fear** Clients:

```
[LoginServer]
Host=login.eqemulator.net:5999
```


# Windows



# macOS Mojave

The EverQuest client can be run through Wine on Mojave.  To configure your system, follow these steps:

1. Install Xcode:

	* Click the Apple Icon in the upper-left corner of your screen⋅⋅
	* Choose App Store...
	* Search for Xcode
	* Install Xcode

2. Install Homebrew:

	* Open Terminal (_/Applications/Utilities/Terminal.app_)
	* Copy and paste this command and execute:

```shell
ruby -e “$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/uninstall)”
```

3. Create a symbolic link between X11 folders:

	* Open Terminal (_/Applications/Utilities/Terminal.app_)
	* Copy and paste this command and execute:

```shell
sudo ln -s /opt/X11 /usr/X11
```

4. Install XQuartz:

	* Open Terminal (_/Applications/Utilities/Terminal.app_)
	* Copy and paste this command and execute:

```shell
brew install Caskroom/cask/xquartz
```

5. Create a symbolic link between library folders:

	* Open Terminal (_/Applications/Utilities/Terminal.app_)
	* Copy and paste this command and execute:

```shell
sudo ln -s /usr/local/lib /usr/X11/lib/*
```

6. Install Wine

	* Open Terminal (_/Applications/Utilities/Terminal.app_)
	* Copy and paste this command and execute:

```shell
brew install --only-dependencies --devel wine
```

7. Configure Wine fonts

	* Open Terminal (_/Applications/Utilities/Terminal.app_)
	* Copy and paste this command and execute:

```shell
winetricks corefonts
```

8. Configure Font Smoothing

	* Open Terminal (_/Applications/Utilities/Terminal.app_)
	* Copy and paste this command and execute:

```shell
cat << EOF > /tmp/fontsmoothing
REGEDIT4

[HKEY_CURRENT_USER\Control Panel\Desktop]
"FontSmoothing"="2"
"FontSmoothingOrientation"=dword:00000001
"FontSmoothingType"=dword:00000002
"FontSmoothingGamma"=dword:00000578
EOF

WINE=${WINE:-wine} WINEPREFIX=${WINEPREFIX:-$HOME/.wine} $WINE regedit /tmp/fontsmoothing 2> /dev/null
```

9. Launch EverQuest

	* Open Terminal (_/Applications/Utilities/Terminal.app_)
	* Navigate to your EverQuest directory (IE _cd Applications/EverQuest/_)
	* Launch with the "patchme" option:

```shell
wine eqgame.exe patchme
```


# macOS High Sierra



# Linux


# Troubleshooting