---
layout: page
title: "Q191992: NdrConvert Causes Access Violation in RPC Client on WinNT 4.0"
permalink: /kb/191/Q191992/
---

## Q191992: NdrConvert Causes Access Violation in RPC Client on WinNT 4.0

{% raw %}

	Article: Q191992
	Product(s): Microsoft Windows NT
	Version(s): winnt:4.0
	Operating System(s): 
	Keyword(s): kbnetwork kbWinNT400sp4fix kbRPC kbSDKPlatform kbGrpDSNet
	Last Modified: 09-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation version 4.0 
	- Microsoft Windows NT Server version 4.0 
	- Microsoft Windows NT Server version 4.0, Terminal Server Edition 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When running an RPC client application on a Windows NT little endian computer
	and connecting to a non-Microsoft RPC server implementation on a big endian
	computer, the RPC client may cause an access violation (AV), and generate a Dr.
	Watson log.
	
	CAUSE
	=====
	
	The Microsoft RPC runtime library improperly converts data.
	
	RESOLUTION
	==========
	
	To resolve this problem, obtain the latest service pack for Windows NT 4.0 or
	Windows NT Server 4.0, Terminal Server Edition. For additional information,
	please see the following article in the Microsoft Knowledge Base:
	
	  Q152734 How to Obtain the Latest Windows NT 4.0 Service Pack
	
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Windows NT 4.0 and Windows NT
	Server 4.0, Terminal Server Edition. This problem was first corrected in Windows
	NT 4.0 Service Pack 4.0 and Windows NT Server 4.0, Terminal Server Edition
	Service Pack 4.
	
	Additional query words: violate
	
	======================================================================
	Keywords          : kbnetwork kbWinNT400sp4fix kbRPC kbSDKPlatform kbGrpDSNet 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbNTTermServ400 kbNTTermServSearch
	Version           : winnt:4.0
	Hardware          : ALPHA x86
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
