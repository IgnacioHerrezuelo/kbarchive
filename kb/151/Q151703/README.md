---
layout: page
title: "Q151703: FIX: Cannot Print a SourceSafe Report From Windows 95"
permalink: /kb/151/Q151703/
---

## Q151703: FIX: Cannot Print a SourceSafe Report From Windows 95

{% raw %}

	Article: Q151703
	Product(s): Microsoft SourceSafe
	Version(s): WINDOWS:4.0
	Operating System(s): 
	Keyword(s): kbSSafe400bug kbSSafe500fix
	Last Modified: 04-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual SourceSafe, 16-bit, for Windows, version 4.0 
	- Microsoft Visual SourceSafe, 32-bit, for Windows 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When attempting to print any SourceSafe reports from a Windows 95 machine, the
	output does not go to the printer. This happens although it appears that
	printing was successful since no errors are reported by Visual SourceSafe or
	Windows 95.
	
	RESOLUTION
	==========
	
	There are four alternate methods to get Visual SourceSafe reports printed.
	
	Method 1
	--------
	
	Run the report from a Windows NT or Windows 3.x machine.
	
	Method 2
	--------
	
	1. On a Windows 95 machine, in the History Report dialog box, choose Clipboard.
	
	2. Click OK to run the report. This is output to the clipboard.
	
	3. Open any other text-editing application. Paste the contents of the clipboard
	  into that application, and then print.
	
	Method 3
	--------
	
	1. On a Windows 95 machine, in the History Report dialog box, choose File.
	
	2. Click OK to run the report.
	
	3. A Report to File dialog box appears to choose file location and name.
	
	4. Open the created file in a text editor, and note that it contains the report
	  along with other ASCII characters which may interfere with proper printing.
	
	5. Remove these ASCII characters, and then print the file.
	
	Method 4
	--------
	
	1. Go to the MS-DOS prompt.
	
	2. Change to the \VSS\WIN32 folder.
	
	3. Enter the following command to print the history of file:
	
	  " "myfile.txt" in the current project:
	
	  ss history -username,password myfile.txt > lpt1:
	
	  " (without the quotation marks)
	
	NOTE: You may need to press the ENTER key twice to send the output to the
	printer.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article. This problem has been fixed in Visual SourceSafe 5.0.
	
	MORE INFORMATION
	================
	
	SourceSafe provides report capability to create reports for both projects and
	files. Reports can be directed to the printer, the clipboard, or to a file.
	
	Steps to Reproduce Problem
	--------------------------
	
	1. In the SourceSafe Explorer, highlight a file on the right side of the
	  Explorer window.
	
	2. Right-click the file, and choose Show History from the pop-up menu.
	
	3. From the History of File dialog box, select Report.
	
	4. In the History Report dialog box, place a check in Include Details. In the
	  Report to selection, choose Printer.
	
	5. Click OK to print the report.
	
	Note that there is no output on the printer an no errors appearing from Windows
	95.
	
	REFERENCES
	==========
	
	Visual SourceSafe Quick Reference Card
	
	For more information about the Visual SourceSafe history reports and printing,
	search on the keywords "Print" (without the quotation marks) and "History"
	(without the quotation marks) in the Help menu.
	
	Additional query words: missing printout
	
	======================================================================
	Keywords          : kbSSafe400bug kbSSafe500fix 
	Technology        : kbSSafeSearch kbAudDeveloper kbSSafe400 kbSSafe16bitSearch kbSSafe32bitSearch
	Version           : WINDOWS:4.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
