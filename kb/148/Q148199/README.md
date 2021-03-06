---
layout: page
title: "Q148199: XCLN: Re-creating a Deleted Schedule+ Free/Busy Agent"
permalink: /kb/148/Q148199/
---

## Q148199: XCLN: Re-creating a Deleted Schedule+ Free/Busy Agent

{% raw %}

	Article: Q148199
	Product(s): Microsoft Exchange
	Version(s): winnt:4.0
	Operating System(s): 
	Keyword(s): kbnetwork
	Last Modified: 26-MAY-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	When you use the Schedule+ Free/Busy Connector in Microsoft Exchange Server
	version 4.0, a Microsoft Schedule+ Free/Busy Connector (Alias: AdminSch) mailbox
	agent must be present. If it is not present, the Schedule+ Free/Busy Connector
	cannot be configured or executed. This article discusses how to replace the
	agent if it is removed.
	
	MORE INFORMATION
	================
	
	NOTE: Take extreme care performing the steps below. All configuration
	information for the Microsoft Mail Connector will be lost, along with any custom
	PC Mail MTA. Re-configure the Microsoft Mail Connector after you re-install it.
	
	If the Schedule+ Free/Busy agent has been removed or is missing from the site,
	the Microsoft Mail Connector must be removed and re-installed through the
	Microsoft Exchange Server Setup Program. Do the following:
	
	1. Run the Setup program in maintenance mode and click Add/Remove.
	
	2. Select the Microsoft Exchange Server Change Option.
	
	3. Clear the MS Mail Connector option. Click OK and continue through the
	  installation process. The Microsoft Mail Connector is removed.
	
	4. Run the Setup program in maintenance mode again and click Add/Remove.
	
	5. Select Microsoft Exchange Server Change Option.
	
	6. Select the Microsoft Mail Connector. Click OK and continue through the
	  installation process.
	
	NOTE: You must reinstall the latest Microsoft Exchange Server Service Pack (SP)
	after removing and re-adding the MS Mail Connector. In addition, you must
	re-install SP2 before re-installing SP3 or SP4.
	
	The Schedule+ Free/Busy agent is in the Recipient container of the site and the
	server, where the Microsoft Mail Connector was re-installed.
	
	
	Additional query words: MSMI
	
	======================================================================
	Keywords          : kbnetwork 
	Technology        : kbExchangeSearch kbExchange400 kbZNotKeyword2
	Version           : winnt:4.0
	
	=============================================================================
	

{% endraw %}
