---
layout: page
title: "Q166543: XFOR: Migration Wizard Hangs with Invalid Entry in SEC File"
permalink: /kb/166/Q166543/
---

## Q166543: XFOR: Migration Wizard Hangs with Invalid Entry in SEC File

{% raw %}

	Article: Q166543
	Product(s): Microsoft Exchange
	Version(s): 5.0
	Operating System(s): 
	Keyword(s): kbusage
	Last Modified: 15-MAY-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 5.0 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	When you use the Migration Wizard to import users from file and there is a
	problem with the secondary file, the application may stop responding. The file
	will be processed up until the point where the error occurred and errors will be
	logged in the Windows NT Event Viewer application log. This will only happen
	when running the Migration Wizard on Windows NT Server 3.51. The problem does
	not occur with Windows NT Server 4.0.
	
	CAUSE
	=====
	
	The problem is caused by a NULL value that is generated when an improperly
	constructed or corrupted entry in the .SEC migration file is read by the
	Migration Wizard. This NULL value is not properly handled and the application
	shuts down.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft Exchange Server
	version 5.0. This problem was corrected in the latest Microsoft Exchange Server
	5.0 U.S. Service Pack. For information on obtaining the service pack, query on
	the following word in the Microsoft Knowledge Base (without the spaces):
	
	  S E R V P A C K
	
	======================================================================
	Keywords          : kbusage 
	Technology        : kbExchangeSearch kbExchange500 kbZNotKeyword2
	Version           : 5.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
