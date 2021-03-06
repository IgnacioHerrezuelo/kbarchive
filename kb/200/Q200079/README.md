---
layout: page
title: "Q200079: XADM: Event ID 2247 Directory Name Object Allocation Failed"
permalink: /kb/200/Q200079/
---

## Q200079: XADM: Event ID 2247 Directory Name Object Allocation Failed

{% raw %}

	Article: Q200079
	Product(s): Microsoft Exchange
	Version(s): winnt:4.0
	Operating System(s): 
	Keyword(s): exc4
	Last Modified: 19-AUG-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 4.0 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	If data compression is turned on for directory synchronization (dirsync)
	messages, you may get the following application log error messages. In addition,
	you may see the Exchange Server available CPU cycles drop to near 0.
	
	  Event ID 2247
	  Source: MTA OpSys
	  Category: Warning
	  Description: "A directory name object allocation command failed' "RD Server
	  MAIN BASE[1114] 12"
	
	You may also receive:
	
	  Event ID: 2380
	  Source: MSExchangeMSMI
	  Category: Session error
	  Description: A memory access violation has occurred that prevents further
	  processing of a message. The access violation that occurred is an attempt to
	  read from 0x4. Please refer to the immediate following events for more
	  information.
	
	  Event ID: 2447
	  Source: MSExchangeMSMI
	  Category: Session error
	  Description: MSMI has failed processing $System message is left in the
	  delivery queue.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Exchange Server version 4.0.
	This problem has been corrected in the latest U.S. service pack for Exchange
	Server version 4.0. For information on obtaining the service pack, query on the
	following word in the Microsoft Knowledge Base (without the spaces):
	
	  S E R V P A C K
	
	MORE INFORMATION
	================
	
	If compression is turned on, then the attachments in the dirsync messages
	generated by the directory exchange agent (DXA) are in a compressed format and
	unreadable when viewed with an editor, similar to:
	
	[ASCII 176][ASCII 229]([ASCII 140][ASCII 220][ASCII 194][ASCII 206]-[ASCII 194]   @[ASCII 208]?-0&[ASCII 238][ASCII 158]FY
	($[ASCII 220][ASCII 177]mu"z"iQ[ASCII 167]/[ASCII 142][ASCII 173]][ASCII 143]#[ASCII 194]@kEdP[ASCII 178]m[ASCII 211][ASCII 186][ASCII 233][ASCII 244][ASCII 173][ASCII 221][ASCII 178]l[ASCII 217]&[ASCII 168]'[ASCII 190][ASCII 216][ASCII 136]'[ASCII 173][ASCII 203][ASCII 182],H[ASCII 168]l[ASCII 235][ASCII 206]'?6[ASCII 188]
	
	An uncompressed message with some formatting applied looks similar to:
	
	[ASCII 162][ASCII 175]
	R pcm:MYNET/MYPO-#@[ASCII 208]?-0&[ASCII 238][ASCII 158]FY
	A Admin  pcm:MYNET/MYPO/Admin0&[ASCII 238][ASCII 158]FY
	A Admin Schedule Plus   pcm:MYNET/MYPO/adminsch"z"iQ
	
	A possible workaround is to turn DXA compression off:
	
	WARNING: Using the raw mode of the Exchange Server Administrator program (admin
	/r) incorrectly can cause serious problems that may require you to reinstall
	Microsoft Windows NT Server and/or Microsoft Exchange Server. Microsoft cannot
	guarantee that problems resulting from the incorrect use of raw mode can be
	solved. Use raw mode at your own risk.
	
	1. Start the Microsoft Exchange Server Administrator program in raw mode by
	  typing the following at a command prompt:
	
	  "c:\exchsrvr\bin\admin /r" (without the quotation marks)
	
	2. Select each Dirsync Requestor object individually.
	
	3. On the File menu, click Raw Properties to view the raw properties of the
	  Requestor object.
	
	4. Look for the DXA-FLAG object, view the number, and subtract 32 from it. For
	  example. You might see a value of 39604. Change it to 39572 to turn
	  compression off the $system messages.
	
	For additional information, please see the following article in the Microsoft
	Knowledge Base:
	
	  Q140946 XADM: Microsoft Mail Interchange Hang During DirSync
	
	Additional query words:
	
	======================================================================
	Keywords          : exc4 
	Technology        : kbExchangeSearch kbExchange400 kbZNotKeyword2
	Version           : winnt:4.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
