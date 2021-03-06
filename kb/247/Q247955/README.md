---
layout: page
title: "Q247955: SMS: Wuser32.exe Does Not Shut Down Upon Client Shutdown"
permalink: /kb/247/Q247955/
---

## Q247955: SMS: Wuser32.exe Does Not Shut Down Upon Client Shutdown

{% raw %}

	Article: Q247955
	Product(s): Microsoft Systems Management Server
	Version(s): winnt:2.0,2.0 SP1
	Operating System(s): 
	Keyword(s): kbsms200 kbsms200bug kbsms120 kbsms120bug kbHelpDesk
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server versions 2.0, 2.0 SP1 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you shut down a Microsoft Windows NT-based client, a dialog box may be
	presented by Wuser32.exe that prevents the client from shutting down until you
	respond to the dialog box by clicking Wait, End Task, or Cancel.
	
	RESOLUTION
	==========
	
	To resolve this problem, obtain the latest service pack for Systems Management
	Server 2.0. For additional information, click the following article number to
	view the article in the Microsoft Knowledge Base:
	
	  Q236325 How to Obtain the Latest Systems Management Server 2.0 Service Pack
	
	You can also resolve this problem by contacting Microsoft Product Support
	Services to obtain the fix.
	
	The English version of this fix should have the following file attributes or
	later:
	
	  Date        Time   Version         Size     File name    Platform
	  -----------------------------------------------------------------
	  03/03/2000  19:16  2.00.1380.1132  272,416  Wuser32.exe  Intel
	  03/03/2000  19:25  2.00.1380.1132  567,280  Ldwmnt.dll   Intel
	  04/02/2000  20:22                       67  Compver.ini
	  03/03/2000  19:16  2.00.1380.1132  394,000  Wuser32.exe  Alpha
	  03/03/2000  19:25  2.00.1380.1132  850,704  Ldwmnt.dll   Alpha
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Systems Management Server
	version 2.0 SP1. This problem was first corrected in Systems Management Server
	2.0 Service Pack 2.
	
	MORE INFORMATION
	================
	
	To install the hotfix, use the appropriate method on the Systems Management
	Server site server.
	
	Method 1: Using the Hotfix Installer
	------------------------------------
	
	NOTE: You can use this method only on Intel-based computers.
	
	1. Copy the hotfix folder structure to a share on your network. Q247955.exe is
	  an SMS Installer file that updates specific files on your site server.
	
	2. Log on to your site server using an account with administrative privileges.
	
	3. On the site server, quit the Systems Management Server Administrator console.
	
	4. Run Q247955.exe and follow the directions in the wizard. You can run the file
	  in Quiet mode by using the /s switch.
	
	Method 2: Manual Installation
	-----------------------------
	
	1. Stop the SMS_EXECUTIVE and the SMS_SITE_COMPONENT_MANAGER services.
	
	2. On the site server, quit the Systems Management Server Administrator console.
	
	3. Replace the Remctrl.exe file in the
	  <SMS_root>\Inboxes\Clicomp.src\Remctrl\I386 folder with the version
	  obtained from the hotfix.
	
	4. Replace the Compver.ini file in the
	  <SMS_root>\Inboxes\Clicomp.src\Remctrl folder with the version obtained
	  from the hotfix.
	
	5. Replace Ldwmnt.dll file in the <SMS_root>\Bin\I386 folder with the
	  version obtained from the hotfix.
	
	6. Start the SMS_EXECUTIVE and the SMS_SITE_COMPONENT_MANAGER services.
	
	NOTE: The default Client Configuration Installation Manager (CCIM) polling
	interval is 23 hours. Therefore, it may take up to 23 hours for the hotfixed
	files to be propagated to the clients. To speed up this process, you can create
	a software distribution for the Setevnt.exe or Cliutils.exe Resource Kit tool,
	along with the appropriate parameter(s) to start a CCIM work cycle. For
	information about the proper syntax to use with these tools, see the Resource
	Kit documentation.
	
	Additional query words: prodsms
	
	======================================================================
	Keywords          : kbsms200 kbsms200bug kbsms120 kbsms120bug kbHelpDesk 
	Technology        : kbSMSSearch kbSMS200 kbSMS200SP1
	Version           : winnt:2.0,2.0 SP1
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
