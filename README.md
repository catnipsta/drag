# drag (EARLY BETA)
Source-based package manager written in bash for Linux distributions.
Utilizes Arch's repo + AUR for wide range of package support.
## commands:
### stash
Update your stash by running without any parameters,</br>
```stash```</br>
or update/add select packages to your stash by passing them as parameters.</br>
```stash htop vi```
### puff
Download the source files listed in the PKGBUILDs for select packages.</br>
```puff htop vi```
### smoke
Tracks installed files and version of package.</br>
You must have run 'make install' or similar with DESTDIR set to the pkgdir before running.</br>
You must pass exactly one argument: the name of the package being installed.</br>
```smoke htop```
### stub
Uninstall select packages.</br>
```stub htop vi```
### hotbox
Lists out of date packages.</br>
```hotbox```
### wiff
View information about select packages.</br>
Information includes version, description, dependencies, and whether the package has been smoked or not.</br>
```wiff htop vi```
### drags
View current stash and smoked packages.</br>
```drags```
## Common Files and Directories
<table>
  <tr>
    <td>/var/cache/drag/stash</td>
    <td>Your stash of PKGBUILDs</td>
  </tr>
  <tr>
    <td>/var/cache/drag/ashtray/(package)/src</td>
    <td>srcdir - where source files are downloaded</td>
  </tr>
  <tr>
    <td>/var/cache/drag/ashtray/(package)/pkg</td>
    <td>pkgdir - where packages are compiled to</td>
  </tr>
  <tr>
    <td>/var/lib/drag/smoked</td>
    <td>Tracking for smoked packages</td>
  </tr>
  <tr>
    <td>/etc/chronic</td>
    <td>List of packages you wish to be ignored by hotbox</td>
  </tr>
</table>

## Configuration
### Compile flags
/etc/profile</br>
Here you can export your MAKEFLAGS, CFLAGS or whatever other variables needed to suit your compiling needs.</br>
Example:
```
export MAKEFLAGS="-j$(nproc)
export CFLAGS="-march=native -O2 -pipe"
export CXXFLAGS="$CFLAGS"
```
### chronic
/etc/chronic</br>
You may list packages in here you wish to be ignored by hotbox</br>
Example:
```
linux
binutils
glibc
gcc
```
## Installation
There are two methods of installation:
  1. Installing to existing systems
  2. Installing to system on mount point (not chroot)
</br>
If you are choosing the second option, you must set the DRAG_ROOT variable, place the scripts and config files under your mount point's file system, and add the mount point's /usr/bin to your PATH variable.</br>
If you are installing to a system on a mount point, setting the DRAG_ROOT variable should look something like:

```
export DRAG_ROOT=/mnt/drive
```
</br>

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
## Package Installation Example
### puff
```
puff htop
```
### cd to srcdir
```
cd /var/cache/drag/ashtray/htop/src
```
### compile
```
cd htop
./autogen.sh
./configure --prefix=/usr
make
make DESTDIR=../../pkg install
```
### smoke
```
smoke htop
```
## FAQ
Q: Can I add my own repositories?</br>
A: As of this moment at least, no you cannot. If you wish to add your own packages though, you may manually place them in the stash directory.</br>
</br>
Q: How does drag handle dependencies?</br>
A: Drag is free of dependency resolution, giving the user full control of their system. If you wish to list the recommended dependencies, you may use the wiff command.</br>
</br>
Q: Do I have to stash a package first in order for puff or wiff to work?</br>
A: No. If you haven't stashed a package previously, puff or wiff will attempt to stash it for you.</br>
</br>
Q: Is the drag package manager meant to be used with a specific distribution?</br>
A: Although drag was created for Stone Linux (coming soon), it can be used practically on any distribution, or even LFS.</br>
