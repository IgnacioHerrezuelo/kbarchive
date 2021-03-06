---
layout: page
title: "Q186629: INFO: Terminal Server Unattended Installation"
permalink: /kb/186/Q186629/
---

## Q186629: INFO: Terminal Server Unattended Installation

{% raw %}

	Article: Q186629
	Product(s): Microsoft Windows NT
	Version(s): winnt:4.0
	Operating System(s): 
	Keyword(s): kbOPK kbSBK
	Last Modified: 11-DEC-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0, Terminal Server Edition 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The unattended installation process with Terminal Server is the same as the
	process for Windows NT Server with three exceptions. The answer file has a new
	option for the number of client licenses and whether to install Internet
	Explorer 4.0, and Sysdiff needs to be run in Terminal Server's Installation
	Mode.
	
	MORE INFORMATION
	================
	
	Answer file
	-----------
	
	Here is a sample answer file for unattended setup. Note that this file would need
	to be modified for your environment (for example, computer name, paths, license
	numbers).
	
	     [Unattended]
	     OemPreinstall = yes
	     NoWaitAfterTextMode = 1
	     NoWaitAfterGUIMode = 1
	     FileSystem = LeaveAlone
	     ExtendOEMPartition = 0
	     ConfirmHardware = no
	     NtUpgrade = no
	     Win31Upgrade = no
	     TargetPath = WTSUAS
	     OverwriteOemFilesOnUpgrade = no
	
	     [UserData]
	     FullName = "BVT Bench"
	     OrgName = "MS"
	     ComputerName = BRADG-UNATTEND
	
	     [GuiUnattended]
	     OemSkipWelcome = 1
	     OEMBlankAdminPassword = 1
	     TimeZone = "(GMT-08:00) Pacific Time (US & Canada); Tijuana"
	     AdvServerType = SERVERNT
	
	     [LicenseFilePrintData]
	     AutoMode = PerServer
	     AutoUsers = 9999
	
	     [TerminalServerDesktops]
	     Quantity = 5
	
	     [InternetExplorer]
	     InstallIE4 = yes
	
	     [Display]
	     ConfigureAtLogon = 0
	     BitsPerPel = 8
	     XResolution = 640
	     YResolution = 480
	     VRefresh = 60
	     AutoConfirm = 1
	
	     [Network]
	     DetectAdapters = ""
	     InstallProtocols = ProtocolsSection
	     InstallServices = ServicesSection
	     InstallInternetServer = InternetParamSection
	     JoinDomain = ntwksta
	     CreateComputerAccount = ntwksta, ntwksta
	
	     [ProtocolsSection]
	     NBF = NBFParamSection
	     TC = TCParamSection
	     NWLNKIPX = NWLNKIPXParamSection
	
	     [NBFParamSection]
	
	     [TCParamSection]
	     DHCP=yes
	
	     [NWLNKIPXParamSection]
	
	     [ServicesSection]
	
	     [InternetParamSection]
	     InstallDir = C:\Inetsrv
	     InstallINETSTP = 1
	     InstallWWW = 1
	     WWWRoot = C:\Inetsrv\WWWRoot
	     InstallGOPHER = 1
	     GopherRoot = C:\Inetsrv\GopherRoot
	     InstallFTP = 1
	     FTPRoot = C:\Inetsrv\FTPRoot
	     InstallADMIN = 1
	     InstallW3SAMP = 1
	     InstallHTMLA = 1
	
	Applications and Sysdiff
	------------------------
	
	If you are preloading software and plan to use Sysdiff, the only difference
	between usage in Windows NT and Terminal Server is that, with Terminal Server,
	you should install applications and run Sysdiff in Installation Mode.
	
	To enter Installation Mode, do one of the following:
	
	- Type the following command at an MS-DOS command prompt:
	
	  "Change User /Install" (without the quotation marks)
	
	- Install applications through the Control Panels Add/Remove Programs tool.
	
	Applications should be tested for full client functionality before using the
	Terminal Server as a template for other servers. You can run applicable
	application compatibility scripts, register .dll files, modify application
	compatibility flags, and so on before using the server as a template.
	
	Additional query words: Unattended Setup
	
	======================================================================
	Keywords          : kbOPK kbSBK 
	Technology        : kbWinNTsearch kbWinNT400search kbWinNTSsearch kbWinNTS400search kbNTTermServ400 kbNTTermServSearch
	Version           : winnt:4.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
