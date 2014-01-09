CentOS Enterprise (and perhaps other *nix distros) currently defaults to GCC 4.4.7. EQEmu makes use of nullptr which wasn't introduced until GCC 4.6. Fortunately, there is a way to install GCC 4.7.2 as either an add-on installation or as a replacement without having to cross-platform compile or make any major changes to your OS installation.

***

First, get and install devtools 1.1 into your yum repo:
```
wget http://people.centos.org/tru/devtools-1.1/devtools-1.1.repo -O /etc/yum.repos.d/devtools-1.1.repo
yum install devtoolset-1.1
```

You can verify you have a new working compiler. You can run this to open a new session with the 4.7.2 compiler enabled (one-time method):
```
scl enable devtoolset-1.1 bash
gcc -v
```

***

The wonderful thing about CMake is that now you can configure only EQEmu to use the new GCC while the rest of your system still recognizes the original GCC files. Run CMake in interactive mode and change the locations (i.e. /usr/bin/gcc changes to /opt/centos/devtoolset-1.1/root/usr/bin/gcc). When CMake goes finishes configure, it will recognize the change and go back through configuration to ensure all locations are correct.

Enjoy!

