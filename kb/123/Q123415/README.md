---
layout: page
title: "Q123415: Disk Space Value May Be Incorrect After Exiting INTERSVR"
permalink: /kb/123/Q123415/
---

## Q123415: Disk Space Value May Be Incorrect After Exiting INTERSVR

{% raw %}

	Article: Q123415
	Product(s): Microsoft Disk Operating System
	Version(s): MS-DOS:5.0a,6.0,6.2,6.21,6.22
	Operating System(s): 
	Keyword(s): 
	Last Modified: 23-NOV-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft MS-DOS operating system versions 5.0a, 6.0, 6.2, 6.21, 6.22 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	After exiting the INTERSVR program, the disk space reported may be incorrect if
	another computer using INTERLNK added or deleted files from the disk drive of
	the server machine.
	
	CAUSE
	=====
	
	MS-DOS avoids recalculating the free disk space by subtracting allocations and
	adding deallocations from a value calculated and stored when the disk is first
	accessed. The copy of MS-DOS running on the server machine is not able to detect
	when individual allocations and deallocations are made by the INTERLNK client
	machine; therefore, the value remains as it was when the INTERSVR program was
	started.
	
	STATUS
	======
	
	This is expected behavior when the INTERSVR program is used. The correct amount
	of space available on the disk is not affected by this number, and the correct
	value is reported after the system is rebooted.
	
	Additional query words: 5.00a 6.00 6.20 6.21 6.22
	
	======================================================================
	Keywords          :  
	Technology        : kbMSDOSSearch kbMSDOS621 kbMSDOS622 kbMSDOS620 kbMSDOS600 kbMSDOS500a
	Version           : MS-DOS:5.0a,6.0,6.2,6.21,6.22
	
	=============================================================================
	

{% endraw %}
