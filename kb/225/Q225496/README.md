---
layout: page
title: "Q225496: PRB: Cannot Execute Stored Procedures with More Than 60 Params"
permalink: /kb/225/Q225496/
---

## Q225496: PRB: Cannot Execute Stored Procedures with More Than 60 Params

{% raw %}

	Article: Q225496
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 6.0
	Operating System(s): 
	Keyword(s): kbDatabase kbSQLServ kbStoredProc kbVBp600 kbDataEnv kbGrpDSVBDB kbGrpDSMDAC kbDSupport
	Last Modified: 23-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Professional Edition for Windows, version 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you try to execute a stored procedure that has 60 parameters or more using
	the Data Environment designer by passing the parameters within your Form module,
	you would get the following Compiler error:
	
	  Subscript out of range
	
	The same error would occur if you try executing the same stored procedure using
	the User Connection Designer within Visual Basic 5.0 and 6.0 applications.
	
	CAUSE
	=====
	
	This is a Visual Basic limitation. Visual Basic does not let you create methods
	with more than 60 arguments.
	
	The behavior basically occurs when you try to invoke any method with more than 60
	parameters (or arguments) within your Visual Basic application using early
	binding. This behavior does not happen when you use late binding to invoke the
	same method within your Visual Basic application.
	
	The following is from the Visual Basic Help file:
	
	  A procedure can have only 60 arguments. This error has the following cause and solution: 
	
		. You specified more than 60 arguments.
	
	  If you must specify more arguments, define a user-defined type to collect multiple arguments of different types, or use a ParamArray as the final argument and pass multiple values to it. You can also pass multiple arguments by placing them in an array.
	
	  For additional information, select the item in question and press F1. 
	
	RESOLUTION
	==========
	
	If you are using the Data Environment Designer::
	
	Pass the parameters using the Call Syntax within the Data Environment as
	follows:
	
	1. Right-click on your Command within the Data Environment Designer.
	
	2. Click on Properties.
	
	3. On the General tab, type your Call syntax under Sql Statement:
	
	    {Call TestProc61 ('1', '2', '3', ... '59', '60', '61')}
	
	  -or-
	
	  Use the ADO command object to execute your procedure.
	
	If you are using the User Connection Designer::
	
	Use the rdoQuery object to execute your procedure.
	
	STATUS
	======
	
	This behavior is by design.
	
	MORE INFORMATION
	================
	
	The following sample demonstrates the behavior with the Data Environment
	Designer. Similar steps could be followed to reproduce the behavior with the
	User Connection Designer.
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Building the SQL Server test table::
	
	  CREATE TABLE dbo.tblTest (
	  Column1 char (5) NULL , Column2 char (5) NULL , Column3 char (5) NULL ,
	  Column4 char (5) NULL , Column5 char (5) NULL , Column6 char (5) NULL ,
	  Column7 char (5) NULL , Column8 char (5) NULL , Column9 char (5) NULL ,
	  Column10 char (5) NULL , Column11 char (5) NULL , Column12 char (5) NULL,
	  Column13 char (5) NULL ,Column14 char (5) NULL , Column15 char (5) NULL,
	  Column16 char (5) NULL ,Column17 char (5) NULL , Column18 char (5) NULL,
	  Column19 char (5) NULL ,Column20 char (5) NULL , Column21 char (5) NULL,
	  Column22 char (5) NULL ,Column23 char (5) NULL , Column24 char (5) NULL,
	  Column25 char (5) NULL ,Column26 char (5) NULL , Column27 char (5) NULL,
	  Column28 char (5) NULL ,Column29 char (5) NULL , Column30 char (5) NULL,
	  Column31 char (5) NULL ,Column32 char (5) NULL , Column33 char (5) NULL,
	  Column34 char (5) NULL ,Column35 char (5) NULL , Column36 char (5) NULL,
	  Column37 char (5) NULL ,Column38 char (5) NULL , Column39 char (5) NULL,
	  Column40 char (5) NULL ,Column41 char (5) NULL , Column42 char (5) NULL,
	  Column43 char (5) NULL ,Column44 char (5) NULL , Column45 char (5) NULL,
	  Column46 char (5) NULL ,Column47 char (5) NULL , Column48 char (5) NULL,
	  Column49 char (5) NULL ,Column50 char (5) NULL , Column51 char (5) NULL,
	  Column52 char (5) NULL ,Column53 char (5) NULL , Column54 char (5) NULL,
	  Column55 char (5) NULL ,Column56 char (5) NULL , Column57 char (5) NULL,
	  Column58 char (5) NULL ,Column59 char (5) NULL , Column60 char (5) NULL
	  ,Column61 char (5) NULL
	  )
	  GO
	
	2. Building the SQL Server Stored Procedure with 61 parameters::
	
	  CREATE PROCEDURE procTest61
	  @Column1 char(10),@Column2 char(10),@Column3 char(10),@Column4 char(10),
	  @Column5 char(10),@Column6 char(10),@Column7 char(10),@Column8 char(10),
	  @Column9 char(10),@Column10 char(10),@Column11 char(10),@Column12 char(10),
	  @Column13 char(10),@Column14 char(10),@Column15 char(10),@Column16
	  char(10),@Column17 char(10),@Column18 char(10),@Column19 char(10),@Column20
	  char(10),@Column21 char(10),@Column22 char(10),@Column23 char(10),@Column24
	  char(10),@Column25 char(10),@Column26 char(10),@Column27 char(10),@Column28
	  char(10),@Column29 char(10),@Column30 char(10),@Column31 char(10),@Column32
	  char(10),@Column33 char(10),@Column34 char(10),@Column35 char(10),@Column36
	  char(10),@Column37 char(10),@Column38 char(10),@Column39 char(10),@Column40
	  char(10),@Column41 char(10),@Column42 char(10),@Column43 char(10),@Column44
	  char(10),@Column45 char(10),@Column46 char(10),@Column47 char(10),@Column48
	  char(10),@Column49 char(10),@Column50 char(10),@Column51 char(10),@Column52
	  char(10),@Column53 char(10),@Column54 char(10),@Column55 char(10),@Column56
	  char(10),@Column57 char(10),@Column58 char(10),@Column59 char(10),@Column60
	  char(10),@Column61 char(10)
	
	  AS
	
	  Insert Into tblTest (
	  Column1,Column2,Column3,Column4,Column5,Column6,Column7,Column8,Column9,
	  Column10,Column11,Column12,Column13,Column14,Column15,Column16,Column17,
	  Column18,Column19,Column20,Column21,Column22,Column23,Column24,Column25,
	  Column26,Column27,Column28,Column29,Column30,Column31,Column32,Column33,
	  Column34,Column35,Column36,Column37,Column38,Column39,Column40,Column41,
	  Column42,Column43,Column44,Column45,Column46,Column47,Column48,Column49,
	  Column50,Column51,Column52,Column53,Column54,Column55,Column56,Column57,
	  Column58,Column59,Column60,Column61 )
	  Values (
	  @Column1,@Column2,@Column3,@Column4,@Column5,@Column6,@Column7,@Column8,
	  @Column9,@Column10,@Column11,@Column12,@Column13,@Column14,@Column15,
	  @Column16,@Column17,@Column18,@Column19,@Column20,@Column21,@Column22,
	  @Column23,@Column24,@Column25,@Column26,@Column27,@Column28,@Column29,
	  @Column30,@Column31,@Column32,@Column33,@Column34,@Column35,@Column36,
	  @Column37,@Column38,@Column39,@Column40,@Column41,@Column42,@Column43,
	  @Column44,@Column45,@Column46,@Column47,@Column48,@Column49,@Column50,
	  @Column51,@Column52,@Column53,@Column54,@Column55,@Column56,@Column57,
	  @Column58, @Column59,@Column60,@Column61 )
	  GO
	
	3. Building the Visual Basic Code with the Data Environment:
	
	1. Create a Standard EXE project in Visual Basic. Form1 is created by default.
	
	2. Add a DataEnvironment to the project. Connection1 is created by default.
	
	3. Set Connection1 to use the SQLOLEDB provider to connect to the your server's
	  Pubs database, or use the MSDASQL provider to connect to a DSN pointing to
	  your server's Pubs database.
	
	4. Insert a stored procedure, procTest61, to Connection1.
	
	5. Add a CommandButton to Form1 from the toolbox. Command1 is created by
	  default.
	
	6. Add the following code to the Command1_Click event:
	
	  Private Sub Command1_Click()
	
	    ' Passing the parameters to execute procTest61 procedure 
	      DataEnvironment1.dbo_procTest61 "1", "2", "3", "4", "5", "6", "7", "8", 
	             "9", "10", "11", "12", "13", "14", "15", "16", "17", "18", "19",                                                       
	             "20", "21", "22", "23", "24", "25", "26", "27", "28", "29",                                                      
	             "30", "31", "32", "33", "34", "35", "36", "37", "38", "39",                                                        
	             "40", "41", "42", "43", "44", "45", "46", "47", "48", "49",                                             
	             "50", "51", "52", "53", "54", "55", "56", "57", "58", "59",                                               
	             "60", "61"  
	      
	      MsgBox "Test passed Successfully..."
	
	  End Sub
	
	7. Once you hit the F5 key to run the project, you would get the Compiler error.
	
	NOTE: If you try to follow the same above steps to execute a stored procedure
	with 60 or less, you would not get the Compiler error.
	
	(c) Microsoft Corporation 1999, All Rights Reserved.
	Contributions by Ammar Abuthuraya, Microsoft Corporation
	
	
	REFERENCES
	==========
	
	For more information, please refer to the Visual Basic documentation.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbDatabase kbSQLServ kbStoredProc kbVBp600 kbDataEnv kbGrpDSVBDB kbGrpDSMDAC kbDSupport kbMDAC250 kbMDAC260 kbATM kbmdac270 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB600Search kbVB600
	Version           : :6.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
