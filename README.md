# drag (EARLY BETA)
Source-based package manager for Linux distributions written in bash.
Utilizes Arch's repo + AUR for wide range of packages.
## commands:
### stash
Update your stash by running without any parameters.</br>
```stash```</br>
or update/add select packages by passing them as parameters.</br>
```stash sudo vi```
### puff
Download the source files listed in the PKGBUILDs for select packages.</br>
```puff sudo vi```
### smoke
Compile and install select packages.</br>
```smoke sudo vi```
### stub
Uninstall select packages.</br>
```stub sudo vi```
### hotbox
Update every outdated package on the system according to current stash.</br>
(It is recommended to update your stash first)</br>
```hotbox```
### wiff
View information about select packages.</br>
Information includes version, description, dependencies, and whether the package has been smoked or not.</br>
```wiff sudo vi```
### drags
View current stash and smoked packages.</br>
```drags```
## Files and Directories
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
    <td>pkgdir - where packages are compiled</td>
  </tr>
  <tr>
    <td>/var/lib/drag/smoked</td>
    <td>Tracking on smoked packages</td>
  </tr>
  <tr>
    <td>/etc/drag/drag.conf</td>
    <td>Variables such as MAKEFLAGS and CFLAGS should be defined here</td>
  </tr>
  <tr>
    <td>/etc/drag/chronic</td>
    <td>List of packages you wish to be ignored by hotbox</td>
  </tr>
</table>

## Configuration
### drag.conf
/etc/drag/drag.conf</br>
You may place your MAKEFLAGS, CFLAGS, CXXFLAGS, or whatever other environment variables you would like set during compile time in this file.</br>
Example:
```
MAKEFLAGS="-j$(nproc)"
CFLAGS="-march=native -O2 -pipe"
CXXFLAGS=$CFLAGS
```
### chronic
/etc/drag/chronic</br>
You may list packages in here you wish not to be updated by hotbox</br>
Reminder: Chronic only affects hotbox, not smoke</br>
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
## FAQ
Q: Do I have to run stash, puff, and smoke chronologically to install packages?</br>
A: No. If you haven't stashed or puffed a package previously, smoke will do it for you. To install any package, you may choose to only use the smoke command.</br>
</br>
Q: Can I add my own repositories?</br>
A: As of this moment at least, no you cannot. If you wish to add your own packages though, you still may manually create them in the stash directory.</br>
</br>
Q: How does drag handle dependencies?</br>
A: Drag is free of dependency resolution, giving the user full control of their system. If you wish to list the recommended dependencies, you may use the wiff command.</br>
</br>
Q: Is the drag package manager meant to be used with a specific distribution?</br>
A: Although drag was created for Stone Linux, it can be used practically on any distribution or even LFS.</br>
