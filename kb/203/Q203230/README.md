---
layout: page
title: "Q203230: FIX: GPF Using ATL Control Array and Accelerator Key"
permalink: /kb/203/Q203230/
---

## Q203230: FIX: GPF Using ATL Control Array and Accelerator Key

{% raw %}

	Article: Q203230
	Product(s): Microsoft Visual Basic for Windows
	Version(s): WINDOWS:5.0
	Operating System(s): 
	Keyword(s): kbATL kbCtrlCreate kbVBp500bug kbVBp600fix kbGrpDSVB
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Learning Edition for Windows, version 5.0 
	- Microsoft Visual Basic Professional Edition for Windows, version 5.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 5.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	You write an ATL control and the TranslateAccelerator of the control calls the
	TranslateAccelerator on its control site for further processing. You put an
	array of this control on the Visual Basic form. Then, you put a CommandButton
	with the Cancel property set to True and unload the form in the Click event of
	the CommandButton. You run the application in the Visual Basic integrated
	development environment (IDE). You press the Esc key when the focus is on one of
	the ATL controls and the form loads. If you run the application again, you get a
	general protection fault (GPF).
	
	This only happens in the Visual Basic 5.0 IDE. It does not occur if you run the
	application as a standalone .exe or if you run it in the Visual Basic 6.0 IDE.
	
	CAUSE
	=====
	
	When the control site is released, the control array is destroyed before the ATL
	control finished processing.
	
	RESOLUTION
	==========
	
	There is currently no known workaround for the Visual Basic 5.0 IDE. Microsoft
	recommends that programmers do not unload the form while the focus is on the ATL
	control array.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article. This bug was corrected in Visual Basic 6.0.
	
	MORE INFORMATION
	================
	
	Steps to Create the ATL control
	-------------------------------
	
	1. Open Visual C++ 6.0. On the File menu, click New, click the Projects tab, and
	  select ATL COM AppWizard from the list box.
	
	2. Type "CtlAtl" (without the quotation marks) in the Project name text box.
	  Click OK and then click Finish.
	
	3. In the Class View, right click the project name and click New ATL Object....
	  In the "Category" list box, click Controls and select the Full Control icon
	  in the Objects list view.
	
	4. Click Next, and type "TstCtl" (without the quotation marks) in the Short name
	  text box. Click the Miscellaneous tab, and select Windowed Only. Click OK to
	  add the new object.
	
	5. In the TstCtl.h file before the following lines:
	
	  };
	
	  #endif //__TSTCTL_H_
	
	  Add the following code:
	
	  STDMETHODIMP GetControlInfo(CONTROLINFO* pCI)
	  {
	     pCI->hAccel = NULL;
	     pCI->cAccel = 0;
	     pCI->dwFlags = 0;
	     return S_OK;
	  }
	
	  STDMETHODIMP TranslateAccelerator(LPMSG lpmsg)
	  {
	     HRESULT hr = S_FALSE;
	
	     CComQIPtr <IOleControlSite, &IID_IOleControlSite>
	           spSite(m_spClientSite);
	
	     if(spSite)
	     {
	        if (lpmsg->message != WM_KEYDOWN) return S_FALSE;
	
	        //call site's  TranslateAccelerator for processing
	        hr = spSite->TranslateAccelerator(
	                      lpmsg,
	                      (DWORD)_SpecialKeyState());
	     }
	     return hr;
	  }
	
	  // Helper function.
	  short _SpecialKeyState()
	  {
	     BOOL bShift = (GetKeyState(VK_SHIFT) < 0);
	     BOOL bCtrl = (GetKeyState(VK_CONTROL) < 0);
	     BOOL bAlt = (GetKeyState(VK_MENU) < 0);
	
	     return (short)(bShift + (bCtrl << 1) + (bAlt << 2));
	  }
	
	6. Build the project. The control is automatically registered.
	
	Steps to Create the Visual Basic Test Project
	---------------------------------------------
	
	1. Create a new Standard EXE project in Visual Basic 5. Form1 is created by
	  default.
	
	2. From the Project menu, click Components, click CtlAtl 1.0 Type Library, and
	  click OK.
	
	3. Add a TstCtl to Form1. Click on the control, copy it and paste it back into
	  the same form. Click Yes to create a control array.
	
	4. Add a Visual Basic CommandButton and set its Cancel property to True.
	
	5. Add the following code to the code window of Form1:
	
	  Option Explicit
	
	  Private Sub Command1_Click()
	     Unload Me
	  End Sub
	
	6. While still in the Visual Basic IDE, run the project and press the Esc key.
	
	RESULT: The form should unload correctly. Immediately run the project a second
	time and you should get an access violation.
	
	NOTE: This problem is specific to Visual Basic 5.0 when working in the IDE.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbATL kbCtrlCreate kbVBp500bug kbVBp600fix kbGrpDSVB 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB500Search kbVBA500 kbVB500
	Version           : WINDOWS:5.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
