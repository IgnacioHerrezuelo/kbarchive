---
layout: page
title: "Q80131: DOCERR: MASM 6.0 Programmer's Guide Errors: Chapters 1-6"
permalink: /kb/080/Q80131/
---

## Q80131: DOCERR: MASM 6.0 Programmer's Guide Errors: Chapters 1-6

{% raw %}

	Article: Q80131
	Product(s): Microsoft Macro Assembler
	Version(s): 6.0,6.0a,6.0b
	Operating System(s): 
	Keyword(s): 
	Last Modified: 06-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Macro Assembler (MASM), versions 6.0, 6.0a, 6.0b 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The following is a list of documentation additions and corrections for Chapters
	1 through 6 of the "Microsoft Macro Assembler Programmer's Guide" for version
	6.0. The section and page numbers are listed first, followed by a description of
	the addition or correction.
	
	MORE INFORMATION
	================
	
	Section 1.3.3, Page 35
	----------------------
	
	At the bottom of the page, the description for the .ERRDIF directive states:
	
	  ...ERRIDNI and .ERRDIFI perform the same action but are case sensitive.
	
	This is incorrect. The line should read:
	
	  ...ERRIDNI and .ERRDIFI perform the same action but are *not* case sensitive.
	
	Section 2.2.4, Page 44
	----------------------
	
	The last sentence of the second paragraph in this section should read:
	
	  These *five* directives also prevent instructions from appearing...
	
	Section 3.3.2, Page 76
	----------------------
	
	The very last line of sample code on this page is
	
	     mov     ax, BYTE PTR [bx] ; Legal
	
	which is moving an 8-bit value into a 16-bit register. This is misleading in the
	context of the example. It would make more sense as follows:
	
	     mov     al, BYTE PTR [bx] ; Legal
	
	Section 4.2.4.1, Page 100
	-------------------------
	
	The sample code at the top of this page has two comments that should be reversed.
	The comment
	
	     ; 8-bit signed multiply
	
	precedes the code that is doing *unsigned* multiplication with MUL. The comment
	should be:
	
	     ; 8-bit *unsigned* multiply
	
	The next piece of code is preceded by the comment:
	
	     ; 16-bit unsigned multiply
	
	This is incorrect. The comment should read:
	
	     ; 16-bit *signed* multiply
	
	Section 5.1.1, Page 112
	-----------------------
	
	Beneath the description of the DUP syntax, the text reads:
	
	  The count value sets the number of times to repeat the last initialvalue
	
	This is incorrect; instead, the description should be:
	
	  The count value sets the number of times to repeat the entire list
	  'initialvalue [,initialvalue]...'
	
	Section 5.1.1, Page 113
	-----------------------
	
	The second line of the sample code at the bottom of the page should be:
	
	     shl     si, 1   ; Scale for word referencing
	
	Section 5.1.2, Page 115
	-----------------------
	
	The second code example, which describes how to declare an array of pointers to
	strings, has a typographical error on the third to the last line. Instead of
	
	     pmsg2  BPBYTE  msg2
	
	it should read as follows:
	
	     pmsg2  PBYTE  msg2
	
	Section 5.1.3.1, Page 120
	-------------------------
	
	The first step of a repeat sequence is described as:
	
	1. Checks the CX register and exits if CX is 0. If the REPE prefix is used, the
	  loop exits if the zero flag is set; if REPNE is used, the loop exits if the
	  zero flag is clear.
	
	This second part of this step is incorrect. The zero flag is not checked until
	step five, at which time it will decide whether to terminate the loop.
	
	Section 5.2.2, Page 128
	-----------------------
	
	The last comment in the sample code on this page is incorrect. It states that the
	last line of code "Allocates and initializes 10 unions," when in fact it
	allocates and initializes 20 unions.
	
	Section 5.2.2, Page 128
	-----------------------
	
	The diagram on this page is misleading. It shows the 2-byte values listed
	sequentially in memory as high byte followed by low byte (for example, |0 2|0
	2|0 2|), when values are actually stored in memory as low byte followed by high
	byte (for example, |2 0|2 0|2 0|). Furthermore, the last element of this array
	is shown to be "array[18]", when the last element is supposed to be
	"array[38]".
	
	Section 5.2.3, Page 132
	-----------------------
	
	The diagram on this page is is misleading. The sample code shows a WORD value
	being loaded with the decimal value 40, but the diagram shows it stored in
	memory as:
	
	  -----------
	  | 4 0 0 0 |
	  -----------
	
	This is confusing because the element that is supposed to contain the decimal
	value 2 is shown as:
	
	  -----------
	  | 2 0 0 0 |
	  -----------
	
	It would be more understandable if the sample code loaded the two array elements
	with the hexadecimal values 40h and 2h so the four digits in the diagram
	corresponded to the four hexadecimal digits in a WORD value as follows:
	
	  -----------------------
	  | 40 00 | ... | 02 00 |
	  -----------------------
	
	Section 5.3.1, Page 136
	-----------------------
	
	The first sentence of the second paragraph is misleading. It should read:
	
	  Global labels and macro names must all be unique. Record field names must
	  also all be unique, but record field names can have the same names as
	  structure field names, macro names, or global labels.
	
	Section 5.3.2, Page 137
	-----------------------
	
	The syntax for defining record variables with the DUP operator is misleading. It
	should read:
	
	  [name] recordname constant DUP ([record_initializer
	                                  [,record_initializer]...])
	
	Section 5.3.3, Page 139
	-----------------------
	
	The sample code on this page has two errors:
	
	1. The comments show the binary arithmetic that takes place but uses an
	  incorrect operand. The numbers should resemble the following (notice the
	  first bit of the first line):
	
	         1101 1001
	     AND 1000 1111
	         ---------
	         1000 1001
	      OR 1000 0000
	         ---------
	         1000 1001
	     XOR 0000 1000
	         ---------
	         1000 0001
	
	2. The condition of the IF statement towards the bottom of the example is shown
	  as "(WIDTH color) GE 8". While this is syntactically correct, it will not do
	  what it is supposed to accomplish. The line should be:
	
	        IF  (WIDTH color) GT 8
	
	Additional query words: 6.00
	
	======================================================================
	Keywords          :  
	Technology        : kbMASMsearch kbAudDeveloper kbMASM600 kbMASM600a kbMASM600b
	Version           : :6.0,6.0a,6.0b
	
	=============================================================================
	

{% endraw %}
