---
layout: page
title: "Q194820: XADM: Cannot Install 5.5 After Internet Explorer 4.01 SP1"
permalink: /kb/194/Q194820/
---

## Q194820: XADM: Cannot Install 5.5 After Internet Explorer 4.01 SP1

{% raw %}

	Article: Q194820
	Product(s): Microsoft Exchange
	Version(s): winnt:5.5
	Operating System(s): 
	Keyword(s): 
	Last Modified: 18-APR-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 5.5 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	When you attempt to install Microsoft Exchange Server 5.5 on an Exchange Server
	5.0 computer on which the Internet Mail Service is installed and Microsoft
	Internet Explorer 4.01 Service Pack 1 (SP1) with Outlook Express has been
	applied, the following error message may be displayed, and the installation
	process may not complete successfully:
	
	  Self registration of the DLL c:\winnt\system32\inetcomm.dll failed.
	
	CAUSE
	=====
	
	When you install Exchange Server 5.5 on an Exchange Server 5.0 computer on which
	the Internet Mail Service is installed, the Setup program attempts to register
	the Inetcomm.dll file. During this registration process, the Inetcomm.dll file
	attempts to load the Msoert.dll file.
	
	When you apply Internet Explorer 4.01 SP1 with Outlook Express, new versions of
	the Inetcomm.dll and Msoert.dll files are copied to your hard disk. When the
	Exchange Server 5.5 Setup program attempts to register the Inetcomm.dll file, it
	uses the new version of the Inetcomm.dll file on your hard disk. However, when
	the Inetcomm.dll file attempts to load the Msoert.dll file, it uses the older
	version of the Msoert.dll file on the Exchange Server 5.5 CD-ROM. This file
	mismatch prevents the Inetcomm.dll file from being registered.
	
	WORKAROUND
	==========
	
	To work around this problem, replace the Inetcomm.dll and Msoert.dll files that
	were copied to your hard disk when you applied Internet Explorer 4.01 SP1 with
	the versions of the files on the Exchange Server 5.5 CD-ROM. Then, install
	Exchange Server 5.5. After Exchange Server 5.5 has been installed, replace the
	Inetcomm.dll and Msoert.dll files from the Exchange Server 5.5 CD-ROM with the
	versions of the files that were copied to your hard disk when you applied
	Internet Explorer 4.01 SP1.
	
	To do so, follow these steps:
	
	1. Rename the Inetcomm.dll and Msoert.dll files in the Winnt\System32 folder on
	  your hard disk to Inetcomm.new and Msoert.new.
	
	2. Copy the Inetcomm.dll and Msoert.dll files from the Exchange Server 5.5
	  CD-ROM to the Winnt\System32 folder on your hard disk.
	
	3. Install Exchange Server 5.5.
	
	4. Rename the Inetcomm.dll and Msoert.dll files in the Winnt\System32 folder on
	  your hard disk to Inetcomm.old and Msoert.old.
	
	5. Rename the Inetcomm.new and Msoert.new files in the Winnt\System32 folder on
	  your hard disk to Inetcomm.dll and Msoert.dll.
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft Exchange Server
	version 5.5.
	
	Additional query words: ims internet mail connector upgrade imc
	
	======================================================================
	Keywords          :  
	Technology        : kbExchangeSearch kbExchange550 kbZNotKeyword2
	Version           : winnt:5.5
	Issue type        : kbbug
	Solution Type     : kbnofix
	
	=============================================================================
	

{% endraw %}
