---
layout: page
title: "Q185821: Ident.exe Retrieves @@IDENTITY From ODBC Inserts"
permalink: /kb/185/Q185821/
---

## Q185821: Ident.exe Retrieves @@IDENTITY From ODBC Inserts

{% raw %}

	Article: Q185821
	Product(s): Microsoft C Compiler
	Version(s): 2.5,2.6,3.5,3.6,5.0,6.0
	Operating System(s): 
	Keyword(s): kbfile kbSample kbDatabase kbDriver kbMFC kbODBC kbSQL kbSQLServ kbVC500 kbGrpDSVCDB kb
	Last Modified: 23-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual C++, 32-bit Enterprise Edition, versions 5.0, 6.0 
	- Microsoft Visual C++, 32-bit Professional Edition, versions 5.0, 6.0 
	- Microsoft Visual C++, 32-bit Learning Edition, version 6.0 
	- Microsoft ODBC Driver for SQL Server, versions 3.5, 3.6 
	- Microsoft Data Access Components versions 2.5, 2.6, 2.7 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	When you insert values into a table with an identity column, SQL Server
	automatically generates the next identifier based on the last used identity
	value. You might want to retrieve this automatically generated identity value
	immediately after an insert.
	
	The Ident.exe sample demonstrates how to retrieve the automatic @@IDENTITY value
	from an insert into a Microsoft SQL Server database. The sample consists of a
	simple MFC AppWizard project based on the CRecordset class. The project was
	modified slightly to allow inserts into the table and to retrieve the
	automatically generated identity value for the insert. It uses the pubs data
	source name (DSN), although any DSN will work, and a table called tblIdentity.
	
	MORE INFORMATION
	================
	
	The following files are available for download from the Microsoft Download
	Center:
	
	  Ident.exe
	
	For additional information about how to download Microsoft Support files, click
	the article number below to view the article in the Microsoft Knowledge Base:
	
	  Q119591 How to Obtain Microsoft Support Files from Online Services
	
	Microsoft used the most current virus detection software available on the date of
	posting to scan this file for viruses. Once posted, the file is housed on secure
	servers that prevent any unauthorized changes to the file.
	
	
	Ident.exe includes an algorithm and sample code that illustrate how to retrieve
	the identity value from a SQL Server database. You can use this method for
	multiple processes or threads doing simultaneous inserts into the same table.
	(Note that threads cannot share connections.)
	
	Project Description
	-------------------
	
	A master identity table, called tblIdentity, is created. It consists of the
	identity, table name, and server process ID number (SPID). An insert trigger
	into tblIdentity is created for each table in the database that satisfies the
	following criteria:
	
	- Inserts are performed on the table.
	
	- The table has an identity column with values that are automatically generated
	  by SQL Server.
	
	- The automatically generated identity value is needed immediately after the
	  insertion.
	
	The following SQL script, located in the Master.sql file, generates the sample
	table, insertTbl:
	
	     CREATE TABLE insertTbl (myAuto int IDENTITY (1, 1) NOT NULL ,
	                             lname varchar (15) NOT NULL ,
	                             fname varchar (15) NOT NULL )
	
	Because names are not unique, the code uses the identity property of SQL Server
	to automatically generate a unique key.
	
	The following SQL script, located in the Master.sql file, creates an insert
	trigger for insertTbl:
	
	     CREATE TRIGGER trgAudit ON insertTbl FOR INSERT
	        AS
	        INSERT INTO tblIdentity VALUES (@@IDENTITY, 'insertTbl', @@SPID)
	
	Immediately after an insertion into tblIdentity, the trigger fires and stores:
	
	- the identity SQL Server generated (@@IDENTITY),
	
	- the table name ("insertTbl" in this case), and
	
	- the SPID (the server process ID number of the current process, guaranteed to
	  be unique for each connection).
	
	After insertion, the program calls a stored procedure (called sp_getID) to
	retrieve the identity value.
	
	The code calls the stored procedure sp_getID (with a negative value for the spid
	parameter) in the one time initialization to get the SPID (the server process ID
	number of the current process, guaranteed to be unique for each connection).
	Applications with multiple threads inserting into the same table must not share
	a connection. Each thread must have it's own connection to guarantee a unique
	SPID.
	
	NOTE: Applications with multiple threads sharing a connection must use a more
	complicated algorithm that includes the thread ID and the SPID to establish a
	unique insertion.
	
	After each insertion, the program calls sp_getID and passes the table name where
	the insert occurred and the SPID that was retrieved in the initial call to
	sp_getID. The stored procedure sp_getID returns the unique identity value that
	SQL Server generated on the insert.
	
	Running the Sample
	------------------
	
	To use the sample application, run the Master.sql file in the SQL Query Tool from
	SQL Enterprise Manager. After running the script, you can verify that the tables
	and triggers were created successfully by running the following SQL statement:
	
	     insert into insertTbl (lname,fname) VALUES ('Smith','Joe')
	     select * from tblIdentity
	
	The Results tab should look similar to the following:
	
	  iID         strTable        SPID
	  ----------- --------------- -----------
	  5           insertTbl       11
	
	  (1 row(s) affected)
	
	The iID and SPID values you see will probably not be 5 and 11. The tblIdentity
	values verify that the Master.sql script was successful.
	
	NOTE: The sample code uses a sub-optimal method to display the identity value and
	is used for illustration purposes only.
	
	The sample uses the SQLExecDirect function to run the stored procedure and
	retrieve the identity value.
	
	REFERENCES
	==========
	
	For more information, please see the following article in the Microsoft
	Knowledge Base:
	
	  Q163446 PRB: Guarantee @@IDENTITY Value on a Per Table Basis
	
	Additional query words: Ident
	
	======================================================================
	Keywords          : kbfile kbSample kbDatabase kbDriver kbMFC kbODBC kbSQL kbSQLServ kbVC500 kbGrpDSVCDB kbGrpDSMDAC kbDSupport kbMDAC250 kbSQLProg 
	Technology        : kbVCsearch kbSQLServSearch kbAudDeveloper kbODBCSearch kbMDACSearch kbMDAC250 kbMDAC260 kbODBCSQLServ350 kbODBCSQLServ360 kbVC500 kbVC600 kbVC32bitSearch kbVC500Search kbMDAC270
	Version           : :2.5,2.6,3.5,3.6,5.0,6.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
