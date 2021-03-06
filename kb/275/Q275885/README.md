---
layout: page
title: "Q275885: XADM: Backup Over Network Won't Work w. 15-Char. Computer Name"
permalink: /kb/275/Q275885/
---

## Q275885: XADM: Backup Over Network Won't Work w. 15-Char. Computer Name

{% raw %}

	Article: Q275885
	Product(s): Microsoft Exchange
	Version(s): 5.5
	Operating System(s): 
	Keyword(s): exc55 kbExchange550preSP5fix
	Last Modified: 08-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 5.5 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	When you back up an Exchange Server computer over the network, the backup may
	stop after a few kilobytes (KB) without any error message. If you run the backup
	locally, the backup works as expected.
	
	CAUSE
	=====
	
	This problem can occur if the computer that is running the Ntbackup.exe program
	to back up the Exchange Server computer over the network has a computer name
	that contains 15 characters or more (for example, if the Ntbackup.exe program
	runs on a computer that has the name Reallybigserver). The name of the Exchange
	Server computer is not important.
	
	RESOLUTION
	==========
	
	A supported fix is now available from Microsoft, but it is only intended to
	correct the problem described in this article and should be applied only to
	systems experiencing this specific problem. This fix may receive additional
	testing at a later time, to further ensure product quality. Therefore, if you
	are not severely affected by this problem, Microsoft recommends that you wait
	for the next Microsoft Exchange Server version 5.5 service pack that contains
	this fix.
	
	To resolve this problem immediately, contact Microsoft Product Support Services
	to obtain the fix. For a complete list of Microsoft Product Support Services
	phone numbers and information about support costs, please go to the following
	address on the World Wide Web:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	NOTE: In special cases, charges that are normally incurred for support calls may
	be canceled, if a Microsoft Support Professional determines that a specific
	update will resolve your problem. Normal support costs will apply to additional
	support questions and issues that do not qualify for the specific update in
	question.
	
	The English version of this fix should have the following file attributes or
	later:
	
	Component: Backup
	
	+---------------------------+
	| File name   | Version     | 
	+---------------------------+
	| Edbbcli.dll | 5.5.2654.15 | 
	+---------------------------+
	|             |             | 
	+---------------------------+
	| Eseback.dll | 5.5.2654.15 | 
	+---------------------------+
	
	
	
	WORKAROUND
	==========
	
	To work around this problem, run the Ntbackup.exe program locally, or use a
	computer that has a name that contains less than 15 characters.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft Exchange Server
	version 5.5.
	
	
	Additional query words:
	
	======================================================================
	Keywords          : exc55 kbExchange550preSP5fix 
	Technology        : kbExchangeSearch kbExchange550 kbZNotKeyword2
	Version           : :5.5
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
