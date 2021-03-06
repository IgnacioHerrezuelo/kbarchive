---
layout: page
title: "Q197808: Domain Trust Relationship Cannot be Created"
permalink: /kb/197/Q197808/
---

## Q197808: Domain Trust Relationship Cannot be Created

{% raw %}

	Article: Q197808
	Product(s): Microsoft Windows NT
	Version(s): WinNT:3.51,4.0,4.5
	Operating System(s): 
	Keyword(s): kbnetwork
	Last Modified: 10-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft BackOffice Server versions 4.0, 4.5 
	- Microsoft Windows NT Server versions 3.51, 4.0 
	- Microsoft Windows NT Server, Enterprise Edition version 4.0 
	- Microsoft Windows NT Server version 4.0, Terminal Server Edition 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you attempt to establish a trust relationship between two domains that do
	not replicate their respective Microsoft Windows Internet Name Service (WINS)
	databases, you receive the following error message:
	
	  Could not find domain controller for this domain
	
	CAUSE
	=====
	
	This behavior may occur if a primary domain controller (PDC) cannot resolve
	another PDC's <Domain name\0x1b> entry through WINS.
	
	RESOLUTION
	==========
	
	To resolve this problem, you can create an LMHOSTS file on both primary domain
	controllers to provide cross-domain name resolution capability. Each file must
	contain the TCP/IP address and <Domain name\0x1b> entry for the opposite
	controller. For information on creating the LMHOSTS file, see the following
	article in the Microsoft Knowledge Base.
	
	  Q180094 How to Write an LMHOSTS File for Domain Validation
	
	After you create the LMHOSTS files, use the NBTSTAT -R command to preload the
	entries into cache.
	
	It is recommended that you also verify that the LMHOSTS lookup function is
	enabled. You can do this by clicking Start, pointing to Settings, clicking
	Control Panel, and then double-clicking Network. Click the Protocols tab,
	double-click TCP/IP Protocol, click the WINS Address tab, and then click to
	select the Enable LMHOSTS Lookup check box. Click OK, and then click Close.
	
	======================================================================
	Keywords          : kbnetwork 
	Technology        : kbWinNTsearch kbWinNT351search kbWinNT400search kbWinNTSsearch kbWinNTSEntSearch kbWinNTSEnt400 kbWinNTS400search kbWinNTS400 kbWinNTS351 kbNTTermServ400 kbNTTermServSearch kbWinNTS351search kbAudDeveloper kbBackOfficeSearch kbBackOfficeServ400 kbBackOfficeServ450
	Version           : WinNT:3.51,4.0,4.5
	Hardware          : ALPHA x86
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
