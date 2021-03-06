---
layout: page
title: "Q81349: Floppy Drives with WordPerfect 5.1 and Windows"
permalink: /kb/081/Q81349/
---

## Q81349: Floppy Drives with WordPerfect 5.1 and Windows

{% raw %}

	Article: Q81349
	Product(s): Microsoft Windows 95.x Retail Product
	Version(s): WINDOWS:3.0,3.0a,3.1,3.11
	Operating System(s): 
	Keyword(s): 
	Last Modified: 12-OCT-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows versions 3.0, 3.0a, 3.1, 3.11 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	WordPerfect version 5.1 may cause erratic floppy drive performance or violated
	system integrity errors when running under Microsoft Windows. Floppy drive
	problems can be caused by the following features:
	
	- WordPerfect's cursor speed enhancement feature
	
	- Saving a file using WordPerfect's F10 function key
	
	MORE INFORMATION
	================
	
	WordPerfect's Cursor Speed Enhancement Feature
	----------------------------------------------
	
	WordPerfect testing has confirmed that the cursor speed enhancement feature
	included with WordPerfect version 5.1 can be linked to floppy drive problems.
	This feature adjusts the system clock timer, which also seems to affect floppy
	drive performance. It is suggested that you use the /NC switch to disable this
	feature for troubleshooting these problems in enhanced mode.
	
	Saving a File Using WordPerfect's F10 Function Key
	--------------------------------------------------
	
	You may have difficulty saving a file to the floppy drive if you use the F10
	(save) key in WordPerfect version 5.1 when you are in Microsoft Windows version
	3.0 enhanced mode. You may receive an error message stating that WordPerfect
	version 5.1 cannot read the drive.
	
	Possible Workarounds
	--------------------
	
	1. Exit Windows and restart Windows, then return to WordPerfect.
	
	2. Open the CONFIG.SYS file in WordPerfect. Make sure HIMEM.SYS is loaded prior
	  to any other device drivers in the CONFIG.SYS file, as in the following
	  example:
	
	        DEVICE=C:\HIMEM.SYS
	        FILES=30
	        BUFFERS=30
	        DEVICE=C:\DRIVERNAME
	
	3. Add the following lines to the [386ENH] section of the SYSTEM.INI:
	
	        HighFloppyReads=NO
	        EMMExclude=E000-EFFF
	
	  This workaround appears to correct a conflict between the way WordPerfect 5.1
	  makes floppy drive calls and some system's shadow RAM addressing.
	
	4. Save your changes and exit by pressing the F7 key in WordPerfect. You can
	  still designate the desired drive with the F7 key. (Verify that the disk has
	  been formatted and is readable at the MS-DOS prompt.)
	
	NOTE: Another way to save in WordPerfect is to block the document by pressing
	ALT+F4 and then pressing F10 to save the "block name" to the floppy disk.
	
	The product included here is manufactured by a vendor independent of Microsoft;
	we make no warranty, implied or otherwise, regarding this product's performance
	or reliability.
	
	Additional query words: 3.00 3.00a 3.0a 3.1 3rdparty 3.11 word perfect wp
	
	======================================================================
	Keywords          :  
	Technology        : kbWin3xSearch kbZNotKeyword3 kbWin300 kbWin300a kbWin310 kbWin311
	Version           : WINDOWS:3.0,3.0a,3.1,3.11
	
	=============================================================================
	

{% endraw %}
