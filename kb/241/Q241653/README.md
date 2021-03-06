---
layout: page
title: "Q241653: Auditing Changes in SCM Not Reflected in User Manager Policies"
permalink: /kb/241/Q241653/
---

## Q241653: Auditing Changes in SCM Not Reflected in User Manager Policies

{% raw %}

	Article: Q241653
	Product(s): Microsoft Windows NT
	Version(s): winnt:4.0,4.0 SP4,4.0 SP5
	Operating System(s): 
	Keyword(s): kbtool kbWinNT4sp6fix
	Last Modified: 16-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0, Terminal Server Edition 
	- Microsoft Windows NT Server versions 4.0 SP4, 4.0 SP5 
	- Microsoft Windows NT Server, Enterprise Edition versions 4.0 SP4, 4.0 SP5 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you attempt to use the Security Configuration Manager (SCM) tool to remove
	two auditing events that are being tracked for an attribute in User Manager for
	Domains (for example, auditing Success and Failure events for the Audit Object
	Access attribute), you can only remove one auditing event. If you are tracking
	two auditing events for an attribute in User Manager for Domains on your Windows
	NT 4.0-based computer, the SCM tool can add an auditing event successfully to
	the tracking that is reflected in User Manager for Domains.
	
	CAUSE
	=====
	
	This behavior occurs because of an incorrect flag set in the Local Security
	Authority (LSA) server library.
	
	RESOLUTION
	==========
	
	Windows NT Server or Workstation 4.0
	------------------------------------
	
	To resolve this problem, obtain the latest service pack for Windows NT 4.0 or the
	individual software update. For information on obtaining the latest service
	pack, please go to:
	
	- http://www.microsoft.com/Windows/ServicePacks/
	
	-or-
	
	- Q152734 How to Obtain the Latest Windows NT 4.0 Service Pack
	
	For information on obtaining the individual software update, contact Microsoft
	Product Support Services. For a complete list of Microsoft Product Support
	Services phone numbers and information on support costs, please go to the
	following address on the World Wide Web:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	
	Windows NT Server 4.0, Terminal Server Edition
	----------------------------------------------
	
	To resolve this problem, obtain the latest service pack for Windows NT Server
	4.0, Terminal Server Edition. For additional information, please see the
	following article in the Microsoft Knowledge Base:
	
	  Q152734 How to Obtain the Latest Windows NT 4.0 Service Pack
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Windows NT 4.0 and Windows NT
	Server 4.0, Terminal Server Edition.
	
	This problem was first corrected in Windows NT Server 4.0 Service Pack 6 and
	Windows NT Server 4.0, Terminal Server Edition Service Pack 6.
	
	MORE INFORMATION
	================
	
	For additional information about the Microsoft Security Configuration Tool Set,
	including Security Configuration Manager, please visit the following Microsoft
	Web site:
	
	  http://www.microsoft.com/TechNet/win2000/win2ksrv/technote/securcon.asp
	
	
	Additional query words:
	
	======================================================================
	Keywords          : kbtool kbWinNT4sp6fix 
	Technology        : kbWinNTsearch kbWinNT400search kbWinNTSsearch kbWinNTSEntSearch kbWinNTSEnt400sp5 kbWinNTSEnt400sp4 kbWinNTS400sp5 kbWinNTS400sp4 kbWinNTS400search kbNTTermServ400 kbNTTermServSearch
	Version           : winnt:4.0,4.0 SP4,4.0 SP5
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
