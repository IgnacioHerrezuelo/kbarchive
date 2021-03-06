---
layout: page
title: "Q234065: XGEN: Troubleshooting the MTA Queue to Internet Mail Service"
permalink: /kb/234/Q234065/
---

## Q234065: XGEN: Troubleshooting the MTA Queue to Internet Mail Service

{% raw %}

	Article: Q234065
	Product(s): Microsoft Exchange
	Version(s): winnt:5.0,5.5
	Operating System(s): 
	Keyword(s): exc5 exc55
	Last Modified: 27-JAN-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, versions 5.0, 5.5 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	If the Message Transfer Agent (MTA) queue to the Internet Mail Service is
	running slowly or not at all, it can be a difficult issue to troubleshoot. This
	article offers some procedures that may be helpful when trying to resolve this
	problem. It assumes that the MTA, Information Store, and Internet Mail Service
	services are processing other mail including mail between mailboxes on the same
	information store, mail to other servers in the site, and mail across other
	connectors.
	
	MORE INFORMATION
	================
	
	When you see mail in the MTA queue (through Performance Monitor or the Microsoft
	Exchange Server Administrator program), that mail is still in the form of a .dat
	file in the Exchsrvr\Mtadata folder. The next stop for this mail is a hidden
	system folder called Mts-Out, which is the folder used by the store for message
	conversion from MDBEF (Exchange) format to SMTP format. The mail gets to the
	Mts-Out folder by means of XAPI calls between the MTA and the information
	store.
	
	If there is a problem with mail moving from Mtadata to Mts-Out, there are several
	things you need to check.
	
	1. Are there any errors or warnings from the Internet Mail Service, MTA, or
	  information store that may relate to slow outbound SMTP mail flow?
	
	2. What are the values at the following registry locations? You may need to
	  increase these values.
	
	  HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\MSExchangeIS\ParametersSystem\BACKGROUND
	  THREADS
	
	  HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\MSExchangeIS\ParametersPrivate\GATEWAY
	  IN THREADS
	
	  HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\MSExchangeIS\ParametersSystem\MAX
	  THREADS (Public + Private)
	
	  "Gateway In Threads" is the number of threads the information store creates on
	  behalf of the Internet Mail Service when the Internet Mail Service logs on to
	  the information store. "Gateway In Threads" moves messages from the MTA into
	  the information store's Mts-Out queue (destined for the Internet Mail
	  Service). "Gateway Out Threads" moves messages (coming in from the Internet
	  Mail Service) out of the information store's Mts-In queue on to the MTA for
	  distribution. So, increasing the "Gateway In Threads" values increases the
	  pipe between the MTA and the information store for outbound Internet Mail
	  Service messages. Change to 0x8 (hex) = 8 (dec).
	
	  NOTE: Gateway in/out threads are used by the information store for any
	  gateway, not just the Internet Mail Service. The "Background Threads" and
	  "Max Threads <Public+Private>" values must be increased accordingly if
	  you increase "Gateway In Threads" value.
	
	3. Turn up logging on the MTA and the Private Information Store. Double-click
	  the MTA to open the properties, click Diagnostics Logging, and under
	  Categories, click X.400 Service, Interface, Field Engineering, and Internal
	  Processing, and set each to maximum. This generates much more MTA logging and
	  also dumps AP logs in the Mtadata folder.
	
	  On the Private Information Store Properties page, under Services, select
	  MSExchangeIS and Private. Under Category, select the following Transport
	  Sending and Transport Delivering, and set these to maximum. This generates
	  Snd*.logs and Dlv*.logs in the Mdbdata folder. The application log size
	  should be at least 30 MB, overwrite as needed.
	
	4. Create a Calls.out file from the MTA, preferably with a "debug" MTA
	  (instructions for this can be found in Microsoft Knowledge Base article,
	  Q178531, "XADM: Generating the Calls.out File," listed below). This file
	  details the state of the MTA at the time of the problem.
	
	5. Send Microsoft Support Professionals the requested data (app log, AP logs,
	  Snd*.logs, and Dlv*.logs from the Mdbdata folder, Calls.out file, and
	  registry configuration information).
	
	For additional information, please see the following articles in the Microsoft
	Knowledge Base:
	
	  Q165505 XFOR: How to View/Delete Messages in MTS-IN and MTS-OUT Queues
	
	  Q197792 XFOR: General Troubleshooting for Stuck Messages in Internet Mail
	  Service
	
	  Q151214 XADM: Send and Receive Logs in MDBDATA Directory
	
	  Q163321 XCON: Interoperability Logs (AP0.LOG)
	
	  Q168906 XCON: Setting up Advanced Logging on Exchange 5.0 and 5.5 MTAs
	
	  Q178531 XADM: Generating the Calls.out File
	
	Additional query words: xapi
	
	======================================================================
	Keywords          : exc5 exc55 
	Technology        : kbExchangeSearch kbExchange500 kbExchange550 kbZNotKeyword2
	Version           : winnt:5.0,5.5
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
