---
layout: page
title: "Q72132: BACKUP Fails When Writing Log File to Unformatted Disk"
permalink: /kb/072/Q72132/
---

## Q72132: BACKUP Fails When Writing Log File to Unformatted Disk

{% raw %}

	Article: Q72132
	Product(s): Microsoft Disk Operating System
	Version(s): MS-DOS:5.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 23-NOV-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft MS-DOS operating system version 5.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The BACKUP command in MS-DOS version 5.0 does not work correctly when the
	destination disk is unformatted and you try to write a log file to that
	unformatted disk.
	
	MORE INFORMATION
	================
	
	BACKUP appears to be trying to write the log file to the destination disk before
	formatting the disk. For example, the following command results in an error if
	the disk in the destination drive is unformatted:
	
	  backup c:\dos5\*.exe a: /f:360 /l:a:\backup.txt
	
	The disk in drive A spins for a short time, at which point the following message
	is displayed:
	
	  General failure error reading drive A
	  Abort, Retry, Fail?
	
	Choosing each of the three options produces different behavior:
	
	1. Choosing Abort causes the program to be successfully aborted.
	
	2. Choosing Retry causes the error to be repeated.
	
	3. Choosing Fail results in BACKUP asking for a disk to be inserted into drive A
	  and produces the following message:
	
	  WARNING! Files in target drive A:
	  A:\ root directory will be erased
	  Press any key to continue . . .
	
	  After a key is pressed, the FORMAT command is invoked, and the disk is
	  successfully formatted. The following message then appears:
	
	  ***Backing up files to drive A:***
	  Diskette Number: 01
	
	  It is quickly followed by the message:
	
	  Error opening logfile
	
	  At this point, the BACKUP program terminates and the DOS prompt appears. The
	  disk in Drive A has no files and contains a label of "BACKUP 001".
	
	Additional query words: 5.00
	
	======================================================================
	Keywords          :  
	Technology        : kbMSDOSSearch kbMSDOS500
	Version           : MS-DOS:5.0
	
	=============================================================================
	

{% endraw %}
