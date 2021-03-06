---
layout: page
title: "Q276287: PRB: SET FORMAT File Scrolls to End of Table in Visual FoxPro"
permalink: /kb/276/Q276287/
---

## Q276287: PRB: SET FORMAT File Scrolls to End of Table in Visual FoxPro

{% raw %}

	Article: Q276287
	Product(s): Microsoft FoxPro
	Version(s): 5.0,5.0a,6.0
	Operating System(s): 
	Keyword(s): kbvfp500 kbvfp500a kbvfp600 kbXBase kbGrpDSFox kbDSupport kbCodeSnippet
	Last Modified: 11-NOV-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, versions 5.0, 5.0a, 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Visual FoxPro offers a level of backward compatibility with files from Dbase. In
	some cases, you might find that Dbase Format (.fmt) files behave erratically by
	scrolling to the end the table, as if the Page Down key is being pressed.
	
	CAUSE
	=====
	
	Visual FoxPro uses Event Model rather than Foundation READ.
	
	RESOLUTION
	==========
	
	There are two recommended workarounds:
	
	- The first method is to recreate the format files as native Visual FoxPro
	  forms.
	
	- The second method requires modifications to the format files. The following
	  code is generated when you create a format file in Dbase, and it varies
	  depending on how the format file was originally designed. To demonstrate this
	  workaround, perform the following steps:
	
	  1. Paste the following code into a program or text file, and save it as
	     Empform.fmt:
	
	  *-- Format file initialization code --------------------------------------------
	
	  IF SET("TALK")="ON"
	     SET TALK OFF
	     lc_talk="ON"
	  ELSE
	     lc_talk="OFF"
	  ENDIF
	
	  *-- This form was created in EGA25 mode
	  SET DISPLAY TO EGA25
	
	  lc_status=SET("STATUS")
	  *-- SET STATUS was ON when you went into the Forms Designer.
	  IF lc_status = "OFF"
	     SET STATUS ON
	  ENDIF
	
	  *-- @ SAY GETS Processing. --------------------------
	
	  *!* MODIFICATION (1 of 2)
	  *!* Set a procedure call to assign keys
	  *!* functionality to the PageUp, PageDown and Escape Keys. 
	  SET PROCEDURE TO SetKey 
	  KeyInit()	&&Initializes the keys
	  *!* 
	
	  *--  Format Page: 1
	  @ 1,0 SAY "EMP_ID" 
	  @ 1,12 GET emp_id PICTURE "XXXXXX" 
	  @ 2,0 SAY "LAST_NAME" 
	  @ 2,12 GET lname PICTURE "XXXXXXXXXXXXXXXXXXXX" 
	  @ 3,0 SAY "FIRST_NAME" 
	  @ 3,12 GET fname PICTURE "XXXXXXXXXX" 
	  @ 6,0 SAY "HIRE_DATE" 
	  @ 6,12 GET hire_date 
	  *-- Format file exit code ---------------------------
	
	  *!* MODIFICATION (2 of 2)
	  *!* Establish the READ command to loop around the fields.
	  READ CYCLE 
	  *!*
	
	  *-- SET STATUS was ON when you went into the Forms Designer.
	  IF lc_status = "OFF"  && Entered form with status off
	     SET STATUS OFF     && Turn STATUS "OFF" on the way out
	  ENDIF
	
	  IF lc_talk="ON"
	     SET TALK ON
	  ENDIF
	
	  RELEASE lc_talk,lc_fields,lc_status
	  *-- EOP: EMPFORM.FMT
	
	  2. Paste the following code into a program or text file, and save it as
	     Setkey.prg:
	
	  FUNCTION KeyInit
	  	ON KEY LABEL PgUp PageUp()
	  	ON KEY LABEL PgDn PageDown()
	  	ON KEY LABEL Esc EscFunc()
	  ENDFUNC
	
	  FUNCTION PageUp
	  IF !BOF()
	  	SKIP -1
	  	SHOW GETS
	  ELSE
	  	GO TOP
	  ENDIF
	  ENDFUNC
	
	  FUNCTION PageDown
	  SKIP
	  IF EOF()
	  	GO BOTTOM
	  ENDIF
	  SHOW GETS
	  ENDFUNC
	
	  FUNCTION EscFunc
	  	ON KEY LABEL PgUp 
	  	ON KEY LABEL PgDn 
	  	ON KEY LABEL Esc
	  	SET STATUS BAR ON
	  	CLEAR
	  	CANCEL
	  ENDFUNC
	
	  3. Paste this code into a program or text file, and save it as Main.prg:
	
	  *!*	Creates a sample table
	  CREATE TABLE emp_table (emp_id c(9),fname c(20),lname c(30),hire_date T(8))
	
	  *!*	Inserts sample records.
	  INSERT INTO emp_table (emp_id,fname,lname,hire_date);
	  	VALUES ('234234325','George','Washington',{^2000/07/01 12:35pm})
	
	  INSERT INTO emp_table (emp_id,fname,lname,hire_date);
	  	VALUES ('456432734','Albert','Einstein',{^2000/08/23 4:40pm})
	
	  INSERT INTO emp_table (emp_id, fname,lname,hire_date);
	  	VALUES ('566753444','Amelia','Earhart',{^2000/10/15 8:00am})
	
	  GO TOP
	
	  *!*	Executes the Format File instead of using the SET FORMAT command.
	  DO empform.fmt &&Calls the Format File
	  USE
	
	  4. Run the program from Visual FoxPro by typing DO MAIN from the Command
	     window and pressing ENTER.
	
	This workaround basically traps for keys like PageUp, PageDown and Escape keys,
	and assigns specific actions that are defined in Setkey.prg. It uses a READ
	CYCLE to prevent the records from scrolling abnormally.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Start Visual FoxPro.
	
	2. Change directory to where your format (.fmt) file is located.
	
	3. Type the following lines and press ENTER after each one:
	
	  USE EMP_table
	  SET FORMAT TO empform.fmt 
	  EDIT
	
	4. Note the behavior at this point.
	
	(c) Microsoft Corporation 2000, All Rights Reserved. Contributions by Reinaldo
	Torrales, Microsoft Corporation.
	
	
	REFERENCES
	==========
	
	For additional information, click the article number below to view the article
	in the Microsoft Knowledge Base:
	
	  Q162683 BUG: BROWSE FORMAT May Cause Blank Browse Window
	
	Additional query words:
	
	======================================================================
	Keywords          : kbvfp500 kbvfp500a kbvfp600 kbXBase kbGrpDSFox kbDSupport kbCodeSnippet 
	Technology        : kbVFPsearch kbAudDeveloper kbVFP500 kbVFP600 kbVFP500a
	Version           : :5.0,5.0a,6.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
