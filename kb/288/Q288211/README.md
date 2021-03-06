---
layout: page
title: "Q288211: XFOR: Addresses for Migrated GroupWise Mail May Appear Truncated"
permalink: /kb/288/Q288211/
---

## Q288211: XFOR: Addresses for Migrated GroupWise Mail May Appear Truncated

{% raw %}

	Article: Q288211
	Product(s): Microsoft Exchange
	Version(s): 5.5
	Operating System(s): 
	Keyword(s): 
	Last Modified: 10-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 5.5 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you attempt to migrate e-mail messages from a Novell GroupWise 5.5 post
	office on a computer that is running the Internet Addressing (GWIA) component
	and the GroupWise 5.2 client, the addresses for the migrated messages may appear
	truncated.
	
	CAUSE
	=====
	
	The GroupWise 5.2 client cannot translate the GWIA addresses because this
	functionality was added in GroupWise version 5.5.
	
	WORKAROUND
	==========
	
	A third-party solution, UniAccess from ComAxis Technology may be used to export
	the GroupWise mail folders and address books to the personal folders (.pst) in
	Microsoft Outlook.
	
	MORE INFORMATION
	================
	
	The Novell GroupWise version 5.5 client is not supported in the Microsoft
	Exchange Migration Wizard. For additional information, click the article number
	below to view the article in the Microsoft Knowledge Base:
	
	  Q268496 XFOR: Migration Wizard Dr. Watson Migrating from GroupWise 5.5
	
	For more information on UniAccess from Comaxis Technology, please visit their Web
	site at the following location:
	
	  http://www.comaxis.com (http://www.comaxis.com)
	
	The third-party contact information included in this article is provided to help
	you find the technical support you need. This contact information is subject to
	change without notice. Microsoft in no way guarantees the accuracy of this
	third-party contact information.
	
	The third-party products discussed in this article are manufactured by vendors
	independent of Microsoft; we make no warranty, implied or otherwise, regarding
	these products' performance or reliability.
	
	Additional query words: netware nds munged exchange
	
	======================================================================
	Keywords          :  
	Component         : GroupWise Migration
	Technology        : kbExchangeSearch kbExchange550 kbZNotKeyword2
	Version           : :5.5
	Issue type        : kbprb
	Solution Type     : kbnofix
	
	=============================================================================
	

{% endraw %}
