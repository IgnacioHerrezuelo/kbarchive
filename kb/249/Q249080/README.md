---
layout: page
title: "Q249080: SMS: Problems Processing a Large Number of Tables with CMDCLEAN"
permalink: /kb/249/Q249080/
---

## Q249080: SMS: Problems Processing a Large Number of Tables with CMDCLEAN

{% raw %}

	Article: Q249080
	Product(s): Microsoft Systems Management Server
	Version(s): winnt:1.2
	Operating System(s): 
	Keyword(s): kbsms200 kbsms120 kbsms120bug
	Last Modified: 08-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server version 1.2 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you use CMDCLEAN to perform database maintenance for a Systems Management
	Server (SMS) 1.2 database, the process may stop before processing all the
	tables.
	
	CAUSE
	=====
	
	This problem can occur when a very large number of tables exist. The most
	current version of CMDCLEAN is unable to process an extremely large number of
	tables.
	
	RESOLUTION
	==========
	
	A supported fix is now available from Microsoft, but it is only intended to
	correct the problem described in this article and should be applied only to
	systems experiencing this specific problem. This fix may receive additional
	testing at a later time, to further ensure product quality. Therefore, if you
	are not severely affected by this problem, Microsoft recommends that you wait
	for the next that contains this fix.
	
	To resolve this problem immediately, contact Microsoft Product Support Services
	to obtain the fix. For a complete list of Microsoft Product Support Services
	phone numbers and information about support costs, please go to the following
	address on the World Wide Web:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	NOTE: In special cases, charges that are normally incurred for support calls may
	be canceled, if a Microsoft Support Professional determines that a specific
	update will resolve your problem. Normal support costs will apply to additional
	support questions and issues that do not qualify for the specific update in
	question.
	
	The English-language version of this software should have the following file
	attributes or later:
	
	  Date        Time      Size     File name       Platform   Version
	  -----------------------------------------------------------------------
	  04/04/2000  5:10pm    29,504   Cmdclean.exe    I386       1.2.0.0
	  04/04/2000  5:12pm    40,208   Cmdclean.exe    ALPHA      1.2.0.0
	
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft products that are
	listed at the beginning of this article.
	
	Additional query words: prodsms
	
	======================================================================
	Keywords          : kbsms200 kbsms120 kbsms120bug 
	Technology        : kbSMSSearch kbSMS120
	Version           : winnt:1.2
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
