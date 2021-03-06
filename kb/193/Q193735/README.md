---
layout: page
title: "Q193735: XFOR: Dates Incorrect After Migrating cc:Mail DB6 Bulletin Board"
permalink: /kb/193/Q193735/
---

## Q193735: XFOR: Dates Incorrect After Migrating cc:Mail DB6 Bulletin Board

{% raw %}

	Article: Q193735
	Product(s): Microsoft Exchange
	Version(s): WinNT:5.0,5.5
	Operating System(s): 
	Keyword(s): kbYear2000 exc55sp2fix
	Last Modified: 20-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, versions 5.0, 5.5 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	When you import bulletin board information from Lotus cc:Mail (DB6) to Microsoft
	Exchange Server and then view the messages in the resulting public folder, some
	of the posted dates on the messages may be incorrect. The posted date may be the
	date the migration was performed, instead of the date the message was originally
	posted to the bulletin board.
	
	For example, if the message was originally posted on January 1, 2001, and you
	perform the migration on July 1, 2002, the posted date on the message appears as
	"7/1/02" (without quotation marks) instead of "1/1/01." This problem is not
	likely to occur before the year 2000.
	
	RESOLUTION
	==========
	
	Exchange Server 5.0
	-------------------
	
	A supported fix that corrects this problem is now available from Microsoft, but
	has not been fully regression tested and should be applied only to systems
	experiencing this specific problem. If you are not severely affected by this
	specific problem, Microsoft recommends that you wait for the next Microsoft
	Exchange Server version 5.0 service pack that contains this fix.
	
	To resolve this problem immediately, contact Microsoft Product Support Services
	to obtain the fix. For a complete list of Microsoft Product Support Services
	phone numbers and information on support costs, please go to the following
	address on the World Wide Web:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	The English version of this fix should have the following file attributes or
	later:
	
	  Component: Migration
	
	  File Name     Version
	  -------------------------
	  Mlmig32.dll   5.0.1461.66
	
	This hotfix has been posted to the following Internet location as Psp2miga.exe
	and Psp2migi.exe:
	
	  ftp://ftp.microsoft.com/bussys/exchange/exchange-public/fixes/Eng/Exchg5.0/Post-SP2-MIG
	
	
	Exchange Server 5.5
	-------------------
	
	To resolve this problem, obtain the latest service pack for Exchange Server
	version 5.5. For more information, please see the following article in the
	Microsoft Knowledge Base:
	
	  Q191014 XGEN: How to Obtain the Latest Exchange Server 5.5 Service Pack
	
	
	The English version of this fix should have the following file attributes or
	later:
	
	  Component: Migration
	
	  File Name     Version
	  ------------------------
	  Mlmig32.dll   5.5.2402.0
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft Exchange Server
	versions 5.0 and 5.5. This problem was first corrected in Exchange Server 5.5
	Service Pack 2.
	
	
	======================================================================
	Keywords          : kbYear2000 exc55sp2fix 
	Technology        : kbExchangeSearch kbExchange500 kbExchange550 kbZNotKeyword2
	Version           : WinNT:5.0,5.5
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
