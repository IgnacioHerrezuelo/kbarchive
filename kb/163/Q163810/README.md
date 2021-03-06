---
layout: page
title: "Q163810: WD97: Returning Bookmarks Sorted by Location or Alphabetically"
permalink: /kb/163/Q163810/
---

## Q163810: WD97: Returning Bookmarks Sorted by Location or Alphabetically

{% raw %}

	Article: Q163810
	Product(s): Word 97 for Windows
	Version(s): WINDOWS:97
	Operating System(s): 
	Keyword(s): kbcode kbdta kbdtacode kbmacroexample word8 kbwordvba word97
	Last Modified: 13-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Word 97 for Windows 
	-------------------------------------------------------------------------------
	
	
	SUMMARY
	=======
	
	You can return a list of bookmarks in a document sorted either alphabetically or
	by placement. Omitting or including the Range object in your command will
	determine that sort order. This article contains examples for both methods.
	
	MORE INFORMATION
	================
	
	Microsoft provides programming examples for illustration only, without warranty
	either expressed or implied, including, but not limited to, the implied
	warranties of merchantability and/or fitness for a particular purpose. This
	article assumes that you are familiar with the programming language being
	demonstrated and the tools used to create and debug procedures. Microsoft
	support professionals can help explain the functionality of a particular
	procedure, but they will not modify these examples to provide added
	functionality or construct procedures to meet your specific needs. If you have
	limited programming experience, you may want to contact a Microsoft Certified
	Partner or the Microsoft fee-based consulting line at (800) 936-5200. For more
	information about Microsoft Certified Partners, please visit the following
	Microsoft Web site:
	
	  http://www.microsoft.com/partner/referral/
	
	For more information about the support options that are available and about how
	to contact Microsoft, visit the following Microsoft Web site:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	Method 1: To Return a List of Bookmarks Sorted Alphabetically
	-------------------------------------------------------------
	
	The following macro demonstrates how to return the list of bookmarks in a
	document alphabetically. Note that, in this example, the Range object has been
	excluded from the ActiveDocument.Bookmarks command line.
	
	     Sub GetBookMarksByName()
	        Dim bmBookMark As Bookmark
	        For Each bmBookMark In ActiveDocument.Bookmarks
	           MsgBox bmBookMark.Name
	        Next
	     End Sub
	
	Method 2: To Return a List of Bookmarks Sorted by Placement
	-----------------------------------------------------------
	
	The following macro demonstrates how to return the list of bookmarks in a
	document by order of placement. Note that, in this example, the Range object is
	part of the ActiveDocument.Bookmarks command line.
	
	     Sub GetBookMarksByPlacement()
	        Dim bmBookMark As Bookmark
	        For Each bmBookMark In ActiveDocument.Range.Bookmarks
	           MsgBox bmBookMark.Name
	        Next
	     End Sub
	
	For more information about Bookmarks, from the Visual Basic Editor, click the
	Office Assistant, type "Bookmarks" (without the quotation marks), click Search,
	and then click to view "Bookmarks Collection."
	
	NOTE: If the Assistant is hidden, click the Office Assistant button on the
	Standard toolbar. If the Assistant is not able to answer your query, please see
	the following article in the Microsoft Knowledge Base:
	
	  Q176476 OFF: Office Assistant Not Answering Visual Basic Questions
	
	For additional information, please see the following article in the Microsoft
	Knowledge Base:
	
	  Q173707 OFF97: How to Run Sample Code from Knowledge Base Articles
	
	
	REFERENCES
	==========
	
	For more information about getting help with Visual Basic for Applications,
	please see the following article in the Microsoft Knowledge Base:
	
	  Q163435 VBA: Programming Resources for Visual Basic for Applications
	
	
	Additional query words: wordcon vb vba vbe
	
	======================================================================
	Keywords          : kbcode kbdta kbdtacode kbmacroexample word8 kbwordvba word97 
	Technology        : kbWordSearch kbWord97 kbWord97Search kbZNotKeyword2
	Version           : WINDOWS:97
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
