---
layout: page
title: "Q132344: FIX: App Terminates Unexpectedly after Windows NT 3.51 Upgrade"
permalink: /kb/132/Q132344/
---

## Q132344: FIX: App Terminates Unexpectedly after Windows NT 3.51 Upgrade

{% raw %}

	Article: Q132344
	Product(s): Microsoft C Compiler
	Version(s): winnt:
	Operating System(s): 
	Keyword(s): kberrmsg kbCRT kbVC kbfix
	Last Modified: 30-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- The C Run-Time (CRT), included with:
	   - *EDITOR Please do not choose this product*Microsoft Visual C++ 32-bit Edition* use 241, 265, 225, versions 1.0, 2.0, 2.1, 2.2 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	After you upgrade to Windows NT version 3.51, malloc or other run-time memory
	allocation functions may fail when unable to grow the run-time library's heap.
	
	Windows applications that are statically linked to the C run-time library and all
	console applications issue the error, "R6018 - Unexpected heap error," and
	terminate.
	
	Windows-based applications which are linked to the DLL version of the C run- time
	library, and MFC applications will unexpectedly terminate with no error message.
	This termination may be preceded by a message saying that the system is low on
	resources and to close down some applications.
	
	CAUSE
	=====
	
	This problem is caused by a change in the return code from the VirtualAlloc()
	function. It formerly returned ERROR_NOT_ENOUGH_MEMORY when it could not commit
	pages. Now it returns ERROR_COMMITMENT_LIMIT. The problem occurs only on Windows
	NT version 3.51 and only when the application hits its commit limit as chosen by
	Windows NT. This limit varies depending on such things as the size of the
	installed memory and the number of applications running. The sample code listed
	in this article causes the R6018 error when run on Windows NT version 3.51 but
	runs to completion under previous versions of Windows NT.
	
	
	RESOLUTION
	==========
	
	The C Run-Time heap manager was changed in Visual C++ 4.0 to no longer use
	VirtualAlloc(). Visual C++ version 4.0 correctly handles the
	ERROR_COMMITMENT_LIMIT case.
	
	This problem can be worked-around in Visual C++ 2.X by allocating large blocks of
	memory using Win32 memory allocation APIs.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem when using malloc on Windows NT
	version 3.51. This problem was corrected in Visual C++, 32-bit edition, version
	4.0.
	
	MORE INFORMATION
	================
	
	Sample Code to Reproduce Problem
	--------------------------------
	
	  /* Compile options needed: none
	  */ 
	
	  #include <stdlib.h>
	  void main()
	  {
	      void * p = malloc( 1024*1024*1024 ); // try to allocate 1GB
	      if( p )
	      {
	          printf( "malloc returned non-NULL\r\n");
	          free(p);
	      }
	      else
	          printf( "malloc returned NULL\r\n");
	  }
	
	Additional query words: 1.00 2.00 2.10 2.20 fatal error die shut down disappear
	
	======================================================================
	Keywords          : kberrmsg kbCRT kbVC kbfix 
	Technology        : kbVCsearch kbAudDeveloper kbCRT
	Version           : winnt:
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
