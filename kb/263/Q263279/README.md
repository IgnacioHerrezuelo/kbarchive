---
layout: page
title: "Q263279: SMS: Advertisement Fails with Error 10003"
permalink: /kb/263/Q263279/
---

## Q263279: SMS: Advertisement Fails with Error 10003

{% raw %}

	Article: Q263279
	Product(s): Microsoft Systems Management Server
	Version(s): winnt:2.0
	Operating System(s): 
	Keyword(s): kbClient kbConfig kbsms200 kbAdvertisement kbPackage kbSoftwareDist
	Last Modified: 10-AUG-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server version 2.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you attempt to run an advertised program on a Microsoft Windows NT
	Workstation or Microsoft Windows 2000 Professional computer, the targeted
	computer fails and generates the following error status message:
	
	  10003
	  An error occurred while preparing to run the program for advertisement
	  "DEF20001" ("Test Running APP from Network Drive" - "Run TESTAPP from O:
	  drive"). The operating system reported error 2147500037: Unspecified error
	  Additional program properties: Command line: O:\TESTAPP.EXE Working
	  directory: C:\WINNT\MS\SMS\clicomp\apa\Bin\ Drive letter (? = any): UNC
	  Possible cause: This message most commonly occurs when the program?s
	  command-line executable file could not be found, when a required drive letter
	  connection to a distribution point could not be established, or when the
	  program is configured to use the Windows NT Client Software Installation
	  Account but the account is not specified, could not be found, or does not
	  have the appropriate permissions. Solution: Check each of the items listed
	  above.
	
	CAUSE
	=====
	
	This problem can occur when both of the following conditions are true:
	
	- The Advertised Program's command line includes a reference to a network path.
	  For example, O:\Setup.exe, where O: is mapped by the logged on user to a
	  network share resource.
	
	- The Advertised Program's environment properties specify "Run with
	  Administrative rights."
	
	WORKAROUND
	==========
	
	When advertising programs where the command lines reference network resources
	directly, you can use either of the following two methods:
	
	The Program Does Not Need to Be Run with Administrative Rights
	--------------------------------------------------------------
	
	In the Program's Environment settings, under Run Mode, click to select the "Run
	with user's rights" option.
	
	The Program Must Be Run with Administrative Rights
	--------------------------------------------------
	
	- In the Program's Environment settings, under Run Mode, click to select the
	  "Run with administrative rights" option.
	
	- Click to select the option "Use Windows NT client software installation
	  account".
	
	- For the Program command line, specify a valid UNC path, including the program
	  name and any required parameters. For example:
	
	  \\server\share\directory\setup.exe /parameter1 /parameter2
	
	NOTE: To use the Windows NT client software installation account, some
	prerequisites must be met:
	
	- You must create a valid Windows NT client software installation account in
	  the domain that is a member of at least one global group.
	
	- You must specify the Windows NT client software installation account in the
	  Site Settings, under "Component Configuration - Software Distribution".
	
	- You must set the "Program can run:" option to "Whether or not a user is
	  logged in" or "Only when no user is logged in".
	
	MORE INFORMATION
	================
	
	A typical scenario may involve running a command line from a network resource
	(other than a Systems Management Server Distribution Point) accessible by the
	user. However, when the option "Run with administrative rights" is selected in
	the Environment tab of a program, this forces the program to launch under the
	context of the local SMSCliToknAcct& account on a Windows NT Workstation or
	Windows 2000 Professional computer. The SMSCliToknAcct& has no access to
	network resources, and the attempt to execute the program fails. A connection is
	provided to valid distribution points by the Systems Management Server Client so
	it does not have to authenticate against the network.
	
	For additional information about usage of the Windows NT client software
	installation account, click the article number below to view the article in the
	Microsoft Knowledge Base:
	
	  Q235811 Using the SMS Windows NT Client Software Installation Account
	
	Additional query words: prodsms
	
	======================================================================
	Keywords          : kbClient kbConfig kbsms200 kbAdvertisement kbPackage kbSoftwareDist 
	Technology        : kbSMSSearch kbSMS200
	Version           : winnt:2.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
