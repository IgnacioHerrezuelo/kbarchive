---
layout: page
title: "Q317189: Err Msg: Stop c000021a {Fatal System Error} The Session..."
permalink: /kb/317/Q317189/
---

## Q317189: Err Msg: Stop c000021a {Fatal System Error} The Session...

{% raw %}

	Article: Q317189
	Product(s): Microsoft Windows NT
	Version(s): 4.0,4.0 SP1,4.0 SP2,4.0 SP3,4.0 SP4,4.0 SP5,4.0 SP6,4.0 SP6a
	Operating System(s): 
	Keyword(s): kbenv kberrmsg kbtool
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation versions 4.0, 4.0 SP1, 4.0 SP2, 4.0 SP3, 4.0 SP4, 4.0 SP5, 4.0 SP6, 4.0 SP6a 
	- Microsoft Windows NT Server versions 4.0, 4.0 SP1, 4.0 SP2, 4.0 SP3, 4.0 SP4, 4.0 SP5, 4.0 SP6, 4.0 SP6a 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about modifying the registry. Before you 
	modify the registry, make sure to back it up and make sure that you understand how to restore 
	the registry if a problem occurs. For information about how to back up, restore, and edit the 
	registry, click the following article number to view the article in the Microsoft Knowledge Base:
	
	  Q256986 Description of the Microsoft Windows Registry
	
	SYMPTOMS
	========
	
	When you start your Windows NT 4.0-based computer, you may receive the following
	error message:
	
	  Stop c000021a {Fatal System Error}
	  The session manager initialization system process terminated unexpectedly with
	  a status of 0xc0000017 (0x00000000, 0x0000000) The system has been shut down.
	
	After you receive this error message, your computer may restart so quickly that
	you are unable to obtain the details of the memory address. This symptom may
	prevent Windows NT from being able to write a valid Memory.dmp file. You may be
	unable to resolve this issue by disabling all third-party services, or by
	repairing your Windows NT installation by using an ERD.
	
	CAUSE
	=====
	
	The error message that is listed in the "Symptoms" section of this article is
	often caused by pending file-rename operations that are scheduled in the Windows
	NT registry, but that cannot be completed.
	
	Programs or Setup programs may schedule a file to be renamed on the next restart
	of Windows NT if the program is prevented from renaming a file because the file
	is in memory.
	
	Windows NT checks a registry key for file-rename operations to be completed early
	in the boot process. If the file-rename operation cannot be completed because
	the file or folder does not exist, the error message that is listed in the
	"Symptoms" section of this article is generated.
	
	
	RESOLUTION
	==========
	
	WARNING: If you use Registry Editor incorrectly, you may cause serious problems
	that may require you to reinstall your operating system. Microsoft cannot
	guarantee that you can solve problems that result from using Registry Editor
	incorrectly. Use Registry Editor at your own risk.
	
	To resolve this issue:
	
	1. Create a parallel installation of Windows NT.
	
	For additional information how to do so, click the article number below to view
	the article in the Microsoft Knowledge Base:
	
	  Q259003 How and Why to Perform a Parallel Installation of Windows NT 4.0
	
	2. Start your computer to the parallel installation of Windows NT, and then
	  start Registry Editor.
	
	3. On the Window menu, click HKEY_LOCAL_MACHINE on Local Machine.
	
	4. On the Registry menu, click Load Hive.
	
	5. Type the path to the System hive of the prior installation, typically
	  "%systemroot%\system32\config\system" (without the quotation marks), and then
	  click "Open" (without the quotation marks).
	
	6. When you are prompted for the name of the key, type "TEST" (without the
	  quotation marks), and then view the following registry entry:
	
	  HKEY_LOCAL_MACHINE\TEST\Select
	
	7. Note the setting for the Current DWord value in the preceding registry key.
	  This is typically 0x1, and is represented as CURRENT:Reg_Dword:0x1. This
	  value indicates that the "CurrentControlSet" for your original Windows NT
	  installation corresponds to ControlSet001 in this window. A value of 2 would
	  indicate that the "CurrentControlSet" for your original Windows NT
	  installation would correspond to ControlSet002, and so on.
	
	8. Locate the following registry key
	
	  HKEY_LOCAL_MACHINE\TEST\ControlSetXXX\Control\Session Manager
	
	  where XXX is the CurrentControlSet that you identified in the preceding step.
	
	9. Under the Session Manager key, note and then delete any
	  PendingFileRenameOperations entries.
	
	10. Click the TEST hive, and then click Unload Hive on the Registry menu.
	
	11. On the Registry menu, click Load Hive.
	
	12. Type the path to the Software hive of the prior installation, typically
	  "%systemroot%\system32\config\Software" (without the quotation marks), and
	  then click Open.
	
	13. When you are prompted for the name of the key, type "TEST2" (without the
	  quotation marks).
	
	14. Remove any PendingFileRenameOperations entries in the following registry
	  keys:
	
	  HKEY_LOCAL_MACHINE\TEST2\Microsoft\Windows\CurrentVersion\RunOnce
	
	  HKEY_LOCAL_MACHINE\TEST2\Microsoft\Windows\CurrentVersion\RunOnceEx
	
	15. Click the TEST2 hive, and then click Unload Hive on the Registry menu.
	
	16. Quit Registry Editor, and then restart your original installation.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbenv kberrmsg kbtool 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTW400sp5 kbWinNTW400sp4 kbWinNTW400sp3 kbWinNTW400sp2 kbWinNTW400sp1 kbWinNTSsearch kbWinNTS400sp6 kbWinNTS400sp5 kbWinNTS400sp4 kbWinNTS400sp3 kbWinNTS400sp2 kbWinNTS400sp1 kbWinNTS400search kbWinNTS400 kbWinNTW400sp6 kbWinNTW400SP6a
	Version           : :4.0,4.0 SP1,4.0 SP2,4.0 SP3,4.0 SP4,4.0 SP5,4.0 SP6,4.0 SP6a
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
