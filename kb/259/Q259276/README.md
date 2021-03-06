---
layout: page
title: "Q259276: PC Win: Personal Name Field in nNw PAB Entry Cannot Be Modified"
permalink: /kb/259/Q259276/
---

## Q259276: PC Win: Personal Name Field in nNw PAB Entry Cannot Be Modified

{% raw %}

	Article: Q259276
	Product(s): Microsoft Mail For PC Networks
	Version(s): 3.5
	Operating System(s): 
	Keyword(s): 
	Last Modified: 02-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Mail for PC Networks, version 3.5 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	After you copy an address from the global address list (GAL) to the personal
	address book (PAB) with the Microsoft Mail for Windows client, the Personal Name
	field for the PAB entry cannot be modified.
	
	When you attempt to obtain mailbox details using the Microsoft Mail client for
	MS-DOS (Mail.exe) from the GAL, you may receive the following error message:
	
	  Notice 3
	  Template file corrupted.
	  Contact Administrator.
	  Press Enter to continue
	
	Also, if you try to get mailbox details with the MS Mail Administrator program
	(Admin.exe), you may receive the following error message:
	
	  Notice 90
	  Template file is corrupted.
	  Contact administrator.
	  Press Enter to continue
	
	CAUSE
	=====
	
	The template file is corrupted.
	
	RESOLUTION
	==========
	
	To resolve this issue, use one of the following methods.
	
	Method 1
	--------
	
	Restore the Admin.inf file from backup prior to when the issue started
	occurring.
	
	Method 2
	--------
	
	Re-create the template data manually. To do this, follow these steps:
	
	1. At a command prompt, change to the Inf subfolder of the Mail database.
	
	2. Rename the existing Admin.inf file.
	
	3. Using the MS Mail Administrator program, re-enter the template information by
	  modifying each of the local addresses. To modify the users' mailboxes, select
	  Local-Admin, and then click Modify.
	
	Method 3
	--------
	
	Use the Template utility to create a new Admin.inf file. the Template utility
	(Template.exe) that is located in the Mailexe folder. To do this, follow these
	steps:
	
	1. At a command prompt, change to the Inf subfolder of the Mail database.
	
	2. Type the following command:
	
	  type nul > admin.txt
	
	  This command creates a zero-byte file, Admin.txt, in the Inf subfolder.
	
	3. Go to the root of the MS Mail database.
	
	4. Change to the drive and subfolder that contain the MS Mail executable files.
	  This is usually the Mailexe subfolder.
	
	5. Type the following (this example assumes that the Maildata subfolder is in
	  the root of drive M):
	
	  template m:\tpl\admin.tpl m:\inf\admin.inf m:\inf\admin.txt -dm
	
	  NOTE: This step creates an Admin.txt file. note that you should check the
	  Admin.txt file for signs of corrupt data. Corrupted data may be indicated by
	  control characters or other illegible characters in the template records. If
	  corrupted records exist in the Admin.txt file, you should remove those
	  records from the file before proceeding with the remaining steps of this
	  procedure.
	  All the records contained in the Admin.txt file should be legible in text
	  format. For example:
	
	  admin
	  Administrator
	  Name:~
	  Phone #:~
	  Fax #:~
	  Address:~
	  Department:~
	  Manager:~
	  ~~
	
	  The end of the record marker is a pair of tildes (~~) in a separate line. Also
	  note that the tilde at the end of the line is a data field placeholder. This
	  tilde can also be replaced with the actual data that is entered for the user
	  data.
	
	6. Change to the Inf subfolder.
	
	7. At the command prompt, rename the Admin.inf file to Admin.old. Type the
	  following command:
	
	  ren admin.inf *.old
	
	8. Go to the root of the MS Mail database.
	
	9. Change to the drive and subfolder that contain the MS Mail executable files.
	  This is usually the Mailexe subfolder.
	
	10. Type the following (this example assumes that the Maildata subfolder is in
	  the root of drive M):
	
	  template m:\tpl\admin.tpl m:\inf\admin.txt m:\inf\admin.inf -dm
	
	These steps create a new Admin.inf file that matches the current Admin.tpl file.
	
	MORE INFORMATION
	================
	
	For more information about MS Mail templates, see Chapter 8 of the Microsoft
	Mail Administrator's Guide.
	
	Additional query words: winmail windows and pm 16 bit
	
	======================================================================
	Keywords          :  
	Technology        : kbMailSearch kbZNotKeyword3 kbMailPCN350
	Version           : :3.5
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
