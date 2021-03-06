---
layout: page
title: "Q214906: SMSINST: Colons Invalid in Path in Default Directory Text Box"
permalink: /kb/214/Q214906/
---

## Q214906: SMSINST: Colons Invalid in Path in Default Directory Text Box

{% raw %}

	Article: Q214906
	Product(s): Microsoft Systems Management Server
	Version(s): WINDOWS:1.0,2.0; winnt:2.0
	Operating System(s): 
	Keyword(s): kbsms200 kbsms120 kbsmsInst
	Last Modified: 09-APR-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server Installer versions 1.0, 2.0 
	- Microsoft Systems Management Server version 2.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When trying to specify a drive letter on the Application tab within the
	Installation Interface properties, entering a colon in the Default Directory
	text box will result in the following error message:
	
	  The default directory field should only contain the name of the directory
	  itself, not the full pathname including the drive letter. Please enter only
	  the directory name itself into this field.
	
	This error prevents you from specifying a drive in the directory path.
	
	CAUSE
	=====
	
	This is by design.
	
	WORKAROUND
	==========
	
	To work around this problem, manually alter the corresponding script item using
	the Script Editor view. In the following example "Test" is used as the Default
	Directory entered on the Application tab within Installation Interface
	properties. To use a specific drive as the default, perform the following
	steps:
	
	1. Go to the Script Editor view.
	
	2. Under If System Has Windows 95 Shell Interface Start Block, find and open the
	  script item Set Variable MAINDIR to %PROGRAM_FILES%\%MAINDIR%.
	
	3. Change the value %PROGRAM_FILES% to X:\program files, in the New Value text
	  box (where X:\ is the preferred default drive letter).
	
	4. Find the script item Set Variable MAINDIR to %SYSDRIVE%:\%MAINDIR% and change
	  the value %SYSDRIVE% to X (where X is the preferred default drive letter).
	
	MORE INFORMATION
	================
	
	
	Additional query words: prodsms smsinst
	
	======================================================================
	Keywords          : kbsms200 kbsms120 kbsmsInst 
	Technology        : kbSMSSearch kbSMS200 kbSMSI100 kbSMSI200
	Version           : WINDOWS:1.0,2.0; winnt:2.0
	Issue type        : kbprb
	Solution Type     : kbnofix
	
	=============================================================================
	

{% endraw %}
