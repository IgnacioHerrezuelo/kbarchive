---
layout: page
title: "Q162205: &quot;Stop 0x1E&quot; Message Reinstalling Windows NT with SP3 and RAS"
permalink: /kb/162/Q162205/
---

## Q162205: &quot;Stop 0x1E&quot; Message Reinstalling Windows NT with SP3 and RAS

{% raw %}

	Article: Q162205
	Product(s): Microsoft Windows NT
	Version(s): 4.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 09-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0 
	- Microsoft Windows NT Workstation version 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you reinstall Windows NT 4.0 over an existing Windows NT 4.0 installation
	with Remote Access Service (RAS), or when you install RAS for the first time,
	you may experience either of the following symptoms:
	
	- Your computer reboots repeatedly.
	
	- You receive the following error message:
	
	  STOP: 0x0000001E (0xC0000005, 0xFF1BBD79, 0x00000000, 0x00000038)
	  KMODE_EXCEPTION_NOT_HANDLED Address ff1bbd79 has base at ff1ae000 - tcpip.sys
	
	CAUSE
	=====
	
	This behavior occurs when Windows NT 4.0 Service Pack 2 or Service Pack 3 is
	installed. The Tcpip.sys file that is installed by the service pack is not
	replaced with the original Tcpip.sys file from the Windows NT 4.0 CD- ROM when
	you reinstall Windows NT or install RAS for the first time.
	
	RESOLUTION
	==========
	
	Use one of the following methods to resolve this issue:
	
	- If you have not logged into your computer, choose the Last Known Good option
	  at boot. Then remove RAS, reinstall RAS, and reapply the latest Service Pack.
	  Perform all of these steps without rebooting.
	
	  -or-
	
	- Replace the Tcpip.sys file installed by the service pack with the original
	  version of the file included on the Windows NT 4.0 CD-ROM. To do so, use one
	  of the following methods, and then reinstall the latest version of the
	  service pack.
	
	  Method 1
	  --------
	
	  If you have access to another computer with Windows NT 4.0 without Windows NT
	  4.0 Service Pack 2 or Service Pack 3 installed, copy the Tcpip.sys file from
	  the %SystemRoot%\system32\drivers folder on the other computer to the
	  corresponding folder on your computer, and then restart your computer.
	
	  NOTE: To use this method, Windows NT must be installed on a FAT partition and
	  you must be able to access your hard disk using MS-DOS, Windows 95, or a boot
	  disk.
	
	  Method 2
	  --------
	
	  If you can dual-boot Windows NT and Windows 95 on your computer, follow these
	  steps:
	
	  1. Start Windows 95.
	
	  2. From a command prompt in Windows 95, expand the Tcpip.sys file from the
	     I386 folder on the Windows NT 4.0 CD-ROM to the
	     %SystemRoot%\system32\drivers folder of your original Windows NT
	     installation. For example, type the following command:
	
	     expand tcpip.sy_ %systemroot%\system32\drivers\tcpip.sys
	
	     NOTE: To properly expand files from the Windows NT CD-ROM, you must use the
	     Expand.exe utility included with Windows NT. The Windows NT Expand.exe
	     utility can only be run from a command prompt in a 32-bit environment such
	     as Microsoft Windows 95 or Windows NT.
	
	  3. Restart your computer and start Windows NT.
	
	  NOTE: To use this method, Windows NT must be installed on a FAT partition.
	
	  Method 3
	  --------
	
	  1. Install Windows NT to a different folder on your hard drive.
	
	  2. Copy the Tcpip.sys file from the %SystemRoot%\system32\drivers folder in
	     the new Windows NT installation to the corresponding folder in the
	     original installation.
	
	  3. Restart your computer to the original Windows NT installation.
	
	  4. Remove the temporary Windows NT installation, and then delete any entries
	     in the Boot.ini file that are entered for that installation.
	
	
	MORE INFORMATION
	================
	
	The Tcpip.sys file provided on the Windows NT 4.0 CD-ROM in the
	%SystemRoot%\system32\drivers folder has the following attributes when it is
	expanded:
	
	  Date     Time      Size      Drive type
	  ---------------------------------------
	  8/2/96   12:30am   133,424   FAT
	  8/1/96    4:30am   133,424   NTFS
	
	Additional query words: prodnt 0x00000050 can't login cannot
	
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400
	Version           : 4.0
	
	=============================================================================
	

{% endraw %}
