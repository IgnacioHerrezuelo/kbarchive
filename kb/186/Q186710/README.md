---
layout: page
title: "Q186710: FEEDIGNOREFINAL is Not a Valid Option"
permalink: /kb/186/Q186710/
---

## Q186710: FEEDIGNOREFINAL is Not a Valid Option

{% raw %}

	Article: Q186710
	Product(s): Microsoft SNA Server
	Version(s): WINDOWS:3.0 SP2,3.0 SP3,4.0,4.0 SP1
	Operating System(s): 
	Keyword(s): 
	Last Modified: 23-SEP-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SNA Server, versions 3.0 SP2, 3.0 SP3, 4.0, 4.0 SP1 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you are configuring an SNA Server 3270 print session with the command line
	utility Snacfg.exe, FEEDIGNOREFINAL is presented as a valid print session
	option. The option may be turned off and on without effecting print output.
	
	CAUSE
	=====
	
	This option was included in Snacfg.exe but never implemented in the SNA Print
	server.
	
	RESOLUTION
	==========
	
	Microsoft has confirmed this to be a problem in SNA Server versions 3.0, 3.0 SP
	2, 3.0 SP 3, 4.0, and 4.0 SP 1. We are researching this problem in the SNA
	Server version 3.0, and will post more information here in the Microsoft
	Knowledge Base as it becomes available.
	
	This problem was corrected in the latest SNA Server version 4.0 U.S. Service
	Pack. For information on obtaining this Service Pack, query on the following
	word in the Microsoft Knowledge Base (without the spaces):
	
	  S E R V P A C K
	
	MORE INFORMATION
	================
	
	This option is not needed. SNA Print Server ignores the last Form Feed in the
	print data stream. When printing with GDI, SNA Print calls EndDoc() to end a
	print job. This function adds a Form Feed therefore, an extra page may result if
	not ignored. When printing with a printer definition file (PDF) this is not the
	case, SNA Print calls EndDocPrinter(), which does not issue a Form Feed,
	however, the END_JOB macro usually contains a Form Feed and can be removed if
	two Form Feeds are in the data stream to avoid an extra page from being printed.
	
	Additional query words: snaprint
	
	======================================================================
	Keywords          :  
	Technology        : kbAudDeveloper kbSNAServSearch kbSNAServ400 kbSNAServ300SP3 kbSNAServ400SP1 kbSNAServ300SP2
	Version           : WINDOWS:3.0 SP2,3.0 SP3,4.0,4.0 SP1
	Issue type        : kbbug
	
	=============================================================================
	

{% endraw %}
