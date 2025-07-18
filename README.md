# drag
Source-based package manager written in bash for Linux distributions.
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
## Common Files and Directories
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
## Installation
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
## Package Installation Example
### smoke
```
smoke htop
```
## FAQ
Q: Can I add my own repositories?</br>
A: As of this moment at least, no you cannot. If you wish to add your own packages though, you may manually place them in the stash directory.</br>
</br>
Q: How does drag handle dependencies?</br>
A: Drag is free of dependency resolution, giving the user full control of their system. If you wish to list the recommended dependencies provided by Arch Linux, you may use the wiff command.</br>
</br>
Q: Do I have to run commands individually in order to install a package?</br>
A: No. You only need to run the smoke command.</br>
</br>
Q: Is the drag package manager meant to be used on a specific distribution?</br>
A: Although drag was created for Whispix, it can be used practically on any distribution, or even LFS.</br>
