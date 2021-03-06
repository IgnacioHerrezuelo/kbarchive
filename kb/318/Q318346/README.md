---
layout: page
title: "Q318346: BUG: No Merge Warning After User Changes the Binding Information"
permalink: /kb/318/Q318346/
---

## Q318346: BUG: No Merge Warning After User Changes the Binding Information

{% raw %}

	Article: Q318346
	Product(s): Microsoft SourceSafe
	Version(s): 
	Operating System(s): 
	Keyword(s): 
	Last Modified: 09-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual SourceSafe 6.0c, used with:
	   - Microsoft Visual Studio.NET (2002), Professional Edition 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	A user may lose data and may not receive a warning message if the user changes
	the binding information for an item under source control.
	
	CAUSE
	=====
	
	This problem occurs because some items in the new binding have different
	contents on the local disk than in the newly bound database.
	
	RESOLUTION
	==========
	
	Contact your administrator. The Get Latest Version command may be able to
	resolve this problem, but the user may continue to lose changes.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce the Behavior
	-------------------------------
	
	1. User 1 creates a solution, adds a file to the solution, and then adds the
	  solution to source control.
	
	2. In Visual SourceSafe Explorer, share and branch the whole solution to another
	  location.
	
	3. User 1 checks out the solution, makes a change, and then checks in the
	  solution.
	
	4. User 2 creates a project in Visual SourceSafe.
	
	5. On the File menu, point to Source Control, and then click Change Source
	  Control. Change the binding root to the new branched location.
	
	6. User 2 makes conflicting edits to the solution and then checks in the
	  solution.
	
	7. User 1 unbinds the solution from the original location and then rebinds it to
	  the new location through the Change Source Control dialog box.
	
	8. In Solution Explorer of the Microsoft Visual Studio .NET integrated
	  development environment (IDE), right-click the solution, and then click Get
	  Latest Version.
	
	  NOTE: If Solution Explorer is not visible, click Solution Explorer on the View
	  menu.
	
	REFERENCES
	==========
	
	For additional information about this problem, click the article numbers below
	to view the articles in the Microsoft Knowledge Base:
	
	  Q305106 HOWTO: SSAFE - Reconnect a Project to Source Control in Visual Studio
	  .NET
	
	  Q318109 PRB: Changes Are Not Saved When You Bind Solution to Another Source
	  Control Project
	
	Additional query words:
	
	======================================================================
	Keywords          :  
	Technology        : kbSSafeSearch kbAudDeveloper kbSSafe600C
	Version           : :
	Issue type        : kbbug
	Solution Type     : kbnofix
	
	=============================================================================
	

{% endraw %}
