---
layout: page
title: "Q106636: FIX: Debugger Does Not Properly Trace Include Files"
permalink: /kb/106/Q106636/
---

## Q106636: FIX: Debugger Does Not Properly Trace Include Files

{% raw %}

	Article: Q106636
	Product(s): Microsoft Fortran Compiler
	Version(s): 1.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 24-MAR-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft FORTRAN PowerStation for MS-DOS, version 1.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	The debugger does not highlight the current point of execution of an include
	file containing executable statements.
	
	CAUSE
	=====
	
	The debugger does not recognize that the include file is in a different source
	window. All lines in the include file are interpreted by the debugger as being
	in the same window as the main source.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in FORTRAN PowerStation version 1.0
	for MS-DOS. This problem has been resolved with FORTRAN PowerStation maintenance
	release version 1.0a for MS-DOS.
	
	MORE INFORMATION
	================
	
	FORTRAN PowerStation version 1.0 can be differentiated from the maintenance
	release version 1.0a by invoking the linker. Typing "Link32 | more " from
	\F32\BIN directory will show version 2.8 for FORTRAN PowerStation version 1.0,
	and it will show version 1.0f for the maintenance release version 1.0a.
	
	To demonstrate the problem:
	
	1. Build the sample code with the project in debug mode.
	
	2. Open a source window for both sample code files (note that the include file
	  will not show up in the list of files associated with the project because the
	  include statement has a label).
	
	3. Single step; the current point will be line 1 of TEST.FOR.
	
	4. Single step; the highlight showing the current point will be at line 2 of
	  TEST.FOR, but the actual current point is line 12 of TEST.INC. The following
	  will be printed to the F32 Debug window:
	
	  Main Line 1
	
	5. Single step; the highlight showing the current point will be at line 3 of
	  TEST.FOR, but the actual current point is line 13 of TEST.INC. The following
	  will be printed:
	
	  Inc Line 2
	
	6. Single step; line 4 of TEST.FOR is shown, but it actually is line 14 of
	  TEST.INC. The following will be printed:
	
	  Inc Line 3
	
	7. Single step; line 5 of TEST.FOR is shown, and it actually is line 5 of
	  TEST.FOR! Both lines 4 of both TEST.INC and TEST.FOR were executed. The
	  following will be printed:
	
	  Inc Line 4
	  Main Line 4
	
	Sample Code (TEST.FOR)
	----------------------
	
	    1   print *, 'Main Line 1'
	  c 2
	    3   include 'test.inc'
	    4   print *, 'Main Line 4'
	    5   end
	
	Sample Code (TEST.INC)
	----------------------
	
	  c 11
	    12  print *, 'Inc Line 2'
	    13  print *, 'Inc Line 3'
	    14  print *, 'Inc Line 4'
	
	Additional query words: 1.00 buglist1.00 fixlist1.00a
	
	======================================================================
	Keywords          :  
	Technology        : kbAudDeveloper kbFortranSearch kbZNotKeyword3 kbFORTRANPower100DOS
	Version           : :1.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
