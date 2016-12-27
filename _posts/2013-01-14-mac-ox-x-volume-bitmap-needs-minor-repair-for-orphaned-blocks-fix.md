---
layout: post
title: How to fix “volume bitmap needs minor repair for orphaned blocks” on OS X 10.8
permalink: /how-to-fix-volume-bitmap-needs-minor-repair-for-orphaned-blocks-on-os-x-10-8/
---

Recently I noticed something strange on my Retina Macbook Pro with OS X 10.8.2 (Mountain Lion):

1. the available disk space stats gives wrong information (less free space than expected)
2. cannot use Boot Camp to create windows partition (says disk needs to be repaired using Disk Utility)

As instructed by Boot Camp, I went to Disk Utility, select the “Macintosh HD” partition and clicked on “Verify Disk”, then I got a whole bunch of logs and it ended with these error messages:

```
Checking volume bitmap.
Volume bitmap needs minor repair for orphaned blocks
Checking volume information.
Invalid volume free block count
(It should be ######## instead of ########)
The volume Macintosh HD was found corrupt and needs to be repaired.
Error: This disk needs to be repaired using the Recovery HD. Restart your computer, holding down the Command key and the R key until you see the Apple logo. When the Mac OS X Utilities window appears, choose Disk Utility.
```

Okay, that’s strange right? I then followed the instruction, restarted my macbook while holding down command+R, went to recovery mode and opened Disk Utility again, clicked on “Verify Disk” and bam, the whole process finished in less than a second, no error found! “That’s great”, i thought. To verify, I restarted OS X once again, went back to Disk Utility and verified the partition once more. Guess what, I got the same error message again! I googled around for the past day, people have been suggesting to use 3rd party software to repair disk, re-install OS X or even replace the hard drive. But to me, this doesn’t seem to be that big of a deal, there must be something very simple that I’ve missed somewhere…

Just to save you from reading more of my ramblings, **here’s what I did to solve this problem:**

1. Go to “System Preferences” – “Security and Privacy”, click on “FileVault” tab, click the lock icon on the bottom left to unlock, and then click on “Turn Off FileVault”. The decryption process will take a while (around 1 hour).
2. When the decryption is done, reboot into Recovery HD
3. Use Disk Utility to verify OS X Partition, this time the process will take much longer and it will give you the same error message
4. Click on “Repair Disk”
5. DONE!
6. (optional) re-enable FileVault
