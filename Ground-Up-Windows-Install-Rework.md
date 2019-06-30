<BODY LANG="en-US" BGCOLOR="#eeeeee" DIR="LTR">

<p><strong>This guide provides instructions for compiling 32-bit Windows server binaries and setting up a local development server.</strong></p>

<hgroup>

<p><h2><strong>Compiler Setup</strong></h2></p>

<ol>

<li><p><h3>Verify Environmental Variable %PATH%</h3></p></li>

<p>[need to develop criteria]</p>

<li><p><h3>Required Programs</h3></p></li>

<p>Some of the pre-requisits for compiling binaries are the same as running a server.</p>

<p>If you have already installed any of the following, the download and installation requirement should be omitted.</p>

<ul>

<li><p>Visual Studio 2017 Community Edition (see notes under install) [<a href="https://visualstudio.microsoft.com/vs/older-downloads/">select Visual Studio 2017 Community Edition</a>]</p></li>

<li><p>MariaDB [<a href="https://downloads.mariadb.org/interstitial/mariadb-10.4.6/winx64-packages/mariadb-10.4.6-winx64.msi/from/http%3A//mirror.nodesdirect.com/mariadb/">download</a>]</p></li>

<li><p>Perl [<a href="https://github.com/EQEmu/eqemu.github.com/raw/master/downloads/ActivePerl-5.12.3.1204-MSWin32-x86-294330.msi">download</a>]</p></li>

<li><p>CMake [<a href="https://github.com/Kitware/CMake/releases/download/v3.14.5/cmake-3.14.5-win64-x64.msi">download</a>]</p></li>

<li><p>Git (see notes under install) [<a href="https://git-scm.com/download/win">download</a>]</p></li>

<li><p>TortoiseGit (optional - see notes under install) [<a href="https://download.tortoisegit.org/tgit/2.8.0.0/TortoiseGit-2.8.0.0-64bit.msi">download</a>]</p></li>

</ul>

<li><p><h3>Install Visual Studio</h3></p></li>

<p>During the install process, double-check the option for c++ command-line compiler. This is required by CMake to determine available compiler options. CMake file generation will fail if this option is not enabled.</p>

<p>[screenshot of option]</p>

<p>Note: Microsoft now requires a user account to download Visual Studio. Clicking the Visual Studio link above will take you to the 'older versions' page. Clicking the download button on this page will prompt you to log in or create an account.</p>

<li><p><h3>Install MariaDB</h3><p></li>

<p>[need specifics on what settings to use]</p>

<p>At the end of the installation process, you will be prompted to install HeidiSQL. It is HIGHLY recommended that you install this program.</p>

<li><p><h3>Install Perl 5.12.3 (32-bit)</h3></p></li>

<p>This installation is self-explanatory. It is recommended that you install in the root directory ("c:\") to avoid possible issues.</p>

<li><p><h3>Install CMake</h3></p></li>

<p>This installation is self-explanatory.</p>

<li><p><h3>Install Git</h3></p></li>

<p>This installation is self-explanatory.</p>

<p>Note: Should you wish to download the repository code with no further chance of updating or restoration, this requirement may be omitted.</p>

<li><p><h3>Install TortoiseGit (optional)</h3></p></li>

<p>This installation is self-explanatory.</p>

<p>Note: If Git is not installed, this installation should be omitted.</p>

<li><p><h3>Restart Computer</h3></p></li>

<p>You will need to restart your computer to ensure that all of the %PATH% additions are loaded into memory.</p>

<li><p><h3>Acquiring the Code</h3></p></li>

<p>At this point, you will need to make a decision on how you want to manage your code.</p>

<p>There are three options:</p>

<ul>

<li><p>Option 1, Retrieve the code as a one-time download (not recommended)</p></li>

<li><p>Option 2, Create a local repository from the parent EQEmulator project that can be updated, managed and maintained (recommended)</p></li>

<li><p>Option 3, Create a local repository from a fork of the EQEmulator project that you manage (recommended only if you want to contribute back to the parent project)</p></li>

</ul>

<p>Note: If you choose to create a fork of the EQEmulator repository, you will need to create a [<a href="https://github.com/">github.com</a>] account.</p>

<p>[walk-through for option 2]</p>

<li><p><h3>Download Dependencies</h3></p></li>

<p>Library dependencies can be downloaded directly from [<a href="https://github.com/EQEmu/eqemu.github.com/raw/master/downloads/WindowsDependencies_x86.zip">here</a>].</p>

<p>Inside of your local code directory, you will need to create a sub-directory called 'dependencies` and unzip the download's contents into it.</p>

<li><p><h3>Running CMake</h3></p></li>

<p>[walk-through]</p>

<li><p><h3>Compiling Code</h3></p></li>

<p>[walk-through]</p>

</ol>

</hgroup>

<hgroup>

<p><h2><strong>Local Server Setup</strong></h2></p>

</hgroup>