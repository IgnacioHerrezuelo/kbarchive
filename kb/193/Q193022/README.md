---
layout: page
title: "Q193022: HOWTO: Set ActiveX Procedure and User Interface Defaults"
permalink: /kb/193/Q193022/
---

## Q193022: HOWTO: Set ActiveX Procedure and User Interface Defaults

{% raw %}

	Article: Q193022
	Product(s): Microsoft Visual Basic for Windows
	Version(s): WINDOWS:5.0,6.0
	Operating System(s): 
	Keyword(s): kbGrpDSVB
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Learning Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Professional Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, versions 5.0, 6.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The purpose of this article is to summarize and clarify the information
	presented in the Visual Basic documentation regarding the use of the Procedure
	Attributes dialog. Specifically, it clarifies the expected behavior of the User
	Interface Default as it applies to the Properties window, and explains the
	difference between the Default Procedure ID and the User Interface Default
	settings.
	
	MORE INFORMATION
	================
	
	The Visual Basic Help states that the User Interface Default (UI Default)
	"Determines which property is highlighted in the property browser ..." The
	following steps describe the behavior of Visual Basic for UI Default
	properties:
	
	1. When a control is selected in design-mode, Visual Basic checks if the user
	  has highlighted any property for the previously selected control. If the
	  highlighted property is available for the selected control, that property
	  will be highlighted. Otherwise, the property marked as UI Default will be
	  highlighted.
	
	2. When Visual Basic is started, the property window always highlights the "UI
	  Default" property. As new controls are added, the "UI Default" property for
	  each control will be highlighted unless the user explicitly selects some
	  other property.
	
	Step-by-Step Example
	--------------------
	
	1. Start a new Visual Basic Standard EXE project. Form1 is created by default.
	  Click on Form1. The property highlighted is "Caption," which is "UI Default"
	  for Form.
	
	2. Add a TextBox, Text1, to Form1. Now, the highlighted property is "Text,"
	  which is the "UI Default" for a TextBox.
	
	3. Add a PictureBox to Form1. Now, the highlighted property is "Picture," and it
	  is the "UI Default."
	
	4. Click on the Form, TextBox, etc., and note that the UI Default is
	  automatically highlighted.
	
	5. Click on Text1. The "Text" property is highlighted. Click on the Name
	  property to select it.
	
	6. Click on other controls and note that the Name property is highlighted for
	  all the controls.
	
	7. Click on Text1 and select the "Alignment" property. Select other controls. If
	  the previously selected property is available, that property will be
	  highlighted. Otherwise, the UI Default property is highlighted.
	
	  This is not intended to confuse, only to point out that the highlighted
	  property in the properties window will vary depending on the state of the
	  IDE, and a property defined as the UI Default will not always be highlighted.
	
	Difference Between Default Procedure ID and User Interface Default
	------------------------------------------------------------------
	
	When you display the Procedure Attributes dialog and press the Advanced button,
	you will see a combo box titled "Procedure ID" and a check box with the
	description "User Interface Default." These fields serve two different purposes;
	the Procedure ID settings are for run-time and the User Interface Default is a
	design-time setting.
	
	The Default setting for Procedure ID is available for Properties or Methods, but
	not for Events. You may have only one Procedure specified as "Default" per
	component. What a default Procedure ID setting means is that the default method
	or property will be executed when no specific member is specified. For example,
	the following statement on the client form will cause the default method of the
	UserControl (in this case a Subroutine) to execute:
	
	     UserControl11
	
	The following line of code will cause the default property of the control to be
	set to the string "This is my control," assuming the default property will
	accept one:
	
	     UserControl11 = "This is my control"
	
	The User Interface Default setting is available for Events or Properties, but not
	for Methods. You can have one UI Default property and one UI Default event per
	component. The purpose of the UI Default for a property is to determine which
	property is displayed in the properties window at design-time when the control
	is selected or placed on a form, subject to the behavior discussed earlier in
	this article. The purpose of the UI Default for an event is to specify which
	event procedure should appear when you double-click on the control. This applies
	to the control when it is seated on a form, not to the control itself.
	
	NOTE: If you are changing User Interface Default properties and they don't seem
	to be taking effect, run the form and then go back into design mode and test
	again. The UI Defaults, particularly the event default that determines which
	event procedure is displayed when double-clicking, may not get refreshed until
	the form has been run.
	
	Additional query words: kbDSupport kbDSD kbVBp kbVBp500 kbVBp600 kbActiveX kbUsage
	
	======================================================================
	Keywords          : kbGrpDSVB 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB500Search kbVB600Search kbVBA500 kbVBA600 kbVB500 kbVB600
	Version           : WINDOWS:5.0,6.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
