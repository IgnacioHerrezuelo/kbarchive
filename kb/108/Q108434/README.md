---
layout: page
title: "Q108434: FIX: CSplitterWnd Class Does Not Handle All Focus Cases"
permalink: /kb/108/Q108434/
---

## Q108434: FIX: CSplitterWnd Class Does Not Handle All Focus Cases

{% raw %}

	Article: Q108434
	Product(s): Microsoft C Compiler
	Version(s): winnt:1.0
	Operating System(s): 
	Keyword(s): kbMFC KbUIDesign kbVCkbbuglist kbfixlist
	Last Modified: 07-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- The Microsoft Foundation Classes (MFC), used with:
	   - Microsoft Visual C++ for Windows, 16-bit edition, version 1.0 
	   - Microsoft Visual C++, 32-bit Editions, version 1.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	A view displayed in a splitter window (CSplitterWnd) loses focus when the
	splitter bar is clicked. A user would expect the focus to be returned to the
	active view when the user stops dragging the splitter bar and releases the mouse
	button.
	
	CAUSE
	=====
	
	CSplitterWnd::StopTracking() attempts to restore the active view's keyboard
	focus by calling SetActiveView(pOldActiveView), where pOldActiveView was set to
	the currently active view on entry to the StopTracking() function. This is
	supposed to set the keyboard focus to the previously active view.
	
	The problem is that SetActiveView() fails to set the keyboard focus in the case
	where the view passed as a parameter is the same as m_pViewActive--the currently
	active view. In this case, it is assumed that the keyboard focus is already on
	the active view, and therefore the SetActiveView() function simply returns. This
	assumption is incorrect because the splitter bar gains focus, doesn't save and
	restore it, and yet leaves the frame's active view pointer the same.
	
	RESOLUTION
	==========
	
	Microsoft has confirmed this to be a problem in the Microsoft Foundation Class
	(MFC) Libraries version 2.0. This problem has been fixed in the MFC Libraries
	version 2.5, which is included in Visual C++ version 1.5 for Windows. In the
	fixed code, CSplitterWnd::StopTracking() (in WINSPLIT.CPP) is modified to
	explicitly set the focus even after calling SetActiveView(). The code is:
	
	     if (pOldActiveView == pParent->GetActiveView())
	        {
	            pParent->SetActiveView(pOldActiveView); // Re-activate.
	            if (pOldActiveView != NULL)
	                pOldActiveView->SetFocus(); // Make sure focus is restored.
	        }
	
	You can include this fix into WINSPLIT.CPP and then rebuild the MFC library by
	following the directions in Appendix B of the "Class Libraries User's Guide" as
	well as the README.TXT file located in the \MSVC\MFC\SRC directory.
	
	Another workaround for the bug is to save and restore the keyboard focus
	throughout the splitter window's tracking process. This can be done by handling
	the WM_LBUTTONDOWN and WM_LBUTTONUP messages in the CSplitterWnd class. The
	following code demonstrates how to accomplish this:
	
	     class CMySplit:public CSplitterWnd    // derive from it.
	     {
	         public:
	         // This is the pointer to the window that
	         // has focus when the splitter starts resizing.
	         HWND hWndFocus;
	
	         // ...rest of your declaration.
	     }
	
	     void CMySplit::OnLButtonDown(UINT nFlags, CPoint point)
	     {
	         //Get CWnd with current focus
	         hWndFocus = ::GetFocus();
	
	         // Remember to call the base class handler.
	         CSplitterWnd::OnLButtonDown(nFlags,point);
	     }
	
	     void CMySplit::OnLButtonUp(UINT nFlags, CPoint point)
	     {
	         //restore focus
	         ::SetFocus(hWndFocus);
	
	         // Remember to call the base class handler.
	         CSplitterWnd::OnLButtonUp(nFlags,point);
	     }
	
	The code above assumes that the focus is being set to one of the windows in the
	splitter window panes before the OnLButtonDown() handler is called. That is, you
	probably wouldn't want to set the focus back to some other window outside of the
	splitter window when the mouse button is released. You could write additional
	code to check to see if the focus is set to a window in one of the panes by
	checking the splitter's frame window's m_pActiveView variable.
	
	STATUS
	======
	
	This problem has been reported in Visual C++ version 1.0 for Windows. This
	problem has been fixed in Visual C++ version 1.5 for Windows and Visual C++ 2.0
	32-bit Edition.
	
	MORE INFORMATION
	================
	
	To demonstrate the problem, perform the following steps:
	
	1. Create an App Wizard generated application.
	
	2. Create a CSplitterWnd in a frame window with two panes that contain CEditView
	  objects.
	
	3. Build the application and run it.
	
	4. Click the mouse in the first pane of the splitter window so that the keyboard
	  focus is assigned to that pane; you'll see the caret blink there.
	
	5. Move the splitter bar to resize the panes.
	
	6. Observe that the keyboard focus is no longer on the CEditView that you
	  clicked previously.
	
	Additional query words: 1.00 2.00 2.10 splitter focus kbNoUpdate
	
	======================================================================
	Keywords          : kbMFC KbUIDesign kbVC kbbuglist kbfixlist
	Technology        : kbAudDeveloper kbMFC
	Version           : winnt:1.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
