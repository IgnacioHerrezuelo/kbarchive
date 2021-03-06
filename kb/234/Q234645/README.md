---
layout: page
title: "Q234645: ODE97: Error Configuring SQL Server Driver During Install of App"
permalink: /kb/234/Q234645/
---

## Q234645: ODE97: Error Configuring SQL Server Driver During Install of App

{% raw %}

	Article: Q234645
	Product(s): Microsoft Access Distribution Kit
	Version(s): WINDOWS:97
	Operating System(s): 
	Keyword(s): kbdta
	Last Modified: 23-NOV-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Office 97 Developer Edition 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you install an application that you built with the Office 97 Developer
	Edition Setup Wizard that includes ODBC Support for SQL Server, you may receive
	the following error message:
	
	  The Setup routine for the SQL Server ODBC Driver could not be loaded due to
	  system error code(1157).
	
	  ODBC's SQL Config Driver Failed for Driver SQL Server.
	
	Setup is not completed successfully.
	
	CAUSE
	=====
	
	You ran the Setup wizard on a computer that has the Microsoft Data Access
	Components version 2.1 (MDAC 2.1) or later and the computer that you tried to
	install your application onto does not have MDAC 2.1 or later installed.
	
	RESOLUTION
	==========
	
	You can use one of the following three methods to work around this problem.
	
	NOTE: After you have used one of the following solutions, you need to re-create
	your disk images and re-install your application to the target computers. To do
	this successfully, you need to rename or remove the newer versions of the files
	listed in step 1 of the "Solution 1" section that were copied to the computer
	during the previous failed installation before you try to reinstall your
	application.
	
	Solution 1
	----------
	
	Moderate: Requires basic macro, coding, and interoperability skills.
	
	NOTE: A file is available for download from the Microsoft Download Center
	(Mdtupdtr.exe) that automatically carries out the manual steps listed for this
	solution. For more information, please see the following article in the
	Microsoft Knowledge Base:
	
	  Q179567 SetupWizard Template Files Updater Available in Download Center
	
	It is possible to change the version of ODBC Components that is included in your
	disk images by changing the entries in one of the Setup Wizard tables. You can
	use this solution if you need the updated ODBC drivers on your development
	computer, but do not need to redistribute the updated ODBC drivers to the target
	computers.
	
	WARNING: Because the following solution will modify the default tables in the
	Setup Wizard, you should back up the following table for reference. If you
	completed a default installation of the Microsoft Office 97 Developer Edition,
	move the following file to a different folder.
	
	  C:\Program Files\Microsoft Office\ODETools\Setup Wizard\Msaccomp\10ODBC
	  Support With SQL Server.MDT
	
	After you have made backups of this table, follow these steps:
	
	1. Copy a version of the ODBC files that can be registered properly by the ODE
	  installation program into the C:\Program Files\Microsoft Office\ODE
	  Tools\Setup Wizard\Redist folder on your development computer.
	
	  
	  +-----------------------------+
	  | ODBCJI32.DLL | ODBCJT32.DLL | 
	  +-----------------------------+
	  | ODBCJTNW.HLP | ODBCJET.HLP  | 
	  +-----------------------------+
	  | ODBCKEY.INF  | ODBCSTF.DLL  | 
	  +-----------------------------+
	  | MSCPXL32.DLL | 12520437.CPX | 
	  +-----------------------------+
	  | 12520850.CPX | ODBCAD32.EXE | 
	  +-----------------------------+
	  | ODBCCP32.DLL | ODBCCP32.CPL | 
	  +-----------------------------+
	  | ODBCCR32.DLL | ODBCINST.HLP | 
	  +-----------------------------+
	  | ODBC16GT.DLL | ODBC32GT.DLL | 
	  +-----------------------------+
	  | DS16GT.DLL   | DS32GT.DLL   | 
	  +-----------------------------+
	  | SQLSRV32.DLL | DBNMPNTW.DLL | 
	  +-----------------------------+
	  | DRVSSRVR.HLP | ODBC32.DLL   | 
	  +-----------------------------+
	  | ODBCINT.DLL  | ODBCTRAC.DLL | 
	  +-----------------------------+
	  | ODBCTL32.DLL |              | 
	  +-----------------------------+
	
	  NOTE: Version 3.6x, or earlier, which is on both the Office 97 Professional
	  CD-ROM and the Microsoft Access 97 CD-ROM, will work.
	
	2. Start Microsoft Access.
	
	3. In the Microsoft Access dialog box, select Open An Existing Database, and
	  then select More Files from the list. Click OK.
	
	4. In the Open dialog box, select All Files (*.*) in the Files Of Type box, and
	  move to the following folder:
	
	  C:\Program Files\Microsoft Office\ODETools\Setup Wizard\Msaccomp
	
	5. Select and open the 10ODBC Support With SQL Server.MDT file.
	
	6. Open the ODBC table and find the lines where the LineID contains the values
	  listed in the following table; then, change Param2 and Param3 to match the
	  list in the table:
	
	+-------------------------------------------------------------------------------------------------------------------------+
	| Line ID           | Param2                | Param3                                                                      | 
	+-------------------------------------------------------------------------------------------------------------------------+
	| add odbctl32_DLL  | $(SwizSetupFilesPath) | C:\Program Files\Microsoft Office\ODETools\Setup Wizard\Redist\ODBCtl32.DLL | 
	+-------------------------------------------------------------------------------------------------------------------------+
	| add odbcji32_DLL  | $(SwizSetupFilesPath) | C:\Program Files\Microsoft Office\ODETools\Setup Wizard\Redist\ODBCJI32.DLL | 
	+-------------------------------------------------------------------------------------------------------------------------+
	| add odbcjt32_DLL  | $(SwizSetupFilesPath) | C:\Program Files\Microsoft Office\ODETools\Setup Wizard\Redist\ODBCJT32.DLL | 
	+-------------------------------------------------------------------------------------------------------------------------+
	| add odbcjtnw_hlp  | $(SwizSetupFilesPath) | C:\Program Files\Microsoft Office\ODETools\Setup Wizard\Redist\ODBCJTNW.HLP | 
	+-------------------------------------------------------------------------------------------------------------------------+
	| add odbcjet_hlp   | $(SwizSetupFilesPath) | C:\Program Files\Microsoft Office\ODETools\Setup Wizard\Redist\ODBCJET.HLP  | 
	+-------------------------------------------------------------------------------------------------------------------------+
	| add odbckey_inf   | $(SwizSetupFilesPath) | C:\Program Files\Microsoft Office\ODETools\Setup Wizard\Redist\ODBCKEY.INF  | 
	+-------------------------------------------------------------------------------------------------------------------------+
	| add odbcstf_DLL   | $(SwizSetupFilesPath) | C:\Program Files\Microsoft Office\ODETools\Setup Wizard\Redist\ODBCSTF.DLL  | 
	+-------------------------------------------------------------------------------------------------------------------------+
	| add mscpxl32_DLL  | $(SwizSetupFilesPath) | C:\Program Files\Microsoft Office\ODETools\Setup Wizard\Redist\MSCPXL32.DLL | 
	+-------------------------------------------------------------------------------------------------------------------------+
	| add 12520437_cpx  | $(SwizSetupFilesPath) | C:\Program Files\Microsoft Office\ODETools\Setup Wizard\Redist\12520437.CPX | 
	+-------------------------------------------------------------------------------------------------------------------------+
	| add 12520850_cpx  | $(SwizSetupFilesPath) | C:\Program Files\Microsoft Office\ODETools\Setup Wizard\Redist\12520850.CPX | 
	+-------------------------------------------------------------------------------------------------------------------------+
	| add odbcad32_exe  | $(SwizSetupFilesPath) | C:\Program Files\Microsoft Office\ODETools\Setup Wizard\Redist\ODBCAD32.EXE | 
	+-------------------------------------------------------------------------------------------------------------------------+
	| add odbccp32_cpl  | $(SwizSetupFilesPath) | C:\Program Files\Microsoft Office\ODETools\Setup Wizard\redist\ODBCCP32.CPL | 
	+-------------------------------------------------------------------------------------------------------------------------+
	| add odbccp32_DLL  | $(SwizSetupFilesPath) | C:\Program Files\Microsoft Office\ODETools\Setup Wizard\Redist\ODBCCP32.DLL | 
	+-------------------------------------------------------------------------------------------------------------------------+
	| add odbccr32_DLL  | $(SwizSetupFilesPath) | C:\Program Files\Microsoft Office\ODETools\Setup Wizard\Redist\ODBCCR32.DLL | 
	+-------------------------------------------------------------------------------------------------------------------------+
	| add odbcinst_hlp  | $(SwizSetupFilesPath) | C:\Program Files\Microsoft Office\ODETools\Setup Wizard\Redist\ODBCINST.hlp | 
	+-------------------------------------------------------------------------------------------------------------------------+
	| add odbc16gt_DLL  | $(SwizSetupFilesPath) | C:\Program Files\Microsoft Office\ODETools\Setup Wizard\Redist\ODBC16GT.DLL | 
	+-------------------------------------------------------------------------------------------------------------------------+
	| add odbc32GT_DLL  | $(SwizSetupFilesPath) | C:\Program Files\Microsoft Office\ODETools\Setup Wizard\Redist\ODBC32GT.DLL | 
	+-------------------------------------------------------------------------------------------------------------------------+
	| add ds16gt_DLL    | $(SwizSetupFilesPath) | C:\Program Files\Microsoft Office\ODETools\Setup Wizard\Redist\DS16GT.DLL   | 
	+-------------------------------------------------------------------------------------------------------------------------+
	| add ds32gt_DLL    | $(SwizSetupFilesPath) | C:\Program Files\Microsoft Office\ODETools\Setup Wizard\Redist\ds32gt.DLL   | 
	+-------------------------------------------------------------------------------------------------------------------------+
	| add sqlsrv32_DLL  | $(SwizSetupFilesPath) | C:\Program Files\Microsoft Office\ODETools\Setup Wizard\Redist\SQLSRV32.DLL | 
	+-------------------------------------------------------------------------------------------------------------------------+
	| add dbnmpntw_DLL  | $(SwizSetupFilesPath) | C:\Program Files\Microsoft Office\ODETools\Setup Wizard\Redist\dbnmpntw.DLL | 
	+-------------------------------------------------------------------------------------------------------------------------+
	| add drvssrvr_hlp  | $(SwizSetupFilesPath) | C:\Program Files\Microsoft Office\ODETools\Setup Wizard\Redist\drvssrvr.hlp | 
	+-------------------------------------------------------------------------------------------------------------------------+
	| add odbc32_DLL    | $(SwizSetupFilesPath) | C:\Program Files\Microsoft Office\ODETools\Setup Wizard\Redist\ODBC32.DLL   | 
	+-------------------------------------------------------------------------------------------------------------------------+
	| add odbcint32_DLL | $(SwizSetupFilesPath) | C:\Program Files\Microsoft Office\ODETools\Setup Wizard\Redist\ODBCINT.DLL  | 
	+-------------------------------------------------------------------------------------------------------------------------+
	| add odbctrac_DLL  | $(SwizSetupFilesPath) | C:\Program Files\Microsoft Office\ODETools\Setup Wizard\redist\ODBCTRAC.DLL | 
	+-------------------------------------------------------------------------------------------------------------------------+
	
	7. Close the database.
	
	The next time that you run the Setup Wizard and select the ODBC Support for SQL
	Server, it will include the specific files that you placed in the Redist folder
	instead of the current ODBC support files on the computer.
	
	Solution 2
	----------
	
	Novice: Requires knowledge of the user interface on single-user computers.
	
	Use the Setup Wizard to create disk images on a computer that matches the lowest
	common configuration for all of the anticipated target computers for your
	application. Some configurations that would suit this purpose:
	
	- Windows 95 or Windows 98 without the Updated SQL Server ODBC Driver
	- Windows NT 4.0 Workstation or Server without the Updated SQL Server ODBC
	  Drivers
	
	Solution 3
	----------
	
	Moderate: Requires basic macro, coding, and interoperability skills.
	
	If you must redistribute the SQL Server 7.0 ODBC driver, use the Setup Wizard to
	create disk images and do not include ODBC Support for SQL Server with the
	Office Developer Edition Disk set.
	
	Include ODBC Support as a separate setup program using the Microsoft Data Access
	Components redistribution set available from the Microsoft Data Access
	Components Web site
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft Office 97 Developer
	Edition.
	
	MORE INFORMATION
	================
	
	When you include the ODBC Support with SQL Server component in an ODE
	application install, the Setup wizard includes the current ODBC files from the
	computer in the disk image that it creates. When MDAC 2.1 or later is installed
	on a computer, a newer version of the SQL Server driver (SQLSRV32.DLL), version
	3.7x or later, is installed. The proper function of this version of SQLSVR32.DLL
	is dependent on a new file, SQLWOA.DLL, which is not included in disk images
	made by the Setup Wizard. Without SQLWOA.DLL, the Setup program can not register
	SQLSRV32.DLL and you receive the error described in the "Symptoms" section of
	this article.
	
	REFERENCES
	==========
	
	For more information about other issues involving the Office 97 Developer
	Edition and distributing applications, please see the following articles in the
	Microsoft Knowledge Base:
	
	  Q179011 ODE: Running Microsoft ODE97 on a Computer with Internet Explorer 4.0
	
	  Q160870 ACC: VBA Functions Break in Databases with Missing References
	
	  Q162884 ODE97: Troubleshooting ODE Setup Wizard Problems
	
	Additional query words: pra the setup routine for the sql odbc server could not be loaded due to system error code 1157 odbc s sql config driver failed for driver sql server.
	
	======================================================================
	Keywords          : kbdta 
	Technology        : kbOfficeSearch kbAudDeveloper kbOffice97Search kbOffice97 kbOffice97DevSearch
	Version           : WINDOWS:97
	Issue type        : kbbug
	Solution Type     : kbnofix
	
	=============================================================================
	

{% endraw %}
