---
layout: page
title: "Q183232: Problems Using Multihoming in Windows 95"
permalink: /kb/183/Q183232/
---

## Q183232: Problems Using Multihoming in Windows 95

{% raw %}

	Article: Q183232
	Product(s): Microsoft Windows 95.x Retail Product
	Version(s): WINDOWS:95
	Operating System(s): 
	Keyword(s): kberrmsg kbnetwork win95 kbAPI kbSDKPlatform kbWinsock kbGrpDSNet
	Last Modified: 17-DEC-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows 95 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you configure multiple network adapters to use the Microsoft Transmission
	Control Protocol/Internet Protocol (TCP/IP), you may experience any of the
	following symptoms:
	
	- Network names may not be resolved correctly if you are using the Windows
	  Internet Name Service (WINS).
	
	- When you try to log onto a remote domain by using the Remote Access Service
	  (RAS), you may receive the following error message:
	
	  No domain controller was available to validate your logon.
	
	- When you try to use the NET USE command at a command prompt in Windows 95,
	  you may receive the following error message:
	
	  Error 53: The computer name specified in the network path cannot be located.
	  Make sure you are specifying the computer name correctly, or try again later
	  when the remote computer is available.
	
	CAUSE
	=====
	
	This behavior can occur if you use static Internet Protocol (IP) addressing on a
	network and then assign a static WINS address. When you do so, Dial-Up
	Networking defaults to the static WINS address instead of the address assigned
	by RAS, or Dynamic Host Configuration Protocol (DHCP).
	
	RESOLUTION
	==========
	
	To resolve this behavior, install the following updated file for Windows 95:
	
	  Ws2setup.exe version 4.71.0030.1 (dated 2/27/98)
	
	This update is available from the following Microsoft Web site:
	
	http://www.microsoft.com/windows/downloads/contents/Updates/W95Sockets2/default.asp?custarea=pers&site=95&openmenu=downloads&highlighteditem=
	
	NOTE: This Web address should be typed as one continuous line.
	
	MORE INFORMATION
	================
	
	When you configure multiple network adapters to use Microsoft TCP/IP, this
	configuration is known as multihoming. For more information about multihoming,
	please see the following article in the Microsoft Knowledge Base:
	
	  Q169035 Windows 95 WinSock Update to Improve Multihoming Support
	
	======================================================================
	Keywords          : kberrmsg kbnetwork win95 kbAPI kbSDKPlatform kbWinsock kbGrpDSNet 
	Technology        : kbWin95search kbZNotKeyword3
	Version           : WINDOWS:95
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
