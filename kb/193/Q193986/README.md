---
layout: page
title: "Q193986: Enable OtherServers Function In The Firewall Environment"
permalink: /kb/193/Q193986/
---

## Q193986: Enable OtherServers Function In The Firewall Environment

{% raw %}

	Article: Q193986
	Product(s): Microsoft SNA Server
	Version(s): WINDOWS:
	Operating System(s): 
	Keyword(s): kbfixlist
	Last Modified: 19-OCT-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SNA Server 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	SNA Server clients are unable to get application sessions on SNA Servers
	configured through the OtherServers registry parameter when the Firewall
	registry entry is also configured on the client. The OtherServers registry entry
	is ignored if the Firewall entry is present.
	
	CAUSE
	=====
	
	The OtherServers and Firewall registry entries are designed to be mutually
	exclusive.
	
	RESOLUTION
	==========
	
	An update is available that allows the Firewall parameter to be ignored when the
	client is trying to connect to a SNA Server defined in the OtherServers
	parameter.
	
	SNA Server 3.0
	--------------
	
	To resolve this problem, obtain the latest service pack for SNA Server version
	3.0. For additional information, please see the following article in the
	Microsoft Knowledge Base:
	
	  Q184307 How to Obtain the Latest SNA Server Version 3.0 Service Pack
	
	
	
	SNA Server 4.0
	--------------
	
	This problem was corrected in the latest SNA Server version 4.0 U.S. Service
	Pack. For information on obtaining this Service Pack, query on the following
	word in the Microsoft Knowledge Base (without the spaces):
	
	  S E R V P A C K
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in SNA Server versions 2.11 SP1,
	2.1 SP2, 3.0, 3.0 SP1, 3.0 SP2, 3.0 SP3, 4.0, and 4.0 SP1. This problem was
	first corrected in SNA Server 3.0 Service Pack 4.
	
	MORE INFORMATION
	================
	
	In addition to the hotfix, a registry parameter has to be added to allow the
	Firewall parameter to be ignored. To add the registry value, perform the
	following steps:
	
	SNA Server Client for Windows NT
	--------------------------------
	
	1. Start Registry Editor (Regedt32.exe), and go to the following location:
	
	  HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services
	  \SnaBase\Parameters\SnaTcp\
	
	  NOTE: The above registry key is one path; it has been wrapped for readability.
	
	2. Add the following information:
	
	  Value Name: UseFireWallWithOtherServers
	  Data Type: REG_SZ
	  String: NO
	
	  NOTE: The default string value is YES, which is also the default if the entry
	  does not exist.
	
	SNA Server Client for Windows 95
	--------------------------------
	
	1. Start Registry Editor (Regedt32.exe), and go to the following location:
	
	  HKEY_LOCAL_MACHINE\Software\Microsoft\SnaBase\Parameters\SnaTcp\
	
	2. Add the following information:
	
	  Value Name: UseFireWallWithOtherServers
	  Data Type: REG_SZ
	  String: NO
	
	  NOTE: The default string value is YES, which is also the default if the entry
	  does not exist.
	
	For Additional information regarding SNA Server and Internet firewalls, please
	check the following article in the Microsoft Knowledge Base:
	
	  Q139508 Internet Firewall Support in SNA Server
	
	
	For additional information regarding the SNA Server OtherServers subkey, please
	see the online Help files.
	
	Additional query words:
	
	======================================================================
	Keywords          :  kbfixlist
	Technology        : kbAudDeveloper kbSNAServSearch
	Version           : WINDOWS:
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
