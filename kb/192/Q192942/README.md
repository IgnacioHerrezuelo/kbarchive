---
layout: page
title: "Q192942: FIX: Call to CWnd::MoveWindow Causes Stack Overflow"
permalink: /kb/192/Q192942/
---

## Q192942: FIX: Call to CWnd::MoveWindow Causes Stack Overflow

{% raw %}

	Article: Q192942
	Product(s): Microsoft C Compiler
	Version(s): winnt:6.0
	Operating System(s): 
	Keyword(s): kbole kbVC600bug kbVS600SP1fix kbMFC600bug kbVC600SP1Fix kbGrpDSMFCATL kbNoUpdate
	Last Modified: 03-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- The Microsoft Foundation Classes (MFC), used with:
	   - Microsoft Visual C++, 32-bit Enterprise Edition, version 6.0 
	   - Microsoft Visual C++, 32-bit Professional Edition, version 6.0 
	   - Microsoft Visual C++, 32-bit Learning Edition, version 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Under certain circumstances, MFC ActiveX control containers will enter a state
	of infinite recursion that eventually leads to a stack overflow. The symptoms of
	this are when the position of a control site changes, the program will seemingly
	hang and eventually produce a stack overflow (0xC00000FD) operating system
	exception. The stack trace looks like this:
	
	  COleControlSite::MoveWindow
	  COleControl::XOleInPlaceObject::SetObjectRects
	  COleControl::OnSetObjectRects
	  COleControlSite::MoveWindow
	  ...
	
	CAUSE
	=====
	
	When the position of the control site changes, the container code changes the
	position of the reflector window (if present) and the tracker rectangles (if
	present). The control container code eventually calls
	COleControl::XOleInPlaceObject::SetObjectRects. (See CTLINPLC.CPP in the MFC
	source.) SetObjectRects() makes a call to GetOuterWindow(), which returns the
	reflector window if present. If the reflector window variable is NULL then the
	same window object is returned, MoveWindow is then called using the returned
	window object. This causes MoveWindow to be called on itself, resulting in a
	recursive loop.
	
	RESOLUTION
	==========
	
	One workaround is to copy the Visual C++ 5.0 version of the MFC42.DLL (File
	version: 4.21.7303) to the home directory of the program experiencing this
	problem. This will cause the program to use the older version of MFC, instead of
	the MFC42.DLL that is located in the Windows system directory.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article. This bug has been fixed in the Visual Studio 6.0
	Service Pack 1.
	
	To obtain this service pack, please see:
	
	  http://msdn.microsoft.com/vstudio/sp/default.asp
	
	For more information on the Visual Studio 6.0 Service Pack 1, please see the
	following articles in the Microsoft Knowledge Base:
	
	  Q193009 INFO: Visual Studio 6.0 Service Pack 1 Readme
	
	  Q194022 INFO: Visual Studio 6.0 Service Packs, What, Where, Why
	
	  Q194295 HOWTO: Tell That Visual Studio 6.0 Service Packa Are Installed
	
	MORE INFORMATION
	================
	
	This bug has been found in WordPerfect 8 that ships as part of Corel Office
	Suite 8. This bug occurs only with the Visual C++ 6.0 version of the MFC42.DLL.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbole kbVC600bug kbVS600SP1fix kbMFC600bug kbVC600SP1Fix kbGrpDSMFCATL kbNoUpdate 
	Technology        : kbAudDeveloper kbMFC
	Version           : winnt:6.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
