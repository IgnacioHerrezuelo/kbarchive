---
layout: page
title: "Q319749: XCON: Error 1824 in Exchange Internet Mail Service"
permalink: /kb/319/Q319749/
---

## Q319749: XCON: Error 1824 in Exchange Internet Mail Service

{% raw %}

	Article: Q319749
	Product(s): Microsoft Exchange
	Version(s): 5.5
	Operating System(s): 
	Keyword(s): 
	Last Modified: 26-JUL-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 5.5 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	The Internet Mail Service may stop working, and the following system event ID
	may be logged in the Application event log:
	
	  The Microsoft Exchange Information Store service terminated with a
	  service-specific error 1824.
	
	CAUSE
	=====
	
	This issue may be caused by either of the following conditions:
	
	- The Exchange Server-based computer is manufactured by Compaq, and the
	  computer is using the Compaq Insight Manager, and a file that is associated
	  with the NetBIOS interface is missing or corrupted.
	
	  -or-
	
	- The network interface card (NIC) is defective or it is using corrupted
	  drivers.
	
	RESOLUTION
	==========
	
	To resolve this issue, use either of the following methods, as appropriate for
	your situation.
	
	Method 1: Reinstall the NetBIOS Interface
	-----------------------------------------
	
	If the Exchange server is manufactured by Compaq and is using the Compaq Insight
	Manager, follow these steps:
	
	1. Quit any antivirus software or backup software.
	
	2. Quit the Insight Manager, and then set the startup settings to deactivated.
	  For more information about how to do this, see the Compaq documentation.
	
	3. Click Start, point to Settings, and then click Control Panel.
	
	4. Double-click Network.
	
	5. Click the Services tab.
	
	6. Remove the NetBIOS interface.
	
	7. Allow the computer to rebind the settings, but do not restart the computer.
	
	8. Reinstall the NetBIOS interface. Do not restart the computer.
	
	9. Reapply your current service pack, and then restart the computer.
	
	10. Start the Insight Manager, and then set the startup settings to activated.
	  For more information about how to do this, see the Compaq documentation.
	
	Method 2: Reinstall the Network Interface Card
	----------------------------------------------
	
	If the Exchange server is not using the Compaq Insight Manager, follow these
	steps:
	
	1. Click Start, point to Settings, and then click Control Panel.
	
	2. Double-click Network, click the Adapters tab, click the network interface
	  card, and then click Remove.
	
	3. Restart the computer.
	
	4. Reinstall the network interface card.
	
	5. Reapply your current service pack, and then restart the computer.
	
	If this procedure does not resolve the issue, try replacing the network interface
	card.
	
	
	MORE INFORMATION
	================
	
	The third-party products that are discussed in this article are manufactured by
	companies that are independent of Microsoft. Microsoft makes no warranty,
	implied or otherwise, regarding the performance or reliability of these
	products.
	
	Additional query words: front page
	
	======================================================================
	Keywords          :  
	Technology        : kbExchangeSearch kbExchange550 kbZNotKeyword2
	Version           : :5.5
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
