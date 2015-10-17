Install lxc-dev on Debian Jessie
================================

This is the steps I originally used to create:

Download and untar orig source & debian files

Note: Check for latest version here:
https://packages.debian.org/source/jessie/lxc

This is for 1:1.0.6-6+deb8u1:
````
DEB_VER=deb8u1
wget http://http.debian.net/debian/pool/main/l/lxc/lxc_1.0.6.orig.tar.xz
wget http://http.debian.net/debian/pool/main/l/lxc/lxc_1.0.6-6+$DEB_VER.debian.tar.xz
tar xf lxc_1.0.6.orig.tar.xz
tar xf lxc_1.0.6-6+$DEB_VER.debian.tar.xz -C lxc-1.0.6
````
I then modded the required files. The process was essentially:

-compare against 1.0.7 from Stretch (which includes lxc-dev again)
-tweak files
-test build (as per what I note below)
-if broken; rinse & repeat...
-once working; commit & celebrate! :smile:

To build (what I used when testing)

-run:
````
dpkg-buildpackage -rfakeroot -us -uc
````
it should autoclean but I was resetting it like this:

warning: all uncommitted changes and untracked files will be deleted!
````
git reset --hard HEAD
git clean -fd
````
