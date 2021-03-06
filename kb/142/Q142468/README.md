---
layout: page
title: "Q142468: FIX: Adding Subitems To Hidden ListView Causes APP Error"
permalink: /kb/142/Q142468/
---

## Q142468: FIX: Adding Subitems To Hidden ListView Causes APP Error

{% raw %}

	Article: Q142468
	Product(s): Microsoft Visual Basic for Windows
	Version(s): WINDOWS:4.0
	Operating System(s): 
	Keyword(s): kbCtrl kbVBp kbVBp400bug kbVBp500fix kbGrpDSVB kbDSupport
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Professional Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Enterprise Edition, 32-bit, for Windows, version 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	A 32-bit Visual Basic application with a ListView control can generate an
	application error or incorrectly display the subitems if the subitems are added
	to a ListView control that is hidden on a form.
	
	RESOLUTION
	==========
	
	To eliminate this behavior, use one of the following methods:
	
	If you want your ListView control in the form to be hidden when the form is
	shown, toggle the Visible property once before adding the subitems to the
	ListView control. To toggle the Visible property, initially set the Visible
	property to True and then reset the Visible property to False.
	
	-or-
	
	At design time, set the ListView control Visible property to True. Then in the
	first line of code in the form's Load procedure, set the ListView control
	Visible property to False.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article. This bug has been fixed in Visual Basic 5.0.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Issue
	------------------------
	
	1. Start the 32-bit version of Visual Basic 4.0, or if it is already running,
	  click New Project on the File menu.
	
	2. Add the following controls to the Form1 form:
	
	  1. One Check Box
	
	  2. Two Image List Boxes
	
	  3. One ListView Control
	
	3. Set the Caption property of the Check box to "ListView Control Visible."
	
	4. Copy the following code to the Code window of the Form1 form:
	
	        Private Sub Check1_Click()
	
	           ListView1.Visible = Check1.Value = 1
	
	        End Sub
	
	        Private Sub Form_Load()
	
	           'Set the ListView control's Column Headers
	           Dim clmX As ColumnHeader
	           Set clmX = ListView1.ColumnHeaders.Add(, , "Author", _
	                      ListView1.Width / 3)
	           Set clmX = ListView1.ColumnHeaders.Add(, , "Author ID", _
	                      ListView1.Width / 3, lvwColumnCenter)
	           Set clmX = ListView1.ColumnHeaders.Add(, , "Birthdate", _
	                      ListView1.Width / 3)
	
	           'Set the ListView control's view property to show a "Report" view
	           ListView1.View = lvwReport
	
	           'Add ListItems to the ListView control
	           'Use an icon file and a bitmap file that comes with Visual Basic
	            Dim imgX As ListImage
	            Set imgX = ImageList1.ListImages.Add(, , LoadPicture _
	                       ("C:\VB\ICONS\WRITING\NOTE06.ICO"))
	            Set imgX = ImageList2.ListImages.Add(, , LoadPicture _
	                       ("C:\VB\REPORT\PROLOGOB.BMP"))
	            ListView1.Icons = ImageList1
	            ListView1.SmallIcons = ImageList2
	
	            Set itmX = ListView1.ListItems.Add(, , "John Doe")
	            itmX.SubItems(1) = "John Dow Sub item"
	
	        End Sub
	
	5. Press the F5 key to run the application.
	
	6. Click the check box. One of the following behaviors occur:
	
	  While using Microsoft Windows NT version 3.51, the following error is
	  returned:
	
	  An application error has occurred and an application error log is being
	  generated. VB32.exe. Exception: access violation (0xc0000005), Address:
	  0x0523ca55.
	
	  While using Microsoft Windows 95, the following error is returned:
	
	  VB32 caused an invalid page fault in module COMCTL32.OCX at 0137:0523ca55.
	
	  -or-
	
	  The ListView control incorrectly displays the subitems.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbCtrl kbVBp kbVBp400bug kbVBp500fix kbGrpDSVB kbDSupport 
	Technology        : kbVBSearch kbAudDeveloper kbVB400Search kbVB400
	Version           : WINDOWS:4.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
