---
layout: page
title: "Q266638: XADM: Information Store Stops Responding Receiving Message"
permalink: /kb/266/Q266638/
---

## Q266638: XADM: Information Store Stops Responding Receiving Message

{% raw %}

	Article: Q266638
	Product(s): Microsoft Exchange
	Version(s): 5.5,5.5 SP1,5.5 SP2,5.5 SP3,5.5 SP4
	Operating System(s): 
	Keyword(s): kbExchange550preSP5fix
	Last Modified: 08-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, versions 5.5, 5.5 SP1, 5.5 SP2, 5.5 SP3, 5.5 SP4 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When the information store (Store.exe) receives a message that includes a
	double-byte character set (DBCS) display name with a missing tailing byte by
	means of Post Office Protocol version 3 (POP3) or Internet Message Access
	Protocol, Version 4rev1 (IMAP4) protocol, the information store causes an access
	violation with the following call stacks:
	
	  
	
	  Function Name
	  ------------------------------------------------------------------------------------------
	  STORE!HrEncodeString+0x451(0x0000000E, 0x000003A4, 0x000003A4, 0x006805D6, 0x00000000, 0x00000001, 0x00000001, 0x14CFCB61, 0x000003DF, 0x1278FCB8, 0x00000000, 0x00
	  000000)
	  store!0x000000000048A274
	  STORE!CmcvtrHdrAddress::HrEmitAddress+0x1c5(0x0000000E, 0x00000000, 0x00000020, 0x00000006, 0x5A7F4AA8, 0x0065C35E, 0x00000000, 0x00000000, 0x00000400, 0x1278FD04)
	  STORE!CmcvtrHdrAddress::HrEmitRecips+0x30a(0x0000000E, 0x5A786830, 0x14CFCB40, 0x00000400, 0x00000004, 0x5A786880)
	  STORE!CmcvtrHdrTo::hrEmit+0x7f(0x0000000E, 0x14CE3240, 0x14CFCB40, 0x00000400, 0x5A786880)
	  STORE!CINETemtr::hrEmit+0x8f(0x0000000E, 0x14CFC528, 0x00000400, 0x1278FDDC)
	  STORE!CConvertStream::Read+0x105(0x6FFF1965, 0x00000003, 0x00000004, 0x00000000)
	  EXCHMEM!MpHeapAlloc+0x101(0x004522A0, 0xFFFFFFFF, 0x5A7862A8)
	  STORE!_except_handler3
	
	RESOLUTION
	==========
	
	A supported fix is now available from Microsoft, but it is only intended to
	correct the problem described in this article and should be applied only to
	systems experiencing this specific problem. This fix may receive additional
	testing at a later time, to further ensure product quality. Therefore, if you
	are not severely affected by this problem, Microsoft recommends that you wait
	for the next Microsoft Exchange Server 5.5 service pack that contains this fix.
	
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
	
	Component: Information store
	
	+----------------------------------------------------------------------+
	| File name | Version     | Date        | Time  | Size      | Platform | 
	+----------------------------------------------------------------------+
	| Store.exe | 5.5.2654.23 | 03-Nov-2000 | 05:33 | 2,620,688 | Intel    | 
	+----------------------------------------------------------------------+
	| Store.exe | 5.5.2654.23 | 03-Nov-2000 | 05:37 | 3,679,504 | Alpha    | 
	+----------------------------------------------------------------------+
	
	NOTE: Because of file dependencies, this fix requires Microsoft Exchange Server
	version 5.5 Service Pack 4.
	
	
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft Exchange Server
	version 5.5.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbExchange550preSP5fix 
	Technology        : kbExchangeSearch kbExchange550 kbZNotKeyword2 kbExchange550SP1 kbExchange550SP2 kbExchange550SP3 kbExchange550SP4
	Version           : :5.5,5.5 SP1,5.5 SP2,5.5 SP3,5.5 SP4
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
