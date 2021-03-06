---
layout: page
title: "Q122848: PRB: #pragma code_seg() Affects Compiler-Generated Functions"
permalink: /kb/122/Q122848/
---

## Q122848: PRB: #pragma code_seg() Affects Compiler-Generated Functions

{% raw %}

	Article: Q122848
	Product(s): Microsoft C Compiler
	Version(s): 1.0,2.0,2.1,4.0,5.0
	Operating System(s): 
	Keyword(s): kbcode kbCompiler kbCPPonly kbVC kbVC100 kbVC200 kbVC210 kbVC400 kbVC500
	Last Modified: 15-FEB-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- The C/C++ Compiler (CL.EXE), included with:
	   - Microsoft Visual C++, 32-bit Editions, versions 1.0, 2.0, 2.1, 4.0 
	   - Microsoft Visual C++, 32-bit Enterprise Edition, version 5.0 
	   - Microsoft Visual C++, 32-bit Professional Edition, version 5.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you use #pragma code_seg() in your C++ code, compiler-generated functions
	are placed in the last code segment or section that is specified with #pragma
	code_seg() instead of being placed in the default code segment or section.
	
	RESOLUTION
	==========
	
	If you want compiler generated functions to be placed in the default code
	segment, include an additional #pragma code_seg() that sets the code segment
	back to the default:
	
	     #pragma code_seg()
	
	STATUS
	======
	
	This behavior is by design.
	
	MORE INFORMATION
	================
	
	The following sample can be used to demonstrate this behavior. Compile the file
	with /DMY_SECTION, and the compiler-generated code is placed in the MY_SECTION
	section. To place the compiler-generated functions in the default code section,
	compile without MY_SECTION defined.
	
	You can determine into which section the code is placed by looking at the .COD
	listing file, generated by using the /FAsc compiler option, or the linker
	mapfile, generated by using the /MAP:filename link option.
	
	Sample Code to Demonstrate Behavior
	-----------------------------------
	
	     /* Compile options needed: /Fc /DMY_SECTION
	     */ 
	     class base
	     {
	         int i;
	     };
	
	     class Simple: virtual base    // Classes with virtual base classes are
	     {                             // non-trivial, and require constructors
	     };
	
	     #pragma code_seg("MY_SECTION")
	
	     void main()
	     {
	         Simple Simple_Class;
	     }
	
	     #ifndef MY_SECTION           // Define MY_SECTION to cause compiler
	     #pragma code_seg()           // generated code to be placed in the
	     #endif                       // MY_SECTION section.
	
	Additional query words: 8.00 9.00 pragma
	
	======================================================================
	Keywords          : kbcode kbCompiler kbCPPonly kbVC kbVC100 kbVC200 kbVC210 kbVC400 kbVC500 
	Technology        : kbVCsearch kbAudDeveloper kbCVCComp
	Version           : :1.0,2.0,2.1,4.0,5.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
