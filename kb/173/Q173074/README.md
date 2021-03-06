---
layout: page
title: "Q173074: PRB: Multiple Visual Basic Printouts Are Not the Same"
permalink: /kb/173/Q173074/
---

## Q173074: PRB: Multiple Visual Basic Printouts Are Not the Same

{% raw %}

	Article: Q173074
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 
	Operating System(s): 
	Keyword(s): kbGrpDSVB
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Learning Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Professional Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, versions 5.0, 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you print what should be identical copies of the same print job, the pages
	do not print the same. Different fonts, text in the wrong place, and multiple
	blank pages are typical.
	
	CAUSE
	=====
	
	The primary cause of differences between print jobs is that the Visual Basic
	Printer Object is not fully reset by the EndDoc method. The values of the
	ScaleMode and a few other properties are inherited by subsequent documents
	unless the application is restarted. The most common source of problems is that
	new values are assigned to the Scale properties: (ScaleMode, ScaleHeight,
	ScaleLeft, ScaleTop, and ScaleWidth). These properties are not reset by the
	NewPage or EndDoc method and should be reset by the programmer to ensure correct
	behavior.
	
	Another cause is that changing some printer properties changes other printer
	properties in ways that are not necessarily intuitive. Changing the ScaleMode
	property affects the other Scale properties and CurrentX/Y, which need to be
	converted to the new coordinate system. Similarly, changing the ScaleLeft/Top
	properties affects the values of CurrentX/CurrentY, respectively.
	
	RESOLUTION
	==========
	
	To work around this behavior, reset the ScaleMode and other properties to their
	original values. The code below enumerates all of the properties of the printer
	object and displays their values on the Immediate pane. During your debug cycle,
	call the code before each print job and compare the results. You can then modify
	your code to correctly reset the appropriate property values:
	
	     Sub PrntProp()
	         Debug.Print "ColorMode   ", Printer.ColorMode
	         Debug.Print "Copies   ", Printer.Copies
	         Debug.Print "CurrentX   ", Printer.CurrentX
	         Debug.Print "CurrentY   ", Printer.CurrentY
	         Debug.Print "DeviceName   ", Printer.DeviceName
	         Debug.Print "DrawMode   ", Printer.DrawMode
	         Debug.Print "DrawStyle   ", Printer.DrawStyle
	         Debug.Print "DrawWidth   ", Printer.DrawWidth
	         Debug.Print "DriverName   ", Printer.DriverName
	         Debug.Print "Duplex   ", Printer.Duplex
	         Debug.Print "FillColor   ", Printer.FillColor
	         Debug.Print "FillStyle   ", Printer.FillStyle
	         Debug.Print "Font.Bold", Printer.Font.Bold
	         Debug.Print "Font.Charset", Printer.Font.Charset
	         Debug.Print "Font.Italic", Printer.Font.Italic
	         Debug.Print "Font.Name", Printer.Font.Name
	         Debug.Print "Font.Size", Printer.Font.Size
	         Debug.Print "Font.Strikethr "; Printer.Font.Strikethrough
	         Debug.Print "Font.Underline "; Printer.Font.Underline
	         Debug.Print "Font.Weight", Printer.Font.Weight
	         Debug.Print "hDC   ", Printer.hDC
	         Debug.Print "Height   ", Printer.Height
	         Debug.Print "Orientation", Printer.Orientation
	         Debug.Print "Page   ", Printer.Page
	         Debug.Print "PaperBin   ", Printer.PaperBin
	         Debug.Print "PaperSize   ", Printer.PaperSize
	         Debug.Print "Port   ", Printer.Port
	         Debug.Print "PrintQuality", Printer.PrintQuality
	         Debug.Print "RightToLeft", Printer.RightToLeft
	         Debug.Print "ScaleHeight", Printer.ScaleHeight
	         Debug.Print "ScaleLeft   ", Printer.ScaleLeft
	         Debug.Print "ScaleTop   ", Printer.ScaleTop
	         Debug.Print "ScaleWidth   ", Printer.ScaleWidth
	         Debug.Print "ScaleMode   ", Printer.ScaleMode
	         Debug.Print "TrackDefault", Printer.TrackDefault
	         Debug.Print "TwipsPerPixelX"; Printer.TwipsPerPixelX
	         Debug.Print "TwipsPerPixelY"; Printer.TwipsPerPixelY
	         Debug.Print "Width   ", Printer.Width
	         Debug.Print "Zoom   ", Printer.Zoom
	     End Sub
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	The following code is based on the example in the Visual Basic Help file. Note
	that after the Printer.EndDoc, the Printer Object Properties are not reset:
	
	      Debug.Print Printer.ScaleTop
	      Debug.Print Printer.ScaleLeft
	      Debug.Print Printer.ScaleWidth
	      Debug.Print Printer.ScaleHeight
	
	      Printer.ScaleTop = -1  ' Set scale for top of grid.
	      Printer.ScaleLeft = -1 ' Set scale for left of grid.
	      Printer.ScaleWidth = 2 ' Set scale (-1 to 1).
	      Printer.ScaleHeight = 2
	      Printer.Line (-1, 0)-(1, 0)    ' Draw horizontal line.
	      Printer.Line (0, -1)-(0, 1)    ' Draw vertical line.
	      For I = -1 To 1 Step 0.05
	          Printer.PSet (I * Rnd, I * Rnd)    ' Draw a point.
	      Next I
	      Printer.EndDoc
	
	      Debug.Print Printer.ScaleTop
	      Debug.Print Printer.ScaleLeft
	      Debug.Print Printer.ScaleWidth
	      Debug.Print Printer.ScaleHeight
	
	Additional query words: kbVBp500 kbVBp600 kbVBp kbdsd kbDSupport kbPrinting KBWIN32SDK KBAPI
	
	======================================================================
	Keywords          : kbGrpDSVB 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB500Search kbVB600Search kbVBA500 kbVBA600 kbVB500 kbVB600
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
