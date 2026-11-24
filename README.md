# burna
Source-based package manager written in bash for UNIX-like systems.
Utilizes Arch's repos + AUR to maximize package support.
## commands:
### stash
Add PKGBUILDs to your stash</br>
### snoop
Edit PKGBUILDs in your stash</br>
### pinch
Download the source files listed in the PKGBUILDs</br>
### roll
Compile packages using the PKGBUILD's instructions</br>
### smoke
Installs packge</br>
-o to smoke without stubbing first.</br>
-b to blaze before smoking.</br>
-bo or -ob to update packages without stubbing previous version.</br>
--bin64 to download the x86_64 Arch Linux binary (NOT RECOMMENDED AND WILL ALMOST CERTAINLY LEAD TO DEPENDENCY VERSION MISMATCHES)</br>
### stub
Uninstall select packages</br>
### wiff
View information about select packages</br>
Information includes version, description, dependencies, and whether the package has been smoked or not.</br>
### burnas
View smoked packages</br>
### blaze
Remove clear stash and ashtray for packages</br>
## Files and Directories
<table>
  <tr>
    <td>$HOME/.cache/burna/stash</td>
    <td>Your stash of PKGBUILDs</td>
  </tr>
  <tr>
    <td>$HOME/.cache/burna/ashtray/(package)/src</td>
    <td>srcdir - where source files are downloaded</td>
  </tr>
  <tr>
    <td>$HOME/.cache/burna/ashtray/(package)/pkg</td>
    <td>pkgdir - where packages are compiled to</td>
  </tr>
  <tr>
    <td>/var/lib/burna/smoked</td>
    <td>Tracking for smoked packages</td>
  </tr>
</table>

## Installation
1. Clone</br>
```
git clone https://github.com/catnipsta/burna.git
```
2. Make scripts executable</br>
```
chmod +x burna/scripts/*
```
3. Move scripts to /usr/bin</br>
```
cp burna/scripts/* /usr/bin/
```
## Package Installation Example
### smoke
```
smoke htop
```
## FAQ
Q: Can I add repositories?</br>
A: As of this moment at least, no you cannot. If you wish to create or edit PKGBUILDs, you may use the snoop command.</br>
</br>
Q: How does burna handle dependencies?</br>
A: burna is free of dependency resolution, giving the user full control of their system. If you wish to list the recommended dependencies provided by Arch Linux, you may use the wiff command.</br>
</br>
Q: Is the burna package manager meant to be used on a specific operating system?</br>
A: Although burna was created for Reaper Linux, it should run on just about any Linux distribution, LFS, and maybe even some BSDs.</br>
