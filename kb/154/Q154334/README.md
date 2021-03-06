---
layout: page
title: "Q154334: PROGRAMMING WINDOWS 95 Corrections and Comments"
permalink: /kb/154/Q154334/
---

## Q154334: PROGRAMMING WINDOWS 95 Corrections and Comments

{% raw %}

	Article: Q154334
	Product(s): Microsoft Press
	Version(s): 
	Operating System(s): 
	Keyword(s): kbdocerr
	Last Modified: 11-JAN-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- MSPRESS Programming Windows 95 ISBN 1-55615-676-6 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article contains comments, corrections, and information on known errors
	relating to the Microsoft Press book "Programming Windows 95," ISBN
	1-55615-676-6.
	
	The following topics are covered:
	
	- Page 109: add EndPaint() to WM_PAINT event handler
	
	- Page 168: typo - code doesn't match sample figure 4-23
	
	- Page 189: Second paragraph "SrcDC" should be "hdcSrc"
	
	- Page 196-197: variable xSize and ySize should be cx and cy
	
	- Page 220: First paragraph, wFormat should be iFormat
	
	- Page 409: CreateWindow uses resolution-based calculation
	
	- Page 578: pstrBuffer Malloc off by one
	
	- Page 646: CCS_ADJUSTABLE flag needed to modify toolbar
	
	- Page 651: Comment regarding FlipStyleFlag function
	
	- Page 653: Code change in ToolBarMessage()
	
	- Page 661: STATBAR.C "popstr" should be "&popstr[iMenu]"
	
	- Page 693: line 14: remove "!" from "if" statement
	
	- Page 716: Use PostMessage() instead of SendMessage()
	
	- Page 827: Fix for POPPRNT.C
	
	- Page 849: Add GMEM_DDESHARE flag to hGlobalMemory call
	
	- Page 985: Mistakenly says "SHOWBIT" instead of "Windows"
	
	MORE INFORMATION
	================
	
	In addition to a description of the book's problems, each entry in this document
	might also include sections labeled "Correction" and "Comments." Please note
	that the "Correction" section is worded for correcting the book and does not
	necessarily address the problem introduced by the book error. The "Comments"
	section contains specific information for working around the problem.
	
	Page 109: add EndPaint() to WM_PAINT event handler
	--------------------------------------------------
	
	Page 109: In the Sinewave example, figure 4.4 the EndPaint() procedure
	has been omitted.
	
	To correct the code:
	
	In the WM_PAINT event handler:
	
	Add:
	
	EndPaint(hwnd,&ps) 
	
	before:
	
	return o;
	
	
	Page 168: typo - code doesn't match sample figure 4-23
	------------------------------------------------------
	
	Page 168: mid-page, "The WM_PAINT processing is..."
	
	Typo in code:
	
	SetViewportOrg (hdc, xClient / 2, yClient / 2);
	SelectClipRgn (hdc, hRgnClip);
	
	Should match code in figure 4-23:
	
	SetViewportOrgEx (hdc, cxClient / 2, cyClient / 2, NULL);
	SelectClipRgn (hdc, hRgnClip); 
	
	
	Page 189: Second paragraph "SrcDC" should be "hdcSrc"
	-----------------------------------------------------
	
	Page 189, second paragraph, third sentence, typo:
	
	Change:
	"BitBlt also uses a rectangle in a source device context
	(whose handle is SrcDC)."
	
	To:
	"BitBlt also uses a rectangle in a source device context
	(whose handle is hdcSrc)."
	
	
	Page 196-197: variable xSize and ySize should be cx and cy
	----------------------------------------------------------
	
	Pages 196-197:
	
	The variables xSize and ySize should read cx and cy to match
	the code in figure 4-26. 
	
	
	Page 220, first paragraph, wFormat should be iFormat
	----------------------------------------------------
	Page 220, first paragraph, third sentence:
	
	Change:
	"...in which case the upper byte of wFormat contains the
	charater-position number of each new tab stop."
	
	To:
	"...in which case the upper byte of iFormat contains the
	character-position number of each new tab stop."
	
	
	Page 409: CreateWindow uses resolution-based calculation
	---------------------------------------------------------
	
	On page 409 the CreateWindow call uses the calculation tm.tmAveCharWidth *
	MAXENV. On high-resolution displays (1280 x 1024), the result of this
	calculation is a value so large that it overflows the 16-bit limits of Win
	95 GDI, and no environment information is displayed on the screen.
	
	Comments:
	
	Changing this value instead to use GetSystemMetrics (SM_CXSCREEN) creates a
	window the width of the screen (clipped to the size of the parent window);
	if you want to be more exact, you could use the sys metrics value in a
	min(...) calculation with the original calculation.
	
	Page 578: pstrBuffer Malloc off by one
	--------------------------------------
	
	The call to malloc at the bottom of the page, ...pstrBuffer = (PSTR)
	malloc (iLength)..., is off by one; it should be (iLength + 1).
	
	Without the +1 you will eventually fault when the trailing NULL is added
	(at the top of page 579). A fault will occur if you load a file whose  size
	is an exact multiple of malloc's granularity.
	
	Correction:
	
	Page 578, line 3 from bottom:
	Change  "malloc (iLength)" to "malloc (iLength + 1)"
	
	Page 646:  CCS_ADJUSTABLE flag needed to modify toolbar
	-------------------------------------------------------
	
	The dwToolBarStyles variable at the bottom of the page needs the
	CCS_ADJUSTABLE flag. Without this flag you cannot perform direct
	manipulation of toolbar elements or double-click to customize the toolbar
	as discussed on pages 624 through 625.
	
	Correction:
	Page 646, line 5 from bottom:
	Change ";" to "|" and add one line below (with proper alignment with
	line 5 from bottom:
	    CCS_ADJUSTABLE ;
	
	Page 651:  Comment regarding FlipStyleFlag function
	---------------------------------------------------
	
	The function FlipStyleFlag() uses a pointer to a DWORD (so it can change
	and return the value) to toggle a bit in that DWORD based on a flag bit (or
	bits). This function can be replaced by the following single line using the
	XOR assignment operator:
	  dwStyle ^= flag;
	
	This line can be placed in a macro if you prefer having a name to better
	explain what is going on. If you want to quickly update FlipStyleFlag()
	without additional changes, replace the function body with:
	  *dwStyle ^= flag;
	
	Note: If flag contains more than one bit and dwStyle has some of these bits
	set and others cleared, the XOR solution will behave a little differently
	from the FlipStyleFlag function; XOR will toggle each bit independently,
	whereas FlipStyleFlag will turn them all off (or on) the first time and
	then toggle them in sync from then on.
	
	FlipStyleFlag appears in other example code as well, including STATBAR.C
	on page 658 and PROPERTY.C on page 693, and should be interchangeable with
	the XOR example above.
	
	Correction:
	
	Page 651: Replace lines 10 through 18 (entire FlipStyleFlag function
	body) with:
	    // XOR dwStyle with flag and store in dwStyle
	    *dwStyle ^= flag;
	    // Note: XOR toggles each bit in dwStyle that
	    //       has a 1 in the corresponding flag.
	
	Page 658: Change FlipStyleFlag() function as noted above
	Page 693: Change FlipFlag() function as noted above
	
	Page 653: Code change in ToolBarMessage()
	-----------------------------------------
	
	Page 653: 
	The code for each case statement in ToolBarMessage() needs to be
	changed to refer to the actual name rather than the index number.
	The sample code is written to refer to the first index as 1. 
	
	Change:
	  case IDM_TB_CHECK :
	  {
	    int nState = ToolBar_GetState (hwndTB, 1);
	    BOOL bCheck = (!(nState & TBSTATE_CHECKED)) ;
	    ToolBar_CheckButton (hwndTB, 1, bCheck ) ;
	    break ;
	  }
	
	To:
	
	  case IDM_TB_CHECK :
	  {
	    int nState = ToolBar_GetState (hwndTB, IDM_FILE_NEW) ;
	    BOOL bCheck = (!(nState & TBSTATE_CHECKED)) ;
	    ToolBar_CheckButton (hwndTB,IDM_FILE_NEW,bCheck);
	    break ;
	  }
	
	This change needs to be made to each case statement that references
	an index number. 
	
	
	Page 661:  STATBAR.C  "popstr" should be "&popstr[iMenu]"
	---------------------------------------------------------
	Page 661, line 14:
	Change "popstr" to "&popstr[iMenu]"
	(STATBAR.C on CD-ROM is correct)
	
	Page 693:  line 14: remove "!" from "if" statement
	--------------------------------------------------
	Page 693, line 14:
	Change:
	if ((hwndModeless) && (!(PropSheet_IsDialogMessage (hwndModeless,
	&msg))))
	To:
	if ((hwndModeless) && ((PropSheet_IsDialogMessage (hwndModeless,
	&msg))))
	
	Comments:
	The error is the "!" just before the PropSheet_IsDialogMessage code. When
	the "!" is present, the net result is either to send all msgs to the main
	window when there is not a modeless prop sheet (correct), or else to skip
	all msgs not handled by the property sheet while passing all property sheet
	msgs back to the main window (which is exactly the opposite of what you
	want to do).
	
	Page 716: Use PostMessage() instead of SendMessage()
	-----------------------------------------------------
	Although the code on page 716 works, the paragraph directly above suggests
	using PostMessage to avoid timing problems.
	
	Correction:
	Page 716, last line of code:
	Change "SendMessage" to "PostMessage"
	
	Page 827: Fix for POPPRNT.C
	----------------------------
	The code in POPPRNT.C improperly initializes the Print common dialog.
	
	Correction:
	POPPRNT.C, Page 827, lines 5 through 8:
	Change:
	      pd.nFromPage  = 0 ;
	      pd.nToPage    = 0 ;
	      pd.nMinPage   = 0 ;
	      pd.nMaxPage   = 0 ;
	
	To:
	      pd.nFromPage  = 1 ;
	      pd.nToPage    = 0xFFFF ;
	      pd.nMinPage   = 1 ;
	      pd.nMaxPage   = 0xFFFF ;
	
	Page 849:  Add GMEM_DDESHARE flag to hGlobalMemory call
	-------------------------------------------------------
	According to the SetClipboardData function description in the Microsoft
	Visual C++ Books Online, DDE memory should be GlobalAlloc'ed using
	GMEM_MOVEABLE and GMEM_DDESHARE flags. However, the sample code uses the
	GHND flag, which is defined in WINBASE.H as (GMEM_MOVEABLE |
	GMEM_ZEROINIT). GHND does not have the GMEM_DDESHARE flag.
	
	Correction:
	Page 849, first line of code:
	Change:
	hGlobalMemory = GlobalAlloc (GHND, iLength + 1) ;
	To:
	hGlobalMemory = GlobalAlloc (GHND | GMEM_DDESHARE, iLength + 1) ;
	
	Page 985: Mistakenly says "SHOWBIT" instead of "Windows"
	--------------------------------------------------------
	On page 985, the second sentence below the SHOWBIT.C program listing
	mistakenly says "SHOWBIT will search for it" when it should say "Windows
	will search for it".
	
	Microsoft Press is committed to providing informative and accurate books. All
	comments and corrections listed above are ready for inclusion in future
	printings of this book. If you have a later printing of this book, it may
	already contain most or all of the above corrections.
	
	Additional query words: mspress ms_press press bookbug
	
	======================================================================
	Keywords          : kbdocerr 
	Technology        : kbMSPressSearch
	Version           : :
	
	=============================================================================
	

{% endraw %}
