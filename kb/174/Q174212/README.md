---
layout: page
title: "Q174212: FIX: ActiveForm Returns Wrong Form"
permalink: /kb/174/Q174212/
---

## Q174212: FIX: ActiveForm Returns Wrong Form

{% raw %}

	Article: Q174212
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 
	Operating System(s): 
	Keyword(s): kbGrpDSVB
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Control Creation Edition for Windows, version 5.0 
	- Microsoft Visual Basic Learning Edition for Windows, version 5.0 
	- Microsoft Visual Basic Professional Edition for Windows, version 5.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 5.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When the ActiveForm property of the Screen object is queried, the wrong form is
	returned as the active form. This behavior occurs after setting the enabled
	property of a Command button on another form to False. The second form is listed
	as the active form, when the form with the calling code is actually the active
	form.
	
	RESOLUTION
	==========
	
	To work around this problem, insert the following line of code immediately after
	the code that sets the enabled property of the button:
	
	     Me.SetFocus
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article. This bug has been fixed in Visual Basic 6.0.
	
	MORE INFORMATION
	================
	
	This behavior occurs only the first time the enabled property of the button is
	set to False. During subsequent attempts or if the button's enabled property is
	initially False, the problem does not occur.
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Create a new "Standard EXE" project in Visual Basic 5.0.
	
	2. Add an MDI form to the project.
	
	3. Add a standard form to the project.
	
	4. Set the MDI Child property of Form1 and Form2 to True.
	
	5. Place a Command button on Form1. Set its caption to "Disable."
	
	6. Insert the following code into the Click event of this button:
	
	        Form2.Command1.Enabled = False
	        'Me.SetFocus         'Uncomment to Workaround this Problem
	        MsgBox Screen.ActiveForm.Name
	
	7. Add a second Command button to Form1. Set its caption to "Enable."
	
	8. Insert the following code into the Click event of this button:
	
	        Form2.Command1.Enabled = True
	
	9. Add a Command button to Form2.
	
	10. Add the following code to the Load event of the MDI form:
	
	        Form1.Show
	        Form2.Show
	        MDIForm1.Arrange 1
	
	11. Run the project, and then click the button labeled "Disable." Note that the
	  message box displays "Form2" when the active form is actually Form1.
	
	12. Click the button labeled "Enable," and then click the button labeled
	  "Disable" one more time. Note that this time, "Form1" is now correctly
	  returned as the active form.
	
	Additional query words: kbVBp500bug kbVBp600fix kbVBp kbdsd kbDSupport kbVBA kbControl
	
	======================================================================
	Keywords          : kbGrpDSVB 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB500Search kbVBA500Search kbVBA500 kbVB500 kbZNotKeyword3
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
