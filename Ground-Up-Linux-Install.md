#### This guide is intended for doing a "from the ground up" installation of a windows server. It is not the recommended or typical route, we suggest using the [[Linux-Server]] install instead for most cases.

* TODO: This guide will have overlap with the linux script, but give more granular control over the steps processed.. 

* debian/ubuntu required packages for dev environment: libstdc++6 build-essential gcc-5 g++-5 libtool cmake curl debconf-utils git git-core libio-stringy-perl liblua5.1 liblua5.1-dev libluabind-dev libmysql++ libperl-dev libperl5i-perl libwtdbomysql-dev libsodium-dev libsodium18 libmysqlclient-dev lua5.1 minizip make mariadb-client nano open-vm-tools unzip uuid-dev zlibc wget
* debian/ubuntu required packages for production environment: liblua5.1 libmysql++ libperl5i-perl lua5.1 zlibc wget
* additional production environment requirements: 
```
wget http://ftp.us.debian.org/debian/pool/main/libs/libsodium/libsodium-dev_1.0.11-1~bpo8+1_amd64.deb -O /eqemu/libsodium-dev.deb \
	&& wget http://ftp.us.debian.org/debian/pool/main/libs/libsodium/libsodium18_1.0.11-1~bpo8+1_amd64.deb -O /eqemu/libsodium18.deb \
	&& dpkg -i /eqemu/libsodium*.deb \
	&& rm -f /eqemu/libsodium-dev.deb \
	&& rm -f /eqemu/libsodium18.deb
```