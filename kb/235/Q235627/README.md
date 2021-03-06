---
layout: page
title: "Q235627: XIMS: AUTH LOGIN Must Use Base-64-Encoded User Name and Password"
permalink: /kb/235/Q235627/
---

## Q235627: XIMS: AUTH LOGIN Must Use Base-64-Encoded User Name and Password

{% raw %}

	Article: Q235627
	Product(s): Microsoft Exchange
	Version(s): winnt:5.5
	Operating System(s): 
	Keyword(s): kbFEA exc55 EXC55SP3Fea
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 5.5 
	-------------------------------------------------------------------------------
	
	
	IMPORTANT: This article contains information about modifying the registry. Before you 
	modify the registry, make sure to back it up and make sure that you understand how to restore 
	the registry if a problem occurs. For information about how to back up, restore, and edit the 
	registry, click the following article number to view the article in the Microsoft Knowledge Base:
	
	  Q256986 Description of the Microsoft Windows Registry
	
	SUMMARY
	=======
	
	Microsoft Exchange Server 5.5 supports the AUTH LOGIN command for clear text
	authentication using a base-64-encoded user name and password. It does not
	accept the AUTH LOGIN command if the user name and password are in an X.500
	Distinguished Name (DN) format. If the AUTH LOGIN command is sent in this
	manner, the following event may appear in the event log on the Exchange Server
	computer, indicating that the authentication attempt was not successful:
	
	  Event ID: 4183
	  Description: Authentication attempt (AUTH LOGIN) from <hostname> as
	  <username> failed: LogonUser() call failed with error: Logon failure:
	  unknown user name or bad password.
	
	Note that when responding to an EHLO command, Exchange Server always indicates
	that it supports the AUTH LOGIN command.
	
	MORE INFORMATION
	================
	
	Microsoft recognizes the fact that some e-mail clients and servers send the AUTH
	LOGIN command with a user name and password in an X.500 DN format. We have
	modified the Internet Mail Service so it can be configured to behave in the
	following manner:
	
	- AUTH commands are not accepted by the server.
	- When responding to an EHLO command, the server does not indicate that it
	  supports the AUTH LOGIN command.
	
	This feature is available in the latest service pack for Exchange Server version
	5.5. For additional information, click the following article number to view the
	article in the Microsoft Knowledge Base:
	
	  Q191014 XGEN: How to Obtain the Latest Exchange Server 5.5 Service Pack
	
	The English version of this feature should have the following file attributes or
	later:
	
	Component: Internet Mail Service
	
	+---------------------------+
	| File name    | Version    | 
	+---------------------------+
	| Imcmsg.dll   | 5.5.2638.0 | 
	+---------------------------+
	| Msexcimc.exe | 5.5.2638.0 | 
	+---------------------------+
	
	This feature was first included in Exchange Server 5.5 Service Pack 3.
	
	
	After you obtain this feature, to modify the behavior of the Internet Mail
	Service:
	
	WARNING: If you use Registry Editor incorrectly, you may cause serious problems
	that may require you to reinstall your operating system. Microsoft cannot
	guarantee that you can solve problems that result from using Registry Editor
	incorrectly. Use Registry Editor at your own risk.
	
	1. Start Registry Editor (Regedt32.exe).
	
	2. Locate the following key in the registry:
	
	  HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSExchangeIMC\Parameters
	
	  NOTE: The above registry key is one path; it has been wrapped for readability.
	
	3. On the Edit menu, click Add Value, and then add the following registry value:
	
	  Value Name: DisableAuth
	  Data Type: REG_DWORD
	  Value: 1 (or any other non-zero value)
	
	4. Quit Registry Editor.
	
	Additional query words: fail
	
	======================================================================
	Keywords          : kbFEA exc55 EXC55SP3Fea 
	Technology        : kbExchangeSearch kbExchange550 kbZNotKeyword2
	Version           : winnt:5.5
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
