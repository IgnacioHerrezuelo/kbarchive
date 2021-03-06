---
layout: page
title: "Q198850: Uninstalled Modem Remains in Fax Server Registry Settings"
permalink: /kb/198/Q198850/
---

## Q198850: Uninstalled Modem Remains in Fax Server Registry Settings

{% raw %}

	Article: Q198850
	Product(s): Microsoft Windows NT
	Version(s): winnt:4.0,4.0a,4.5
	Operating System(s): 
	Keyword(s): kbenv kbhw kbprint kbHardware
	Last Modified: 11-JUN-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft BackOffice Small Business Server versions 4.0, 4.0a, 4.5 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about modifying the registry. Before you modify the registry, make sure to back it up and make sure that you understand how to restore the registry if a problem occurs. For information about how to back up, restore, and edit the registry, click the following article number to view the article in the Microsoft Knowledge Base:
	
	  Q256986 Description of the Microsoft Windows Registry
	
	SYMPTOMS
	========
	
	Whenever a modem is added to Small Business Server (SBS), an entry for the modem
	is added under the fax server registry settings. When a modem is removed,
	however, the entry remains in the registry. This may cause some unintended
	interruptions in the fax service, or various other symptoms.
	
	RESOLUTION
	==========
	
	To correct this problem, use the following procedure to delete the unneeded
	entry:
	
	WARNING: If you use Registry Editor incorrectly, you may cause serious problems
	that may require you to reinstall your operating system. Microsoft cannot
	guarantee that you can solve problems that result from using Registry Editor
	incorrectly. Use Registry Editor at your own risk.
	
	1. Click Start, point to Settings, click Control Panel, and then double- click
	  Services.
	
	2. Stop the Microsoft Fax Service.
	
	3. Run Registry Editor (Regedt32.exe)
	
	4. Go to the following key:
	
	     HKEY_LOCAL_MACHINE\Software\Microsoft\Fax\Devices\ 
	
	  At this time, you may want to save the key in case an entry needs to be
	  restored.
	
	5. There will be a key for each installed and uninstalled modem. The keys will
	  have been named using a random, 8-digit number. Delete the keys that are not
	  needed.
	
	6. Restart the Microsoft Fax Service.
	
	MORE INFORMATION
	================
	
	If you are unable to determine which modem keys are needed and which can be
	deleted from the registry, follow this procedure.
	
	1. Before stopping the Microsoft Fax Service, click Start, point to Settings,
	  click Control Panel, and then double-click Fax Server.
	
	2. Click the Receive tab. Select an installed modem and change one of the
	  settings (CSID, Rings before answer, routing options, and so on). Repeat for
	  all installed modems.
	
	3. In the registry, look under the parameters for each modem listed. The ones
	  that are currently installed will have the new values, while the unneeded
	  modem entries will have the old values.
	
	4. After you restart the Microsoft Fax Service, reset the changed values back to
	  the original settings.
	
	======================================================================
	Keywords          : kbenv kbhw kbprint kbHardware 
	Technology        : kbAudDeveloper kbSBServSearch kbSBServ400 kbSBServ400a kbSBServ450
	Version           : winnt:4.0,4.0a,4.5
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
