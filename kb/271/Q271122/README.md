---
layout: page
title: "Q271122: SMS: Users Are Unexpectedly Notified of an Advertised Program"
permalink: /kb/271/Q271122/
---

## Q271122: SMS: Users Are Unexpectedly Notified of an Advertised Program

{% raw %}

	Article: Q271122
	Product(s): Microsoft Systems Management Server
	Version(s): 2.0,2.0 SP1,2.0 SP2,2.0 SP3
	Operating System(s): 
	Keyword(s): kbenv kbsetup kbsms200bug kbsms200fix kbAdvertisement kbPackage kbSoftwareDist kbsms200
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server versions 2.0, 2.0 SP1, 2.0 SP2, 2.0 SP3 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When an administrator sends a mandatory advertisement for a program with the
	"Run once for first user who logs on" property defined, only the first logged on
	user will be required to run it, but each subsequent user that logs on will be
	notified of the available advertisement.
	
	As they are notified, users who are unaware that a package has already been
	installed by another user on the same computer may reinstall a previously
	installed package. When the package is reinstalled, multiple advertisement
	status messages are reported to the Systems Management Server (SMS) database for
	each computer.
	
	CAUSE
	=====
	
	This behavior is according to original product design.
	
	RESOLUTION
	==========
	
	To resolve this problem, obtain the latest service pack for Systems Management
	Server version 2.0. For additional information, click the following article
	number to view the article in the Microsoft Knowledge Base:
	
	  Q288239 SMS: How to Obtain the Latest Systems Management Server 2.0 Service
	  Pack
	
	
	WORKAROUND
	==========
	
	To work around this behavior, use one of the following methods.
	
	- Deploy Microsoft Installer (MSI) packages that contain the logic to verify if
	  a software package is already installed. If a package is already installed,
	  any current user settings may be updated, but the majority of the
	  installation routine is bypassed.
	
	For additional information about MSI packages, click the article number below to
	view the article in the Microsoft Knowledge Base:
	
	  Q262230 Microsoft Installer Programs and Systems Management Server 2.0
	
	- Use script logic with SMS Installer or other scripting languages to verify
	  the presence of a package before the installation routine starts.
	
	- Disable any notifications that are specified in Advertised Programs Client
	  Agent properties.
	
	  NOTE: In the preceding methods, multiple advertisement status messages can
	  still be generated if users run already-installed packages.
	
	- Stop any users from installing programs manually, by specifying an assigned
	  (mandatory) advertisement. Do not enable the "Allow users to run the program
	  independently of assignments" option as this option can cause the preceding
	  behavior.
	
	NOTE: Users who are not notified of new advertisements can still run the SMS
	Advertised Programs Wizard to locate and to install programs.
	
	STATUS
	======
	
	Microsoft has confirmed that this is a problem in the Microsoft products that
	are listed at the beginning of this article. This problem was first corrected in
	Systems Management Server 2.0 Service Pack 4.
	
	MORE INFORMATION
	================
	
	With the hotfix installed, the following notification behavior will occur.
	
	Basic Behavior for Non-Mandatory Advertisements
	-----------------------------------------------
	
	1. Create a new advertisement for a program and target it to a collection of
	  computers. The program property is set to "Run once for fist user who logs
	  on," and this is the default setting.
	
	  The following checks will be made by APM before the notification is displayed:
	
	   - Check if the advertisement is new for the logged-on user by looking into
	     the user's subfolder under the "New" folder.
	
	   - Check the "Complete" folder to see if the program has already been
	     started. This is determined based on the presence of a job file and the
	     "Last Run Time" being later than the "Presented Time" of the
	     advertisement. Note that the "Presented Time" appears in the SMS
	     Administration tool as the "Start Time."
	
	   - Check the "Run once for first user who logs on" flag. If the user has not
	     run the program (based on the preceding checks), a notification is given.
	
	2. Run the program the first time. There is no change from the current behavior.
	
	3. Log in as another user. No notification will be given. This is because the
	  "Run once for first user who logs on" flag is set and the program has already
	  been run after the "Presented Time" of the advertisement. The "Presented
	  Time" is checked because a new advertisement may have been be created for the
	  same program because the package files were changed and the SMS administrator
	  wants the clients to run the program again. In this case, APM will find a new
	  advertisement with a "Presented Time" that is later than the "Last Run Time,"
	  so a notification is given.
	
	  A current advertisement's "Start Time" in the SMS Administration tool is
	  changed. The administrator can now use this to again notify and offer a
	  program to a user.
	
	Mandatory Advertisements Without "Allow Users to Run the Program Independently of Assignments"
	----------------------------------------------------------------------------------------------
	
	No change from current behavior.
	
	Mandatory Advertisements with "Allow Users to Run the Program Independently of Assignments"
	-------------------------------------------------------------------------------------------
	
	The same checks and code changes are applicable to this type as they are to the
	non-mandatory ones.
	
	Advanced Scenarios
	------------------
	
	1. Non-mandatory advertisement that is targeted to computers with a program that
	  is specified to "Run once for every user who logs on".
	
	  Behavior: Every new user that logs on should receive a "New Advertisement"
	  notification. If a user who has already received notification logs back on,
	  they do not receive a notification.
	
	2. Mandatory advertisement that is targeted to computers with a program that is
	  specified to "Run once for every user who logs on".
	
	  Behavior: Because mandatory advertisements do not present notifications, no
	  notifications should be received by any user. The program should only be run
	  once by every user if the schedule is non-recurring (ASAP, logon, logoff, and
	  non-interval time).
	
	3. Mandatory advertisement with "Allow user to run program independently of
	  assignments" that is targeted to computers with a program that is specified
	  to "Run once for every user who logs on."
	
	  Behavior: Every new user that logs on should receive a "New Advertisement"
	  notification. If the same user who has already been given notification logs
	  on again, that user does not receive a notification. The program (if run
	  manually or automatically due to mandatory assignment) should only run once.
	
	4. Non-mandatory advertisement that is targeted to users with a program that is
	  specified to "Run once for every user who logs."
	
	  Behavior: Every new user in the collection that logs on should receive a "New
	  Advertisement" notification. If the same user who has already seen the
	  notification logs on again, that user does not receive a notification.
	
	5. Mandatory advertisement that is targeted to users with a program that is
	  specified to "Run once for every user who logs on."
	
	  Behavior: As mandatory advertisements do not show notifications, no
	  notification should be received by any user. The program should be only run
	  once by every user in the collection if the schedule is non-recurring (ASAP,
	  logon, logoff and non-interval time).
	
	6. Mandatory advertisement with "Allow users to run the program independently of
	  assignments" that is targeted to users with a program that is specified to
	  "Run once for every user who logs on."
	
	  Behavior: Every new user in the collection that logs on will receive a "New
	  Advertisement" notification. If the same user who has already seen the
	  notification logs on again, that user does not receive a notification. If the
	  program is run manually or automatically due to mandatory assignment,
	  notification is only given once.
	
	7. Second non-mandatory advertisement, after running the program under the first
	  advertisement, that is targeted to computers with a program that is specified
	  to "Run once for every user who logs on."
	
	  Behavior: Every new user that logs on will receive a "New Advertisement"
	  notification. If the same user who has already seen the notification logs on
	  again, that user receives a notification. This happens because the "Presented
	  Time" of the second advertisement is after the "Last Run Time" of the
	  program, and the administrator intended that the user run the program again.
	
	8. Second mandatory advertisement, after running the program under the first
	  advertisement, that is targeted to computers with a program that is specified
	  to "Run once for every user who logs on."
	
	  Behavior: Every new user that logs on should receive a "New Advertisement"
	  notification. If the same user who has already seen the notification logs on
	  again, that user does not receive the notification. The program (if run
	  manually or automatically because of mandatory assignment) should only run
	  once.
	
	9. Scenarios 7 and 8, but targeted to users.
	
	  Behavior: Same as in scenarios 7 and 8.
	
	10. Scenarios 7 and 8, but when the program has not yet been run even under the
	  first advertisement.
	
	  Behavior: Similar behavior, but the advertisement will be merged, and only a
	  single notification and program start occurs.
	
	11. Create Program1 which is dependent on Program2 and target Program1 to
	  systems or users.
	
	  Behavior: The advertisement and Program1's settings will dictate program
	  execution through the dependent program chain (specifically, Program2).
	
	
	
	Additional query words: prodsms
	
	======================================================================
	Keywords          : kbenv kbsetup kbsms200bug kbsms200fix kbAdvertisement kbPackage kbSoftwareDist kbsms200preSP3 kbsms200preSP4fix 
	Technology        : kbSMSSearch kbSMS200 kbSMS200SP1 kbSMS200SP2 kbSMS200SP3
	Version           : :2.0,2.0 SP1,2.0 SP2,2.0 SP3
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
