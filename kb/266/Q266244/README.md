---
layout: page
title: "Q266244: HOWTO: Create Full-Screen Applications for the PocketPC"
permalink: /kb/266/Q266244/
---

## Q266244: HOWTO: Create Full-Screen Applications for the PocketPC

{% raw %}

	Article: Q266244
	Product(s): Microsoft C Compiler
	Version(s): WINDOWS:3.0
	Operating System(s): 
	Keyword(s): kbDSupport kbGrpDSETK
	Last Modified: 09-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft eMbedded Visual C++ version 3.0, used with:
	   - Microsoft Windows CE Platform SDK for Pocket PC 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The documentation clearly describes how to use the SHFullScreen API in a
	non-Microsoft Foundation Class (MFC) Win32 application to create full-screen
	windows on the PocketPC. However, the documentation does not describe the same
	procedure for MFC-based applications. This article describes how to make
	full-screened applications for the PocketPC by using either the Win32 API or
	MFC.
	
	MORE INFORMATION
	================
	
	For applications that target Windows CE, it has become popular to use as much of
	the screen of the smaller Palm-sized devices as possible. The new user interface
	(UI) of the PocketPC platform requires additional work for an application to use
	the entire screen area.
	
	To understand the comments in the code examples in the article, the new PocketPC
	UI terms are described:
	
	- The taskbar is located at the top of the screen, displays application
	  captions, and gives the user access to start applications.
	
	- The command bar, also known as the menu bar, is located at the bottom of the
	  screen.
	
	- The soft input panel (SIP) button is located on the command bar, to the
	  lower-right corner of the screen.
	
	To achieve a window that uses as much screen as possible, the application calls
	SHFullScreen to hide these elements.
	
	NOTE: To make dialog boxes full-screen, if the dialog box has any controls with
	the WS_TABSTOP style set, SHFullScreen will not hide the SIP button. If you
	notice that the SIP button unexpectedly cannot be hidden, see the dialog box
	resources in the resource editor and view the properties dialog box for each of
	the controls. Verify that the Tab Stop check box is not selected for all
	controls.
	
	For a plain Win32 application that uses the CreateWindow or CreateWindowEx
	function for its main UI, call SHFullScreen to hide the imposing UI elements to
	enable complete full-screen coverage, call the ShowWindow function to hide the
	application's command bar, and then adjust the window's size by using the
	MoveWindow function.
	
	The sample code below illustrates this method. This code has been adapted from
	the SHAPI Win32 Pocket PC SDK sample.
	
	        #define MENU_HEIGHT 26
	        RECT rc;
	
	        //get window size
	        GetWindowRect(hWnd, &rc);
	
	        SHFullScreen(hWnd, SHFS_HIDETASKBAR | SHFS_HIDESIPBUTTON);
	        ShowWindow(hwndCB, SW_HIDE);
	
	        MoveWindow(hWnd, 
	  		  rc.left, 
	  		  rc.top-MENU_HEIGHT, 
	  		  rc.right, 
	  		  rc.bottom+MENU_HEIGHT, 
	  		  TRUE);  
	
	NOTE: If you want to restore the original size of the application, use
	SHFS_SHOWTASKBAR and SHFS_SHOWSIPBUTTON. However, MoveWindow is called with the
	bottom parameter decreased by two times the MENU_HEIGHT. For example:
	
	        // Code to revert back to not full-screen:
	        RECT rc;
	        GetWindowRect(hWnd, &rc);
	        SHFullScreen(hWnd, SHFS_SHOWTASKBAR | SHFS_SHOWSIPBUTTON);
	        ShowWindow(hwndCB, SW_SHOW);
	        MoveWindow(hWnd, 
	           rc.left, 
	           rc.top+MENU_HEIGHT, 
	           rc.right, 
	           rc.bottom-(2*MENU_HEIGHT), 
	             TRUE);  
	
	For a Win32 application dialog box, the SHInitDialog function is used in the
	handler for WM_INITDIALOG. SHInitDialog is used in conjunction with the
	SHFullScreen function to hide the UI elements and achieve a full-screen dialog
	box:
	
	       case WM_INITDIALOG:
	
	  #define MENU_HEIGHT 26
	        SHINITDLGINFO shidi;
	        RECT rc;
	    
	        shidi.hDlg = hDlg;
	        shidi.dwMask = SHIDIM_FLAGS;
	        shidi.dwFlags = SHIDIF_FULLSCREENNOMENUBAR;
	    
	        SHInitDialog(&shidi);
	
	        GetWindowRect(hDlg, &rc);
	        MoveWindow(hDlg, 
	           rc.left, 
	           rc.top-MENU_HEIGHT, 
	           rc.right, 
	           rc.bottom,
	         TRUE);
	
	        SetForegroundWindow(hDlg);
	        SHFullScreen(hDlg, SHFS_HIDETASKBAR | SHFS_HIDESIPBUTTON);
	
	The following discusses how to perform similar tasks from within MFC
	applications. There are two main types of MFC applications for Windows CE,
	dialog-based and SDI or Document/View support applications. To accomplish what
	the SHAPI Win32 sample demonstrates, you must access data members of MFC
	classes.
	
	The following illustrates the process for a Document/View type of application.
	This code is for a command handler that will put the application in full-screen
	mode:
	
	  void CMainFrame::OnFullscreen() 
	  {
	        #define MENU_HEIGHT 26
	        RECT rc;
	
	        //get window size
	        GetWindowRect(&rc);
	
	        ::SHFullScreen(m_hWnd, SHFS_HIDETASKBAR | SHFS_HIDESIPBUTTON);
	        ::ShowWindow(this->m_hCommandBar, SW_HIDE);
	
	        MoveWindow(rc.left, 
	  		  rc.top-MENU_HEIGHT, 
	  		  rc.right, 
	  		  rc.bottom+MENU_HEIGHT, 
	  		  TRUE);	
	  }
	
	If a dialog box is to be displayed to cover the entire screen, similar code is
	placed in the OnInitDialog handler. One difference is that the MFC framework for
	PocketPC creates an empty command bar in CDialog that must be hidden:
	
	  BOOL CMfctest2Dlg::OnInitDialog()
	  {
	     m_bFullScreen = FALSE;
	     CDialog::OnInitDialog();
	
	     // Call SHInitDialog with flags for full screen.
	     SHINITDLGINFO shidi;
	
	     shidi.dwMask = SHIDIM_FLAGS;
	     shidi.dwFlags = SHIDIF_FULLSCREENNOMENUBAR;
	     shidi.hDlg = m_hWnd;
	     SHInitDialog(&shidi);
	
	     // Set the icon for this dialog box. The framework does this automatically
	     //  when the application's main window is not a dialog box.
	     SetIcon(m_hIcon, TRUE);   // Set big icon.
	     SetIcon(m_hIcon, FALSE);  // Set small icon.
	
	  // TODO: Add extra initialization here.
	     ::CommandBar_Show(m_pWndEmptyCB->m_hWnd, FALSE);
	
	     // SHFullScreen fails if dialog box is not foreground.
	     SetForegroundWindow();  
	     SHFullScreen(m_hWnd, SHFS_HIDETASKBAR | SHFS_HIDESIPBUTTON);
	
	     // Resize the window over the taskbar area.
	  #define MENU_HEIGHT 26
	     RECT rect;
	     GetWindowRect(&rect);
	     rect.top -= MENU_HEIGHT;
	     MoveWindow(&rect, TRUE);
	  	
	     return TRUE;
	  }
	
	Additional query words:
	
	======================================================================
	Keywords          : kbDSupport kbGrpDSETK 
	Technology        : kbVCsearch kbAudDeveloper kbWinCEETKSearch
	Version           : WINDOWS:3.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
