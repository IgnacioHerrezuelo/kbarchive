---
layout: page
title: "Q150567: Btrieve Clients May Fail to Connect to Servers Running RAS, IPX/"
permalink: /kb/150/Q150567/
---

## Q150567: Btrieve Clients May Fail to Connect to Servers Running RAS, IPX/

{% raw %}

	Article: Q150567
	Product(s): Microsoft Windows NT
	Version(s): 3.11,3.5,3.51
	Operating System(s): 
	Keyword(s): 
	Last Modified: 20-FEB-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation versions 3.5, 3.51 
	- Microsoft Windows NT Server versions 3.5, 3.51 
	- Microsoft Windows for Workgroups version 3.11 
	- Microsoft Windows 95 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When Remote Access Service (RAS) is installed on a Windows NT Server running
	NWLink (IPX/SPX) protocol, client/server applications that depend on SAP and RIP
	protocols may not be able to connect to their servers.
	
	Btrieve is one such application. Btrieve clients may appear to hang when they are
	unable to access the Btrieve database engine running on the NT server.
	
	CAUSE
	=====
	
	When RAS is installed on the NT Server, also installed is an IPX router. This
	router considers zero to be an invalid network number. If, under the
	configuration option for NWLink, autodetect is chosen for frame type and no
	routers or a Novell server is present on the local network, then zero may be
	chosen as the network number. If IPX/SPX protocol frame types are configured
	manually, then the network numbers associated with these frame types default to
	zero.
	
	You can find out (http://support.microsoft.com/download/support/mslfiles/out) the
	network numbers associated with a given frame type by executing the IPXROUTE
	CONFIG command at a command prompt.
	
	
	WORKAROUND
	==========
	
	To solve this problem, enter a valid network number for each frame type
	specified in the registry on the Windows NT Server. (A valid network number is
	an eight-digit hexadecimal number whose value is greater than zero; for example,
	AABBCCDD.)
	
	WARNING: Using Registry Editor incorrectly can cause serious, system-wide
	problems that may require you to reinstall Windows NT to correct them. Microsoft
	cannot guarantee that any problems resulting from the use of Registry Editor can
	be solved. Use this tool at your own risk.
	
	1. Open the Registry Editor (Regedt32.exe).
	
	2. Go to the following location:
	
	  HKEY_LOCAL_MACHINE\SYSTEM\CurrentcontrolSet\Services
	  \NWLnkIPX\Netconfig\<adapter name>
	
	3. Look for the value entries for the NetworkNumber and PktType parameters.
	
	4. Each value in the PktType parameter specifies a frame type, and and each
	  frame type must have a corresponding value entry in the NetworkNumber
	  parameter. For details on these settings, see:
	
	  "Services for NetWare Networks: Microsoft Windows NT Server," version 3.5,
	  Appendix A, Pages, 114-115.
	
	5. Restart the computer.
	
	
	The Btrieve product discussed here is manufactured by Pervasive Software Inc.
	(formerly Btrieve Technologies Inc.), a vendor independent of Microsoft; we make
	no warranty, implied or otherwise, regarding this product's performance or
	reliability.
	
	Additional query words: btrieve novell database
	
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNT351search kbWinNT350search kbWinNTW350 kbWinNTW350search kbWinNTW351search kbWinNTW351 kbWinNTSsearch kbWinNTS351 kbWinNTS350 kbWinNTS351search kbWinNTS350search kbAudDeveloper kbWin95search kbWFWSearch kbZNotKeyword3 kbWFW311
	Version           : :3.11,3.5,3.51
	
	=============================================================================
	

{% endraw %}
