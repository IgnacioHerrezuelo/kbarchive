---
layout: page
title: "Q136325: INFO: Three Types of Drag-and-Drop with Visual SourceSafe"
permalink: /kb/136/Q136325/
---

## Q136325: INFO: Three Types of Drag-and-Drop with Visual SourceSafe

{% raw %}

	Article: Q136325
	Product(s): Microsoft SourceSafe
	Version(s): 
	Operating System(s): 
	Keyword(s): kbSSafe400 kbSSafe500 kbSSafe600
	Last Modified: 01-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual SourceSafe for Windows, versions 4.0, 5.0, 6.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	In Visual SourceSafe, files and projects can be dragged from one location and
	dropped to another location. There are three operations that can be performed
	with drag-and-drop: share, share and branch, and move.
	
	- Share. The files and histories are under multiple projects, but there is
	  physically only one copy of the files and histories in the SourceSafe
	  database.
	
	- Share and branch. Copies of the files and histories are made. The branched
	  files maintain links to the original files.
	
	- Move. The project is moved to a new location.
	
	This article describes the mouse buttons, keystrokes, and shortcut menus that
	control which type of drag-and-drop is used.
	
	MORE INFORMATION
	================
	
	When working with projects, the right mouse button drag-and-drop displays a menu
	with the following options: share, share and branch, and move. The left mouse
	button drag-and-drop is a share drag-and-drop, where a new subproject is created
	under the target project, and the files from the source project are shared with
	the new subproject.
	
	
	In addition, when working with projects, pressing the ALT key or the SHIFT key
	along with the left mouse button results in a share and branch drag- and-drop.
	
	When working with files, the right mouse button drag-and-drop displays a menu
	with the following options: share, share and branch, and in version 6.0, move.
	The left mouse button drag-and-drop is a share drag-and-drop.
	
	In addition, when working with files, pressing the ALT key or the SHIFT key along
	with the left mouse button results in a share drag-and-drop.
	
	To summarize:
	
	  Share               left mouse button
	                      right mouse button + Share on the shortcut menu
	
	  Share and Branch    [SHIFT|ALT] left mouse button
	                      right mouse button + Branch on the shortcut menu
	
	  Move                right mouse button + Move on the shortcut menu (in
	                      versions prior to 6.0 this option is only available
	                      for projects.)
	
	NOTE: It is not possible to do file moves.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbSSafe400 kbSSafe500 kbSSafe600 
	Technology        : kbSSafeSearch kbAudDeveloper kbSSafe600 kbSSafe400 kbSSafe500
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
