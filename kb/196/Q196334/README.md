---
layout: page
title: "Q196334: How to Determine If a Hotfix Is Compatible w/ Terminal Server"
permalink: /kb/196/Q196334/
---

## Q196334: How to Determine If a Hotfix Is Compatible w/ Terminal Server

{% raw %}

	Article: Q196334
	Product(s): Microsoft Windows NT
	Version(s): winnt:4.0
	Operating System(s): 
	Keyword(s): kbfaq
	Last Modified: 11-DEC-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0, Terminal Server Edition 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	When installing hotfixes on a server running Windows NT Server 4.0, Terminal
	Server Edition, it is important to confirm that the hotfix has been built to run
	on Terminal Server. Hotfixes that are built to run on Windows NT Server 4.0,
	Terminal Server Edition will have the 0x8000 bit set in the last two bytes of
	the FileVer property of the VS_FIXEDFILEINFO structure. You can use the
	Filever.exe utility to examine this structure.
	
	MORE INFORMATION
	================
	
	When you use the FILEVER utility on Apimon.exe from the Support directory of the
	Windows NT Terminal Server Edition CDROM, you will see the following
	information:
	
	  filever /v apimon.exe
	  --a-- W32i APP ENU  4.0.1381.32772 shp    184,080 06-16-1998 apimon.exe
	       Language        0x0409 (English (United States))
	       CharSet         0x04b0 Unicode
	       OleSelfRegister Disabled
	       CompanyName     Microsoft Corporation
	       FileDescription API Monitor Debugger
	       InternalName    apimon.exe
	       OriginalFilenam apimon.exe
	       ProductName     Microsoft(R) Windows NT(TM) Operating System
	       ProductVersion  4.00
	       FileVersion     4.00
	       LegalCopyright  Copyright (C) Microsoft Corp. 1981-1998
	
	       VS_FIXEDFILEINFO:
	       Signature:      feef04bd
	       Struc Ver:      00010000
	       FileVer:        00040000:05658004 (4.0:1381.32772)
	       ProdVer:        00040000:05658004 (4.0:1381.32772)
	       FlagMask:       0000003f
	       Flags:          00000000
	       OS:             00040004 NT Win32
	       FileType:       00000001 App
	       SubType:        00000000
	       FileDate:       00000000:00000000
	
	Note that the FileVer property shows a version number of 00040000:05658004 (in
	hex) and 4.0:1381.32772 (in decimal). In this example, the last two bytes are
	0x8004. Because the 0x8000 bit is set, this file was built for Terminal Server.
	Therefore, any number greater than 32767 in last position of the dotted decimal
	version number will be compatible.
	
	The Filever.exe utility can be found in the Windows NT Server 4.0 Resource Kit
	Supplement Two (or later). For more information, see the resource kit
	documentation and the following article in the Microsoft Knowledge Base:
	
	  Q181385 Update.exe from Service Pack May Overwrite Newer OEM Files
	
	Additional query words:
	
	======================================================================
	Keywords          :  kbfaq
	Technology        : kbWinNTsearch kbWinNT400search kbWinNTSsearch kbWinNTS400search kbNTTermServ400 kbNTTermServSearch
	Version           : winnt:4.0
	Hardware          : ALPHA x86
	Issue type        : kbhowto kbinfo
	
	=============================================================================
	

{% endraw %}
