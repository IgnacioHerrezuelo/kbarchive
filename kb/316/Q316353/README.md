---
layout: page
title: "Q316353: HOW TO: Configure a User Account to Use a Roaming User Profile"
permalink: /kb/316/Q316353/
---

## Q316353: HOW TO: Configure a User Account to Use a Roaming User Profile

{% raw %}

	Article: Q316353
	Product(s): Microsoft Windows NT
	Version(s): 4.0
	Operating System(s): 
	Keyword(s): kbUser kbAudITPro kbHOWTOmaster
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0 
	- Microsoft Windows NT Workstation version 4.0 
	-------------------------------------------------------------------------------
	
	
	IN THIS TASK
	------------
	
	- SUMMARY
	
	   - Requirements
	- How to Create a Shared Folder to Store Roaming User Profiles
	- How to Configure a User Account to Use a Roaming User Profile in a Windows NT
	  4.0-Based Domain
	
	- REFERENCES
	
	SUMMARY
	=======
	
	This step-by-step article describes how to configure a user account to use a
	roaming user profile. To do so, you must create a shared folder to store roaming
	user profiles, and then configure the user account to use a roaming user
	profile. After you complete this procedure, the user's profile, including the
	user's unique desktop settings, is stored on a server, and the profile is
	available to the user when the user logs on to any Windows NT 4.0-based computer
	in the domain.
	
	Requirements
	------------
	
	- A Windows NT Server 4.0-based computer (that meets the requirements listed on
	  the Hardware Compatibility List [HCL]) that is a primary domain controller
	  must be available on the network when you configure the user account.
	
	- If you decide not to store roaming user profiles on the primary domain
	  controller, an additional Windows NT Server 4.0-based computer must be
	  available on the network.
	
	How to Create a Shared Folder to Store Roaming User Profiles
	------------------------------------------------------------
	
	Before you configure a user account to use a roaming user profile, you must
	create a shared folder on a Windows NT Server 4.0-based computer in the domain
	to store the roaming user profiles. This shared folder is often located on a
	domain controller, but it can also be located on any Windows NT Server 4.0-based
	computer in the domain.
	
	To create a shared folder to store roaming user profiles:
	
	1. Click Start, point to Programs, and then click Windows NT Explorer.
	
	2. Click the drive on which you want to create a shared folder to store roaming
	  user profiles.
	
	3. On the File menu, point to New, and then click Folder.
	
	4. Type a name for the new folder, and then press ENTER.
	
	  NOTE: Typically, the folder that is used to store roaming user profiles is
	  called "Profiles". However, you can assign any name that you want to the
	  folder.
	
	5. Right-click the folder you created in step 2, and then click Sharing.
	
	6. Click Shared As, type the name that you want to assign to the shared folder
	  in the Share Name box, and then click OK.
	
	  NOTE: The Profiles folder is commonly shared as "Profiles."
	
	7. Quit Windows NT Explorer.
	
	How to Configure a User Account to Use a Roaming User Profile in a Windows NT 4.0-Based Domain
	----------------------------------------------------------------------------------------------
	
	To configure user accounts in the domain, you can use any Windows NT Server
	4.0-based computer in the domain or any Windows NT Workstation 4.0-based
	computer that is running Windows NT Server Tools in the domain. In addition, you
	must be logged on as either an administrator or as a user that is a member of
	the Administrators local group or the Account Operators local group in the
	domain.
	
	To configure a user account to use a roaming user profile:
	
	1. Click Start, point to Programs, point to Administrative Tools (Common), and
	  then click "User Manager for Domains".
	
	2. Double-click the user account to which you want to assign a roaming profile,
	  and then click Profile.
	
	3. Type the complete path to the shared folder that contains the user's profile
	  in the User Profile Path box, and then click OK.
	
	  Use the following format for the user profile path:
	
	  \\<server_name>\<shared_folder_name>\<user_profile_folder_name>
	
	  For example, if you want to store the user's roaming profile in a folder that
	  has the same name as the user account in a shared folder that is named
	  "Profiles" on a server that is named "Server1," type the following path:
	
	  "\\Server1\Profiles\%username%" (without the quotation marks)
	
	  NOTE: Windows NT automatically replaces the %username% variable with the user
	  account name when it creates and accesses the user profile. When you use this
	  variable, you can type the same path for all users.
	
	4. Click OK, and then quit User Manager for Domains.
	
	The next time the user logs on, the user profile folder that you specified in
	step 4 is created. When the user logs off, the user's profile is copied to the
	new folder.
	
	REFERENCES
	==========
	
	For more information about how to configure roaming user profiles, refer to
	Module 2 of Microsoft Official Curriculum, Course Number 803, "Administering
	Microsoft Windows NT 4.0."
	
	For additional information about how to install Windows NT Server Tools, click
	the article number below to view the article in the Microsoft Knowledge Base:
	
	  Q168476 How to Create Mandatory Profiles with Windows NT 4.0
	
	Additional query words:
	
	======================================================================
	Keywords          : kbUser kbAudITPro kbHOWTOmaster 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400
	Version           : :4.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
