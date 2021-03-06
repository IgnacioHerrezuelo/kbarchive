---
layout: page
title: "Q214573: XADM: Store Handle Leak with Invalid POP3 NTLM Authentication"
permalink: /kb/214/Q214573/
---

## Q214573: XADM: Store Handle Leak with Invalid POP3 NTLM Authentication

{% raw %}

	Article: Q214573
	Product(s): Microsoft Exchange
	Version(s): winnt:5.0
	Operating System(s): 
	Keyword(s): kbExchange500preSP3fix
	Last Modified: 08-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 5.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	The Microsoft Exchange Information Store service may leak handles when POP3
	users attempt to use NTLM authentication with credentials that fail to be
	authenticated. To observe if this happening, start Performance Monitor and add
	the Handle Count counter for the Services.exe instance under the PROCESS object.
	This counter will increase as failed logins increase.
	
	CAUSE
	=====
	
	The Exchange Information Store service creates a credential handle (in
	Services.exe) when a user attempts to log on. If the credentials that are passed
	in fail authentication, the Information Store service does not free the handle.
	Instead, it creates a new handle on the next attempt. These handles are not
	freed up until the Exchange Information Store service is stopped.
	
	NOTE: This behavior is corrected in Version 5.5 of the product.
	
	
	RESOLUTION
	==========
	
	A supported fix is now available from Microsoft, but it is only intended to
	correct the problem described in this article and should be applied only to
	systems experiencing this specific problem. This fix may receive additional
	testing at a later time, to further ensure product quality. Therefore, if you
	are not severely affected by this problem, Microsoft recommends that you wait
	for the next Microsoft Exchange Server version 5.0 service pack that contains
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
	
	Component: Information Store
	
	+--------------------------+
	| File name  | Version     | 
	+--------------------------+
	| Mdbmsg.dll | 5.0.1461.83 | 
	+--------------------------+
	| Store.exe  | 5.0.1461.83 | 
	+--------------------------+
	
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft Exchange Server
	version 5.0.
	
	Additional query words: services.exe crash perfmon
	======================================================================
	Keywords          : kbExchange500preSP3fix 
	Technology        : kbExchangeSearch kbExchange500 kbZNotKeyword2
	Version           : winnt:5.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
