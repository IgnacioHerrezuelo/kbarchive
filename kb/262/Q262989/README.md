---
layout: page
title: "Q262989: XFOR: Lotus cc:Mail Migration Event 1030 Error Message"
permalink: /kb/262/Q262989/
---

## Q262989: XFOR: Lotus cc:Mail Migration Event 1030 Error Message

{% raw %}

	Article: Q262989
	Product(s): Microsoft Exchange
	Version(s): 5.5 SP3
	Operating System(s): 
	Keyword(s): exc55sp3
	Last Modified: 08-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 5.5 SP3 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	If you apply the Exchange Server 5.5 Post Service Pack 3 migration fix that is
	documented in the following Microsoft Knowledge Base article
	
	  Q244702 XFOR: Exchange Server 5.5 Post-SP3 Migration Fixes Available
	
	and then run the Migration Wizard to migrate from Lotus cc:Mail, you may receive
	the following error message:
	
	  Event ID: 1030
	  Source: MSExchangeMig
	  Type: Error
	  Description: Invalid Token 'RRT: %1' found within a Message context in the
	  exported file. Account '%2' did not migrate successfully.
	
	CAUSE
	=====
	
	This issue can occur if a return receipt message in the Lotus cc:Mail post
	office is migrated.
	
	
	RESOLUTION
	==========
	
	To resolve this problem, obtain the latest service pack for Exchange Server 5.5.
	For additional information, please see the following article in the Microsoft
	Knowledge Base:
	
	  Q191014 XGEN: How to Obtain the Latest Exchange Server 5.5 Service Pack
	
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft Exchange Server
	version 5.5 Service Pack 3. This problem was first corrected in Exchange Server
	5.5 Service Pack 4.
	
	MORE INFORMATION
	================
	
	The 1030 error occurs during both one-step and two-step migration.
	
	Additional query words:
	
	======================================================================
	Keywords          : exc55sp3 
	Technology        : kbExchangeSearch kbZNotKeyword2 kbExchange550SP3
	Version           : :5.5 SP3
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
