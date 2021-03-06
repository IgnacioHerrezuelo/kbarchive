---
layout: page
title: "Q128995: PRB: Unrecognized Command Verb Error When Instantiate Object"
permalink: /kb/128/Q128995/
---

## Q128995: PRB: Unrecognized Command Verb Error When Instantiate Object

{% raw %}

	Article: Q128995
	Product(s): Microsoft FoxPro
	Version(s): WINDOWS:3.0
	Operating System(s): 
	Keyword(s): kberrmsg
	Last Modified: 12-FEB-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, version 3.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	The "Unrecognized Command Verb" error is returned when the ADDOBJECT() method or
	the CREATEOBJECT() function are used in a form or a program, but the highlighted
	line does not contain any error.
	
	CAUSE
	=====
	
	The error that yields the "Unrecognized Command Verb" is in the class definition
	of the object that is instantiated. The class is defined in a procedure file
	(.PRG) or a Visual Class Library (.VCX) that are not open for editing.
	
	WORKAROUND
	==========
	
	To isolate the source of the error, instantiate the object from the Command
	window. Additionally, if the .PRG or .VCX file that contains the class
	definition is not in the current directory, issue a SET PATH command to set a
	path to the source file. When the error occurs, the procedure file will be
	opened in the Trace window, and the line of code that contains the error will be
	highlighted.
	
	STATUS
	======
	
	This behavior is by design.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Include the following lines in a .PRG file, and save it as PRGTEST.
	
	     DEFINE CLASS claserror as CUSTOM
	        Myprop "test"  && The equal sign is omitted
	     ENDDEFINE
	
	2. Create a Form.
	
	3. Right-click, and from the popup, select Code. Select the Init event handler
	  and type this code:
	
	     SET PROCEDURE TO PRGTEST
	     This.AddObject('oerror','claserror')  && To add the object
	
	4. Attempt to save the form. The error "Unrecognized Command Verb" is displayed,
	  and the lines that contain This.Addobject is highlighted. The highligted line
	  is, however, correct.
	
	5. To find the line that causes the problem, type the following lines in the
	  Command window:
	
	     SET PROCEDURE TO PRGTEST
	     oerror=CREATEOBJECT('claserror')
	
	Additional query words: VFoxWin debug 3.00
	
	======================================================================
	Keywords          : kberrmsg 
	Technology        : kbVFPsearch kbAudDeveloper kbVFP300
	Version           : WINDOWS:3.0
	
	=============================================================================
	

{% endraw %}
