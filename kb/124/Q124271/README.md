---
layout: page
title: "Q124271: PRB: Heap Walker's Object: USER LocalWalk Doesn't Track Data"
permalink: /kb/124/Q124271/
---

## Q124271: PRB: Heap Walker's Object: USER LocalWalk Doesn't Track Data

{% raw %}

	Article: Q124271
	Product(s): Microsoft Windows Software Development Kit
	Version(s): WINDOWS:3.1
	Operating System(s): 
	Keyword(s): kb16bitonly
	Last Modified: 06-NOV-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows Software Development Kit (SDK) 3.1 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Using the Microsoft Windows Heap Walker application (HEAPWALK.EXE), you choose
	Object:USER Localwalk(DATASEG) to do a local walk of the USER heap. After saving
	the results in a file, you open the file to discover all the count and size
	values are zero as in this example:
	
	-----------------------------------------
	OBJECT              COUNT      SIZE
	Class                   0         0
	Window                  0         0
	String                  0         0
	Menu                    0         0
	Clipbrd                 0         0
	ComboBox                0         0
	Palette                 0         0
	EditCtrl                0         0
	WindowList              0         0
	OwnerDraw               0         0
	SPB                     0         0
	CheckPoint              0         0
	DCE                     0         0
	MoveWinPos              0         0
	Properties              0         0
	ListBox                 0         0
	Misc                    0         0
	Atoms                   0         0
	LockInputState          0         0
	HookList                0         0
	UserSeeUserDo           0         0
	HotKeyList              0         0
	Handle Table            0         0
	-----------------------------------------
	
	CAUSE
	=====
	
	The Heap Walker application obtains the information for the chart by walking the
	USER module's local heap using the LocalFirst() and LocalNext() functions in the
	ToolHelp library. The entries correspond to the wType values in the LOCALENTRY
	structure of the ToolHelp library. The documentation on the LOCALENTRY structure
	in the Windows SDK Help file states that these wType values are included only in
	the debugging version of USER.EXE, not in the retail version. Therefore, because
	Heap Walker uses ToolHelp to obtain these values, no values are found in the
	retail version of Windows.
	
	RESOLUTION
	==========
	
	Switch to the Debug version of Windows, and run the Heap Walker application.
	This will produce correct results. For more information on the debugging version
	of Windows and how to switch to it, search on the phrase "Windows Debugging
	Version" in the Windows version 3.1 SDK Help file (WIN31WH.HLP) or refer to the
	topic "Windows Debugging Version" in Appendix C of the "Programming Tools for
	Windows" manual, which is part of the Visual C++ version 1.50 "Professional
	Tools User's Guide."
	
	NOTE: When you try to reproduce the same behaviour in the Heap Walker application
	for GDI heap by choosing Object:GDI LocalWalk(DATASEG), you will see that the
	table shows correct values for individual GDI objects. This is by design.
	
	
	STATUS
	======
	
	This behavior is by design.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Run the Microsoft Windows Heap Walker application (HEAPWALK.EXE) shipped with
	  the Microsoft Windows versions 3.0 and 3.1 SDK or the Visual C++ version
	  1.50.
	
	2. Choose the Object:USER Localwalk(DATASEG) menu option to do a local walk of
	  the USER heap.
	
	3. From the USER Heap(Local Walk) window, choose Heap:Save.
	
	4. Open the file created by Heap Walker (usually \WINDOWS\HWL00.TXT) with a text
	  editor, and scroll to the bottom.
	
	5. Notice that there are columns for OBJECT, COUNT, and SIZE, but all the COUNT
	  and SIZE values are zeros.
	
	Additional query words: 3.00 3.10 heapwalker no32bit
	
	======================================================================
	Keywords          : kb16bitonly 
	Technology        : kbAudDeveloper kbWin3xSearch kbSDKSearch kbWinSDKSearch kbWinSDK310
	Version           : WINDOWS:3.1
	
	=============================================================================
	

{% endraw %}
