---
layout: page
title: "Q118969: X400: Err Msg: Error Malformed Address:Typ"
permalink: /kb/118/Q118969/
---

## Q118969: X400: Err Msg: Error Malformed Address:Typ

{% raw %}

	Article: Q118969
	Product(s): Microsoft Mail For PC Networks
	Version(s): MS-DOS:3.2
	Operating System(s): 
	Keyword(s): 
	Last Modified: 05-NOV-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Mail Gateway to X.400, version 3.2 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When the Microsoft Mail Gateway to X.400 is processing outgoing messages from
	Microsoft Mail for Appletalk Networks, this error may be generated:
	
	  ERROR 3 (creating P1 originator address): Malformed address: type <2>
	
	  NETWORK/POSTOFFICE/USERID
	
	  14:59:26 Extracting message from local message store: 0000043B 14:59:26 ERROR
	  3 (creating P1 originator address): Malformed address:
	  type <2> MACNET/MACPO/1F0001MF
	  14:59:26 ERROR 3 (converting PC mail message to X.400): No Originator Found
	  14:59:26 ERROR 3 (converting PC mail message to X.400): local form to X400
	  conversion
	  14:59:26 ERROR -18 (processing mail bound for X.400): Receive from local
	  message store Failed
	  14:59:26 WARNING -1 (processing mail bound for X.400): FROM:
	  MACNET/MACPO/1F0001MF
	  14:59:26 WARNING -1 (processing mail bound for X.400): SUBJECT: Test
	  14:59:26 ERROR -1 (collecting mail from local message store): ProcessMail()
	  14:59:26 WARNING -1 (receiving message): Failed receiving message
	
	CAUSE
	=====
	
	This error indicates that no address conversion exists for the sending
	network/postoffice.
	
	RESOLUTION
	==========
	
	Follow these steps to add a new entry:
	
	1. Go into the X.400 3.2 Admin program.
	
	2. Select "Addressing Conversion" in the Addressing section.
	
	3. Type in the Mail Connection Proxy Network name: "MACNET" (without the
	  quotation marks).
	
	4. Fill in the X.400 addressing fields appropriate to your system.
	
	5. Select Add.
	
	6. Restart the X400 Gateway to so it reads in this information.
	
	Additional query words:
	
	======================================================================
	Keywords          :  
	Technology        : kbMailSearch kbMailGateSearch kbZNotKeyword3 kbMailGatex400320
	Version           : MS-DOS:3.2
	
	=============================================================================
	

{% endraw %}
