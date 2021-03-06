---
layout: page
title: "Q243917: SNA Workstation 4.0 Access Violation When SnaBase Ends"
permalink: /kb/243/Q243917/
---

## Q243917: SNA Workstation 4.0 Access Violation When SnaBase Ends

{% raw %}

	Article: Q243917
	Product(s): Microsoft SNA Server
	Version(s): WINDOWS:4.0,4.0 SP1,4.0 SP2,4.0 SP3
	Operating System(s): 
	Keyword(s): _IK kbSNA400sp4fix kbSNA400PreSP4fix
	Last Modified: 08-DEC-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SNA Server, versions 4.0, 4.0 SP1, 4.0 SP2, 4.0 SP3 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When using SNA Workstation 4.0 or 4.0 Service Pack 1, the following problems may
	occur:
	
	- a 3270 emulator may stop responding while opening a new 3270 session
	
	- SnaBase.exe may fail with an access violation (C0000005) when being stopped,
	  with the following stack trace:
	
	  FramePtr  RetAddr   Param1   Param2   Param3   Function Name
	  13f6fca8  77f64ba2  00080000 000f2440 13f6fcd4 NTDLL!RtlpCoalesceFreeBlocks+0x2bc
	  13f6fcd8  0101dbf9  00080000 00000000 000f2448 NTDLL!RtlFreeHeap+0x7c
	  13f6fce8  0101b760  00000000 6723e4a8 00000001 SNABASE!CleanupCaching+0x19
	  13f6fcf0  6723e4a8  00000001 00000000 6727a5e0 SNABASE!NapTermCallback+0xa0
	  13f6fd10  67239925  00000000 00000000 00000000 SNADMOD!TermSnaDmod_int+0x68
	  6727a5e0  00000002  000000f4 000000f8 000000f0 SNADMOD!DMODServiceThread+0xa55
	
	CAUSE
	=====
	
	This problem is caused by a regression introduced into SNA Workstation 4.0
	Service Pack 1 due to an unrelated change made within SNA Server, which shares
	various components. The problem does not affect any version of SNA Server. It is
	specific to SNA Workstation only.
	
	RESOLUTION
	==========
	
	To resolve this problem, obtain the latest service pack for SNA Server 4.0. For
	additional information, please see the following article in the Microsoft
	Knowledge Base:
	
	  Q215838 How to Obtain the Latest SNA Server Version 4.0 Service Pack
	
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft SNA Workstation
	version 4.0 and version 4.0 Service Pack 1.
	
	This problem was first corrected in SNA Server 4.0 Service Pack 4.
	
	Additional query words:
	
	======================================================================
	Keywords          : _IK kbSNA400sp4fix kbSNA400PreSP4fix 
	Technology        : kbAudDeveloper kbSNAServSearch kbSNAServ400 kbSNAServ400SP1 kbSNAServ400SP2 kbSNAServ400SP3
	Version           : WINDOWS:4.0,4.0 SP1,4.0 SP2,4.0 SP3
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
