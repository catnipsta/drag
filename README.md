# drag (EARLY BETA)
Linux source-based package manager written in bash.
Utilizes Arch's repo + AUR for wide range of packages.
## commands:
### stash
Update your stash by running without any parameters.
```stash```
or update/add select packages by passing them as parameters.
```stash sudo vi```
### puff
Download the source files listed in the PKGBUILDs for select packages.
```puff sudo vi```
### smoke
Compile and install select packages.
```smoke sudo vi```
### stub
Uninstall select packages.
```stub sudo vi```
### hotbox
Update every outdated package on the system according to current stash.
(It is recommended to update your stash first)
```hotbox```
### wiff
View information about select packages.
Information includes version, description, dependencies, and whether the package has been smoked or not.
```wiff sudo vi```
### drags
View current stash and smoked packages.
```drags```
## Files and Directories
/var/cache/drag/stash                 - your stash of PKGBUILDS
/var/cache/drag/ashtray/(package)/src - srcdir - where source files are downloaded
/var/cache/drag/ashtray/(package)/pkg - pkdir  - where packages are compiled
/var/lib/drag/smoked                  - tracking on smoked packages
/etc/drag/drag.conf                   - variables such as MAKEFLAGS and CFLAGS should be set in here
/etc/drag/chronic                     - list packages in this file you would not like to be affected by running 'hotbox'
## Configuration
### drag.conf
/etc/drag/drag.conf
You may place your MAKEFLAGS, CFLAGS, CXXFLAGS, or whatever other environment variables you would like set during compile time in this file.
Example:
```
MAKEFLAGS="-j$(nproc)"
CFLAGS="-march=native -O2 -pipe"
CXXFLAGS=$CFLAGS
```
### chronic
/etc/drag/chronic
You may list packages in here you wish not to be updated by running 'hotbox'
Reminder: Chronic only affects hotbox, not smoke
Example:
```
linux
binutils
glibc
gcc
```
## Installing
There are two methods of installation:
  1. Installing to existing systems
  2. Installing to system on mount point (not chroot)
</br>
If you are taking the second route, you must set the DRAG_ROOT variable, place the scripts and config files under your mount point's file system, and add the mount point's /usr/bin to your PATH variable.
If you are installing to a system on a mount point, setting the DRAG_ROOT variable should look something like:</br>
```
export DRAG_ROOT=/mnt/drive
```

1. Clone</br>
```
git clone https://github.com/catnipsta/drag.git
cd drag
```
2. Make scripts executable</br>
```
chmod +x scripts/*
```
3. Move scripts to /usr/bin</br>
```
mv scripts/* /usr/bin/
```
4. Optionally, create/edit configuration files
