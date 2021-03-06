---
layout: page
title: "Q135401: INF: How to Upgrade ODBC SDK version 2.10a to 2.10b"
permalink: /kb/135/Q135401/
---

## Q135401: INF: How to Upgrade ODBC SDK version 2.10a to 2.10b

{% raw %}

	Article: Q135401
	Product(s): Open Database Connectivity (ODBC)
	Version(s): WINDOWS:2.10b
	Operating System(s): 
	Keyword(s): 
	Last Modified: 25-AUG-1999
	
	2.10b
	WINDOWS
	kbsetup
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Open Database Connectivity, version 2.10b 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article describes where to get the Microsoft Open Database Connectivity
	(ODBC) version 2.10b Software Development Kit (SDK) files, and how to upgrade
	from version 2.10a.
	
	MORE INFORMATION
	================
	
	A self-expanding PKzip file called ODBC210B.EXE is available via the Internet at
	the site listed below to enable you to upgrade the ODBC SDK version 2.10a to
	ODBC SDK version 2.10b.
	
	  ftp://ftp.microsoft.com/developr/ODBC/public/ODBC210B.EXE
	
	
	The zipfile expands to the following files:
	
	  ODBC16UT DL_         3,221 08-17-94  12:00a
	  ODBC32   DL_         3,888 08-17-94  12:00a
	  ODBC16   IN_         4,036 06-02-95   2:30p
	  ODBC32   IN_         2,960 06-02-95   2:02p
	  ODBCSDK  IN_         6,031 06-02-95   2:57p
	  EXPAND   EXE        16,129 09-30-93   5:20a
	  README   TXT           203 07-25-95   9:07a
	
	When expanded to their appropriate sizes, ODBC32.DLL (ODBC Thunking Driver
	Manager) and ODBC16UT.DLL are the complete set of files required to upgrade the
	components from the ODBC 2.10a SDK to version 2.10b. The file EXPAND.EXE has
	been included with this zipfile for your convenience.
	
	Use the following commands to expand the two required components:
	
	  expand odbc16ut.dl_ odbc16ut.dll
	  expand odbc32.dl_ odbc32.dll
	
	If the ODBC SDK version 2.10a is already installed on your computer, you can
	upgrade to version 2.10b by using the following commands:
	
	  copy odbc16ut.dll c:\windows\system
	  copy odbc32.dll c:\windows\system
	
	If you have not installed 2.10a on your computer yet and have the Microsoft
	Developer Network (MSDN) Level 2, July 1995 CD and would like to install the
	entire ODBC 2.10b SDK at once, you should copy the ODBC 2.10a SDK from the MSDN
	CD, then copy the required 2.10b components and the updated INF files included
	with this zipfile into the directory on your harddrive where you would like to
	install the ODBC 2.10b SDK.
	
	This is a good option if you expect to install ODBC 2.10b onto several computers
	on your network. The ODBC 2.10a SDK is located in the ODBC\X86 directory of the
	CD marked "U.S.: Windows NT Service Packs, Windows Versions, and SDKs." It is
	also marked "CD 2 of 19 of the MSDN Development Platform CDs."
	
	Use the following commands to create a setup directory for the installation of
	the ODBC 2.10b SDK (in this example, your CD drive is drive D: and the install
	directory that you wish to create is C:\ODBC210B\INSTALL, under which you have
	previously copied the ODBC 2.10a SDK):
	
	1. cd <to the directory where the zipfile is expanded>
	
	2. expand odbc16.in_ odbc16.inf
	
	3. expand odbc32.in_ odbc32.inf
	
	4. expand odbcsdk.in_ odbcsdk.inf
	
	5. copy *.inf c:\odbc210b\install
	
	6. copy d:\odbc\x86\*.* c:\odbc210b\install
	
	At this point, you are prepared to install ODBC SDK 2.10b from
	C:\ODBC210B\INSTALL by running SETUP.EXE.
	
	Additional query words: odbcsdk
	
	======================================================================
	Keywords          :  
	Technology        : kbAudDeveloper kbODBCSearch
	Version           : WINDOWS:2.10b
	
	=============================================================================
	

{% endraw %}
