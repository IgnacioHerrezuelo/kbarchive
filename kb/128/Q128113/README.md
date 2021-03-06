---
layout: page
title: "Q128113: FIX: Assertion Failed Line 178 or Line 527 in ARCCORE.CPP"
permalink: /kb/128/Q128113/
---

## Q128113: FIX: Assertion Failed Line 178 or Line 527 in ARCCORE.CPP

{% raw %}

	Article: Q128113
	Product(s): Microsoft C Compiler
	Version(s): winnt:
	Operating System(s): 
	Keyword(s): kbcode kbFileIO kbMFC kbVC150bug kbVC151bug kbVC152fix kbVC210fix kbGrpDSMFCATL kbNoUpd
	Last Modified: 06-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- The Microsoft Foundation Classes (MFC), used with:
	   - Microsoft Visual C++, versions 1.5, 1.51 
	   - Microsoft Visual C++ 32-bit Edition, versions 1.0, 2.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	If a CArchive object is used with a user-defined buffer and the buffer is
	destroyed before the CArchive object has been destroyed, an assertion failure
	might occur. The message in the output window would be similar to:
	
	- Test Windows Application: File arccore.cpp, Line 178, Assertion Failed!
	
	-or-
	
	- Test Windows Application: File arccore.cpp, Line 527, Assertion Failed!
	
	This will happen even if the CArchive object has been properly closed by using
	the CArchive::Close function.
	
	CAUSE
	=====
	
	The CArchive destructor can be found in the <MSVC install>\MFC\SRC
	directory in the file ARCCORE.CPP. The function is implemented as follows:
	
	  // In 16-bit MFC:
	
	  CArchive::~CArchive()
	  {
	    ASSERT(AfxIsValidAddress(m_lpBufStart,
	       (UINT)(m_lpBufMax - m_lpBufStart)));
	    // ...
	    // ...
	  }
	
	  // In 32-bit MFC:
	
	  CArchive::~CArchive()
	  {
	    ASSERT(m_bDirectBuffer || m_lpBufStart != NULL);
	    ASSERT(m_bDirectBuffer ||
	        AfxIsValidAddress(m_lpBufStart,m_lpBufMax - m_lpBufStart,
	           IsStoring()));
	    // ...
	    // ...
	
	  }
	
	If a user-defined buffer is used for the archive (by passing it in as the lpBuf
	parameter to the CArchive constructor), it should be valid to call
	CArchive::Close on the archive, and then destroy the buffer before destroying
	the CArchive object. However, the above ASSERT will be executed when the
	CArchive object is destroyed whether the user-supplied buffer has been destroyed
	or not.
	
	If the buffer is destroyed before the CArchive object is destroyed, m_lpBufStart
	might no longer point to a valid memory address. By default it points to the
	address of the user-supplied buffer.
	
	RESOLUTION
	==========
	
	1. You can safely ignore the assertion failure. It is harmless.
	
	2. If you are using a user-supplied buffer, ensure that the CArchive object is
	  destroyed before the buffer is freed. If the CArchive object is allocated on
	  the stack, it can be allocated on the heap so that the CArchive object can be
	  destroyed before the buffer, as in this example:
	
	     char *pBuf = new char[516];
	     CFile file("C:\\TMP.DAT",CFile::modeCreate | CFile::modeWrite);
	     CArchive *pArchive = new CArchive(&file,CArchive::store,
	                                        512,pBuf);
	     // Use pArchive in here, then destroy it
	     delete pArchive;
	
	     // NOW free up the buffer
	     delete pBuf;
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article. This bug was corrected in Microsoft Visual C++ for
	Windows, version 1.52 and in Microsoft Visual C++, 32-bit Edition, version 2.1.
	
	Additional query words: 1.00 1.50 1.51 2.00 2.50 2.51 2.10 3.00 3.10 globalalloc load store
	
	======================================================================
	Keywords          : kbcode kbFileIO kbMFC kbVC150bug kbVC151bug kbVC152fix kbVC210fix kbGrpDSMFCATL kbNoUpdate 
	Technology        : kbAudDeveloper kbMFC
	Version           : winnt:
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
