---
layout: page
title: "Q283056: Error Message &quot;Unable to Load Your Profile&quot; When You Install SMS"
permalink: /kb/283/Q283056/
---

## Q283056: Error Message &quot;Unable to Load Your Profile&quot; When You Install SMS

{% raw %}

	Article: Q283056
	Product(s): Microsoft Windows NT
	Version(s): 2.0,4.0
	Operating System(s): 
	Keyword(s): kbenv kberrmsg kbsms200
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server version 2.0 
	- Microsoft Windows NT Server version 4.0 
	- Microsoft Windows NT Workstation version 4.0 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about modifying the registry. Before you 
	modify the registry, make sure to back it up and make sure that you understand how to restore 
	the registry if a problem occurs. For information about how to back up, restore, and edit the 
	registry, click the following article number to view the article in the Microsoft Knowledge Base:
	
	  Q256986 Description of the Microsoft Windows Registry
	
	SYMPTOMS
	========
	
	When you attempt to install Systems Management Server (SMS) version 2.0 client
	software, you may receive the following error message:
	
	  Unable to load your profile, please contact your administrator.
	
	This error message is displayed on the screen after the current user has logged
	on to the computer.
	
	CAUSE
	=====
	
	This behavior can occur if the "default user" profile has either been replaced
	with a preconfigured profile or has been corrupted. This behavior can cause the
	SMS client software to be unable to make the security changes to the protected
	storage key when it attempts to create a new user profile for one of the SMS
	client software accounts, the SMSCliToknAcct$ account.
	
	RESOLUTION
	==========
	
	WARNING: If you use Registry Editor incorrectly, you may cause serious problems
	that may require you to reinstall your operating system. Microsoft cannot
	guarantee that you can solve problems that result from using Registry Editor
	incorrectly. Use Registry Editor at your own risk.
	
	To work around this behavior, use one of the following three methods:
	
	- Ignore the errors on the client. The profile is able to load despite the
	  errors. The errors occur only during SMS client installation. Most computers
	  report this behavior only one time. After the installation has completed, the
	  profile loads properly. The SMS client also runs properly. Subsequent logon
	  attempts do not report the profile load error.
	
	- For each computer that exhibits this behavior:
	  1. Connect to the admin share, or log on locally to the affected computer.
	
	  2. Load and edit the permissions in the "default user" Ntuser.dat file. To
	     perform this step, you must load the Ntuser.dat file as a registry hive:
	     a. Start Regedt32.exe.
	
	     b. Click the HKEY_LOCAL_MACHINE hive.
	
	     c. On the Registry menu, click Load Hive.
	
	     d. Specify the Ntuser.dat file at the %Systemroot%\Profiles\Default User
	        folder on the affected computer.
	
	     e. You are asked to specify a "key name." This key name is used to
	        identify the hive that you are loading and is a subkey of
	        HKEY_LOCAL_MACHINE. Enter any name that is not already in use.
	
	     f. Locate HKEY_LOCAL_MACHINE/<Key Name>/Software/Microsoft/Protected
	        Storage System Provider/<Sid>. The security identifier (SID) is
	        for the user who created the profile that had been copied to the
	        default user (for example,
	        S-1-5-21-1234567890-1234567890-123456789-1001). The SID can be
	        unavailable because you do not have permission to access this key.
	        Click this key. On the Security menu, click Permissions, and then add
	        the group "Everyone" with full control access.
	
	     g. Click the key name. On the Registry menu, click Unload.
	
	- Replace the Ntuser.dat file or the entire user profile for "default user"
	  with an unmodified copy from another computer. This step, however, is not
	  recommended because a new user can lose the benefit of obtaining a
	  preconfigured default profile.
	
	MORE INFORMATION
	================
	
	The default user profile is located in the %Systemroot%\Profiles\Default User
	folder. When a new user logs on, the computer copies the "default user" profile
	to the new users profile folder under the %Systemroot%\Profiles\<Username>
	folder. You may be unable to make the security changes to the protected storage
	key when the preconfigured (default user) profile is used to create a new
	profile for the SMSCLiToknAcct$ account.
	
	The registry key is located at:
	
	  HKEY_CURRENT_USER/Software/Microsoft/Protected Storage System
	  Provider/<Sid>
	
	NOTE: The preceding registry key is one path; the key may have been wrapped for
	readability.
	
	To confirm this behavior, enable userenv logging as discussed in the following
	article:
	
	  Q154120 Debugging User Profiles and System Policies in Windows NT 4.0
	
	The output from the logging can be similar to the following output:
	
	  C:\Winnt\Profiles\Smsclitoknacct\Ntuser.dat
	  CopyProfileDirectory: Leaving with a return value of 1
	  IssueDefaultProfile: Leaving successfully
	  RestoreUserProfile: Successfully setup the local default.
	  SetupNewHive: Entering
	  ApplySecurityToRegistryKey : Failed to open subkey
	  S-1-5-21-1283131943-1217870647-1252928729-500, error = 5
	  ApplySecurityToRegistryKey : Failed to apply security to subkey Protected
	  Storage System Provider, error = 5
	  ApplySecurityToRegistryKey : Failed to apply security to subkey Microsoft,
	  error = 5
	  ApplySecurityToRegistryKey : Failed to apply security to subkey Software,
	  error = 5
	  SetupNewHive: Failed to apply security to user registry tree, error = 5
	  SetupNewHive: Leaving with a return value of 0
	  RestoreUserProfile: SetupNewHive failed
	  RestoreUserProfile: About to Leave. Final Information follows:
	  ApplySecurityToRegistryKey : Failed to open subkey
	  S-1-5-21-1283131943-1217870647-1252928729-500, error = 5
	  ApplySecurityToRegistryKey : Failed to apply security to subkey Protected
	  Storage System Provider, error = 5
	
	The SID that is listed, S-1-5-21-1283131943-1217870647-1252928729-500, belongs to
	the local administrator account because the administrator had been the user that
	created the profile, which had been copied to the default user profile during
	the operating system installation. An error occurred after the operating system
	copied the profile from the default user to the new user account (SMSClitokn$,
	in this scenario) and attempted to change the permissions on the protected
	storage key.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbenv kberrmsg kbsms200 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbSMSSearch kbSMS200
	Version           : :2.0,4.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
