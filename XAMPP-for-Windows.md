XAMPP is an all-in-one package with many programs. The important ones are MySQL, Apache, PHP, and Perl.

***

**Home Page:** [XAMPP for Windows] (http://www.apachefriends.org/en/xampp-windows.html)

**Current Version (WinXP & 2K3):** [1.8.2-6] (http://sourceforge.net/projects/xampp/files/XAMPP%20Windows/1.8.2/xampp-win32-1.8.2-6-VC9-installer.exe/download)

**Current Version (WinVista+ & 2008+):** [5.5.19] (http://downloads.sourceforge.net/project/xampp/XAMPP%20Windows/5.5.19/xampp-win32-5.5.19-0-VC11-installer.exe) or [5.6.3](http://downloads.sourceforge.net/project/xampp/XAMPP%20Windows/5.6.3/xampp-win32-5.6.3-0-VC11-installer.exe)

**Version Info:** The latest version numbers aren't sequential with previous releases of XAMPP. The numbering system is now based upon the PHP version included in the package.

**Note:** If you are compiling a 32-bit server, you must use Perl 5.12. XAMPP comes with 5.16, so you will need to replace that component with the [appropriate version] (ActivePerl-5.12).

***

1. Select the appropriate installer package for your system. It is recommended to install in your root directory (i.e. c:\xampp) to alleviate problems with permissions and folders with spaces in the name.
2. Install the program with the following at a minimum: MySQL, Apache, PHP, and Perl.
3. Start Apache and MySQL.
4. Open http://localhost and establish the appropriate security for your configuration.
5. Open http://localhost/phpmyadmin and create the `peq` and `peq_qs` databases. Also, you should create a user/password specifically for your peq databases. Don't forget to GRANT the appropriate permissions!