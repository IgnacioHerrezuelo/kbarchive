---
layout: page
title: "Q130835: Class Browser: How to Save Data to a File"
permalink: /kb/130/Q130835/
---

## Q130835: Class Browser: How to Save Data to a File

{% raw %}

	Article: Q130835
	Product(s): Microsoft FoxPro
	Version(s): 3.0
	Operating System(s): 
	Keyword(s): kbvfp
	Last Modified: 15-FEB-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, Professional Edition, version 3.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The Class Browser is a tool provided with the Professional Edition of Visual
	FoxPro. It allows you to browse and perform diverse tasks on classes stored in
	visual class libraries (.VCX files). In particular, you can use the Class
	Browser to save the source code for class definitions to a program file.
	
	MORE INFORMATION
	================
	
	Saving the source code of a visual class definition to a program file might be
	useful when debugging an application. The EXPORTCLASS() method of the Class
	Browser generates and displays the definition source code of a selected class.
	
	You can save this information to a program file (.PRG). The EXPORTCLASS method is
	called when you choose the View Class Code button in the Class Browser. You can
	also call it interactively, or customize the Class Browser to prompt a Save As
	dialog to save information to a file. These two methods are described below.
	
	NOTE: Attempting to run the .prg file may create an error. Not all of the code
	exported to the .prg file is directly supported by the Visual FoxPro language.
	The ExportClass method is not intended to create program code for a class
	definition. Its purpose is to allow you to view how the class is defined. In
	particular, the type of objects that will not work when the code from the Class
	Browser is exported to a program file are container type objects that contain
	other objects. For example, if you create a grid and change the ColumnCount
	property to something other than -1, and use the Class Browser to export the
	code to a .prg file, you will receive an "Syntax Error" message when trying to
	run the .prg file. This happens because there is a set number of columns,
	headers, and text boxes assigned to the grid. If the ColumnCount is left at -1,
	the grid will properly populate itself from the table dynamically. The same
	thing happens with a PageFrame. If the code for the PageFrame is copied to a
	.prg file and there are no objects on the PageFrame, then the code works
	properly. Adding an object to the PageFrame and then copying the code to a .prg
	file causes the "Syntax Error" message.
	
	Method One: Use the ExportClass Method Interactively
	----------------------------------------------------
	
	1. Choose Class Browser from the Tools menu to start the Class Browser.
	
	2. Select the visual class library, and select the class.
	
	3. From the Command window, type:
	
	     lcCode=_oBrowser.ExportClass()
	
	4. To save the information to a file, use this code:
	
	        SET PRINT TO TESTCLASS.PRG
	        SET PRINT ON
	        ?lcCode
	        SET PRINT TO
	        SET PRINT OFF
	
	Method Two: Create an Add-in to Customize the View Class Definition Button
	--------------------------------------------------------------------------
	
	WARNING: If you use the following information to customize the Class Browser,
	your customized Class Browser may no longer be supported by Microsoft.
	
	You can create an add-in that will extend the functionality of the View Class
	Definition button. To execute this add-in, right-click the View Class definition
	button. The code is displayed in a window, and the SaveAs dialog is displayed to
	save the code to a program file. Sample code for the add-in is included below.
	
	For more information about the ExportClass and the Addin methods of the Class
	Browser, please search for "Class Browser Methods" in the Help menu.
	
	How to Install or Remove the Add-In
	-----------------------------------
	
	To install the add-in:
	
	1. Start the Class Browser.
	
	2. Type the following code in the Command window:
	
	        _oBrowser.AddIn('Export SaveAs','exportsv','cmdExport.RightClick')
	
	Exportsv is the name of the program to execute when the RightClick event is
	triggered.
	
	To remove the add-in, type the following code in the Command window:
	
	     _oBrowser.AddIn('Export SaveAs',.NULL.)
	
	Sample Code for the Add-In
	--------------------------
	
	     *  EXPORTSV.PRG
	     *  After installing the add-in, right-click the mouse on the View Class
	     *  Definition button.
	     *
	     *  You can also link this code to the Click event handler rather than
	     *  the Right-click event handler. Change the install method
	     *  parameter passed to AddIn() to 'cmdExport.Click' and then add
	     *  oSource.lNoDefault=.T. to the program below.
	
	     LPARAMETERS oSource
	     LOCAL lcCode,lcFileName,lnLastSelect
	
	     *-- Execute export class method.
	     *-- Note:  If you don't want the code to be displayed in the window,
	     *          don't pass the .T. parameter.
	     lcCode=oSource.ExportClass(.T.)
	
	     IF EMPTY(lcCode)        &&& No code was generated
	        RETURN
	     ENDIF
	
	     *-- Get file to save the generated class code to.
	     lcFileName=GETFILE('prg')
	     IF EMPTY(lcFileName)    &&& No file was selected or entered.
	             RETURN
	     ENDIF
	
	     *-- Create a cursor to save the generated string to a file.
	     lnLastSelect=SELECT()
	     IF USED('tempexport')
	          USE IN tempexport
	     ENDIF
	     CREATE CURSOR tempexport (mCode M)
	     INSERT INTO tempexport (mCode) ;
	                  VALUES (lcCode)
	     COPY MEMO mCode TO (lcFileName)
	     IF USED('tempexport')
	          USE IN tempexport
	     ENDIF
	     SELECT (lnLastSelect)
	     RETURN
	
	Additional query words:
	
	======================================================================
	Keywords          : kbvfp 
	Technology        : kbVFPsearch kbAudDeveloper kbVFP300
	Version           : :3.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
