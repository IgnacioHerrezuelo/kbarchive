---
layout: page
title: "Q156526: General Error=51 Connecting to an Access Datasource"
permalink: /kb/156/Q156526/
---

## Q156526: General Error=51 Connecting to an Access Datasource

{% raw %}

	Article: Q156526
	Product(s): Internet Information Server
	Version(s): winnt:1.0,2.0
	Operating System(s): 
	Keyword(s): kbinterop
	Last Modified: 25-DEC-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Internet Information Server versions 1.0, 2.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you perform a query to an Microsoft Access database using Internet Database
	Connector (IDC), you may receive the following error:
	
	  [State=S1000][Error=51][Microsoft][ODBC Microsoft Access 7.0
	  Driver]General Error
	  Not enough information to connect to this DSN with SQLConnect. Use
	  SQLDriverConnect.
	
	CAUSE
	=====
	
	This can be caused by one of two reasons.
	
	- The key for this datasource has a permission restriction applied.
	
	- The key for the datasource does not have the appropriate subkey values added.
	  This can be caused by a corrupt key or the subkey is missing.
	
	The key location is:
	
	HKEY_LOCAL_MACHINE\SOFTWARE\ODBC\ODBC.INI\Access_data_source_name\Engines\Jet 2.x
	
	WORKAROUND
	==========
	
	If the key for this datasource has a permission restriction applied, make sure
	the user who is logging into the database has read and execute permissions to
	the datasource key.
	
	If the key for the datasource does not have the appropriate subkey values added.
	The Access_data_source_name will exist, but the other subkey will not be there.
	If you delete the datasource from the ODBC Manager, the entry may remain in the
	registry. You may have to remove the entire entry of the Datasource from the
	registry manually and then add a new datasource from the ODBC Manager.
	
	MORE INFORMATION
	================
	
	See Chapter 8 of the on-line product documentation for the Internet Information
	Server (IIS) version 2.0 for a more complete guide in the use of IDC. This
	chapter also includes help on creating System DSNs.
	
	Included with IIS are numerous IDC/HTX samples located in the
	X:\IIS_Directory\Scripts\Samples\ directory, where X is the drive letter and
	iis_Directory is the name given to the install directory of IIS.
	
	See the Windows NT Resource Kit for further information on the use of the
	Registry Editor.
	
	Additional query words: iis http
	
	======================================================================
	Keywords          : kbinterop 
	Technology        : kbiisSearch kbiis200 kbiis100
	Version           : winnt:1.0,2.0
	
	=============================================================================
	

{% endraw %}
