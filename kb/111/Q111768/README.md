---
layout: page
title: "Q111768: PRB: Control Bar Not Visible After Calling Create"
permalink: /kb/111/Q111768/
---

## Q111768: PRB: Control Bar Not Visible After Calling Create

{% raw %}

	Article: Q111768
	Product(s): Microsoft C Compiler
	Version(s): winnt:2.0,2.1,4.0
	Operating System(s): 
	Keyword(s): kbMFC kbToolbar KbUIDesign kbVC kbGrpDSMFCATL kbMFCCtrlBar
	Last Modified: 07-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- The Microsoft Foundation Classes (MFC), used with:
	   - Microsoft Visual C++ for Windows, 16-bit edition, versions 1.0, 1.5, 1.51, 1.52 
	   - Microsoft Visual C++, 32-bit Editions, versions 2.0, 2.1, 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	A control bar is not immediately visible after a call to Create. The control bar
	becomes visible only when the parent window is resized (or minimized\maximized).
	This behavior is true for all the built-in framework classes derived from
	CControlBar:
	
	     CDialogBar
	     CToolBar
	     CStatusBar
	
	CAUSE
	=====
	
	A control bar is initially placed at position (0,0) with size (0,0) so that the
	parent frame can control the size and position. The size and position are
	recomputed when a call is made to RecalcLayout. If a call is made to Create,
	then the control bar will not become visible until RecalcLayout is called for
	the parent frame window. The control bar becomes visible when the main frame
	window is resized, because CFrameWnd has a WM_SIZE handler that calls
	RecalcLayout.
	
	RESOLUTION
	==========
	
	Use one of the following to resolve this issue:
	
	- If the control bar is ALWAYS going to be attached to the frame window when it
	  is created, then create the control bar once in the OnCreate message handler
	  for the frame window. This would apply to the main frame window of an SDI
	  (CFrameWnd) or MDI (CMDIFrameWnd) application, or to an MDI Child Window
	  (CMDIChildWnd).
	
	- If the control is to be created dynamically (for example, a toolbar that
	  pops-up only under certain circumstances), make a call to RecalcLayout for
	  the parent frame window to cause the control bar to be properly resized and
	  drawn.
	
	MORE INFORMATION
	================
	
	There are two code segments below that show how to create a CDialogBar attached
	to a CMDIChildWnd. The first sample creates a CDialogBar as soon as the child
	window is created (that is, the child window always has the dialog bar). The
	second sample shows a function that will properly create and display a dialog
	bar at any time.
	
	Sample Code
	-----------
	
	     /* Compile options needed: None
	        Sample 1 - Override OnCreate.
	     
	        Note that the dialog template is called IDD_CHILDBAR
	        and that CMyMDIChild has a member variable declaration:
	        CDialogBar m_dlgbar;
	     */ 
	     int CMyMDIChild::OnCreate(LPCREATESTRUCT lpCreateStruct)
	     {
	          if (CMDIChildWnd::OnCreate(lpCreateStruct) == -1)
	               return -1;
	     
	         m_dlgbar.Create(this,IDD_CHILDBAR,CBRS_TOP,115);
	     
	          return 0;
	     }
	     
	     /*
	       Sample 2 - Creating a dialog bar at any time.
	       Note that the dialog template is called IDD_CHILDBAR
	       and that CMyMDIChildWnd has a member variable declaration:
	       CDialogBar *m_pdlgbar;
	     */ 
	     void CMyMDIChild::CreateDialogBar()
	     {
	         m_pDlgBar = new CDialogBar();
	         m_pDlgBar->Create(this,IDD_CHILDBAR,CBRS_TOP,115);
	         RecalcLayout();
	     }
	
	Because you are allocating a CDialogBar object, you need to call delete m_pDlgBar
	when you close the application or there will be a memory leak.
	
	Additional query words: WM_SIZE CRect tool bar status tool-bar status-bar statusbar
	
	======================================================================
	Keywords          : kbMFC kbToolbar KbUIDesign kbVC kbGrpDSMFCATL kbMFCCtrlBar 
	Technology        : kbAudDeveloper kbMFC
	Version           : winnt:2.0,2.1,4.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
