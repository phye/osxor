# Issues
Default OSX file system is *half* case-insensitive.
This make it weird for projects that contain file names with mixing upper and lower cases(such as [linux](https://kernel.org/linux.git)). 

# Solutions
An easy solution is to create a disk image file with case sensitive file system, mount that disk image to the external file system, and
store git projects within the case sensitive file system.

However, disk image will not be mounted automatically by OS X (=/etc/fstab= is obsolete in OSX and also disk image file itself is not file
system). As a result, a launchd configuration file(plist file) becomes mandatory.

# Usage
1. Create Disk Image File (TBD)

2. Mount (Attach in hdiutil) the Disk Image File 

3. Place the plist file in the directory to `/Library/LaunchDaemons` with modification to the disk image file path in the plist file.

4. Create soft links if necessary as usually the mount point are within `/Volumes` which may not be what you want.
