---
layout: page
title: "Q235994: How Windows NT Saves Window Size and Location Parameters"
permalink: /kb/235/Q235994/
---

## Q235994: How Windows NT Saves Window Size and Location Parameters

{% raw %}

	Article: Q235994
	Product(s): Microsoft Windows NT
	Version(s): winnt:4.0
	Operating System(s): 
	Keyword(s): kbenv
	Last Modified: 11-JUN-2002
	
	IMPORTANT: This article contains information about modifying the registry. Before you modify the registry, make sure to back it up and make sure that you understand how to restore the registry if a problem occurs. For information about how to back up, restore, and edit the registry, click the following article number to view the article in the Microsoft Knowledge Base:
	
	  Q256986 Description of the Microsoft Windows Registry
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation version 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article describes how Windows NT saves the size and location of a window
	when it is closed.
	
	MORE INFORMATION
	================
	
	WARNING: If you use Registry Editor incorrectly, you may cause serious problems
	that may require you to reinstall your operating system. Microsoft cannot
	guarantee that you can solve problems that result from using Registry Editor
	incorrectly. Use Registry Editor at your own risk.
	
	Windows saves size and location information for closed windows in the following
	registry location:
	
	  HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer\Streams
	
	Windows saves size and location information for up to 28 different windows. Each
	window's size and location parameters are stored in a subkey of the Streams key.
	The subkeys are assigned sequentially on a per-user basis. For example, when a
	new user logs on, the first window's parameters are stored in the subkey named
	0. The second window's parameters are stored in a subkey named 1. After 28
	subkeys have been created and a new window is opened, the parameters for the
	twenty-ninth window overwrite the parameters for one of the first 28 windows.
	When a window for which the parameters were overwritten is opened, the window
	opens with the default parameters for that window.
	
	Windows stores the association for the Streams subkeys with a particular window
	in the following location:
	
	  HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer\StreamMRU.
	
	For example, if the Streams key has eight subkeys (0-7), the printers folder is
	assigned the Streams subkey named 6, you delete all of the Streams subkeys, and
	you then open the Printers folder, the printer is assigned the subkey named 6
	again. This occurs because Windows has an entry in StreamMRU that associates the
	6 subkey with the Printers folder. However, if you had deleted all of the
	Streams subkeys and the values in the StreamMRU key, the Printers folder would
	have been assigned the next sequential Streams subkey, which would be 0.
	
	Troubleshooting
	---------------
	
	This may be useful if StreamMRU settings become "cross linked." In some cases,
	multiple programs may write window size and location information to the same
	Streams subkey. In this case, the stored size and location for program B's
	window might actually be the size and location for program A's window. Deleting
	the StreamMRU data and Streams subkeys should resolve this situation. Also,
	creating a new user account resolves this issue because the Streams and
	StreamMRU subkeys are created when a new user opens a window.
	
	NOTE: Do not delete the MRUList value from the StreamMRU key.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbenv 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search
	Version           : winnt:4.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
