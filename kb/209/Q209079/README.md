---
layout: page
title: "Q209079: BUG: TreeView Properties Set in Design do not Work at Run-Time"
permalink: /kb/209/Q209079/
---

## Q209079: BUG: TreeView Properties Set in Design do not Work at Run-Time

{% raw %}

	Article: Q209079
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 1.0,2.0,2.11,3.0
	Operating System(s): 
	Keyword(s): kbToolkit kbVBp600bug kbOSWinCEsearch
	Last Modified: 26-FEB-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows CE Toolkit for Visual Basic 6.0, version 1.0 
	- Microsoft eMbedded Visual Basic, version 3.0, on platform(s):
	   - Microsoft Windows CE versions 2.0, 2.11 for the Handheld PC 
	   - Microsoft Windows CE version 2.11 for the Palm-size PC 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	If either the FontBold or FontItalic property is set to True at design-time, the
	text in the TreeView does not appear as either bold or italic at run-time.
	
	RESOLUTION
	==========
	
	If the FontBold or FontItalic property is set at run-time, the text in the
	TreeView displays correctly.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Start a new Windows CE HPC Project in Visual Basic. Form1 is created by
	  default.
	
	2. From the Project menu, choose Components. In the Components dialog box, click
	  the Controls tab, then select the Microsoft CE TreeView Control 6.0.
	
	3. Add a TreeView control and a command button to Form1.
	
	4. Change the FontBold and FontItalic properties of the TreeView to True.
	
	5. Paste the following code into the code module of Form1:
	
	     Option Explicit
	
	     Private Sub Command1_Click()
	         TreeViewCtl1.FontBold = Not TreeViewCtl1.FontBold
	         TreeViewCtl1.FontItalic = Not TreeViewCtl1.FontItalic
	     End Sub
	
	     Private Sub Form_Load()
	         Dim xNod
	         Set xNod = TreeViewCtl1.Nodes.Add(, tvwFirst, "Parent", "Parent    Node")
	     End Sub
	
	6. Run the program.
	
	RESULTS: The node added to the TreeView does not appear as either bold or italic.
	However, clicking Command1 successfully sets these properties.
	
	The expected behavior is that setting either the FontBold or FontItalic property
	to True at design-time would cause the text to appear as either bold or italic.
	
	The same problem is exhibited with with the FontStrikethrough, FontUnderline and
	FontSize properties.
	
	Additional query words: kbDSupport vbce vbce6 kbGrpVB
	
	======================================================================
	Keywords          : kbToolkit kbVBp600bug kbOSWinCEsearch 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword2 kbVBeMbSearch kbWinCETKVBSearch kbWinCESearch
	Version           : :1.0,2.0,2.11,3.0
	Issue type        : kbbug
	Solution Type     : kbpending
	
	=============================================================================
	

{% endraw %}
