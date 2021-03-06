---
layout: page
title: "Q168510: SMS: Event ID 330 Occurs When Attempting to Compress Package"
permalink: /kb/168/Q168510/
---

## Q168510: SMS: Event ID 330 Occurs When Attempting to Compress Package

{% raw %}

	Article: Q168510
	Product(s): Microsoft Systems Management Server
	Version(s): winnt:1.2
	Operating System(s): 
	Keyword(s): kbnetwork kbConfig kbScheduler smsconfig smsscheduler
	Last Modified: 30-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server version 1.2 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Package compression fails with event ID 330 error, even though it appears that
	the Systems Management Server service account has all the appropriate rights to
	the source directory.
	
	  Non-fatal Error in module: SMS_SCHEDULER
	
	  Operation: Compress
	  Object: Package
	  Object name: A0100100
	  Error code: 1002
	
	  An error occurred while trying to compress the contents of the source
	  directory specified for the server version of the package.
	
	The following is the corresponding excerpt from the Sched.log file:
	
	     Creating package file
	     '\\SERVER\SMS_SHRI\site.srv\sender.box\tosend\A0100100.S00'.~
	     $$<SMS_SCHEDULER><Mon Apr 21 09:02:14 1997~><thread=168>
	     ~Package source \\SERVER\SHARE\APP doesn't exist or we failed
	     to access it, Win32 Error = 5   $$<SMS_SCHEDULER><Mon Apr 21 09:02:14
	     1997~><thread=168>
	     ~Cannot compress the package file, return code = 4865
	     $$<SMS_SCHEDULER><Mon Apr 21 09:02:14 1997~><thread=168>
	     Creation of compressed package file failed!~   $$<SMS_SCHEDULER><Mon Apr
	     21 09:02:14 1997~><thread=168>
	
	CAUSE
	=====
	
	It is possible that the password for the Scheduler service's entry for the
	Systems Management Server service account is not the same as the current
	password in the Windows NT Server Security Account Manager (SAM) database. This
	may happen if the Systems Management Server service account is improperly
	changed by clicking Account on the Site Properties menu, as this functionality
	does not check the account against the SAM database.
	
	Changing the service account through the Site Operations: Service Account option
	in Systems Management Server Setup does provide the functionality of checking
	the account and password.
	
	WORKAROUND
	==========
	
	To work around this problem, set the Systems Management Server service account
	name and password through the Site Operations: Service Account option of Systems
	Management Server Setup. This option shuts down the services to change the
	service account.
	
	
	Additional query words: prodsms sms
	
	======================================================================
	Keywords          : kbnetwork kbConfig kbScheduler smsconfig smsscheduler 
	Technology        : kbSMSSearch kbSMS120
	Version           : winnt:1.2
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
