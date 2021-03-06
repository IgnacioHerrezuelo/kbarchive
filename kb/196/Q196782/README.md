---
layout: page
title: "Q196782: BUG: WizardBar Can't Delete Functions That Return void"
permalink: /kb/196/Q196782/
---

## Q196782: BUG: WizardBar Can't Delete Functions That Return void

{% raw %}

	Article: Q196782
	Product(s): Microsoft C Compiler
	Version(s): 6.0
	Operating System(s): 
	Keyword(s): kbwizard kbide kbVC600bug kbGrpDSTools kbNoUpdate
	Last Modified: 12-FEB-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual C++, 32-bit Enterprise Edition, version 6.0 
	- Microsoft Visual C++, 32-bit Professional Edition, version 6.0 
	- Microsoft Visual C++, 32-bit Learning Edition, version 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	The WizardBar "Delete" command is available only for functions that do not
	return void.
	
	RESOLUTION
	==========
	
	Use the ClassView pane to locate the function. Right-click the function, then
	click Delete.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article.
	
	
	MORE INFORMATION
	================
	
	WizardBar is a dockable toolbar that extends ClassView functionality by
	"tracking" your keyboard focus. It accesses features from ClassWizard and
	ClassView functions. You may select a class or function and navigate to its
	declaration or definition. WizardBar also offers a Delete command to remove both
	of a function's declaration and definition. However, this command does not
	appear on the right-click context menu if the function returns void.
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. From the File menu, click New; click the Projects tab and select MFC
	  AppWizard (exe) from the Projects list. Give it a name and click OK; here it
	  is called WizBug. Click Finish, then click OK to confirm and load the
	  project.
	
	2. Make the WizardBar visible: right-click any blank space in the menu region,
	  and select WizardBar if it is not already checked.
	
	3. Select CWizBugApp from the first WizardBar drop-down list.
	
	4. Right-click in the WizardBar and select Add Member Function. In the Function
	  Type field, type void. In the Function Name field, type MyFun. Click OK.
	
	  NOTE: The WizBug.cpp file appears with the cursor at the beginning of MyFun's
	  definition.
	
	5. Right-click in the WizardBar.
	
	  NOTE: There is no Delete command in the context menu.
	
	6. In the WizardBar C++ Members drop-down list, select InitInstance.
	
	7. Right-click in the WizardBar.
	
	  NOTE: The Delete command now appears.
	
	To verify the resolution:
	
	1. Expand WizBug classes in the ClassView pane by clicking on the +.
	
	2. Expand CWizBugApp in the ClassView pane.
	
	3. Right-click MyFun. Click Delete. Click OK the confirmation dialog box.
	
	Additional query words: kbDSupport
	
	======================================================================
	Keywords          : kbwizard kbide kbVC600bug kbGrpDSTools kbNoUpdate 
	Technology        : kbVCsearch kbAudDeveloper kbVC600 kbVC32bitSearch
	Version           : :6.0
	Issue type        : kbbug
	Solution Type     : kbnofix
	
	=============================================================================
	

{% endraw %}
