---
layout: page
title: "Q198921: FIX: Visual C++ ATL Provider Fails when Used with SQL DTS"
permalink: /kb/198/Q198921/
---

## Q198921: FIX: Visual C++ ATL Provider Fails when Used with SQL DTS

{% raw %}

	Article: Q198921
	Product(s): Microsoft C Compiler
	Version(s): 6.0,7.0
	Operating System(s): 
	Keyword(s): kbDatabase kbOLEDB kbVC600bug kbATL300bug kbSQLServ700 kbVS600sp2bug kbVS600sp3fix kbGr
	Last Modified: 07-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual C++, 32-bit Enterprise Edition, version 6.0 
	- Microsoft SQL Server version 7.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	SQL Server version 7.0 Data Transformation Services (DTS) works with an OLE DB
	provider as a source or destination. If you use DTS Import Wizard with a Visual
	C++ ATL wizard-generated OLE DB Provider as source, when you execute the package
	the following error occurs:
	
	  Required connection properties have not been specified in a connection
	  object.
	
	CAUSE
	=====
	
	This is caused by a bug in the ATL Provider templates. The ATL Provider
	templates incorrectly returns initialization properties when
	IDBProperties::GetPropertyInfo() is called with the property set GUID is set to
	DBPROPSET_DBINITALL.
	
	RESOLUTION
	==========
	
	To resolve this problem, upgrade to Microsoft Visual Studio 6.0 Service Pack
	3.0.
	
	Also, to get DTS to import from the default ATL wizard-generated provider, do the
	following:
	
	1. In the Select Source Tables window, the SQL Destination table name is shown
	  as [databasename].[dbo].[*]. Change the table name "*" to another valid
	  identifier.
	
	2. Change the destination data-types. This can be accomplished in one of two
	  ways:
	
	   - Change the T-SQL Syntax
	
	     a. Click Transform in the Select Source Tables window. The Wizard shows
	        decimal destination type for FileAttributes, FileSizeHigh, and
	        FileSizeLow columns in the source.
	
	     b. Change data type of FileAttributes to Varchar(4).
	
	     c. Change data type of FileSizeHigh and FileSizeLow to int.
	
	   - Change the provider column map
	
	     In the file that has the declaration for CFilesWindowsFile (FilesRS.h)
	     change the property map for the rowset to more accurately specify the
	     source datatypes.
	
	  PROVIDER_COLUMN_ENTRY_FIXED("FileAttributes", 1, DBTYPE_I4, dwFileAttributes)
	  PROVIDER_COLUMN_ENTRY_FIXED("FileSizeHigh", 2, DBTYPE_I4, nFileSizeHigh)
	  PROVIDER_COLUMN_ENTRY_FIXED("FileSizeLow", 3, DBTYPE_I4, nFileSizeLow)
	  PROVIDER_COLUMN_ENTRY_STR("FileName", 4, cFileName)
	  PROVIDER_COLUMN_ENTRY_STR("AltFileName", 5, cAlternateFileName)
	
	3. Complete the remaining steps and the data should be copied correctly.
	
	Another workaround is to specify SQL Server as the data source instead of ATL
	provider in the DTS Import Wizard. Then, select the Use a query to specify the
	data option and use a distributed query to retrieve data from the ATL provider.
	Following is an example query:
	
	  Select * from Openrowset ('MyProv.MyProv', '','c:\*.*')
	
	NOTE: You must apply the fixes in Service Pack 3.0 to enable the provider to work
	with a SQL distributed query.
	
	STATUS
	======
	
	This bug was corrected in Visual Studio 6.0 Service Pack 3.0.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Create an ATL project using the ATL COM AppWizard.
	
	2. Create an ATL OLE DB provider by clicking New ATL Object on the Insert menu,
	  and then select Data Access for the Category and Provider for the Object.
	
	3. Build the ATL OLE DB Provider.
	
	4. Register the provider on a machine with SQL Server 7.0 installed.
	
	5. Run DTS Import Wizard and select the ATL provider as Source (you don't need
	  to specify a Server, UserID, or Password) and choose SQL Server as the
	  Destination.
	
	6. In the Select Source Tables window, "MSSQL7\BINN\*.*" is shown as the source
	  table. You can preview all data retrieved by the ATL provider. In the
	  Destination field box, the SQL table name is shown as
	  "[<databasename>].[dbo].[*]".
	
	When you finish the wizard and run it, the execution fails with the following
	error:
	
	  Required connection properties have not been specified.
	
	
	REFERENCES
	==========
	
	For additional information about fixes needed to use ATL OLEDB provider with SQL
	7.0 distributed query, please see the following articles in the Microsoft
	Knowledge Base:
	
	  Q200921 OpenQuery with ATL Provider Fails When Set Up with SEM
	
	  Q198520 ATL OLE DB Provider Fails When Called from SQL 7.0 Query
	
	Additional query words: kbDatabase kbAtl kbOLEDB
	
	======================================================================
	Keywords          : kbDatabase kbOLEDB kbVC600bug kbATL300bug kbSQLServ700 kbVS600sp2bug kbVS600sp3fix kbGrpDSVCDB kbVS600SP1bug kbMDACNoSweep 
	Technology        : kbVCsearch kbSQLServSearch kbAudDeveloper kbSQLServ700 kbVC600 kbVC32bitSearch
	Version           : :6.0,7.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
