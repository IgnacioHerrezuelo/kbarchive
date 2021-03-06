---
layout: page
title: "Q182529: Controlling Message Size Traced in SNA Server Message Traces"
permalink: /kb/182/Q182529/
---

## Q182529: Controlling Message Size Traced in SNA Server Message Traces

{% raw %}

	Article: Q182529
	Product(s): Microsoft SNA Server
	Version(s): WINDOWS:3.0,3.0 SP1,3.0 SP2,3.0 SP3,4.0,4.0 SP1
	Operating System(s): 
	Keyword(s): 
	Last Modified: 15-MAR-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SNA Server, versions 3.0, 3.0 SP1, 3.0 SP2, 3.0 SP3, 4.0, 4.0 SP1 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about editing the registry.
	Before you edit the registry, make sure you understand how to restore it if
	a problem occurs. For information about how to do this, view the "Restoring
	Registry Key" Help topic in Regedit.exe or the "Restoring a Registry Key"
	Help topic in Regedt32.exe.
	
	SUMMARY
	=======
	
	Microsoft SNA Server supports dynamic message tracing of various interfaces,
	including client-server messages and server-host messages, using the snatrace
	tool. By default, the entire message size is traced to SNA Server trace files
	(stored in <snaroot>\traces\ with an *.ATF extension, where trace files
	can be viewed using the SNA Server "tracevwr" tool). However, in some cases, it
	may be desirable to only trace a limited portion of each message, to reduce the
	growth and size of the message trace files. SNA Server supports this feature by
	configuring the "MaxRecordLength" registry entry as described below.
	
	MORE INFORMATION
	================
	
	It is possible to specify the maximum traced message size for SNA Server
	messages, SNA Server link service messages, and SNA Server Application messages.
	The message types for which you can specify maximum traced message size are:
	
	- Data Link Control messages (between SNA Server and link service)
	
	- SNA Server Format messages (between SNA Server and host)
	
	- LU6.2 messages (between SNA Server client and SNA Server)
	
	- 3270 messages (between SNA Server client and SNA Server)
	
	Configuring the MaxRecordLength limits the size of the "element data" traced
	within each message. For Data Link Control (DLC) messages, the "element data"
	contains the RH, RU command, and application data. If MaxRecordLength is set to
	"3," the RH bytes will be traced, but the RU command byte and application data
	will not be traced. However, the decoded TH, RH, and RU commands, if present,
	will still be indicated in the header portion of each traced message. The
	MaxRecordLength parameter does not affect tracing of any other trace fields
	(such as Windows NT process ID, thread ID, date and time stamp, and so on).
	
	WARNING: Using Registry Editor incorrectly can cause serious problems that may
	require you to reinstall your operating system. Microsoft cannot guarantee that
	problems resulting from the incorrect use of Registry Editor can be solved. Use
	Registry Editor at your own risk.
	
	For information about how to edit the registry, view the "Changing Keys And
	Values" Help topic in Registry Editor (Regedit.exe) or the "Add and Delete
	Information in the Registry" and "Edit Registry Data" Help topic in
	Regedt32.exe. Note that you should back up the registry before you edit it.
	
	When SNA Server message tracing is enabled, you can specify the maximum traced
	message size by setting the following registry parameter:
	
	  HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\SnaServr
	  \Parameters\MaxRecordLength: REG_SZ:  <message size in bytes>
	
	NOTE: The above registry key is one path; it has been wrapped for readability.
	
	This value already exists but is a REG_DWORD type. It must be deleted and
	re-entered as a REG_SZ. Also, the SNA Server service must be stopped and started
	for the message size to take effect. This value defaults to 0xFFFF, indicating
	that you need to trace the entire message.
	
	To enable this setting for SNA Server link services (for example, for DLC
	messages), configure the following registry value:
	
	  HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\<linkservicename>
	  \Parameters\MaxRecordLength: REG_SZ: <message size in bytes>
	
	NOTE: The above registry key is one path; it has been wrapped for readability.
	
	This value already exists but is a REG_DWORD type. It must be deleted and
	re-entered as a REG_SZ. Also, the SNA Server link service must be stopped and
	started for the message size to take effect. This value defaults to 0xFFFF,
	indicating that the entire message should be traced.
	
	
	Additional query words:
	
	======================================================================
	Keywords          :  
	Technology        : kbAudDeveloper kbSNAServSearch kbSNAServ300 kbSNAServ400 kbSNAServ300SP3 kbSNAServ300SP1 kbSNAServ400SP1 kbSNAServ300SP2
	Version           : WINDOWS:3.0,3.0 SP1,3.0 SP2,3.0 SP3,4.0,4.0 SP1
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
