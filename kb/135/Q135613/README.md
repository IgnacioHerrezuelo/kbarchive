---
layout: page
title: "Q135613: FIX: Exiting Wizard-Generated Form Causes Several Errors"
permalink: /kb/135/Q135613/
---

## Q135613: FIX: Exiting Wizard-Generated Form Causes Several Errors

{% raw %}

	Article: Q135613
	Product(s): Microsoft FoxPro
	Version(s): WINDOWS:3.0
	Operating System(s): 
	Keyword(s): kbbuglist kbfixlist
	Last Modified: 24-MAR-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, version 3.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you try to exit from a wizard-generated form, the following errors occur:
	
	  FOR i=1 to m.nTablesUsed
	  Error: 27
	  Not a numeric expression
	  Method: destroy
	  Line: 52
	
	followed by:
	
	  If USED(aTablesUsed[m.i,1] AND
	  ATC(".TMP",DBF(aTablesUsed[m.i,1]))=0 &&skip for views
	  Error: 31
	  Invalid subscript reference
	  Method: destroy
	  Line: 53
	
	followed by two more error messages.
	
	CAUSE
	=====
	
	The form generated by the Form Wizard has been placed into a form set. The Form
	Wizard code is not currently designed to work in a form set.
	
	WORKAROUND
	==========
	
	Remove the form from the form set to resolve the issue.
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft products listed at
	the beginning of this article. This problem was corrected in Visual FoxPro 3.0b
	for Windows.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Problem
	--------------------------
	
	1. On the Tools menu, click Wizards and then Form.
	
	2. Within the Form Wizard, use any desired table and select any options you
	  like. On the Final step, select 'Save form and modify it in the Form
	  Designer.'
	
	3. In the Form Designer, on the Form menu, click Create Formset.
	
	4. In the Property window for Form1, change the Visible property to true (.T.).
	
	5. Save and run the form.
	
	6. Click the Exit button on the wizard-generated form, and note that the errors
	  occur.
	
	Additional query words: 3.00 VFoxWin fixlist3.00b buglist3.00
	
	======================================================================
	Keywords          :  kbbuglist kbfixlist
	Technology        : kbVFPsearch kbAudDeveloper kbVFP300
	Version           : WINDOWS:3.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
