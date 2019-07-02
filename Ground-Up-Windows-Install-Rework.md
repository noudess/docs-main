<BODY LANG="en-US" BGCOLOR="#eeeeee" DIR="LTR">

<p><strong>This guide provides instructions for compiling 32-bit Windows server binaries and setting up a local development server.</strong></p>

<p><strong>Read through this guide before starting to ensure an understanding of the process.</strong></p>

<p><strong>Please direct any questions to our server support channel in [<a href="https://discord.gg/QHsm7CD">discord</a>].</strong></p>

<br>

<hgroup>

<p><h2><strong>Compiler Setup</strong></h2></p>

<p>The current c/c++ support standard of the EQEmulator server code base mandates the use of Visual Studio 2013 or later compilers.</p>

<p>Given this, minimum compiler requirements restrict building code on older operating systems. <a href="https://docs.microsoft.com/en-us/visualstudio/productinfo/vs2013-sysrequirements-vs#--visual-studio-2013">Visual Studio 2013 Minimum Requirements</a></p>

<p>This setup assumes an install on a 64-bit Windows operating system with 32-bit target binaries.</p>

<br>

<ul>
	
<li><p><h3>Verify System Environment Variable %Path% Length</h3></p></li>
	
<p>Sometimes an automated server installation will fail due to the %Path% variable being full. This can happen with a manual installation as well.</p>
	
<p>Since this guide installs more programs than are required to just operate a server, verifying the length of %Path% is critical before we start.</p>
	
<p>The easiest way to find it is to:</p>
	
<ul>
		
<li><p>Click on your start button</p></li>
			
<li><p>Type 'environment variable' into your search programs and files text box</p></li>
			
<li><p>Click on 'Edit system environment variables'</p></li>
			
<li><p>Click the 'Environment Variables' button on the window that pops up</p></li>
			
<li><p>Ensure the variable 'Path' is selected in the system variables section (bottom text box)</p></li>
			
<li><p>Click the 'Edit' button</p></li>
		
</ul>
	
<p>You may check the length of your %Path% variable by copying the 'Variable value' contents and pasting them into a text editor that supports 'selection' count.</p>
	
<img src="https://user-images.githubusercontent.com/3311166/60465078-3b56b180-9c1e-11e9-89c5-0137a6ed84ba.png">

<br><br>
	
<p>Registry values are only allocated 1024 bytes of storage. However, environmental variables may contain up to 2048 bytes through the use of an alias.</p>
	
<p>If your selection count is greater than 768 characters, you may need to setup an alias to prevent corruption of the %Path% variable.</p>
	
<br>
	
<li><p><h3>Required Programs</h3></p></li>
	
<p>Some of the pre-requisites for compiling binaries are the same as running a server.</p>
	
<p>If you have already installed any of the following, the download and installation requirement should be omitted.</p>
		
<ul>
		
<a name="back_msvs"></a>
		
<li><p>Visual Studio 2017 Community Edition (see <a href="Ground-Up-Windows-Install-Rework#note_msvs">note</a> under install) [<a href="https://visualstudio.microsoft.com/vs/older-downloads/">select Visual Studio 2017 Community Edition</a>]</p></li>
		
<li><p>MariaDB (64-bit) [<a href="https://downloads.mariadb.org/interstitial/mariadb-10.4.6/winx64-packages/mariadb-10.4.6-winx64.msi/from/http%3A//mirror.nodesdirect.com/mariadb/">download</a>]</p></li>
		
<li><p>Perl v5.12.3.1204 (32-bit) [<a href="https://github.com/EQEmu/eqemu.github.com/raw/master/downloads/ActivePerl-5.12.3.1204-MSWin32-x86-294330.msi">download</a>]</p></li>
		
<li><p>CMake (64-bit) [<a href="https://github.com/Kitware/CMake/releases/download/v3.14.5/cmake-3.14.5-win64-x64.msi">download</a>]</p></li>
		
<a name="back_git"></a>
		
<li><p>Git (64-bit - see <a href="Ground-Up-Windows-Install-Rework#note_git">note</a> under install) [<a href="https://git-scm.com/download/win">download</a>]</p></li>
		
<a name="back_tgit"></a>
		
<li><p>TortoiseGit (64-bit - optional - see <a href="Ground-Up-Windows-Install-Rework#note_tgit">note</a> under install) [<a href="https://download.tortoisegit.org/tgit/2.8.0.0/TortoiseGit-2.8.0.0-64bit.msi">download</a>]</p></li>
		
</ul>
	
<p>Note: TortoiseGit is a menu-driven, addon-on gui interface for Git. Though optional, this instructional provides for its use.</p>
	
<p>Some programs may be able to use newer versions, or even the lastest releases, without issue. But, this is not the case with Perl and (later) dependencies.</p>
	
<p>The above list of programs is known to work for compiling working server binaries.</p>
	
<br>
	
<li><p><h3>Install Visual Studio</h3></p></li>
	
<p>During the install process, ensure the option for 'Desktop development with C++' is checked.</p>
	
<p>This package is required to compile c/c++ code and by CMake to determine available compiler options. It will cause CMake file generation to fail if not enabled.</p>
	
<img src="https://user-images.githubusercontent.com/3311166/60468475-b40e3b80-9c27-11e9-8b2b-462bd0f22165.png">
	
<br><br>
	
<a name="note_msvs"></a>
	
