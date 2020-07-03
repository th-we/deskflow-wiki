# Installing dependencies for Linux
All section have the versions of the operating system they work with listed in the title, Other versions may still work as well


### Ubuntu 16.04 - 20.04 
```
sudo apt-get update 
sudo apt-get install git cmake qtbase5-dev build-essential libx11-dev libxtst-dev libgl1-mesa-dev libssl-dev libavahi-compat-libdnssd-dev debhelper devscripts qttools5-dev qttools5-dev-tools
```
For a more up to date list of packages see https://github.com/symless/dockerImages/tree/master/synergy-core/ubuntu

### Debian 9 - 10
```
sudo apt-get update 
sudo apt-get install git cmake qtbase5-dev build-essential libx11-dev libxtst-dev libgl1-mesa-dev libssl-dev libavahi-compat-libdnssd-dev debhelper devscripts qttools5-dev qttools5-dev-tools qt5-default
```
For a more up to date list of packages see https://github.com/symless/dockerImages/tree/master/synergy-core/debian

### CentOS 7.6 - 8
May also work for RHEL
```
sudo yum update 
sudo yum install avahi-compat-libdns_sd-devel avahi-compat-libdns_sd cmake3 git make make libXtst-devel qt5-qtbase-devel qt5-qtdeclarative-devel qt5-qttools-devel libcurl-devel openssl-devel gcc-c++ c++ rpm-build rpmlint
```
For a more up to date list of packages see https://github.com/symless/dockerImages/tree/master/synergy-core/centos

### Fedora 28 - 30
```
sudo yum update 
sudo yum install avahi-compat-libdns_sd-devel avahi-compat-libdns_sd cmake3 git gpg make libXtst-devel qt5-qtbase-devel qt5-qtdeclarative-devel qt5-qttools-devel libcurl-devel openssl-devel rpm-build rpmlint
```
For a more up to date list of packages see https://github.com/symless/dockerImages/tree/master/synergy-core/fedora


