---
layout: page
title: "Q181449: XADM: Error -1022 When Starting the Information Store"
permalink: /kb/181/Q181449/
---

## Q181449: XADM: Error -1022 When Starting the Information Store

{% raw %}

	Article: Q181449
	Product(s): Microsoft Exchange
	Version(s): winnt:4.0
	Operating System(s): 
	Keyword(s): exc4
	Last Modified: 16-FEB-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you try to start the Microsoft Exchange Information Store service, the
	following message occurs:
	
	  The Microsoft Exchange Information Store service returned service specific
	  error 4294966274.
	
	The following entries are generated in the Windows NT event log:
	
	  Event ID: 31
	  Source: EDB
	  Type: Error
	  Category: Logging/Recovery
	  Description:
	  MSExchangeIS ((313) ) Unable to read the log header. Error -1022.
	
	  Event ID: 1120
	  Source: MSExchangeIS
	  Type: Error
	  Category: General
	  Description:
	  Error -1022 initializing the Microsoft Exchange Server Information Store
	  database.
	
	CAUSE
	=====
	
	The above errors can be caused by a corrupt Microsoft Exchange Transaction Log
	file. A -1022 error also indicates a potential hardware issue; the Event
	Viewer's System log should be scanned for indications hardware malfunctions.
	
	WORKAROUND
	==========
	
	Rename the Edb.chk file in the Exchsrver\Mdbdata folder. Try starting the
	Information Store service again.
	
	The following events should be generated in the event log:
	
	  Event ID: 18
	  Source: EDB
	  Type: Information
	  Category: Logging/Recovery
	  Description:
	  MSExchangeIS ((137) ) The database is running recovery steps.
	
	  Event ID: 71
	  Source: EDB
	  Type: Information
	  Category: Logging/Recovery
	  Description:
	  MSExchangeIS ((137) ) Redoing log file d:\exchsrvr\MDBDATA\edb00004.log.
	
	  Event ID: 71
	  Source: EDB
	  Type: Information
	  Category: Logging/Recovery
	  Description:
	  MSExchangeIS ((137) ) Redoing log file d:\exchsrvr\MDBDATA\edb00005.log.
	
	The above event indicates which log files have been successfully replayed. In the
	above example, edb00005.log was successfully replayed. Therefore, the problem
	exists in the edb00006.log file.
	
	If there are no Event ID 71 messages generated, the problem may be in the Edb.log
	file, in which case the resolution is to move all the log files out of the
	MDBDATA directory and then restart the Microsoft Information Store service.
	
	Additional query words:
	
	======================================================================
	Keywords          : exc4 
	Technology        : kbExchangeSearch kbExchange400 kbZNotKeyword2
	Version           : winnt:4.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
