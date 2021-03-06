---
layout: page
title: "Q150303: XCLN: How to Back Up Profile Rules to a Different .PST"
permalink: /kb/150/Q150303/
---

## Q150303: XCLN: How to Back Up Profile Rules to a Different .PST

{% raw %}

	Article: Q150303
	Product(s): Microsoft Exchange
	Version(s): WINDOWS:4.0,5.0
	Operating System(s): 
	Keyword(s): kbusage
	Last Modified: 25-MAR-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Windows 95/98 client, versions 4.0, 5.0 
	- Microsoft Exchange Windows 3.x client, versions 4.0, 5.0 
	- Microsoft Exchange Windows NT client, versions 4.0, 5.0 
	- Microsoft Exchange Macintosh client, versions 4.0, 5.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	You can back up profile rules to a separate .PST file. For example, you might
	want to save the .PAB and .PST files, but not the rules. Or you might want to
	make a copy of the rules and apply them to different mailboxes.
	
	MORE INFORMATION
	================
	
	To back up rules, follow these steps:
	
	1. Create a new Personal Folder (PST).
	
	2. Add a new folder to the PST named Test.
	
	3. Select the new folder.
	
	4. Click Application Design on the Tools menu and select the Copy Folder Design
	  option.
	
	  NOTE: This step applies to Outlook users only. Choose Folder from the File
	  menu and selct the Copy Folder Design.
	
	5. Select the Inbox.
	
	6. Make sure the Rules box is selected.
	
	7. Click the OK button.
	
	This will copy the rules to the folder in the PST. The rules will not do anything
	in this folder except exist.
	
	If the Microsoft Exchange Server is lost with no hope of recovery or restoration,
	you can reverse the above procedure to copy the rules back to your Inbox after
	the Microsoft Exchange Server is re-installed.
	
	For additional information on how to import rules from this PST file to another
	mailbox, please see the following article in the Microsoft Knowledge Base:
	
	  Q152852 XADM: Steps to Move User and Inbox Assistant Rules
	
	Additional query words:
	
	======================================================================
	Keywords          : kbusage 
	Technology        : kbHWMAC kbOSMAC kbExchangeSearch kbExchange500 kbExchange400 kbExchangeClientSearch kbZNotKeyword kbZNotKeyword2 kbZNotKeyword3 kbExchange500Mac kbExchange400Mac kbExchange400NT kbExchange500NT kbExchange400Win95 kbExchange500Win95
	Version           : WINDOWS:4.0,5.0
	
	=============================================================================
	

{% endraw %}
