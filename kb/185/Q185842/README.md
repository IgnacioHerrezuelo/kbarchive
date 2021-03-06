---
layout: page
title: "Q185842: XADM: 4.0 Server in 5.5 Site Does Not Function Properly"
permalink: /kb/185/Q185842/
---

## Q185842: XADM: 4.0 Server in 5.5 Site Does Not Function Properly

{% raw %}

	Article: Q185842
	Product(s): Microsoft Exchange
	Version(s): WINDOWS:4.0,5.5
	Operating System(s): 
	Keyword(s): 
	Last Modified: 12-APR-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, versions 4.0, 5.5 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	If you use the Setup.exe program in the Server\Support\Exch40\<platform>
	folder on the Microsoft Exchange Server 5.5 CD-ROM to install an Exchange Server
	4.0 computer in an Exchange Server 5.5 site, and then apply Exchange Server 4.0
	Service Pack 5 on the Exchange Server 4.0 computer, the server may no longer
	function properly. In particular, multiple errors related to the message
	transfer agent (MTA) or the directory may occur.
	
	CAUSE
	=====
	
	This problem occurs if the Exchange Server 4.0 database schema is not updated
	before you apply Exchange Server 4.0 Service Pack 5. The Exchange Server
	database schema is updated when you apply Exchange Server 4.0 Service Pack 2 or
	when you install Exchange Server 4.0a.
	
	WORKAROUND
	==========
	
	To work around this problem, use one of the following methods:
	
	- Apply Exchange Server 4.0 Service Pack 2 before you apply Exchange Server
	  Service Pack 5. For information about how to obtain Service Pack 2, please
	  see the following article in the Microsoft Knowledge Base:
	
	  Q152858 XGEN: How to Obtain Exchange Server 4.0 U.S. Service Pack 2
	
	- Install Exchange Server 4.0 from a network share using the installation files
	  from the Exchange Server 4.0a CD-ROM instead of the files from the Exchange
	  Server 4.0 CD-ROM. Be sure to replace the 4.0a Setup.exe program on the
	  network share with the Setup.exe program in the
	  Server\Support\Exch40\<platform> folder on the Exchange Server 5.5
	  CD-ROM. After you install Exchange Server 4.0a, reapply Exchange Server 4.0
	  Service Pack 5.
	
	MORE INFORMATION
	================
	
	Installing Exchange Server from an Exchange Server 4.0a CD-ROM is equivalent to
	applying Exchange Server 4.0 Service Pack 2 on an existing Exchange Server 4.0
	computer.
	
	Additional query words: sp5
	
	======================================================================
	Keywords          :  
	Technology        : kbExchangeSearch kbExchange550 kbExchange400 kbZNotKeyword2
	Version           : WINDOWS:4.0,5.5
	Issue type        : kbbug
	
	=============================================================================
	

{% endraw %}
