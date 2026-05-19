---
title: DD Linux
tags:
 - linux-core-utils
draft: true
---


The disk distroyer (DD)
Operates directly on raw btes of file, partition or disk.


Uses
- Creating bootable drives
  dd if=/dev/sda of=/tmp/storage # transferred all thats in disk sda to storage # cool for cloning environments.
  # no need for count if you want to copy all thats in source to destination.
- Backing up linux disks
- Creating large blank files
- Creating a swap file
  dd if=/dev/zero of=/tmp/swapfile bs=2048 count=500 # 1000 blocks of 2048 bytes to create 2 Gigs
- Wiping by writing zeros
  dd if=/dev/zero of=/dev/sdX bs=16M
- Wiping by writing random data
  dd if=/dev/urandom of=/dev/sdX bs=16M
- Backup master boot record
  dd if=/dev/sda of=mbr_backup.bin bs=512 count=1
- Copy files, partitions or whole disks across networks or on the same computer.
- Common options
 -skip=num # ignore num blocks at start of input or source
 -seek=num # ignore first num blocks at start of output or destination
 -conv=a,b,c
   - noerror: continue on error
     dd if=/dev/sdd of=/dev/sda conv=noerror
   - sync: pad every input block with /null char to match input block size
   - ascii, ebcdic, ibm: handle conversions between ascii , ebcic and ibm encodings
   - sparse: seek other than write null bytes to save space.
   - lcase,ucase: upper case to lower case and vice versa
    dd if=input.txt of=output.txt conv=ucase
   - excl: fail if output file already exists to prevent accidental overrites.
 -status=
 -iflag/oflag=
 -ibd/obs= # spearating input block size from output block size



* Sources
 - Savvynik on DD:  https://www.youtube.com/watch?v=KAuiHFbFE_o
 - CodeLucky on DD: https://youtu.be/xtlH44mYUXk?si=QxiTXOfke9nz-3_U
 - Wikipedia article: https://en.wikipedia.org/wiki/Dd_(Unix)



Forks