# drag
Source-based package manager written in bash for UNIX systems.
Utilizes Arch's repos + AUR to maximize package support.
## commands:
### stash
Add PKGBUILDs to your stash</br>
```stash htop```
### snoop
Edit PKGBUILDs in your stash</br>
```snoop htop```
### pinch
Download the source files listed in the PKGBUILDs.</br>
```pinch htop```
### roll
Compile packages using the PKGBUILD's instructions</br>
```roll htop```
### smoke
Installs packge.</br>
Includes file and version tracking.</br>
```smoke htop```
### stub
Uninstall select packages.</br>
```stub htop```
### wiff
View information about select packages.</br>
Information includes version, description, dependencies, and whether the package has been smoked or not.</br>
```wiff htop```
### drags
View smoked packages.</br>
```drags```
## Files and Directories
<table>
  <tr>
    <td>$HOME/.cache/drag/stash</td>
    <td>Your stash of PKGBUILDs</td>
  </tr>
  <tr>
    <td>$HOME/.cache/drag/ashtray/(package)/src</td>
    <td>srcdir - where source files are downloaded</td>
  </tr>
  <tr>
    <td>$HOME/.cache/drag/ashtray/(package)/pkg</td>
    <td>pkgdir - where packages are compiled to</td>
  </tr>
  <tr>
    <td>/var/lib/drag/smoked</td>
    <td>Tracking for smoked packages</td>
  </tr>
</table>

## Installation
1. Clone</br>
```
git clone https://github.com/catnipsta/drag.git
```
2. Make scripts executable</br>
```
chmod +x drag/scripts/*
```
3. Move scripts to /usr/bin</br>
```
cp drag/scripts/* /usr/bin/
```
## Package Installation Example
### smoke
```
smoke htop
```
## FAQ
Q: Can I add my own repositories?</br>
A: As of this moment at least, no you cannot. If you wish to create or edit PKGBUILDs, you may use the snoop command.</br>
</br>
Q: How does drag handle dependencies?</br>
A: Drag is free of dependency resolution, giving the user full control of their system. If you wish to list the recommended dependencies provided by Arch Linux, you may use the wiff command.</br>
</br>
Q: Is the drag package manager meant to be used on a specific distribution?</br>
A: Although drag was created for Whispix, it can be used on practically any distribution, or even LFS.</br>
