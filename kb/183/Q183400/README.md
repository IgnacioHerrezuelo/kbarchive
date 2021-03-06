---
layout: page
title: "Q183400: XADM: Specific Events That ISINTEG Attempts to Fix"
permalink: /kb/183/Q183400/
---

## Q183400: XADM: Specific Events That ISINTEG Attempts to Fix

{% raw %}

	Article: Q183400
	Product(s): Microsoft Exchange
	Version(s): WINDOWS:5.5
	Operating System(s): 
	Keyword(s): 
	Last Modified: 08-APR-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 5.5 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Isinteg.exe can be used to detect and attempt to fix specific problems in the
	information store. This article lists Windows NT Application Log events that can
	point to problems in the information store. Each event is followed by a
	description of the event and the test that is used with Isinteg.exe.
	
	MORE INFORMATION
	================
	
	  Event ID: 1025
	  Description: An error occurred. Function name or description of problem:
	  EcGetRestriction. Error: 0x57a
	  Test: -test search
	  
	  Event ID: 1186
	  Description: A database inconsistency (EcSetSpecialRights/ACLID) was
	  encountered while performing an upgrade.
	  Test: -test acllistref
	
	  Event ID: 1186
	  Description: A database inconsistency (2.1A/AMIDRefCt) was encountered
	  while performing an upgrade.
	  Description: A database inconsistency (2.1A/AMIDRef) was encountered
	  while performing an upgrade.
	  Description: A database inconsistency (2.1B/AMID) was encountered while
	  performing an upgrade.
	  Description: A database inconsistency (2.2D/AMID) was encountered while
	  performing an upgrade.
	  Test: -test aclitemref
	
	  Event ID: 1186
	  Description: A database inconsistency (2.1A/ACLID) was encountered while
	  performing an upgrade.
	  Description: A database inconsistency (2.1B/ACLID) was encountered while
	  performing an upgrade.
	  Description: A database inconsistency (2.2D/ACLID) was encountered while
	  performing an upgrade.
	  Description: A database inconsistency (2.1A/ACLRef) was encountered
	  while performing an upgrade.
	  Test: -test acllistref
	
	  Event ID: 1186
	  Description: A database inconsistency (2.1B/cnset) was encountered while
	  performing an upgrade.
	  Test: -test aclitemref
	
	  Event ID: 1198
	  Description: A database inconsistency was encountered while performing
	  an upgrade to version 2.19.
	  FID: <value>
	  MID: <value>
	  INID: <value>
	  Description: A database inconsistency was encountered while performing
	  an upgrade to version 2.2a.
	  FID: <value>
	  MID: <value>
	  INID: <value>
	  Test: -test folder
	
	  Event ID: 7200
	  Description: Background thread FDsWaitTask halted due to error code
	  <value>.
	  Test: -test mailbox
	
	  Event ID: 7200
	  Description: Background thread EcFlushInTransitUserMail halted due to
	  error code <value>.
	  Test: -test folder
	
	  Event ID: 7201
	  Description: Background thread FDoMaintenance encountered a problem.
	  Error code <value>.
	  Test: -test folder,artidx
	
	  Event ID: 7201
	  Description: Background thread FDoPeriodic encountered a problem. Error
	  code <value>.
	  Test: -test rowcounts, dumpsterref
	
	  Event ID: 8500
	  Description: Unable to move mailbox <mailbox name>. A problem occurred
	  while opening an attachment. Internal parent folder ID: <value>, parent
	  message ID: <value>; Error code: <value>.
	  Test: -test message
	
	  Event ID: 8501
	  Description: Unable to move mailbox <mailbox name>. A problem occurred
	  while opening an attachment. Parent folder name: <name>, parent message
	  subject: <subject>; Error code: <value>.
	  Test: -test message
	
	  Event ID: 8502
	  Description: Unable to move mailbox <mailbox name>. A problem occurred
	  while opening an attached message.
	  Internal parent folder ID: <value>, parent message ID: <value>; Error
	  code: <value>.
	  Test: -test message
	
	  Event ID: 8503   Unable to move mailbox <mailbox name>.
	  Description: A problem occurred while opening an attached message.
	  Parent folder name: <value>, parent message subject: <value>; Error
	  code: <value>.
	  Test: -test message*
	
	  Event ID: 8504
	  Description: Unable to move mailbox <mailbox name>. A problem occurred
	  while getting the properties for a folder. Internal folder ID: <value>;
	  Error code: <value>.
	  Test: -test folder*
	
	  Event ID: 8505
	  Description: Unable to move mailbox <mailbox name>. A problem occurred
	  while getting the properties for a folder. Folder name: <value>; Error
	  code: <value>.
	  Test: -test folder*
	
	  Event ID: 8506
	  Description: Unable to move mailbox <mailbox name>. A problem occurred
	  while getting the properties for a message. Internal parent folder ID:
	  <value>; Message ID: <value>; Error code: <value>.
	  Test: -test folder,message*
	
	  Event ID: 8507
	  Description: Unable to move mailbox <mailbox name>. A problem occurred
	  while getting the properties for a message. Parent folder name: <value>;
	  Message subject: <value> Error code: <value>.
	  Test: -test folder,message*
	
	  Event ID: 8508
	  Description: Unable to move mailbox <mailbox name>. A problem occurred
	  while getting the properties for an attachment. Internal parent folder
	  ID: <value>, parent message ID: <value>; Error code: <value>.
	  Test: -test attach
	
	  Event ID: 8509
	  Description: Unable to move mailbox <mailbox name>. A problem occurred
	  while getting the properties for an attachment. Parent folder name:
	  <value>, parent message subject: <value>; Error code: <value>.
	  Test: -test attach
	
	* The problems causing this message to appear may not be related to the integrity
	of the information store.
	
	The events shown above may be, but are not necessarily, a result of a corrupted
	information store. Consequently, in some cases the suggested option does not
	repair the problem associated with the event log ID and description. If the
	suggested test does not resolve the problem, Microsoft Technical Support will
	direct you to other diagnostic methods.
	
	For more information, see the Isinteg.rtf file on the Exchange Server 5.5 CD, in
	the following location:
	
	  Server\Support\Utils\Isinteg.rtf
	
	======================================================================
	Keywords          :  
	Technology        : kbExchangeSearch kbExchange550 kbZNotKeyword2
	Version           : WINDOWS:5.5
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
