---
layout: page
title: "Q287425: SMS: Successfully Using NetworkLoginProfile Class in Sms_def.mof"
permalink: /kb/287/Q287425/
---

## Q287425: SMS: Successfully Using NetworkLoginProfile Class in Sms_def.mof

{% raw %}

	Article: Q287425
	Product(s): Microsoft Systems Management Server
	Version(s): 2.0
	Operating System(s): 
	Keyword(s): kbnetwork win95 win98 kbClient kbConfig kbSecurity kbWBEM kbsms200 kbInventory
	Last Modified: 12-APR-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server version 2.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	When you modify the Sms_def.mof file to collect information from the
	NetworkLoginProfile class during hardware inventory, the account information may
	not be returned as expected.
	
	This article describes the necessary requirements to successfully use the
	NetworkLoginProfile class in the Sms_def.mof file.
	
	MORE INFORMATION
	================
	
	The NetworkLoginProfile class enumerates all local profiles and network accounts
	for a computer, and it then queries a domain controller to gain information
	about those accounts. In versions of Windows Management Instrumentation (WMI)
	earlier than 1.5, this enumeration is inaccurate. WMI version 1.5 successfully
	completes class enumeration. You can obtain the latest version of WMI by
	clicking the link in the "References" section of this article. Only WMI version
	1.1 is included in the Systems Management Server (SMS) service packs.
	
	For computers that are running either Microsoft Windows 95, Microsoft Windows 98,
	or Microsoft Windows 98 Second Edition (SE), you may have to enable the creation
	of profiles for this class to work properly. For Windows 98-based computers, you
	configure this in Control Panel by using the Users program tool. For Windows
	95-based computers, you configure this in Control Panel by using the Passwords
	program tool.
	
	REFERENCES
	==========
	
	To download the latest WMI version, go to the following Microsoft Web site:
	
	  http://msdn.microsoft.com/downloads/default.asp?url=/downloads/sample.asp?url=/MSDN-FILES/027/001/552/msdncompositedoc.xml
	  (http://msdn.microsoft.com/downloads/default.asp?url=/downloads/sample.asp?url=/MSDN-FILES/027/001/552/msdncompositedoc.xml)
	
	Additional query words: prodsms hinv wbem wmi windows
	
	======================================================================
	Keywords          : kbnetwork win95 win98 kbClient kbConfig kbSecurity kbWBEM kbsms200 kbInventory 
	Technology        : kbSMSSearch kbSMS200
	Version           : :2.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
