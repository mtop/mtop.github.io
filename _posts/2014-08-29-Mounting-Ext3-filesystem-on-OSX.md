---
layout: post
title: Mounting an Ext3 filesystem on OSX
published: true
category: Unix
tags: [Unix, OSX, Ext3]
---
Mounting a Ext3 file system (comonly used by GNU/Linux systems) from a USB-drive on an Mac OSX machine is almost as easy as it was to mount a USB-stick on Mandriva in 2005. It's only slightly more complicated, and the only difference is that you will have to install some additional software on your Mac. So, to get started:

- Download and install the [OSXFUSE](http://osxfuse.github.io/)
- Download and install the [Ext2 FUSE module](http://sourceforge.net/projects/fuse-ext2/)
- Then plug in your USD-disk and whait for it to show up as a mounted disk in Finder.   

The file system will be automatically mounted as "Read only" which is probably not what you want. On my system it shows up as "disk1s1", so we'll make a note of that and then unmount the partition (click the littler symbol next to the name in finder, or run the command:
 
 ```
 sudo umount /dev/disk1s1").   
 ```

- Create a mount point in your file system using the command "mkdir /Volumes/USB".

The mount point is a directory that will contain all the files from the mounted file system. In this example I'm using /Volumes/USB, but the mount point can be anywhere you'd like.  
	   
- Mount the external file system on "/Volumes/USB" using the command: 

```
"fuse-ext2 -o force /dev/disk1s1 /Volumes/USB
```

The "-o force" part of the command is what makes the file system mount in Read and Write mode.  

And that is it. 
