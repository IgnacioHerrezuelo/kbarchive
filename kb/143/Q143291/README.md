---
layout: page
title: "Q143291: HOWTO: Resize CPropertyPages at Run Time"
permalink: /kb/143/Q143291/
---

## Q143291: HOWTO: Resize CPropertyPages at Run Time

{% raw %}

	Article: Q143291
	Product(s): Microsoft C Compiler
	Version(s): 4.0,5.0,6.0
	Operating System(s): 
	Keyword(s): kbcode kbDlg kbMFC kbPropSheet KbUIDesign kbVC kbVC400 kbVC500 kbVC600 kbGrpDSMFCATL
	Last Modified: 01-APR-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- The Microsoft Foundation Classes (MFC), used with:
	   - Microsoft Visual C++, 32-bit Editions, version 4.0 
	   - Microsoft Visual C++, 32-bit Enterprise Edition, versions 5.0, 6.0 
	   - Microsoft Visual C++, 32-bit Professional Edition, versions 5.0, 6.0 
	   - Microsoft Visual C++, 32-bit Learning Edition, version 6.0 
	   - Microsoft Visual C++.NET (2002) 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	To resize CPropertyPages in a CPropertySheet at run time:
	
	1. Derive a class from CPropertySheet and override OnInitDialog().
	
	2. In OnInitDialog(), resize the CPropertySheet, CTabCtrl, and CPropertyPage(s)
	  by using MoveWindow() or SetWindowPos().
	
	3. Save the size and position of the CPropertyPage.
	
	4. Handle TCN_SELCHANGE in the CPropertySheet, and resize the page.
	
	5. Handle ID_APPLY_NOW in the CPropertySheet, and resize the page.
	
	MORE INFORMATION
	================
	
	The CPropertySheet is actually a dialog with a CTabCtrl. Each CPropertyPage is a
	child of the CPropertySheet and is only displayed inside the CTabCtrl. This is
	why we also have to resize the CTabCtrl. To get the CTabCtrl, call
	CPropertySheet::GetTabControl(). If you are changing the height of the property
	sheet, it may also be necessary to move the sheet's buttons. The "Sample Code"
	section of this article illustrates this.
	
	The CPropertySheet remembers the size and position of its CPropertyPages when
	they are first created. When a different tab is selected by the user, the
	CPropertySheet receives a TCN_SELCHANGE notification. In response to this, the
	CPropertySheet shows the new page using the size and position it had when it was
	first created. The same thing happens when the user clicks the Apply button
	(ID_APPLY_NOW). This is why we have to save the new size and position so we can
	use it to resize the pages later.
	
	Sample Code
	-----------
	
	   /* Compile options needed: default
	   */ 
	
	   // This example adds 50 pixels to the width and height of
	   // each page. CMySheet is derived from CPropertySheet. m_PageRect is a
	   // member variable of CMySheet and is of type RECT. WM_RESIZEPAGE is a
	   // user-defined message.
	
	   // ... prototypes that need to be added to your class definition
	
	   class CMySheet : public CPropertySheet
	   {
	   // ... other members
	
	   // ... make sure you have these members
	   protected:
	       RECT m_PageRect;
	       virtual BOOL OnNotify(WPARAM wParam, LPARAM lParam, LRESULT* pResult);
	       virtual BOOL OnInitDialog();
	       afx_msg LRESULT OnResizePage(WPARAM wParam, LPARAM lParam);
	       afx_msg void OnApplyNow();
	   };
	
	   // ... modify and/or implement functions in the .cpp file...
	
	   #define WM_RESIZEPAGE WM_USER + 111
	
	   BEGIN_MESSAGE_MAP(CMySheet, CPropertySheet)
	       //{{AFX_MSG_MAP(CMySheet)
	       // NOTE - the ClassWizard will add and remove mapping macros here.
	
	       // ... other message map entries
	
	       //}}AFX_MSG_MAP
	
	       // ... add the 2 following entries here
	       ON_MESSAGE (WM_RESIZEPAGE, OnResizePage)
	       ON_COMMAND (ID_APPLY_NOW, OnApplyNow)
	
	   END_MESSAGE_MAP()
	
	   BOOL CMySheet::OnInitDialog()
	   {
	       CPropertySheet::OnInitDialog();
	
	       RECT rc;
	
	       // resize the sheet
	       GetWindowRect (&rc);
	       ScreenToClient (&rc);
	       rc.right += 50;
	       rc.bottom += 50;
	       MoveWindow (&rc);
	
	       // resize the CTabCtrl
	       CTabCtrl* pTab = GetTabControl ();
	       ASSERT (pTab);
	       pTab->GetWindowRect (&rc);
	       ScreenToClient (&rc);
	       rc.right += 50;
	       rc.bottom += 50;
	       pTab->MoveWindow (&rc);
	
	       // resize the page
	       CPropertyPage* pPage = GetActivePage ();
	       ASSERT (pPage);
	       // store page size in m_PageRect
	       pPage->GetWindowRect (&m_PageRect);
	       ScreenToClient (&m_PageRect);
	       m_PageRect.right += 50;
	       m_PageRect.bottom += 50;
	       pPage->MoveWindow (&m_PageRect);
	
	       // move the OK, Cancel, and Apply buttons
	       CWnd* pWnd = GetDlgItem(IDOK);
	       pWnd->GetWindowRect(&rc);
	       rc.bottom += 50;
	       rc.top += 50;
	       ScreenToClient(&rc);
	       pWnd->MoveWindow(&rc);
	
	       pWnd = GetDlgItem(IDCANCEL);
	       pWnd->GetWindowRect(&rc);
	       rc.bottom += 50;
	       rc.top += 50;
	       ScreenToClient(&rc);
	       pWnd->MoveWindow(&rc);
	
	       pWnd = GetDlgItem(ID_APPLY_NOW);
	       pWnd->GetWindowRect(&rc);
	       rc.bottom += 50;
	       rc.top += 50;
	       ScreenToClient(&rc);
	       pWnd->MoveWindow(&rc);
	
	       CenterWindow();
	
	       return TRUE;
	   }
	
	   LONG CMySheet::OnResizePage(UINT, LONG)
	   {
	       // resize the page using m_PageRect which was set in OnInitDialog()
	       CPropertyPage* pPage = GetActivePage ();
	       ASSERT (pPage);
	       pPage->MoveWindow (&m_PageRect);
	
	       return 0;
	   }
	
	   BOOL CMySheet::OnNotify(WPARAM wParam, LPARAM lParam, LRESULT* pResult)
	   {
	       NMHDR* pnmh = (LPNMHDR) lParam;
	
	       // the sheet resizes the page whenever it is activated
	       // so we need to resize it to what we want
	       if (TCN_SELCHANGE == pnmh->code)
	           // user-defined message needs to be posted because page must
	           // be resized after TCN_SELCHANGE has been processed
	           PostMessage (WM_RESIZEPAGE);
	
	       return CPropertySheet::OnNotify(wParam, lParam, pResult);
	   }
	
	   void CMySheet::OnApplyNow()
	   {
	       // the sheet resizes the page whenever the Apply button is clicked
	       // so we need to resize it to what we want
	       PostMessage (WM_RESIZEPAGE);
	   }
	
	Additional query words: CPropertyPage size resize
	
	======================================================================
	Keywords          : kbcode kbDlg kbMFC kbPropSheet KbUIDesign kbVC kbVC400 kbVC500 kbVC600 kbGrpDSMFCATL 
	Technology        : kbAudDeveloper kbMFC
	Version           : :4.0,5.0,6.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
