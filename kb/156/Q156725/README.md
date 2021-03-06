---
layout: page
title: "Q156725: XFOR: MS Mail X.400 Gateways and Exchange X.121 Addresses"
permalink: /kb/156/Q156725/
---

## Q156725: XFOR: MS Mail X.400 Gateways and Exchange X.121 Addresses

{% raw %}

	Article: Q156725
	Product(s): Microsoft Exchange
	Version(s): winnt:4.0
	Operating System(s): 
	Keyword(s): kbusage
	Last Modified: 19-DEC-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	If your Microsoft Exchange Server sends a message indirectly via a Shared File
	System (SFS) X.400 gateway, and part of the X.400 O/R address contains:
	
	  X.121=
	
	and there is a period between the X and the 1, the X.400 gateway will fail to
	process the message. The following error will appear on the X.400 gateway if it
	is running with the -lvd command line option:
	
	  15:46:15 Extracting message from local message store: 00000020
	  15:46:15 DEBUG (Converting PC Mail message to X400): Translating to X400
	  15:46:15 ERROR 3 (Creating P1 Recipient address): Malformed address: type
	  <16>
	
	CAUSE
	=====
	
	The SFS X.400 gateway will only process X.121 addresses when there is no period
	between the X and the 1. The period will be present when an X.400 address is
	imported from Microsoft Mail to Microsoft Exchange Server using Directory
	Synchronization (DirSync) and the address is of the format
	c=gb;a=admd;p=prmd;x.121=1234567890. This is a valid address, but not an address
	that the SFS X.400 gateway will be able to process.
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft Exchange Server
	version 4.0. This problem was corrected in the latest Microsoft Exchange Service
	Pack. For information on obtaining the Service Pack, query on the following word
	in the Microsoft Knowledge Base:
	
	  " SERVPACK " (without the quotation marks)
	
	
	Additional query words:
	
	======================================================================
	Keywords          : kbusage 
	Technology        : kbExchangeSearch kbExchange400 kbZNotKeyword2
	Version           : winnt:4.0
	
	=============================================================================
	

{% endraw %}
