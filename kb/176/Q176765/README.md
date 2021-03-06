---
layout: page
title: "Q176765: BUG: Placing Icons in Picture Object Causes Memory Leak"
permalink: /kb/176/Q176765/
---

## Q176765: BUG: Placing Icons in Picture Object Causes Memory Leak

{% raw %}

	Article: Q176765
	Product(s): Microsoft FoxPro
	Version(s): 3.0b,5.0,5.0a,6.0
	Operating System(s): 
	Keyword(s): kbvfp kbvfp300 kbvfp500 kbvfp500a kbGrpDSFox
	Last Modified: 22-OCT-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, versions 3.0b, 5.0, 5.0a, 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	A program that loads a series of icon files into the Picture property of a
	Visual FoxPro image object causes a memory leak in Visual FoxPro 3.0b, 5.0x, and
	6.0. Eventually, the operating system becomes unstable and the computer locks.
	
	CAUSE
	=====
	
	Loading the icon files may create a leak in process memory. As the program runs,
	increasing amounts of RAM are consumed. When the program starts using virtual
	memory, performance suffers and the computer may lock.
	
	RESOLUTION
	==========
	
	Currently, there is no resolution, but following are two workarounds:
	
	- Use a bitmap instead of an icon file to display an image in the Picture
	  property.
	
	-or-
	
	- Use an OLE container control that contains the Visual FoxPro HWND .ocx
	  control to display the icon.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	WARNING: Running the code below causes a low memory situation on the computer.
	This condition may cause the operating system to become unstable. Close all open
	applications and save your data before using this procedure. In Microsoft
	Windows 95 and Microsoft Windows NT, press the CTRL+ALT+DEL keys simultaneously
	to invoke the Close Dialog window or the Task Manager, respectively.
	
	Create and run a program that contains the following code:
	
	     LOCAL ARRAY laIcons[1,1]
	     LOCAL loForm, lnI, lnFile, lnFiles
	
	     loForm = CREATEOBJECT('Form')
	     loForm.HEIGHT = 600
	     loForm.WIDTH = 200
	
	     FOR lnI = 1 TO 10
	     loForm.ADDOBJECT('imgObject' + ALLTRIM(STR(lnI)), 'Image')
	     WITH loForm.CONTROLS[lnI]
	     .LEFT    = 10
	     .TOP     = 10 + (lnI ) * 50
	     .WIDTH   = 25
	     .HEIGHT  = 25
	     .VISIBLE = .T.
	     ENDWITH
	     ENDFOR
	
	     loForm.ADDOBJECT('lblCounter', 'Label')
	     loForm.lblCounter.TOP      = 1
	     loForm.lblCounter.LEFT     = 1
	     loForm.lblCounter.AUTOSIZE = .T.
	     loForm.lblCounter.VISIBLE  = .T.
	     loForm.SHOW()
	     lnFiles = ADIR(laIcons, HOME() ;
	     + 'SAMPLES\GRAPHICS\ICONS\COMPUTER\*.ICO')
	
	     FOR lnI = 1 TO 1000
	     loForm.lblCounter.CAPTION = 'Loop :' + PADL(lnI, 4)
	     FOR lnFile = 1 TO lnFiles - 10
	     loForm.CONTROLS[ 1].PICTURE = ;
	     HOME() + 'SAMPLES\GRAPHICS\ICONS\COMPUTER\' + laIcons[lnFile , 1]
	     loForm.CONTROLS[ 2].PICTURE = ;
	     HOME() + 'SAMPLES\GRAPHICS\ICONS\COMPUTER\' + laIcons[lnFile+1, 1]
	     loForm.CONTROLS[ 3].PICTURE = ;
	     HOME() + 'SAMPLES\GRAPHICS\ICONS\COMPUTER\'+ laIcons[lnFile+2, 1]
	     loForm.CONTROLS[ 4].PICTURE = ;
	     HOME() + 'SAMPLES\GRAPHICS\ICONS\COMPUTER\'+laIcons[lnFile + 3, 1]
	     loForm.CONTROLS[ 5].PICTURE = ;
	     HOME() + 'SAMPLES\GRAPHICS\ICONS\COMPUTER\'+laIcons[lnFile + 4, 1]
	     loForm.CONTROLS[ 6].PICTURE = ;
	     HOME() + 'SAMPLES\GRAPHICS\ICONS\COMPUTER\'+laIcons[lnFile + 5, 1]
	     loForm.CONTROLS[ 7].PICTURE = ;
	     HOME() + 'SAMPLES\GRAPHICS\ICONS\COMPUTER\'+laIcons[lnFile + 6, 1]
	     loForm.CONTROLS[ 8].PICTURE = ;
	     HOME() + 'SAMPLES\GRAPHICS\ICONS\COMPUTER\' + laIcons[lnFile+7, 1]
	     loForm.CONTROLS[ 9].PICTURE = ;
	     HOME()+'SAMPLES\GRAPHICS\ICONS\COMPUTER\' + laIcons[lnFile + 8, 1]
	     loForm.CONTROLS[10].PICTURE = ;
	     HOME()+'SAMPLES\GRAPHICS\ICONS\COMPUTER\' + laIcons[lnFile + 9, 1]
	     IF INKEY(0.001, 'HM') = 27
	     CANCEL
	     ENDIF
	     ENDFOR
	     ENDFOR
	
	The first indication of a memory problem appears when the icons no longer appear
	in the individual image objects. The number of iterations before this symptom
	appears depends on the amount of physical RAM installed on the computer. Once
	the memory leak consumes all the physical RAM, Visual FoxPro begins using
	virtual memory. At this point, performance suffers greatly and the operating
	system may lock.
	
	REFERENCES
	==========
	
	Visual FoxPro Help 3.0b, 5.0, 5.0a; search on: Visual FoxPro HWND Control
	
	Additional query words:
	
	======================================================================
	Keywords          : kbvfp kbvfp300 kbvfp500 kbvfp500a kbGrpDSFox 
	Technology        : kbVFPsearch kbAudDeveloper kbVFP300b kbVFP500 kbVFP600 kbVFP500a
	Version           : :3.0b,5.0,5.0a,6.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
