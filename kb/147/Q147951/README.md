---
layout: page
title: "Q147951: Supported Platforms for SNA Server Clients"
permalink: /kb/147/Q147951/
---

## Q147951: Supported Platforms for SNA Server Clients

{% raw %}

	Article: Q147951
	Product(s): Microsoft SNA Server
	Version(s): WINDOWS:2.0,2.1,2.11,2.11 SP1,3.0
	Operating System(s): 
	Keyword(s): kbnetwork
	Last Modified: 13-JUN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SNA Server, versions 2.0, 2.1, 2.11, 2.11 SP1, 3.0, on platform(s):
	   - the operating system: Microsoft Windows NT 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article includes a table that represents all possible SNA Server
	combinations of client types and platforms. If there is a choice of a client
	type to use, it is recommended that you use the SNA Server client for the
	platform. For example, in Windows NT, use the SNA Server client for Windows NT.
	
	               SNA Server Client types
	
	Platform    MS-DOS  OS/2  Windows 3.x  Windows NT   Windows 95
	--------------------------------------------------------------
	MS-DOS        X      N         N           N           N
	OS/2          M      X         N           N           N
	Windows 3.x   X1     N         X           N           N
	Windows NT    X2     N         X3          X           X
	Windows 95    M      N         X4          N           X
	
	Clients for UNIX and Macintosh are provided by third party software developers,
	and are supported in the platforms designated by the client's vendor.
	
	The following lists and describes the different marks used in the table above:
	
	 Marks   Description
	 -----   -----------
	
	  X<#>   Represents the client type that is compatible with the associated
	         platform. <#> is mentioned below.
	  N      Not applicable or not supported.
	  M<#>   May work, but has not been tested. <#> is mentioned below.
	
	  <#>    Description
	  ---    -----------
	   1     MS-DOS SNA Server Client on Windows 3.x platform (for use with
	         IBM PC Support). For additional information, please see the
	         following article in the Microsoft Knowledge Base:
	
	            ARTICLE-ID: Q107193
	            TITLE     : Running IBM PC Support/400 on SNA Server
	
	   2     MS-DOS SNA Server Client on Windows NT platform (for use with IBM
	         PC Support). For additional information, please see the following
	         article in the Microsoft Knowledge Base:
	
	            ARTICLE-ID: Q103684
	            TITLE     : IBM PC Support/400 and Windows NT
	
	   3     Windows 3.x SNA Server Client on Windows NT platform. The Windows
	         3.x SNA Server client must be used on a Windows NT computer
	         (where a 16-bit 3270/FMI application runs). The Windows NT SNA
	         Server client provides a thunking layer for all other SNA Server
	         API's. There are special instructions for the installation of the
	         Windows SNA Server 3.x client in Windows NT (where the actual SNA
	         Server is running on the system:
	
	          - Start the Windows SNA Server 3.x client setup on the SNA
	            Server.
	          - In the "Client/Server Protocols" dialog box, select the
	            TCP/IP. NOTE: If you have SNA Server 2.11 SP1, select Novell
	            Netware.
	          - In the "SNA Server Location" dialog box, select the Remote.
	            Enter the IP address or computer name of the SNA Server that
	            the Windows 3.x client is being installed. In other words, the
	            remote destination is pointing to itself. If you select Novell
	            Netware, then enter the SNA Server domain name and add the
	            following entries to the [wnap] section in WIN.INI:
	
	               [wnap]
	               Remote=<domainname>
	               NosType=NETWARE
	
	            In this configuration, both 32-bit and 16-bit 3270/FMI
	            applications can work on the same computer).
	
	   4        Windows 3.x SNA Server Client on Windows 95 platform. The
	            Windows 3.x SNA Server client must be used in Windows 95 if
	            you want to run any 16-bit SNA Server aware application. No
	            thunking is provided for any SNA Server API on the Windows 95
	            SNA Server client. To use the Windows 95 SNA Server client, a
	            32-bit application must be used.
	
	Additional query words: prodsna sp1 unix mac macintosh parker
	
	======================================================================
	Keywords          : kbnetwork 
	Technology        : kbAudDeveloper kbSNAServSearch
	Version           : WINDOWS:2.0,2.1,2.11,2.11 SP1,3.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
