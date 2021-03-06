---
layout: page
title: "Q322829: XADM: Internet Mail Service Does Not Start Successfully"
permalink: /kb/322/Q322829/
---

## Q322829: XADM: Internet Mail Service Does Not Start Successfully

{% raw %}

	Article: Q322829
	Product(s): Microsoft Exchange
	Version(s): 5.5
	Operating System(s): 
	Keyword(s): 
	Last Modified: 07-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 5.5 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	You may notice the following behavior:
	
	- The Microsoft Exchange Server 5.5 Internet Mail Service may not start
	  successfully.
	
	- There may be an error 2140.
	
	- A Dr. Watson error in the Exchange information store process (Store.exe).
	
	Additionally, the following events may be logged in the Application event log of
	the Windows 2000 Event Viewer:
	
	  
	
	  Date:     <date>         Event ID: 4116
	  Time:     <time>         Source:   MSExchangeIMC
	  User:     N/A            Type:     Error
	  Computer: <ServerName>   Category: Internal Processing
	
	  Description:
	  An error was returned from the messaging software the
	  Internet Mail Service uses to process messages on the Microsoft ExchangeServer. It is possible that the piece of mail being processed at the time will not be delivered. The message that was being processed has been moved to the "BAD" folder. Use the appropriate utilities found in the SUPPORT directory of your Exchange CD to view and manipulate these messages.
	
	-and-
	
	  
	
	  Date:     <date>         Event ID: 4023
	  Time:     <time>         Source:   MSExchangeIMC
	  User:     N/A            Type:     Error
	  Computer: <ServerName>   Category: Initialization/Termination
	
	  Description:
	  Unable to start the Internet Mail Service because the work threads could not be initialized.
	
	-and-
	
	  
	
	  Date:     <date>         Event ID: 4182
	  Time:     <time>         Source:   MSExchangeIMC
	  User:     N/A            Type:     Error
	  Computer: <ServerName>   Category: Internal Processing
	
	  Description:
	  A serious error has occurred while trying to send mail into the Exchange Information Store. The Internet Mail Service is being shut down.
	
	-and-
	
	  
	
	  Date:     <date>         Event ID: 3039
	  Time:     <time>         Source:   MSExchangeIMC
	  User:     N/A            Type:     Error
	  Computer: <ServerName>   Category: Internal Processing
	
	  Description:
	  The error 0x80040115 was encountered while trying to communicate with the message store. An attempt to refresh the connection will be made. If not successful, the service will be shut down.
	
	The following error events may also be displayed in the Event Viewer:
	
	  Event ID: 1011
	  Event ID: 4037
	
	CAUSE
	=====
	
	This behavior may occur because of a corrupted message, or because the Internet
	Mail Service is damaged.
	
	RESOLUTION
	==========
	
	To resolve this issue, use the steps in the following methods, in the order in
	which they are presented.
	
	NOTE: Before you continue with the following methods, Microsoft recommends that
	you perform a full backup, to prevent data loss.
	
	Method 1: Remove the Corrupted Mail Item
	----------------------------------------
	
	Use the Microsoft Exchange Messaging Database (MDB) Viewer utility (Mdbvu32.exe)
	to remove any messages from the BAD folder. To do this, follow these steps:
	
	1. Download the Profinst utility. To do this, visit the following Microsoft Web
	  site:
	
	  DownloadDownload Profinst.exe now
	  (http://download.microsoft.com/download/exch50/Utility/1/NT4/EN-US/Profinst.exe)
	
	For additional information about how to download Microsoft Support files, click
	the following article number to view the article in the Microsoft Knowledge
	Base:
	
	  Q119591 How to Obtain Microsoft Support Files from Online Services
	
	Microsoft scanned this file for viruses. Microsoft used the most current
	virus-detection software that was available on the date that the file was
	posted. The file is stored on secure servers that prevent any unauthorized
	changes to the file.
	
	2. At a command prompt, change to the folder that contains the Profinst.exe
	  file, and then type the following command, where <ims> is the test
	  profile that you want to create:
	
	  profinst /service=msexchangeimc /name=<ims> /type=gateway
	
	3. Start the Mdbvu32.exe program. Mdbvu32.exe is on the Exchange Server 5.5
	  CD-ROM in the Server\Support\Utils\I386 folder. You can run the tool directly
	  from the CD-ROM, or you can copy the following files to a specific folder,
	  and then run Mdbvu32 from that folder:
	
	  Mdbvu32.exe
	  Propvu32.dll
	  Statvu32.dll
	  Tblvu32.dll
	  Xvport.dll
	
	4. In the "MAPILogonEx(MAPI_LOGON_UI)" dialog box, click to select the
	  MAPI_EXPLICIT_PROFILE check box, and then click OK.
	
	5. In the "Profile name" list, click the profile that you created with the
	  Profinst tool (for example, click "ims"), and then click OK.
	
	6. On the MDB menu, click OpenMessageStore.
	
	7. Click "Mailbox - Internet Mail Service (<ServerName>)", and then click
	  Open.
	
	  NOTE: If "Mailbox - Internet Mail Service (ServerName)" is not displayed,
	  click Private Folders, and then click Open.
	
	8. On the MDB menu, click Open Root Folder.
	
	9. In the Child Folders box, click Bad.
	
	10. In the "Messages in Folder" list, click a message.
	
	11. In the "Operations available" list, click IpFld->DeleteMessages(), click
	  Call Function, and then click OK to confirm the message deletion.
	
	12. When you finish deleting the messages from the Bad folder, click Close.
	
	13. On the Session menu, click Exit, click OK in the IpMDB->StoreLogoff()
	  dialog box, and then click OK.
	
	If the issue is not resolved, continue to the "Method 2: Reinstall the Internet
	Mail Service" section of this article.
	
	For additional information about how to obtain and use the Exchange MDB Viewer
	utility, click the article number below to view the article in the Microsoft
	Knowledge Base:
	
	  Q165505 XFOR: How to View or Delete Messages in MTS-IN and MTS-OUT Queues
	
	Method 2: Reinstall the Internet Mail Service
	---------------------------------------------
	
	1. Remove the Internet Mail Service. To do this, follow these steps:
	
	  a. Start the Microsoft Exchange Administrator program.
	
	  b. Expand the site, expand Configuration, and then click Connections.
	
	  c. In the right pane, click "Internet Mail Service (<ServerName>)", and
	     then press the DELETE key.
	
	  d. Click Yes to confirm the deletion of the Internet Mail Service.
	
	2. Confirm that the Internet Mail Connector is removed. To do so, follow these
	  steps:
	
	  a. In the Administrator program, expand Servers under Configuration.
	
	  b. Expand your server, expand Private Information Store, and then click
	     Mailbox Resources.
	
	  c. Verify that the Internet Mail Connector is not displayed in the right
	     pane.
	
	     NOTE: If the Internet Mail Connector is displayed, you must defragment the
	     private information store database (Priv.edb).
	
	For additional information about how to defragment Exchange Server databases,
	click the article number below to view the article in the Microsoft Knowledge
	Base:
	
	  Q255035 How to Recover Hard Drive Space from Exchange Server Databases
	
	3. Reinstall the Internet Mail Service, and then configure the Internet Mail
	  Service. To do so, follow these steps:
	
	  a. In the Administrator program, click Connections under Configuration.
	
	  b. On the File menu, point to New Other, and then click Internet Mail
	     Service.
	
	  c. Follow the steps in the Internet Mail Wizard to install, and then
	     configure the Internet Mail Service.
	
	4. Quit the Administrator program.
	
	5. Stop, and then restart the Internet Mail Service. To do so, follow these
	  steps:
	
	  a. Click Start, point to Settings, click Control Panel, and then double-click
	     Services.
	
	  b. In the Service list, click "Microsoft Exchange Internet Mail Service", and
	     then click Stop. Click Yes to confirm stopping this service.
	
	  c. Click Start.
	
	  d. When the Internet Mail Service is started, click Close.
	
	MORE INFORMATION
	================
	
	For additional information, click the article number below to view the article
	in the Microsoft Knowledge Base:
	
	  Q191548 Troubleshooting Guide for the Internet Mail Connector/Internet Mail
	  Service
	
	To obtain Service Pack 4 (SP4) for Microsoft Exchange Server 5.5, please visit
	the following Microsoft Web site:
	
	  http://www.microsoft.com/exchange/downloads/55/sp4.asp
	
	For additional information about post-Service Pack 4 updates to the Internet Mail
	Service, click the article number below to view the article in the Microsoft
	Knowledge Base:
	
	  Q289258 XGEN: Exchange Server 5.5 Post-Service Pack 4 Internet Mail Service
	  Fixes Available
	
	Additional query words: front page
	
	======================================================================
	Keywords          :  
	Technology        : kbExchangeSearch kbExchange550 kbZNotKeyword2
	Version           : :5.5
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
