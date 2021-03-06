---
layout: page
title: "Q162804: STOP 0x00000079 After Applying Windows NT 4.0 Post-SP2 KRNL Fix"
permalink: /kb/162/Q162804/
---

## Q162804: STOP 0x00000079 After Applying Windows NT 4.0 Post-SP2 KRNL Fix

{% raw %}

	Article: Q162804
	Product(s): Microsoft Windows NT
	Version(s): winnt:4.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 10-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation version 4.0 
	- Microsoft Windows NT Server version 4.0 
	- Microsoft Windows NT Server version 4.0, Terminal Server Edition 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	On a multiprocessor system, after you apply the Windows NT 4.0 Post-SP2 (Service
	Pack 2) KRNL-FIX (Krnl40x.exe, where x is the processor type) the system will
	display a STOP error message:
	
	  STOP: 0x00000079 (0x00000002 0x00000002 0x00000000 0x00000000)
	
	CAUSE
	=====
	
	This error is a mismatched HAL STOP error message. It is caused by applying the
	single processor Ntoskrnl.exe, rather than using the Ntkrnlmp.exe file, which
	needs to be renamed to Ntoskrnl.exe before the fix is applied.
	
	The README file from the fix includes this information:
	
	  Note: If the target computer is a multiprocessor system, then perform the
	  following command in order to replace the uniprocessor version of the kernel
	  with the multiprocessor version. This step must not be done if the target
	  computer is a uniprocessor system.
	
	  Copy NTKRNLMP.EXE NTOSKRNL.EXE
	
	  To install this hotfix, put the new Ntoskrnl.exe, hotfix.exe, and hotfix.ini
	  in the same (temporary) directory, and then type:
	
	  "hotfix /install" (without the quotation marks)
	
	  After installation, type "hotfix" (without the quotation marks) to verify that
	  it was installed correctly, then perform a reboot the system.
	
	RESOLUTION
	==========
	
	To correct this problem, do one of the following:
	
	- If Windows NT is installed on a FAT partition, replace Ntoskrnl.exe in the
	  %SystemRoot%\System32 directory with the Ntkrnlmp.exe from the Post-SP2
	  KRNL-FIX. In the %SystemRoot%\System32 directory, rename Ntkrnlmp.exe to
	  Ntoskrnl.exe.
	
	  Reboot the computer and restart Windows NT.
	
	
	
	-OR-
	
	- Use the following KB article to modify your ERD diskette to replace the
	  Single processor kernel with the Muliprocessor kernel.
	
	  ARTICLE ID: Q164471
	  TITLED : Replacing System Files Using a Modified Emergency Repair Disk
	
	-OR-
	
	- If Windows NT is installed on an NTFS partition, re-install Windows NT to a
	  separate directory (parallel installation). Boot into this new installation.
	  Go to the original Windows NT %SystemRoot%\System32 directory and replace
	  Ntoskrnl.exe with the Ntkrnlmp.exe from the Post- SP2 KRNL-FIX. In the
	  %SystemRoot%\System32 directory, rename Ntkrnlmp.exe to Ntoskrnl.exe.
	
	  Reboot the computer and restart Windows NT, starting into the original version
	  of Windows NT. If the original version now starts properly, the "parallel
	  installation" can be deleted. This can be done using Explorer, File Manager
	  or My Computer.
	
	  WARNING: Use caution when deleting operating system subdirectories or
	  modifying the Boot.ini.
	
	  Delete ONLY the Windows NT directory that was created for the parallel
	  installation; do NOT delete the original installation.
	
	  In addition, the Boot.ini can be modified to remove references to this now
	  non-existent version of Windows NT. If the parallel installation was
	  installed to a directory called Winnt.bak, delete only those lines in
	  Boot.ini that have Winnt.bak. Also, make sure that the "DEFAULT=" entry is
	  directed back to the ARC path and directory for the original installation of
	  Windows NT.
	
	  For additional information on the Boot.ini file, please see the following
	  article in the Microsoft Knowledge Base:
	
	  ARTICLE-ID: Q102873
	  TITLE : BOOT.INI and ARC Path Naming Conventions and Usage
	
	Additional query words: 0x79 SP2 hotfix
	
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbNTTermServ400 kbNTTermServSearch
	Version           : winnt:4.0
	
	=============================================================================
	

{% endraw %}
