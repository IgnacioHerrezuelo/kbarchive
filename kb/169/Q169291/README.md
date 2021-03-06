---
layout: page
title: "Q169291: Using Scopes with Different Subnet Masks in a Superscope"
permalink: /kb/169/Q169291/
---

## Q169291: Using Scopes with Different Subnet Masks in a Superscope

{% raw %}

	Article: Q169291
	Product(s): Microsoft Windows NT
	Version(s): 2000,4.0
	Operating System(s): 
	Keyword(s): kbWinNT400sp4fix
	Last Modified: 09-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0 
	- Microsoft Windows NT Server version 4.0, Terminal Server Edition 
	- Microsoft Windows 2000 Advanced Server 
	- Microsoft Windows 2000 Server 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you use a superscope made up of scopes with different subnet masks, client
	computers may not be able to get an IP address using DHCP. This situation will
	occur if the first scope in the superscope is full.
	
	Example
	-------
	
	You have a single segment using the following addresses:
	
	  192.168.1.1-255, subnet mask 255.255.255.0
	  192.168.2.1-62, subnet mask 255.255.255.192
	
	You use one DHCP server, create a scope for each network, and then create a
	superscope using these two scopes. This procedure will allow your DHCP server to
	assign addresses from either scope to clients on the same physical segment.
	
	After the 192.168.1.0 scope is full, a client can no longer get an IP address
	using DHCP. If you look at the event viewer log on your computer running Windows
	NT DHCP server, you will see that the server sent a NACK to itself for an
	address it just tried to give out.
	
	RESOLUTION
	==========
	
	To resolve this problem, obtain the latest service pack for Windows NT 4.0 or
	Windows NT Server 4.0, Terminal Server Edition. For additional information,
	please see the following article in the Microsoft Knowledge Base:
	
	  Q152734 How to Obtain the Latest Windows NT 4.0 Service Pack
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Windows NT 4.0 and Windows NT
	Server 4.0, Terminal Server Edition. This problem was first corrected in Windows
	NT 4.0 Service Pack 4.0 and Windows NT Server 4.0, Terminal Server Edition
	Service Pack 4.
	
	
	MORE INFORMATION
	================
	
	For more information on superscopes, please see the following article in the
	Microsoft Knowledge Base:
	
	  Q161571 Using DHCP "Superscopes" to Serve Multiple Logical Subnets
	
	For more information about the NACKing behavior introduced in SP2, please see the
	following article in the Microsoft Knowledge Base:
	
	  Q163055 DHCP Client May Fail with NT 4.0 SP2 Multinetted DHCP Server
	
	
	Additional query words:
	
	======================================================================
	Keywords          : kbWinNT400sp4fix 
	Technology        : kbWinNTsearch kbWinNT400search kbwin2000AdvServ kbwin2000AdvServSearch kbwin2000Serv kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbwin2000ServSearch kbwin2000Search kbNTTermServ400 kbNTTermServSearch kbWinAdvServSearch
	Version           : :2000,4.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
