---
layout: page
title: "Q128245: CPIC/APPC Program May Hang Opening a Dependent APPC Session"
permalink: /kb/128/Q128245/
---

## Q128245: CPIC/APPC Program May Hang Opening a Dependent APPC Session

{% raw %}

	Article: Q128245
	Product(s): Microsoft SNA Server
	Version(s): WINDOWS:2.0,2.1,2.11
	Operating System(s): 
	Keyword(s): 
	Last Modified: 13-JUN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SNA Server, versions 2.0, 2.1, 2.11, on platform(s):
	   - the operating system: Microsoft Windows NT 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	Under SNA Server 2.0 or 2.1, when a CPIC or APPC application allocates a
	dependent LU6.2 session where the dependent APPC LU is defined in SNA Server
	Admin to be a "Member of Default Outgoing Local APPC LU Pool", the allocate
	request may hang. Within an APPC application, the call to [MC_]ALLOCATE may not
	return. Within a CPIC application, the call to CMINIT may not return (since CPIC
	runs over APPC, the underlying APPC [MC_]ALLOCATE hangs).
	
	CAUSE
	=====
	
	SNA Server 2.0 and 2.1 do not correctly implement pooling of dependent APPC
	LU's, however, the SNA Server Admin program does not prevent it. The problem
	doesn't occur if independent APPC LU's are configured to be a member of the
	default outgoing APPC LU pool.
	
	With dependent APPC LU's, SNA Server may have allocated the dependent APPC LU/LU
	session to another APPC or CPIC application. If a second APPC or CPIC
	application attempts to open the same dependent APPC LU (which can occur if a
	dependent APPC LU is configured to be a member of the default APPC LU pool), the
	second application's [MC_]ALLOCATE call will hang until the session becomes
	available.
	
	
	RESOLUTION
	==========
	
	To solve the problem on SNA Server 2.0 or 2.1, each CPIC or APPC application
	must use a unique dependent Local APPC LU.
	
	For an APPC application, the application must be predefined to use a specific
	dependent Local APPC LU alias. If the Local LU alias is left blank, the default
	Local APPC LU can be associated to a user or group within the "Users and Groups"
	window of SNA Server Admin.
	
	For a CPIC application, the Local APPC LU alias must be preset within SNA Server
	by either:
	
	- Defaulting the user/group to use a specific Local APPC LU alias:
	
	  Within the "Users and Groups" window of SNA Admin, the user or group record
	  can be configured with a default Local and Remote APPC LU aliases.
	
	-or-
	
	- Defaulting the workstation to use a specific Local APPC LU alias:
	
	  The SNA Server client software can be defined with a default Local APPC LU
	  alias, as described in the CPI-C API section of Appendix C in the SNA Server
	  Reference Guide:
	
	  Windows NT clients (within the Registry):
	
	           HKEY_LOCAL_MACHINE
	            \SYSTEM
	              \CurrentControlSet
	                \Services
	                  \SnaBase
	                    \Parameters
	                      \Client
	
	           application: REG_SZ: localLUalias
	
	  Win 3.x clients (within WIN.INI) or OS/2 clients (within SNA.INI):
	
	           [ApplicationName]
	           APPCLLU=localLUalias
	
	  where application is the name of the CPIC application (without the .EXE
	  extension).
	
	STATUS
	======
	
	This problem is fixed in SNA Server 2.11. The fix involves changes to the server
	and the client software, so both ends must be updated to SNA Server 2.11.
	
	Additional query words: prodsna 2.00 2.10 2.11 3.50 allocate
	
	======================================================================
	Keywords          :  
	Technology        : kbAudDeveloper kbSNAServSearch
	Version           : WINDOWS:2.0,2.1,2.11
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
