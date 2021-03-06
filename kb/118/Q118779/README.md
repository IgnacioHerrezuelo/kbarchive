---
layout: page
title: "Q118779: Calling Microsoft Excel Macro from FoxPro for Macintosh"
permalink: /kb/118/Q118779/
---

## Q118779: Calling Microsoft Excel Macro from FoxPro for Macintosh

{% raw %}

	Article: Q118779
	Product(s): Microsoft FoxPro
	Version(s): MACINTOSH:2.5b,2.5c,3.0b
	Operating System(s): 
	Keyword(s): kbcode
	Last Modified: 11-FEB-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Macintosh, version 3.0b 
	- Microsoft FoxPro for Macintosh, versions 2.5b, 2.5c 
	-------------------------------------------------------------------------------
	
	
	SUMMARY
	=======
	
	When you are developing an application in FoxPro for Macintosh, you may
	sometimes need to tap into the functionality of another application. This
	article demonstrates how to execute a macro written in Microsoft Excel version
	4.0 for Macintosh and return a result.
	
	MORE INFORMATION
	================
	
	To run a Microsoft Excel macro, three components are necessary: the Microsoft
	Excel macro, the AppleScript script, and the FoxPro Command window.
	
	To create a simple Microsoft Excel macro that fills in the first 50 cells of the
	first column of a worksheet, do the following:
	
	1. In Microsoft Excel, open a new worksheet.
	
	2. Open a new macro sheet.
	
	3. Beginning in cell A1 of the macro sheet, enter the following commands:
	
	        =FOR("counter",1,50)
	        =FORMULA(counter)
	        =SELECT(,"R[1]C")
	        =NEXT()
	        =SELECT(,"R[-1]C")
	        =RETURN(CELL("contents"))
	
	  NOTE: The macro must return a value or the following error message will
	  occurs:
	
	        Microsoft Excel got an error:
	        "RUN(\"FILLCOL!FILLCOL\")" doesn't
	        understand the do script message.
	
	4. Define the name FILLCOL for the macro. To define a name for a macro, select
	  the first cell of the macro, in this case A1, and choose Define Name from the
	  Formula menu. In the Define Name dialog box, type the name FILLCOL and select
	  the Command option button at the bottom of the dialog box.
	
	5. Save the macro sheet with the name FILLCOL.
	
	To create the AppleScript, do the following:
	
	1. Open the AppleScript Script Editor.
	
	2. Enter the following code for the script:
	
	        tell application "Macintosh HD:Excel:Microsoft Excel"
	           make new document
	           set retVal to Evaluate "RUN(\"FILLCOL!FILLCOL\")"
	           return (retVal as string)
	        end tell
	
	3. Save the script with the name RunXLMacro and close it.
	
	In the FoxPro Command window, execute the following commands:
	
	     RUNSCRIPT RunXLMacro TO ret
	     WAIT WINDOW ret
	
	The macro is executed synchronously. This means that control is not returned to
	the user until after the macro has completed execution. If the FoxPro desktop
	and Command windows are not maximized, you should see the macro execute in the
	background, filling in the first fifty cells of a new worksheet with the numbers
	1 through 50. If you can't see the macro executing, switch to Microsoft Excel
	once control returns to FoxPro and look at the new worksheet.
	
	REFERENCES
	==========
	
	Microsoft Excel "Function Reference"
	
	Additional query words: vFoxMac FoxMac Ascript Apple Script Scripting
	
	======================================================================
	Keywords          : kbcode 
	Technology        : kbHWMAC kbOSMAC kbVFPsearch kbAudDeveloper kbFoxproSearch kbFoxPro250bMac kbFoxPro250cMac kbVFP300bMac
	Version           : MACINTOSH:2.5b,2.5c,3.0b
	
	=============================================================================
	

{% endraw %}