<p>Note: Microsoft now requires a user account to download Visual Studio. Clicking the Visual Studio link above will take you to the 'older versions' page. Clicking the download button on this page will prompt you to log in or create an account. [<a href="Ground-Up-Windows-Install-Rework#back_msvs">back</a>]</p>
	
<br>
	
<li><p><h3>Install MariaDB</h3><p></li>
	
<p>[need specifics on what settings to use]</p>
	
<p>At the end of the installation process, you will be prompted to install HeidiSQL. It is HIGHLY recommended that you install this program.</p>
	
<br>
	
<li><p><h3>Install Perl 5.12.3 (32-bit)</h3></p></li>
	
<p>This installation is self-explanatory.</p>
	
<p>It is recommended that you install in the root directory ("c:\") to avoid possible issues.</p>
	
<br>
	
<li><p><h3>Install CMake</h3></p></li>
	
<p>This installation is self-explanatory.</p>
	
<br>
	
<li><p><h3>Install Git</h3></p></li>
	
<p>This installation is self-explanatory.</p>
	
<a name="note_git"></a>
	
<p>Note: Should you wish to download the repository code with no further chance of updating or restoration, this requirement may be omitted. [<a href="Ground-Up-Windows-Install-Rework#back_git">back</a>]</p>
	
<br>
	
<li><p><h3>Install TortoiseGit (optional)</h3></p></li>
	
<p>This installation is self-explanatory.</p>
	
<a name="note_tgit"></a>
	
<p>Note: If Git is not installed, this installation should be omitted. [<a href="Ground-Up-Windows-Install-Rework#back_tgit">back</a>]</p>
	
<br>
	
<li><p><h3>Restart Computer</h3></p></li>
	
<p>You will need to restart your computer to ensure that all of the %Path% additions are loaded into memory.</p>
	
<br>
	
<li><p><h3>Acquiring the Code</h3></p></li>
	
<p>At this point, you will need to make a decision on how you want to manage your code.</p>
	
<p>There are three options:</p>
		
<ul>
		
<li><p>Option 1, Retrieve the code as a one-time download (unmanaged - not recommended)</p></li>
		
<li><p>Option 2, Create a local repository from the parent EQEmulator project that can be updated, managed and maintained (recommended)</p></li>
		
<li><p>Option 3, Create a local repository from a fork of the EQEmulator project that you manage (recommended only if you want to contribute back to the parent project)</p></li>
		
</ul>
	
<p>Note: If you choose to create a fork of the EQEmulator repository, you will need to create a [<a href="https://github.com/">github.com</a>] account.</p>
	
<p>If you choose options 1 or 2, create a sub-directory called 'git-eqemulator' in the root directory of c: drive.</p>
	
<p>If you choose option 3, create a sub-directory called 'git-&lt;git-username&gt;' in the root directory of c: drive. (example: git username is 'Pavlov', directory name would be 'git-pavlov')</p>
	
<p>The purpose of this directory is to facilitate code management. We'll refer to this as the 'account' directory.</p>
	
<p>For option 1:</p>
	
<ul>
		
<li><p>Download [<a href="https://github.com/EQEmu/Server/archive/master.zip">Server-master.zip</a>]</p></li>
		
<li><p>Place it inside of the account directory</p></li>
		
<li><p>Unpack its contents</p></li>
		
<li><p>Rename the local code directory from 'Server-master' to 'Server'</p></li>
		
<li><p>Move on to <a href="Ground-Up-Windows-Install-Rework#step_dependencies">Download Dependencies</a></p></li>
		
</ul>
	
<p>For other options, go to the EQEmulator server code repository web page at <a href="https://github.com/EQEmu/Server">https://github.com/EQEmu/Server</a></p>
	
<p>If you chose option 3 and are creating a fork, click on the fork button to add the repository to your account. You should be redirected to your fork's main repository page.</p>
	
<img src="https://user-images.githubusercontent.com/3311166/60550151-0e290280-9cf5-11e9-966e-e8d1fec1c80e.png">
	
<br><br>
	
<p>Finally, click the clone button, then open in desktop button to create a local code repository on your computer. When prompted for where to create it, select the account directory created above.</p>
	
<img src="https://user-images.githubusercontent.com/3311166/60550164-21d46900-9cf5-11e9-882b-439dea49c8e8.png">
	
<br><br>
	
<p>You should now have a managed local code repository on your computer.</p>
	
<p>Note: It is helpful to create a shortcut to the account directory and place it on your desktop.</p>
	
<br>
	
<a name="step_dependencies"></a>
	
<li><p><h3>Download Dependencies</h3></p></li>
	
<p>Library dependencies can be downloaded from [<a href="https://github.com/EQEmu/eqemu.github.com/raw/master/downloads/WindowsDependencies_x86.zip">here</a>].</p>
	
<p>Inside of your local code directory, you will find a sub-directory called 'dependencies`.</p>
	
<p>Just place this download inside of the 'dependencies' folder and unpack its contents.</p>
	
<br>
	
<li><p><h3>Running CMake</h3></p></li>
	
<p>[walk-through]</p>
	
<br>
	
<li><p><h3>Compiling Code</h3></p></li>
	
<p>[walk-through]</p>
	
<br>
	
<li><p><h3>Code Maintenance</h3></p></li>
	
<p>[final thoughts...]</p>
	
</ul>

</hgroup>

<br>

<hgroup>

<p><h2><strong>Local Server Setup</strong></h2></p>

<br>

</hgroup>
