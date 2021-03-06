---
layout: page
title: "Q169611: BUG: OLE AutoActivate Property Fails When Set To &quot;1 - GotFocus&quot;"
permalink: /kb/169/Q169611/
---

## Q169611: BUG: OLE AutoActivate Property Fails When Set To &quot;1 - GotFocus&quot;

{% raw %}

	Article: Q169611
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 
	Operating System(s): 
	Keyword(s): kbVBp400bug kbVBp500bug kbVBp600bug kbGrpDSVB
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Control Creation Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Learning Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Professional Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Standard Edition for Windows, version 4.0 
	- Microsoft Visual Basic Professional Edition for Windows, version 4.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	The Visual Basic OLE Container Control has an AutoActivate property that enables
	a user to activate an OLE object in different ways. Setting this property to "1
	- GetFocus" does not automatically activate the application that provides the
	OLE object when the OLE container control receives the focus.
	
	RESOLUTION
	==========
	
	To work around this bug, code needs to be added to the OLE Container Control's
	GotFocus event to automatically activate the application that provides the OLE
	object when the control receives the focus. The following code makes the OLE
	Container Control behave as though its AutoActivate property were set to "1 -
	GotFocus":
	
	     Private Sub OLE1_GotFocus()
	        OLE1.DoVerb (vbOLEShow)
	     End Sub
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article. We are researching this bug and will post new
	information here in the Microsoft Knowledge Base as it becomes available.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Start a new Standard EXE project. Form1 is added by default.
	
	2. Add an OLE Container control (OLE1) to Form1 and add any OLE Object to the
	  container control.
	
	3. Set the OLE Container control's AutoActivate property to "1 - GetFocus."
	
	4. Press the F5 key to run the program. When the OLE Container control receives
	  focus it will not AutoActivate.
	
	To see the behavior that should occur when the OLE Container control receives the
	focus, change the AutoActivate property to "2 - DoubleClick" and run the form or
	implement the workaround provided above.
	
	REFERENCES
	==========
	
	For more information about the DoVerb method of OLE Container control search the
	on-line Help for the topic "DoVerb."
	
	Additional query words: kbole
	
	======================================================================
	Keywords          : kbVBp400bug kbVBp500bug kbVBp600bug kbGrpDSVB 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB500Search kbVB600Search kbVBA500Search kbVBA500 kbVBA600 kbVB500 kbVB600 kbVB400Search kbVB400 kbZNotKeyword3
	Issue type        : kbbug
	
	=============================================================================
	

{% endraw %}
