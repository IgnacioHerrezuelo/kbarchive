---
layout: page
title: "Q43008: Debug Does Not Display Changes Made by _dos_setvect()"
permalink: /kb/043/Q43008/
---

## Q43008: Debug Does Not Display Changes Made by _dos_setvect()

{% raw %}

	Article: Q43008
	Product(s): See article
	Version(s): 2.00
	Operating System(s): MS-DOS
	Keyword(s): ENDUSER | buglist2.00 | mspl13_c
	Last Modified: 2-MAY-1989
	
	The QuickC Version 2.00 debug window will not update the display of an
	entry in the interrupt vector table after _dos_setvect is used to
	change that entry. The program below will reproduce the problem.
	
	To demonstrate the problem, do the following:
	
	1. Start QuickC.
	
	2. Load the program below.
	
	3. Open the debug window and set watches on the following:
	
	    hptr
	    saveint
	    ptr
	    *ptr (use hex format)
	    lp (use hex format)
	
	Use the F8 key to step into the program. Saveint contains the address
	of the old interrupt handler. Hptr contains the address of the new
	interrupt handler. Ptr points to the interrupt vector, thus *ptr shows
	the address of the interrupt handler and should be different after the
	call to _dos_setvect. However, it is not. Notice that lp does contain
	the correct address, demonstrating that internally all addresses are
	being held correctly. The watch window is simply not displaying the
	altered interrupt vector properly.
	
	The following sample program will demonstrate the problem:
	
	#include <stdio.h>
	#include <dos.h>
	#define THE_INT 0x12
	
	void interrupt far handler() ;
	
	void (interrupt far *hptr)() ;
	void (interrupt far *saveint)() ;
	long far* ptr ;
	unsigned long lp ;
	
	void main ( void )
	{
	hptr = handler ;
	saveint = _dos_getvect ( THE_INT ) ;
	
	FP_SEG ( ptr ) = 0 ;
	FP_OFF ( ptr ) = 0x48 ;    /* make ptr point to where the interrupt
	                            * THE_INT is in interrupt vector table
	                            */
	
	/* following will do the same thing by searching for the address
	 * rather than setting ptr directly:
	 */
	FP_SEG ( ptr ) = 0 ;
	FP_OFF ( ptr ) = 0 ;
	while (*ptr++ != (long) saveint) ;
	ptr -- ;
	*/
	
	_dos_setvect ( THE_INT, hptr ) ;   /* set to new handler */
	lp = *ptr ;
	
	_dos_setvect ( THE_INT, saveint ) ; /* reset handler */
	}
	
	void interrupt far handler()
	{
	}

{% endraw %}
